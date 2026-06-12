---
title: "how do i set the next OS that grub boots from terminal?"
date: 2009-12-21
forum: General Help
---

### Post by nerdy_kid on 2009-12-21
Hi, i was wondering how to change the boot option the GRUB2 will boot on the next reboot -- so i want to be able to set it to start winXP and then reboot and have it autostart it with out me manualy hitting ESC and selecting it.  I found a program in the software channels but its GUI and for GRUB. :(

thanks in advance

---

### Post by jerrrys on 2009-12-21
this any help

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Leppie on 2009-12-21
open /etc/default/grub with a text editor and modify GRUB_DEFAULT=0 to GRUB_DEFAULT="xxx", where you have to substiture xxx with the exact menu entry for your windows xp, save it and run:
```
$sudo update-grub
```

you can retrieve the exact menu entry like this (if you have not modified it):
```
$cat /boot/grub/grub.cfg | grep Windows
```

---

### Post by nerdy_kid on 2009-12-21
ok, but i want the change to be temporary, so in Ubuntu i can set GRUB2 to boot WinXP, reboot (all remotely btw) into XP, and then upon another reboot, it will boot back into Ubuntu again.

---

### Post by nerdy_kid on 2009-12-21
btw, grub-choose-default is the package im talking about, need that except GRUB2 capable and no GUI -- any ideas?

[edit] im an idiot, its GRUB not GRUB2, but i still need no GUI

---

### Post by drs305 on 2009-12-21
Take a look at the manpage for *grub-reboot*

I haven't used it but this command looks like what you are looking for. Make sure you use the exact menuentry (or number).

---

### Post by nerdy_kid on 2009-12-21
> **drs305 said:**
> Take a look at the manpage for *grub-reboot*

I haven't used it but this command looks like what you are looking for. Make sure you use the exact menuentry (or number).


ahhhh perfect!!! thanks a ton man!

---

