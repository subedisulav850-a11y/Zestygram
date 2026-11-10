# Zestygram for Android

Zestygram is an **unofficial Telegram client** based on the Telegram for Android source code. It is not developed, endorsed, or supported by Telegram. This fork uses its own app name, launcher icon and Android application ID (`com.zestygram.client`).

## Zestygram features

- **Feature hub:** open **Settings → Zestygram**.
- **Deleted-message archive:** opt-in, on-device history, capped at 500 messages. It only saves messages received while the archive is enabled and cannot recover messages deleted before capture. Secret chats, service messages and self-destructing content are excluded. Turn it off or clear the archive at any time.
- **Ghost mode setup:** shortcut to Telegram's actual Last Seen & Online privacy controls. It does not hide read receipts selectively or bypass Telegram's server-side rules.
- **Custom-name profile link:** makes a Markdown-style `[Name](tg://user?id=12345)` link. This links to a profile; it does not guarantee a notification ping.
- **Zestygram Plus:** free client-side appearance customizations. This does not grant Telegram Premium or change account entitlements.
- **Community promotion:** in-app link to [@zestygram](https://t.me/zestygram).

## Requirements

- Android Studio 2025.1.4
- Android SDK 36 and Build Tools 36.0.0
- Android NDK 27.2.12479018
- JDK version supported by the Android Gradle Plugin bundled with this project

## Configure before building or publishing

1. Register your application and obtain your own Telegram API ID and API hash. Replace the sample `APP_ID` and `APP_HASH` in `TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java`.
2. Replace the `google-services.json` files in the Android application modules (including `TMessagesProj_App` and `TMessagesProj_AppStandalone`) with your own Firebase project configuration for these application IDs:
   - `com.zestygram.client` (release)
   - `com.zestygram.client.beta` (debug)
   - `com.zestygram.client.web` (standalone)
3. Replace the sample signing keystore in `TMessagesProj/config` and update the signing passwords/alias in `gradle.properties`.
4. Review `BuildVars.java` and replace all sample OAuth, Maps, SafetyNet/Play Integrity and store values with credentials registered to your app. Disable integrations you do not configure.
5. Keep the unofficial-client notice and publish the modified source in accordance with the repository's GNU GPL license and any applicable Telegram API requirements.

The repository's sample credentials and signing setup are for development only. They are not production credentials. The Firebase JSON package names in this fork are adjusted so Gradle can resolve the expected application variants; replace that file with a genuine Firebase configuration before relying on push notifications or publishing.

## Build commands

From the repository root:

```bash
./gradlew :TMessagesProj_App:assembleAfatRelease
```

For a debug build:

```bash
./gradlew :TMessagesProj_App:assembleAfatDebug
```

## Upstream source and protocol documentation

- [Telegram Android source](https://github.com/DrKLO/Telegram)
- [Telegram API documentation](https://core.telegram.org/api)
- [MTProto documentation](https://core.telegram.org/mtproto)
- [MTProto security guidelines](https://core.telegram.org/mtproto/security_guidelines)

