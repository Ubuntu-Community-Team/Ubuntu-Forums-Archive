---
title: "Desktop Launcher"
date: 2006-06-24
forum: General Help
---

### Post by joeybc2001 on 2006-06-24
How can I make a desktop launcher (shortcut) in xubuntu 6.06?

I can drag an app from thunar to the desktop - but it creates a copy of the application not a launcher on the desktop.

---

### Post by loell on 2006-06-24
right click any icon on the desktop
at the bottom there is "create new" -> launcher :)

---

### Post by m_gasior on 2006-06-24
Open Mousepad and write something like this (*this is for Firefox launcher*):

[Desktop Entry]
Exec=/usr/bin/firefox
Icon=/usr/share/pixmaps/firefox.png
StartupNotify=true
Terminal=false
Type=Application
Name=Firefox

Then save as **firefox.desktop** in your **Desktop** directory.

---

