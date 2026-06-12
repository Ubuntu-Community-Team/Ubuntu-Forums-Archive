---
title: "GUI problems on startup"
date: 2006-03-25
forum: General Help
---

### Post by epothes on 2006-03-25
My laptop works fine and the operating system does too. Whenever I run GNOME, Xorg, or whatever the screen turns off but the system continues to run like normal. I know the GUI comes on but my screen just turns off. Can someone help me? It would make me very happy. ^_^

---

### Post by ruibernardo on 2006-03-26
I would sugest to set the resolution of your desktop and the refresh rate of your monitor.

One way of doing this is editing /etc/X11/xorg.conf as root

sudo gedit /etc/X11/xorg.conf

and see if  HorizSync and VertRefresh rates are set according the the manufacturer specs of your monitor, then restart X.

---

### Post by Hairy_Palms on 2006-03-26
at the console type sudo dpkg-reconfigure xserver-xorg

---

### Post by pteja on 2006-03-26
[QUOTE=Hairy_Palms]at the console type sudo dpkg-reconfigure xserver-xorg[/QUOTE]

I had the same problem. It got fixed when I ran the command:
sudo dpkg-reconfigure xserver-xorg

and selected vesa driver. I left all other options at default values. Later I installed ATI drivers.

------
:-) help
------

---

