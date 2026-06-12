---
title: "How to run shortcut as root?"
date: 2010-11-29
forum: General Help
---

### Post by VixinG on 2010-11-29
I created shortcut on desktop to game:
```

[Desktop Entry]
Name=League of Legends
Exec=env WINEPREFIX="/root/.wine" WINEDEBUG=-all wine "/root/.wine/dosdevices/c:/Program Files/League of Legends/lol.launcher.exe"
Type=Application
StartupNotify=true
Path=/root/.wine/drive_c/Program Files/League of Legends
Icon=EC27_lol.launcher.0

```
what should I add there to run this application as Root? Because if I run it as normal user, I get "permission denied" error. When running using terminal, I type all what is in "Exec=" without 'env' but with 'sudo' at the beginning, and it works...
thx 4 help ;)

---

### Post by Verbeck on 2010-11-29
either you've installed the program as root (which is a very bad idea : never use sudo with windows installers) [s]or the shortcut is wrong[/s]
if its installed as root, i suggest you reinstall it as a normal user

after that, the shortcut should be something like ;
 
[Desktop Entry]
Name=League of Legends
Exec=env WINEPREFIX="**/home/username/**.wine" WINEDEBUG=-all wine "**/home/username/**.wine/dosdevices/c:/Program Files/League of Legends/lol.launcher.exe"
Type=Application
StartupNotify=true
Path=**[B]/home/username/**[/B].wine/drive_c/Program Files/League of Legends
Icon=EC27_lol.launcher.0

---

### Post by VixinG on 2010-11-29
> **Verbeck said:**
> either you've installed the program as root (which is a very bad idea : never use sudo with windows installers) [s]or the shortcut is wrong[/s]
if its installed as root, i suggest you reinstall it as a normal user

after that, the shortcut should be something like ;
 
[Desktop Entry]
Name=League of Legends
Exec=env WINEPREFIX="**/home/username/**.wine" WINEDEBUG=-all wine "**/home/username/**.wine/dosdevices/c:/Program Files/League of Legends/lol.launcher.exe"
Type=Application
StartupNotify=true
Path=**[B]/home/username/**[/B].wine/drive_c/Program Files/League of Legends
Icon=EC27_lol.launcher.0
Thanks but..... it's not the answer for my question :confused:

---

### Post by matt_symes on 2010-11-29
Hi

It's old but it might get you nearer.

[http://ubuntuforums.org/showthread.php?t=24008](http://ubuntuforums.org/showthread.php?t=24008)

There is also this

[http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu](http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu)

Kind regards

---

