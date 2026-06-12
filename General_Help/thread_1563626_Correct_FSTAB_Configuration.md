---
title: "Correct FSTAB Configuration"
date: 2010-08-29
forum: General Help
---

### Post by kelvinator on 2010-08-29
I am running 10.04 and see the following error whenever I start my PC:

An error occurred while mounting /proc/bus/usb. Press S to skip mounting or M for manual recovery.

The relevant lines in FSTAB are:
usbfs  /proc/bus/usb   usbfs  auto              0  0

/dev/sdb1 /media/sdb1 vfat      uid=[MYNAME],owner,users,user  0  0

If I comment these lines the error goes away but any connected USB devices are stuck as being owned by root. If the lines are restored the error returns but USB devices can then be used without any problems. 

I am looking for a tutorial in the correct configuration of FSTAB to make this go away.

---

