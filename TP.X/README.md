# Monitor PIC16F887 — LDR & PWM

Aplicación web (HTML + CSS + JavaScript vanilla) para comunicarse con un PIC16F887 mediante **Web Serial API**.

## Requisitos

- Navegador **Google Chrome** o **Microsoft Edge** (Web Serial API).
- Servidor local (la Web Serial API requiere un contexto seguro: `http://localhost` funciona).

## Cómo ejecutar

1. Abre la carpeta del proyecto en Visual Studio Code.
2. Instala la extensión **"Live Server"** (o cualquier servidor estático).
3. Click derecho en `index.html` → **"Open with Live Server"**.
   - Alternativa con Python: `python -m http.server 8000` y abrir `http://localhost:8000`.
4. En la página, presiona **"Conectar"**, selecciona el puerto COM del PIC y elige 9600 baudios.

## Protocolo UART

- **PIC → PC**: tramas `L123\r\n` donde `123` es el valor ADC (000-255).
- **PC → PIC**: 2 caracteres ASCII con el porcentaje de PWM (`00`-`99`), sin saltos de línea.

## Archivos

- `index.html` — Estructura de la interfaz.
- `style.css` — Estilos (tema oscuro, responsive).
- `script.js` — Lógica: Web Serial API, parsing UART, Chart.js, tabla, CSV.

## Calibración Lux

La función `convertAdcToLux()` en `script.js` actualmente usa `lux = ADC` como placeholder.
Reemplázala con tu ecuación de calibración experimental cuando la tengas.
