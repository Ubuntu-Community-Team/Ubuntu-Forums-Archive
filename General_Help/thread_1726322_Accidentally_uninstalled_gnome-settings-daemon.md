---
title: "Accidentally uninstalled gnome-settings-daemon"
date: 2011-04-11
forum: General Help
---

### Post by zashuna on 2011-04-11
Yeah, I know, it's pretty stupid. Regardless, the minute I realized that happened, I reinstalled it right away. The next time I turned on my computer, I can't log back in. In the login screen, I don't have any options for "sessions". I must have screwed up the settings when I uninstalled it. Any help would be appreciated.

---

### Post by Krytarik on 2011-04-11
By doing so you have removed a couple of other packages that are depending on it. You can reinstall them all by reinstalling the metapackage "ubuntu-desktop":
- when you are at the login screen, press Ctrl+Alt+F1 to switch to a console
- login there
- enter:
```
sudo apt-get install ubuntu-desktop
```- restart GDM:
```
sudo service gdm restart
```- you will get automatically to the hopefully fixed login screen

Greetings.

---

