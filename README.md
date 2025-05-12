

```markdown
# 🖥️ Полная кастомизация Ubuntu (![image](https://github.com/user-attachments/assets/9cf3b8fd-f999-4acc-9a7b-36e323fe4d37)

)

## 1. Установка базовых компонентов
```bash
# Основные инструменты
sudo apt update
sudo apt install -y gnome-shell-extensions gnome-tweaks chrome-gnome-shell git

# Дополнительные настройки (Tweaks+)
sudo apt install -y gnome-shell-extension-prefs dconf-editor
```

## 2.  расширения (список)
```bash
# Установка всех ваших расширений
ДЕЛАТЬ ЧЕРЕЗ ТЕРМИНАЛ,ПЕРЕВЕДИТЕСЬ В РУТ РЕЖИМ ПЕРЕД УСТАНОВКОЙ(sudo su)
EXTENSIONS=(
    "blur-my-shell@aunetx"
    "burn-my-windows@schneeqans.github.com"
    "compiz-alike-magic-lamp-effect@hermes83.github.com"
    "compiz-windows-effect@hermes83.github.com"
    "CustomizeClockOnLockScreen@pratap.fastmail.fm"
    "dash-to-dock@mixxgx.gmail.com"
    "desktop-cube@schneeqans.github.com"
    "user-theme@gnome-shell-extensions.gcampax.github.com"
)

for EXT in "${EXTENSIONS[@]}"; do
    gnome-extensions enable "$EXT"
done
```
## 3. Резервное копирование
```bash
# Экспорт всех настроек
dconf dump / > full_gnome_backup.dconf

# Импорт (при переустановке)
dconf load / < full_gnome_backup.dconf
```

## 4. Настройки.Скачиваем две папки в закрепленке,дальше вставляем их в данную директорию '/home/your_linux_user_name'. После установки вставляем этот скрипт

### Внешний вид (Appearance)
```bash
gsettings set org.gnome.desktop.interface cursor-theme 'ArcStarry-cursors'
gsettings set org.gnome.desktop.interface icon-theme 'Win11-purple'
gsettings set org.gnome.shell.extensions.user-theme name 'Lavanda-Sea'
gsettings set org.gnome.desktop.interface gtk-theme 'Orchis-Light'
```

### Панель задач (Ubuntu Dock)
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock dock-position 'LEFT'
gsettings set org.gnome.shell.extensions.dash-to-dock dash-max-icon-size 40
gsettings set org.gnome.shell.extensions.dash-to-dock autohide true
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
```

## 5. Конфиг Burn My Windows (анимации)
```bash
# Magic Lamp эффект
gsettings set org.gnome.shell.extensions.burn-my-windows close-effect "magic-lamp"
gsettings set org.gnome.shell.extensions.burn-my-windows magic-lamp-intensity "1.5"

# Эффекты Compiz
gsettings set org.gnome.shell.extensions.compiz-windows-effect minimize-effect "genie"
gsettings set org.gnome.shell.extensions.compiz-alike-magic-lamp-effect duration "400"
```

## 6. Доп. настройки
### Фон рабочего стола
```bash
gsettings set org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/ubuntu-default-greyscale-wallpaper.png'
gsettings set org.gnome.desktop.background picture-uri-dark 'file:///usr/share/backgrounds/ubuntu-default-greyscale-wallpaper.png'
```

### Часы на экране блокировки
```bash
gsettings set org.gnome.shell.extensions.customize-clock format '%H:%M'
```

## 7. Системные требования
```bash
# Проверка версий
gnome-shell --version  # Должно быть ≥ 42
lsb_release -a        # Ubuntu 22.04+ рекомендовано

# Решение проблем
sudo apt install -y libmutter-10-0 gir1.2-mutter-10 libgconf-2-4
```



---

🔧 **Важные нюансы вашей конфигурации:**
1. Все анимации работают только на X11 (не Wayland)
2. Для `Desktop Cube` требуется:
   ```bash
   sudo apt install -y libgtk-3-dev libgjs-dev
   ```
3. Шрифты и курсоры должны быть в:
   - `~/.fonts/`
   - `~/.icons/`

📌 **Мой уникальный стиль требует:**
- Отключить все стандартные анимации GNOME
- Использовать только темную тему для Orchis-Light
- Dash to Dock должен быть всегда слева без автопрятания

![Схема ваших настроек](БУДЕТ ДОБАВЛЕНО В БУДУЩЕМ)
```

/home/ваш_пользователь/
├── .themes/
│   └── Lavanda-Sea/
├── .icons/
│   └── Win11-purple/


Прошу выставить звездочку если вам помог данный гайд,удачи!!
                                                                                 ``` В БУДУЩЕМ ПОСТАРАЮСЬ СДЕЛАТЬ ГАЙД НА КАСТОМИЗАЦИЮ ARCH LINUX ```
                                                                                                         
