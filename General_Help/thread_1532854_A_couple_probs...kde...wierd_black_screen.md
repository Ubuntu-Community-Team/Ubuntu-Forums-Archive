---
title: "A couple probs...kde...wierd black screen"
date: 2010-07-17
forum: General Help
---

### Post by Gargon0 on 2010-07-17
so i currently have ubuntu 10.4 on my HP Pavilion dv6000...i tried recently installed kde 4 and when realizing it wasnt for me i tried to get it off. I manage to get it off and the apps that came with it but now i have a kubuntu load screen when i boot/reboot/n shutdown my pc when there is supposed to be the ubuntu screen (thats prob one) so i tried to load an ubuntu live cd that ive used before and it wouldnt work and i notice that this screen pops up [http://picasaweb.google.com/lh/photo/0-LxFJXFy0yMXrt6FbR3Tw?feat=directlink]("http://picasaweb.google.com/lh/photo/0-LxFJXFy0yMXrt6FbR3Tw?feat=directlink") ...i dont know what it means but im still trying to find out...this screen also pops up if my pc isnt properly shutdown...thanks to any and all who can help in advance!

---

### Post by Gargon0 on 2010-07-17
Anyone?

---

### Post by Gargon0 on 2010-07-17
Am I incredibly the wrong section?

---

### Post by AlphaLexman on 2010-07-17
There are different login managers.

GDM is the login manager for ubuntu and gnome.
KDM is the login manager for kubuntu and kde.
XDM (or XFDM, I'm not sure) is the login manager for xubuntu and xfce.

Gnome, kde and xfce are all different window managers available on almost any distro of Linux.

I am guessing you did a complete install of kde-desktop on top of a fresh ubuntu install. Maybe the kdm login manager is the default now. You can still choose a gnome session from the kde login manager.

If it is a visual/appearance problem you are trying to solve, you will have to reset the GDM login manager to be the default login manager.

As far as the live CD issue and google picasa, I have no help or advice, sorry.

---

### Post by Gargon0 on 2010-07-17
thank you and how do i reset GDM login manager exactly?

---

### Post by AlphaLexman on 2010-07-17
Try this:[FONT=monospace]
[/FONT]```
[FONT=monospace]sudo dpkg-reconfigure gdm
```

[/FONT]Found it on [http://www.howtogeek.com/howto/ubunt...kdm-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/")

---

### Post by Gargon0 on 2010-07-17
thank you

---

