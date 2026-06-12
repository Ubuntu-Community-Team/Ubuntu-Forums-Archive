---
title: "New install boots to Command line login"
date: 2011-02-21
forum: General Help
---

### Post by Jnk1296 on 2011-02-21
I'm still a bit new to Ubuntu but lately i decided to dual boot install Ubuntu with my Windows 7. After a lot of hair pulling, i finally managed to boot the live cd environment with "nomodeset". From there i installed ubuntu. When it finished installing, i booted to the new ubuntu install only to be presented with a command line login. If i change the boot line from "quiet splash" to "nomodeset", i can coax ubuntu to boot in low graphics mode. However this is not a permanent fix, and doing so causes a 2 inch offest of the screen on the right hand side. Only the have the missing 2 inches appear on the left side. If from the "Ubuntu is running in low graphics mode" message, i select "console login", and type "startx" i just comes out with "X Server Fatal error- No Screens found". I also tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
```but it still didn't help. I'm running out if ideas here, can anyone point me in the right direction?

EDIT: This is a cd that i got free from Canonical themselves. It's Ubuntu 10.04 LTS, and I have Intel Integrated Graphics.

---

### Post by Rubi1200 on 2011-02-21
Hi and welcome to the forums :-)

First we need to know which specific graphics card.

Next, you should probably try the i915.modeset=1 parameter rather than nomodeset.

Finally, take a look here for issues and possible solutions:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

