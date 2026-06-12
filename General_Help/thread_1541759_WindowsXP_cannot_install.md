---
title: "WindowsXP cannot install"
date: 2010-07-29
forum: General Help
---

### Post by duf on 2010-07-29
Hello,

I have a laptop HP Pavilion, on which I installed Ubuntu 10.O4.
I erased the whole disk and used the option manually define the partitions.

Here is my partition table given by gparted:

Partition         File system       Mount point
unallocated                                           1 MiB
/dev/sda1           vfat             /windows
/dev/sda2           ext4             /
/dev/sda3           extended         extended
/dev/sda5           linux-swap
/dev/sda4           ext4             /home

I installed Ubuntu and everything went fine.

But now I want to install WinXP from an original Microsoft CD-rom and I get the follow error:  Unable to install windows, no hard disks found, contact your dealer (or something like that, it is translated from Dutch)

I tried everything, formatting my hard disk with gparted NTFS, formatting  mkfs.vfat, with no luck.

Any suggestions?

---

### Post by oldfred on 2010-07-29
did you put a boot flag on sda1? Windows needs that to boot but I did not think it did to install as it will add it as part of the install.

---

### Post by prodigy_ on 2010-07-29
It's quite possible that your HDD is in [ACHI mode](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface), or it's just attached to a controller for which a specific driver is needed, &#1077;tc.

In any such case, since XP distributive includes only the most basic drivers, you might need to download the missing driver and make a new installation CD. [nLite](http://www.nliteos.com/) can be used for that - it's a nice wizard-like tool that always worked for me.

---

### Post by Goolie on 2010-07-29
I always hear about problems installing Windows AFTER Ubuntu.

If all else fails, format the entire disk, and just install XP then Ubuntu.

---

### Post by prodigy_ on 2010-07-29
> **Goolie said:**
> format the entire disk
Won't help if it's a driver issue. And it certainly looks like a driver issue. Because if Windows installer has the necessary driver, the presence of Linux partitions won't give it a pause. (In fact any OS installer will happily overwrite any partition, if told to do so.)

---

