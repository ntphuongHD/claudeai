# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build & Test Commands

```bash
# Build
./gradlew assembleDebug          # Build debug APK
./gradlew assembleRelease        # Build release APK
./gradlew build                  # Build all variants

# Test
./gradlew test                   # Run unit tests
./gradlew testDebugUnitTest      # Run unit tests for debug variant only
./gradlew connectedAndroidTest   # Run instrumented tests (requires connected device/emulator)

# Other
./gradlew lint                   # Run lint checks
./gradlew clean                  # Clean build outputs
```

## Project Overview

Android application using Jetpack Compose and Material 3. Key versions:
- **Kotlin:** 2.0.21
- **AGP:** 9.0.1
- **Compile/Target SDK:** 36, **Min SDK:** 24
- **Compose BOM:** 2025.07.00

## Architecture

**Single-module** Android app (`app/`). Entry point is `MainActivity.kt`.

- `MainActivity.kt` — Uses `ComponentActivity` with `NavigationSuiteScaffold` for adaptive navigation across three destinations (Home, Favorites, Profile). State persisted via `rememberSaveable`.
- `ui/theme/` — Material 3 theming: `Color.kt` (palette), `Theme.kt` (light/dark + dynamic color for Android 12+), `Type.kt` (typography).

All dependencies are version-managed via `gradle/libs.versions.toml` (version catalog). The project uses non-transitive R classes for faster builds.

## Testing

- **Unit tests:** `app/src/test/` — JUnit 4
- **Instrumented tests:** `app/src/androidTest/` — AndroidJUnit4 + Espresso + Compose UI testing
hi