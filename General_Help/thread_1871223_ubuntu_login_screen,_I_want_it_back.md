---
title: "ubuntu login screen, I want it back"
date: 2011-10-28
forum: General Help
---

### Post by elliotn on 2011-10-28
I installed kubuntu-desktop and I have been using kdm as my default logo screen. now I need the default ubuntu gdm login window, how to get it back

---

### Post by deloquencia on 2011-10-28
Won't it an **apt-get install kdm- gdm** make it? Perhaps KDE'll prevent you from making it that way.

When it fails, so try to edit **/etc/X11/default-display-manager**, change kdm to gdm and the init script /etc/init.d/xdm should run at the end of runlevel 2 gdm.

Hope it'll work :)

---

### Post by ajgreeny on 2011-10-28
The command ```
sudo dpkg-reconfigure gdm
```should allow you to choose which one to use in future.

---

