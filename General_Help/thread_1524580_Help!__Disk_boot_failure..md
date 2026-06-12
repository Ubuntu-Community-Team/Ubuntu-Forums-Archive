---
title: "Help!  Disk boot failure."
date: 2010-07-05
forum: General Help
---

### Post by pondering-panda on 2010-07-05
Hi.  I'm fairly new to Ubuntu and Linux in general, but have been running a fresh install of Ubuntu 9.10 64-bit on my desktop for about 6 months.  Yesterday the machine crashed would not shut down by any means and I was ultimately forced to unplug it.  

Upon restarting I was presented with 

> CLIENT MAC ADDRESS: ** ** ** ** ** ** GUID *********-****-****-****-************
DHCP ...... followed by

> PXE-E53: No boot filename recieved

PXE-M0F: Exiting PXE ROM
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTERI have checked the bios boot priorities and they seem fine.

After having searched around the internet for a bit I think that the grub loader (?) is missing/not installed/unavailable.  I tried to reinstall it via booting Ubuntu from CD, but I can't seem to mount my hard disk.  

This leads me to the conclusion that my HDD is knackered, which is a surprise considering its only 6 months old.  

Any help would be greatly recieved.  Thanks in advance.

---

### Post by pondering-panda on 2010-07-05
UPDATE:  Tried a fresh install of Ubuntu and no partition was apparrent for me to install anything to.  

So probabbly one dead hard disk.

---

### Post by ajgreeny on 2010-07-05
Sounds suspiciously like it, I agree, but before you give up completely, from the live CD try ```
sudo fdisk -l
``` to see if that finds a disk and partitions, or run gparted and see what that finds.  I am not sure if the live CD includes the Disk Utility in the System->Administration menu, but if it does, use that as well.

Probably will not help, but you never know!

---

### Post by pondering-panda on 2010-07-05
fdisk produced nothing at all

ie:

```
ubuntu@ubuntu:/$ sudo fdisk -l
ubuntu@ubuntu:/$ 

```gparted is on the live CD and this too found absolutely nothing.

So, yeah.  Looks pretty dead.

Thanks for your help though.  :KS

---

