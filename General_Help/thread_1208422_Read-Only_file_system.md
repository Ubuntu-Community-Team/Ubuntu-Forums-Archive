---
title: "Read-Only file system"
date: 2009-07-09
forum: General Help
---

### Post by superstoffer on 2009-07-09
Hi guys and girls,

I have upgraded to 9.04 Jaunty on my dedicated box, but now I can't connect with NX Client nor VNC because the system is set to read-only...

I have tried to Google the matter, but I couldn't find a complete solution...
For connection from my Windoze, I use PuTTY...

So can anybody help me turn my system back to rw?

Edit:

Does anybody know how to remount the system so it's not Read Only?
My etc/fslab looks like this:


/dev/sda1       /       ext3    default,rw,errors=remount-ro       0       1
/dev/sda2       /home   ext3    defaults                0       2
/dev/sda3       none    swap    defaults                0       0
proc            /proc   proc    defaults        0       0
sysfs           /sys    sysfs   defaults        0       0

---

### Post by superstoffer on 2009-07-09
I tried:

sudo mount -o remount,rw /dev/hda1

but only got:

mount: / not mounted already, or bad option

Can anybody help?

---

