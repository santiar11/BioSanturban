# BioSanturbán

Monitoreo de biodiversidad en el Páramo de Santurbán. Proyecto de Ingeniería del Software II, Universidad Industrial de Santander (2026).
Equipo: Santiago Ardila, Jean Lucas Nova, Jaider Quintero y Álvaro Martínez.

| Ruta | Contenido |
|---|---|
| `/` | Página de inicio con los enlaces y la descarga de la APK |
| `/app/` | App de campo instalable (usa la cámara, el GPS, la batería y la conexión reales del teléfono) |
| `/prototipo/` | Prototipo completo: app de campo y plataforma institucional, con condiciones de campo simuladas |
| `/presentacion/` | Diapositivas (flechas del teclado, clic o deslizar). El QR de la última diapositiva apunta a la página de inicio |
| `/descargas/` | Aquí va `BioSanturban.apk` |

Es un sitio estático: no necesita compilación ni dependencias.

## 1. Subir a GitHub
1. En github.com crea un repositorio nuevo, por ejemplo `biosanturban` (público o privado).
2. En el repositorio vacío elige **Add file → Upload files** y arrastra **el contenido** de esta carpeta (no la carpeta misma).
3. Pulsa **Commit changes**.

## 2. Publicar en Vercel
1. Entra a vercel.com con tu cuenta de GitHub y elige **Add New… → Project**.
2. Importa el repositorio `biosanturban`.
3. En *Framework Preset* deja **Other**, sin comando de compilación ni carpeta de salida. Pulsa **Deploy**.
4. Vercel te da una dirección como `https://biosanturban.vercel.app` (si el nombre está ocupado, será otra; el QR de la presentación se ajusta solo).

Cada vez que subas un cambio al repositorio, Vercel publica la nueva versión automáticamente.

## 3. Generar la APK con PWABuilder (sin Android Studio)
1. Abre https://www.pwabuilder.com y pega la dirección de la app: `https://TU-DOMINIO/app/`.
2. Pulsa **Package For Stores → Android → Generate Package**. En las opciones:
   - *Package ID*: `co.edu.uis.biosanturban`
   - *App name*: `BioSanturbán Campo`
   - Activa **Location delegation** (para que la app use el GPS).
   - *Signing key*: **Create new**. Guarda bien el archivo de firma y sus contraseñas: se necesitan para publicar actualizaciones.
3. Descarga el `.zip`. Adentro vienen un archivo `.apk` (para instalar directamente), un `.aab` (solo para Google Play) y `assetlinks.json`.
4. En el repositorio:
   - Sube el `.apk` a la carpeta `descargas/` con el nombre **`BioSanturban.apk`**.
   - Crea la carpeta `.well-known` en la raíz y sube ahí `assetlinks.json`. Con este archivo la app abre a pantalla completa, sin la barra del navegador.
5. Vercel vuelve a publicar solo. En la página de inicio se activará el botón **Descargar APK**.

## 4. Instalar en el teléfono
1. Escanea el QR de la última diapositiva o abre la página de inicio en el celular.
2. Pulsa **Descargar APK** y abre el archivo.
3. Si Android lo pide, permite **instalar apps de origen desconocido** para el navegador.
4. Al abrir la app, acepta los permisos de **ubicación** y **cámara**.

## Qué hace y qué no hace la versión del teléfono
- Usa la cámara real para las fotos y el GPS real para la ubicación, la altitud y el recorrido.
- Detecta si hay conexión y la batería real del teléfono.
- Funciona sin internet después de abrirla una vez (mapa descargado y catálogo incluidos).
- Los registros se guardan en el teléfono. La sincronización es una demostración dentro del mismo teléfono: todavía no hay un servidor real, así que lo que registres no aparece en la plataforma de otro equipo.
- El recorrido se registra mientras la app está abierta; con la pantalla apagada se pausa.
- En esta versión de prueba, las cuentas nuevas quedan activas de inmediato (en el prototipo completo las aprueba el administrador).

Cuentas de demostración: `lmartinez`, `jrojas`, `dpabon`, `admin`. Contraseña: `santurban`.

## Créditos de las fotografías
Las fotos de especies, daños y paisajes son de sus autores, en su mayoría de Wikimedia Commons con licencias libres; el detalle está en `creditos.txt` y en la pantalla de créditos de la app.
