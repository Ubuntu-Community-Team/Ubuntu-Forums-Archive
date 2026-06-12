---
title: "install both ati and nvidia drivers..."
date: 2009-08-22
forum: General Help
---

### Post by P4man on 2009-08-22
Hi,

I used to have a live usb stick to carry around, and I had used this trick:

[http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive#Nvidia_driver](http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive#Nvidia_driver)

to make it automatically load nvidia binary drivers on systems with an nvidia card. On systems with an ati or intel card, it would then just load the default opensource drivers. It worked like a treat!

However, now I did a regular install on my stick, no more casper live cd stuff to improve boot time.. but  since some of my machines have ATI and others nVidia cards, Im looking for a way to have the binary nvidia driver loaded automatically on an nvidia machine, and at the very least the opensource ATI on an ati machine, much like my live stick used to. Now I have to alter my xorg.conf each time..

If thats not doable, at least a grub entry for each would be nice.

Anyone got any ideas ?

---

### Post by P4man on 2009-08-22
actually, Im already half way there I think.

I basically used the same script:
```

#!/bin/bash
# Exit if no nVidia card installed
lspci | grep nVidia || exit 0
# Let nVidia create a new /etc/X11/xorg.conf
nvidia-xconfig
```

and put it in /etc/rc2.d/S01nvidia-xconfig

This works! 

If I put "ati" as driver in my xorg.conf and boot on an ati machine, it works fine. I plug the stick in an nvidia machine, it rewrites the xorg.conf with default nvidia settings and I get compiz and all.

Of course, if I again boot on an ATI machine, nothing is done, so now I need to add some lines to detect ATI and something that will generate a default ati xorg.conf.

Anyone?

---

### Post by P4man on 2009-08-22
I guess i could make a xorg.conf for ati, nvidia (and perhaps intel) video, and test with lspci and rewrite the xorg file depending what string I find in lspci. Problem is, my bash scripting skills are non existent, so if anyone feels like helping a hand, this could be neat!

---

### Post by P4man on 2009-08-23
ok, never mind. I got it working :D

---

### Post by dadep on 2009-10-19
Hi P4man

> **P4man said:**
> ok, never mind. I got it working :D


nice! I'm interested too in something similar.

Can you post your solution?

Thank You

dadep

---

### Post by P4man on 2009-10-19
I posted my solution here:
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

