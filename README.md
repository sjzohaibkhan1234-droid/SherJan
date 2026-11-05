# VoiceMaster

## Assumptions
- Android Studio Ladybug+, JDK 17, min SDK 26, target/compile 35. Personal-use sideloaded app (not Play Store).
- Wake word ("Hey Master") needs a Picovoice AccessKey; dependency is stubbed in build.gradle.kts. Push-to-talk (in-app mic + floating mic) works out of the box.
- Vosk offline STT is optional; Android's on-device recognizer is requested via EXTRA_PREFER_OFFLINE.
- Replies are in Urdu (system prompt). UI is English.

## Build & run
1. Open the folder in Android Studio, let Gradle sync.
2. Run on a physical phone (Android 8+). Install the Hindi/Urdu offline speech pack in Google app settings and a Urdu/Hindi voice in Google TTS.
3. Settings tab: paste your Claude API key, then tap buttons 1-6 in order.
   - Accessibility: Settings > Accessibility > VoiceMaster Control > ON. On Android 13+ sideloaded apps need: App info > ⋮ > "Allow restricted settings" first.
4. Tap "Start floating mic service", then speak: "WhatsApp kholo", "7:30 ka alarm lagao", "Ammi ko call karo".

## Known limitations & workarounds
- Wi-Fi/Bluetooth cannot be toggled silently on Android 10+: app opens the system panel.
- Screenshot / lock screen need Accessibility global actions (API 28+).
- Background mic: Android 14+ blocks starting mic from background; use the floating button (user tap) rather than always-on listening.
- Banking/password screens are blocked by design (package list + password-field detection).
- Cannot access other apps' private data; "full access" = what Android permissions + Accessibility allow.
- Calls/SMS always require a spoken "yes" first.
- Some OEMs kill background services: grant battery exemption and "autostart".
