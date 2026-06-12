---
title: "GRUB Re-install problems"
date: 2010-06-19
forum: General Help
---

### Post by Rabbut on 2010-06-19
Hi,

I've just installed Windows 7 in a separate partition to play with. Trouble is, it's wiped out GRUB. I was expecting this and I know last time this happened it was easy to fix.:-k

The forum serch found a thread with 3 ways to re-install GRUB. I've tried each, and none have wored.

**Methods I've tried**

**1)**The aptitude install grub-pc command ran and said it had worked correctly. On re-bootong, Windows started without any GRUB screens on the way.

**2)**The chroot method stated it installed correctly after raising a few warnings - after I used the --force command, as the install failed without it. Again, reboot and get Windows without a GRUB screen...

**3)** Normal grub-install command (no chroot). This went as per the chroot command.

Any other option I've missed? :confused: From where I'm sat, it looks like I'll have to do a clean Linux re-install on the disk and then restore my linux files again from a back-up - something I'm not particularly over-joyed by the prospect of...

---

### Post by bcbc on 2010-06-19
if you had to use --force then you were installing grub to a partition (/dev/sdXY). 
You need to install it to the drive MBR (/dev/sdX). 

this link has good instructions...[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Rabbut on 2010-06-19
bcbc, Thanks for that. Just tried again with the modified command and it's worked a treat :) It's always something simple with these things isn't it :oops:

Thanks again
Rabbut

---

