---
title: "desktop icons on KDE"
date: 2006-05-16
forum: General Help
---

### Post by sabredog on 2006-05-16
Just installed KDE and would like to add some shortcuts to my windows XP HDD and my documents partition, mounted in /media/windows and/media/documents respectively.

Gnome places the shortcut icons on the desktop automatically but KDE has not.

Also KDE's file manager does not see these mount points either however KDE knows they are there in system info.

Also, how do I get enough permission to alter the shortcut icons already displayed. The link to my windows LAN needs this for an icon change.

cheers and thanks

---

### Post by barbarian on 2006-05-16
Hello,
> Gnome places the shortcut icons on the desktop automatically but KDE has not.

menu>system settings>Desktop>Behavior>Show icons on desktop


> Also KDE's file manager does not see these mount points either however KDE knows they are there in system info.

in konqueror address bar type /media

> Also, how do I get enough permission to alter the shortcut icons already displayed. The link to my windows LAN needs this for an icon change.


sudo chmod 777 /media/windows_partition

---

