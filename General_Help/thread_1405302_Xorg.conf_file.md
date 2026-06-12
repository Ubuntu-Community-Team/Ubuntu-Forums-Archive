---
title: "Xorg.conf file"
date: 2010-02-12
forum: General Help
---

### Post by sushilsc on 2010-02-12
hi,

  I installed Ubuntu 9.10  on Dell 1555 and I do not find the /etc/X11/Xorg.conf  file.

  Where I can find it or is there a way to generate it (with proper settings for may laptop) without much efforts??

 Thanks a lot.

 with best regards, 
 sushil

---

### Post by ajgreeny on 2010-02-12
9.10 does not have such a file as default , but you can certainly produce an empty one with ```
gksudo  gedit /etc/X11/xorg.conf
```and then put your own config in it, but exactly what that will be need to be depends on the hardware in your machine, particularly the graphics card, and whether or not you have a proprietary driver running.

Run ```
sudo lshw -C display
``` to find your graphics card, if you don't know what is in the computer.

---

### Post by Scunizi on 2010-02-12
IF you're trying to fix your resolution google xrandr which controls it now.

---

