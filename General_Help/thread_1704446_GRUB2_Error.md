---
title: "GRUB2 Error"
date: 2011-03-10
forum: General Help
---

### Post by gus_zernial on 2011-03-10
I have an AMD system with Kubuntu 10.10 64-bit, Grub2 and 
2.6.37.1 custom kernel. There are several disks in the 
system, the boot disk is on an OCZ-AGILITY 120GB SATA SSD. 
After several weeks of normal operation, for some reason 
the system stopped booting, giving the message ...

error: out of memory > Entering rescue mode > grub rescue>

I can thereafter boot the system with the Kubuntu install disk, go into system rescue mode, go into a root shell on the boot disk, issue update-grub, and the system will then boot correctly the following time. But the time after that, back to the grub out of memory error.

The only other thing noticed is that in system rescue mode the
boot disk does not always get the same /dev/sdX identifier.

Anyone know what's wrong and how to fix?

Thx, Gus

---

