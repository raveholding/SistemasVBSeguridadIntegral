# Sistemas VB Seguridad Integral — Lista para salir al mercado

Estado al 3/11/2026 · versión 2.2.0

## Listo en esta versión

- [x] Producto genérico: sin datos de clientes, logo e íconos propios, valores de fábrica neutros.
- [x] **Cámaras y grabadores de cualquier marca con un botón**: búsqueda en la red (ONVIF, ARP, puertos) → Agregar con usuario y clave → el sistema trae marca, modelo, canales, dirección de video exacta y PTZ (ONVIF). Alta por marca sin ONVIF y por dirección RTSP.
- [x] Varios equipos a la vez (además del grabador Dahua por número de serie), canales con nombre, habilitar/deshabilitar, PTZ por ONVIF.
- [x] **Asistente de instalación** de 6 pasos al primer ingreso (obliga a cambiar los PINs de fábrica).
- [x] **Pantalla que se adapta al dispositivo**: tablet de pared, celular, PC y monitor de cámaras.
- [x] **Periféricos detectados**: cámaras, micrófonos, parlante, USB serie, NFC, huella, voz, pantalla táctil, lector QR.
- [x] **Video portero:** el visitante llama desde su celular y el panel lo ve en vivo, con foto de respaldo en el aviso y opción de hablarle.
- [x] Teclado de PC en todos los PINs (incluido el numérico).
- [x] Revisión de seguridad con 11 correcciones (ver `docs/SEGURIDAD.md`).
- [x] 240 pruebas automáticas (34 del servidor + 206 en navegador).

## Falta para el lanzamiento comercial

| Prioridad | Tarea | Por qué |
|---|---|---|
| 1 | **Acceso remoto simple** (relé o túnel de Vincular; el dueño escanea un QR) | Hoy se usa Tailscale; para el público general tiene que ser tan simple como DMSS con el número de serie. |
| 1 | **Servidor ntfy propio** de Vincular | ntfy.sh público no garantiza el servicio para muchos clientes. |
| 1 | **Seguridad P1** (ver `docs/SEGURIDAD.md`): cerradura con desafío-respuesta, un dominio por cliente, PINs de respaldo con hash | Lo más grave de lo pendiente. |
| 1 | **Pruebas de campo** con equipos reales: XVR y cámara IP Dahua, NVR Hikvision, cámara ONVIF genérica; 7 días seguidos con cortes provocados de WiFi, internet y luz | Validar ONVIF y RTSP reales, estabilidad y reconexión. |
| 2 | Porteros con video Dahua (VTO): timbre, atender, abrir | Completar la compatibilidad que ofrece DMSS. |
| 2 | Eventos de Hikvision (ISAPI alertStream) | Hoy Hikvision entra con video y PTZ, sin eventos inteligentes. |
| 2 | Centrales de alarma y control de acceso (Dahua y genéricos por contacto seco/ESP32) | Armar/desarmar y recibir alarmas desde el panel. |
| 2 | WhatsApp Business API oficial (opcional por cliente) | CallMeBot es para uso personal. |
| 3 | Imagen lista para enchufar (mini-PC / Raspberry Pi 5) con actualización automática | "Caja VB": el cliente solo la conecta al router. |
| 3 | Kit, precios, manual del dueño, términos de servicio y política de privacidad | Venta como producto cerrado. |
| 3 | Cartel de videovigilancia y modelo de manual de tratamiento de datos (AAIP, Disposición 10/2015) incluidos en el sistema | Cada cliente debe declarar la base y señalizar; el sistema le da los modelos. |

## Pruebas antes de cada versión

```bash
cd server && npm run setup && npm test
python3 tests/e2e.py && python3 tests/e2e_plataforma.py && python3 tests/e2e_instalacion.py && python3 tests/e2e_videoportero.py
python3 tests/e2e_portero.py && python3 tests/e2e_accesos.py && python3 tests/qr.test.py
```

---
Sistemas VB Seguridad Integral · Vincular Business · Sistema VB — WhatsApp (387) 4484132 · vincularbusiness@gmail.com
