# Currant

Витрина приложений white-currant для macOS: каталог с описаниями и скриншотами, скачивание и обновление в один клик.
Новые приложения появляются в каталоге сами. Установка проверяет подпись разработчика и нотаризацию Apple, чужие сборки не ставятся.

*[English below](#english)*

## Установка

**Вручную.** Скачайте `Currant.dmg` со страницы [Releases](https://github.com/white-currant/Currant/releases/latest), откройте и перетащите Currant в «Программы».

**Через терминал, одной командой** (ничего больше не нужно):

```bash
curl -fsSL -o /tmp/Currant.dmg https://github.com/white-currant/Currant/releases/latest/download/Currant.dmg \
  && hdiutil attach -nobrowse -quiet -mountpoint /tmp/Currant-dmg /tmp/Currant.dmg \
  && rm -rf /Applications/Currant.app && cp -R /tmp/Currant-dmg/Currant.app /Applications/ ; \
hdiutil detach -quiet /tmp/Currant-dmg; rm -f /tmp/Currant.dmg
```

Запуск: `open -a Currant`. Удаление: `rm -rf /Applications/Currant.app`.
Обновления приходят автоматически ([Sparkle](https://sparkle-project.org)); вручную — меню «Проверить обновления…».

Приложения ставятся в `/Applications`. Currant не собирает никаких данных: он читает публичные страницы GitHub и скачивает нотаризованные DMG из релизов.

Исходный код Currant закрыт. Используемый компонент: [Sparkle](https://sparkle-project.org) (MIT).

## Как приложение попадает в витрину

Витрина находит публичные репозитории white-currant с темой `currant-app` и файлом `currant.json` в корне. Исходники приложения хранятся в отдельном закрытом репозитории, а в публичном лежат только релизы, лента обновлений и описание:

```
currant.json     описание приложения для витрины
currant/         иконка и скриншоты
appcast.xml      лента обновлений Sparkle
README.md
```

Пример `currant.json`:

```json
{
  "name": "Tick",
  "tagline": "Чеклисты и памятки в стиле авиационных карт",
  "description": ["Абзац 1", "Абзац 2"],
  "features": ["Возможность 1", "Возможность 2"],
  "bundleID": "com.yulion.tick",
  "appFile": "Tick.app",
  "dmgAsset": "Tick.dmg",
  "category": "Продуктивность",
  "minOS": "macOS 14",
  "accent": "F2B705",
  "icon": "currant/icon.png",
  "screenshots": ["currant/screenshot-1.png"]
}
```

Необязательное поле `glow` (HEX) задаёт цвет свечения на странице приложения вручную.

---

## English

A showcase for white-currant's macOS apps: catalogue, descriptions, screenshots, one-click install and update.
Installs are verified against the developer's code signature and Apple notarization; foreign builds are refused.

**Install by hand:** download `Currant.dmg` from [Releases](https://github.com/white-currant/Currant/releases/latest), open it and drag Currant to Applications.

**Install from the terminal, one command:**

```bash
curl -fsSL -o /tmp/Currant.dmg https://github.com/white-currant/Currant/releases/latest/download/Currant.dmg \
  && hdiutil attach -nobrowse -quiet -mountpoint /tmp/Currant-dmg /tmp/Currant.dmg \
  && rm -rf /Applications/Currant.app && cp -R /tmp/Currant-dmg/Currant.app /Applications/ ; \
hdiutil detach -quiet /tmp/Currant-dmg; rm -f /tmp/Currant.dmg
```

Currant's source code is closed. It uses [Sparkle](https://sparkle-project.org) (MIT).
