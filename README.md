## i3 tiling window manager

Kurzer Überblick über mein Setup und Installationsanleitung.

Video: https://www.youtube.com/@pixeledi

- <https://i3wm.org/>
- Befehle im Überblick <https://i3wm.org/docs/refcard.html>

> ⚠️ Login mit Passwort aktivieren, damit man jederzeit zurückspringen und seinen Desktop wie Cinnamon auswählen kann, für den Fall dass man sich die i3 config versehentlich kaputt gemacht hat\\

### i3 installieren

```bash
sudo apt update && sudo apt upgrade
sudo apt install i3
```

Alternativ auch über die Softwareverwaltung des Systems

### Darkmode

```
sudo apt install lxappearance

lxappearance
```

Das Programm starten und Theme auswählen.

## Oh My Zsh

Aufgeräumtes und effektives Terminal

- <https://ohmyz.sh/>

```
sudo apt install zsh

sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Kitty Terminal Emulator

- <https://sw.kovidgoyal.net/kitty/>
- Themes: <https://github.com/dexpota/kitty-themes>

```
sudo apt-get install kitty
```

i3 config

```
# start a terminal#bindsym $mod+Return exec i3-sensible-terminalbindsym $mod+Return exec kitty
```

## Keychain für SSH Verwaltung

- <https://www.funtoo.org/Funtoo:Keychain>

```
sudo apt update
sudo apt install keychain
nano ~/.zshrc
```

  
Keychain Setup

```
eval keychain --eval --agents ssh privatey1 privatkey2 id_rsa
```

SSH Keys sind unter

```
cd ~/.ssh
ls
```

## Auflösung ändern

Zuerst Displays identifizieren

```
xrandr
```

Auflösung anpassen

```
xrandr --output Virtual-1 --mode 1920x1080
```

Diesen teil in i3 config

```
nano ~/.config/i3/config

exec --no-startup-id xrandr --output Virtual-1 --mode 1920x1080
```

super+shift+r für reload der i3 settings um syntax check zu machen

Falls man mehrer Monitore hat und diese anordnen will, dieser Command kommt dann auch zb am Ende der i3 config.

```
exec --no-startup-id  xrandr --output DP-1 --mode 1680x1050 --rotate left --output DP-4 --mode 1920x1080 --right-of DP-1 --output DP-2 --mode 1920x1080 --right-of DP-4
```

### rofi App-Launcher

```
sudo apt install rofi

nano ~/.config/i3/config
```

dmenu_run oder mod+d suchen und anpassen

```
bindsym $mod+d exec --no-startup-id rofi -show drun
```

rofi theme eingeben und zb monoki suchen

Icons im Menü hinzufügen

```bash
sudo apt install papirus-icon-theme

/home/pixeledi/.config/rofi
nano config.rasi

configuration {
	show-icons: true;
}
```

### i3 Statusbar

Die Anleitung in dem Repo ist gut ausgeführt.

- <https://github.com/tobi-wan-kenobi/bumblebee-status>

### Titelbar der einzelnen Fenster entfernen

```
nano ~/.config/i3/config
```

font pango suchen und auf 0 ändern

```
font pango:monospace 0
for_window [class=".*"] title_format " "
```

---

### Sonstige Quellen

- <https://github.com/addy-dclxvi/i3-starterpack>
- <https://codeberg.org/cizordj/i3-themer>
- <https://github.com/polybar/polybar>
- <https://github.com/adi1090x/polybar-themes>

Tiling Manager for Windows (not tested)

- <https://github.com/glzr-io/glazewm>