# Despliegue de una aplicación híbrida en Android

1. Instalar dependencias:
    ```bash
    npm install @capacitor/android
    npm install @capacitor/assets --save-dev
    ```

2. Generar carpeta android:
    ```bash
    npx cap add android
    ```

3. Establecer `icon-only.png`, `icon-foreground.png`, `icon-background.png`, `splash.png`, `splash-dark.png` en la carpeta [`.\assets`](./assets).

4. Generar los recursos nativos:
    ```bash
    npx capacitor-assets generate
    ```

5. Añadir a [`.\android\app\src\main\AndroidManifest.xml`](.\android\app\src\main\AndroidManifest.xml):
    ```xml
    <uses-feature android:name="android.hardware.camera" android:required="false" />
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.INTERNET" />
    ```

6. Modificar el final de [`.\android\app\src\main\res\values\styles.xml`](.\android\app\src\main\res\values\styles.xml):
    ```xml
    <style name="AppTheme.NoActionBarLaunch" parent="AppTheme.NoActionBar">
        <item name="android:windowBackground">@color/nuevocolorfondo</item>
    </style>
    ```

7. Crear [`.\android\app\src\main\res\values\colors.xml`](.\android\app\src\main\res\values\colors.xml):
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <resources>
      <color name="nuevocolorfondo">#ffffff</color>
    </resources>
    ```

8. Crear [`.\android\app\src\main\res\values-night\colors.xml`](.\android\app\src\main\res\values-night\colors.xml):
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <resources>
      <color name="nuevocolorfondo">#121212</color>
    </resources>
    ```

9. Añadir en [`.\android\app\src\main\res\layout\activity_main.xml`](.\android\app\src\main\res\layout\activity_main.xml) en los apartados `androidx.coordinatorlayout.widget.CoordinatorLayout` y `WebView`:
    ```xml
    android:background="@color/nuevocolorfondo"
    ```

10. Modificar [`.\android\app\src\main\res\values\strings.xml`](.\android\app\src\main\res\values\strings.xml):
    ```xml
    <string name="app_name">Incidencias</string>
    <string name="title_activity_main">Incidencias</string>
    ```

11. Construir la aplicación, sincronizar los activos y abrir el proyecto en Android Studio:
    ```bash
    npx ionic build --prod
    npx cap sync android
    npx cap copy android
    npx cap open android
    ```

12. Generar APK: Build > Generate Signed App Bundle or APK... > APK > Rellenar ambas contraseñas > release > Create
