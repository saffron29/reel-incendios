# Revisión del guion generado con IA · Sesión 15

**Autor:** Frank Pinares Gutiérrez
**Documento fuente:** `informe.pdf` (README de `incendios-record`, «¿Es 2026 un año récord de incendios en el Perú?», 12 páginas, 4,144 palabras)
**Modelo que escribió el guion:** Claude (vía Claude Code), con el prompt de `guion.py --solo-prompt`
**Guion sin corregir:** `guion_claude_original.json` · **Guion corregido:** `guion.json` (campo `revisado_a_mano`)

## Verificación automática

`guion.py` marcó las 6 cifras como `ok` (`20 oct 2026`, `12 de 15`, `+34 %`, `12 953`, `9` y una escena sin cifra), y
no encontró cifras dudosas en los posts. Aun así, la lectura contra la fuente encontró tres afirmaciones del guion y tres
de los posts que no eran fieles al informe.

## Correcciones al guion

| Escena | El modelo escribió | El informe dice | Corrección y motivo |
|---|---|---|---|
| 2 | «por debajo del **promedio histórico**» | «0,81 veces el promedio del periodo **2012–2025**» | «del promedio de los catorce años previos». La comparación es con 14 años de VIIRS S-NPP, no con toda la historia. La etiqueta «Puesto nacional de 2026 en focos» no decía entre qué años era el puesto 12 de 15: pasó a «Ranking nacional de focos, 2012–2026». |
| 5 | «El récord **llegó tarde** y en la sierra, no en la Amazonía» | «el récord de 2026 **sería** tardío y concentrado en la sierra, y no en la Amazonía»; el déficit amazónico «podría deberse en parte a la nubosidad» | «El récord sería tardío y concentrado en la sierra». El modelo convirtió una inferencia prudente en un hecho. |
| 6 | «Mira el tablero completo: **el enlace está en mi perfil**» | El tablero «puede abrirse directamente en el navegador o publicarse a través de GitHub Pages» | El tablero no está publicado (`https://saffron29.github.io/incendios-record/` responde 404): la frase prometía un enlace inexistente. Se cambió por una invitación a comentar: «¿Cómo se vive la temporada de incendios en tu región?». |

## Correcciones a los posts

| Post | El modelo escribió | Corrección y motivo |
|---|---|---|
| LinkedIn | «El récord **es** tardío y está concentrado en la sierra» | «sería tardío y concentrado», como dice el informe. |
| X | «Arequipa (+34 %) y Lima (+32 %) baten su récord» | «superan su récord previo (+34 % y +32 %)». Sin la referencia podía leerse como alza frente al promedio, y frente al promedio Arequipa está en ×2. |
| Facebook | «Mira el tablero completo: el enlace está en mi perfil» | Se eliminó: el tablero no está publicado. |

## Lo que no se cambió, y por qué

- **Escena 3** («Arequipa y Lima sí baten su récord… treinta y cuatro por ciento más focos que su máximo anterior»): el informe dice que ambos superan su máximo bajo las cuatro medidas, y que Arequipa tiene 962 focos frente a 718 (2013), un 34 % más.
- **Escena 4** («en veinte días hubo doce mil novecientos cincuenta y tres focos, el récord de la serie»): del 1 al 20 de octubre hubo 12 953 focos, «los más intensos de toda la serie», por encima de 2020 (12 712). El modelo **no** confundió esta cifra con la del monitor del profesor (12 984 focos, +126 %, del 1 al 16 de octubre), que también aparece en el informe.
- **Escena 1**: la fecha de corte (20 de octubre de 2026) es el último día completo de INPE que usa el informe.

## Lección

Los números se verifican con código; las afirmaciones las verifica una persona. Los tres errores tenían cifras
correctas: dos exageraban la certeza o el alcance de una afirmación («histórico», «llegó tarde») y uno prometía algo que
no existe (el enlace al tablero).

## Producción del reel

| Requisito | Resultado |
|---|---|
| Duración | 49.2 s (6 escenas, 135 palabras) |
| Resolución, fotogramas y códecs | 1080 × 1920, 30 fps, H.264 + AAC 48 kHz |
| Sonoridad | −14.6 LUFS integrados, picos en −1.4 dBFS (normalización `loudnorm` en dos pasadas) |
| Voz | Qwen3-TTS-12Hz-0.6B-Base en CPU, con 20 s de referencia recortados de una grabación de 89 s |
| Control con Whisper (WER por escena) | 0.00 · 0.04 · 0.00 · 0.00 · 0.14 · 0.04: ninguna superó 0.25, no se regeneró ninguna escena |
| Subtítulos | 135 palabras con tiempo, en `reel.srt` y dentro del video |
| Aviso de IA | «VOZ GENERADA CON IA» en todo el video y al final de los tres posts |
| Tiempo total | 519 s (8.7 min) en un Intel i5-8250U sin GPU |
