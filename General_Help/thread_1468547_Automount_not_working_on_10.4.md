---
title: "Automount not working on 10.4"
date: 2010-05-01
forum: General Help
---

### Post by atari05 on 2010-05-01
I upgraded to 10.4 the other day. After the upgrade all seemed well. However, today I noticed that CD's, external usb drives, usb thumb drives will not auto mount.

Anyone else having this issue?


**NOTE** The system does "see" the disks (confirmed in DMESG) and they do show in disk utility and from there I can manually mount them. It seems nautilus doesn't want to auto mount even though its checked in gcong

---

### Post by atari05 on 2010-05-01
SOLVED:

I did a quick move of the .gnome2 directory (to like .gnome2_orig), restarted X and everything seems to be happy now as far as auto mount goes.

---

