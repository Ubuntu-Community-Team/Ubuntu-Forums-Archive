---
title: "Server Question."
date: 2010-04-20
forum: General Help
---

### Post by Roasted on 2010-04-20
Say you're somebody who wants to deploy an Ubuntu server using the actual server edition, BUT you're sort of skeptical about the whole terminal ONLY thing. Could you install the gnome GUI and just run startx whenever you want to fire up the GUI for more visual assistance? 

If so, is there a way to kill the GUI safely and bring it back to headless mode after you're done?

---

### Post by NightwishFan on 2010-04-20
Yes you can, just do not install a display manager like GDM. To leave, just log out, I assume you would go back to CLI prompt.

---

### Post by undecim on 2010-04-20
Also, look into setting up VLC to use a GUI over the network.

---

### Post by Sin@Sin-Sacrifice on 2010-04-20
Yes... ```
sudo apt-get install ubuntu-desktop
``` whenever you want to use GUI then startx. Whenever you want to use CLI press ctrl+alt+F1 and you can stop gdm with ```
/etc/init.d/gdm stop
```

EDIT: If you want headless to be default you'll have to google it. I'm pretty sure when you install the GUI it will take over.

---

### Post by Iowan on 2010-04-20
[ServerGUI]("https://help.ubuntu.com/community/ServerGUI")
There are also options like **ebox** and **webmin**.

---

### Post by Roasted on 2010-04-21
Oh yeah - Doesn't webmin have a terminal screen on the actual web interface? Geez maybe that alone would handle it. GUI through webmin + terminal through webmin at once...

---

