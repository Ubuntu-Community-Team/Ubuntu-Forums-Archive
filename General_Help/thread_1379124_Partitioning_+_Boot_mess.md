---
title: "Partitioning + Boot mess"
date: 2010-01-12
forum: General Help
---

### Post by exuro1 on 2010-01-12
Hi,

To start, I'm using Ubuntu Karmic as my main Ubuntu OS. 

Today I partitioned the HDD and installed an older version of ubuntu (a customized version). The ubuntu I installed also installed grub with it, which was no real problem until I realised that, whilst I can see the entry on the grub startup menu for Karmic, when I try to boot it - it goes to a black screen which a blinking cursor ( _ ) in the top left-hand corner. I've tried editing the grub configuration file (menu.lst) but the problem persists.

When I checked my partitions with 'fdisk -l' it's a mess. This is the output:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          46      369463+  83  Linux
/dev/hda3   *          47        7296    58235625    5  Extended
/dev/hda5            7111        7296     1494013+  82  Linux swap / Solaris
/dev/hda6            2551        6924    35134092   83  Linux
/dev/hda7            6925        7110     1494013+  82  Linux swap / Solaris
/dev/hda8              47        2440    19229742   83  Linux
/dev/hda9            2441        2550      883543+  82  Linux swap / Solaris

Partition table entries are not in disk order

1)Do I need so many Swap partitions?
2)My Karmic installation resides on /dev/hda6. Is there a way I can set it so that hda6 is the parition that is booted off?
3)If no to #2, is there anyway I can use the current grub config to boot the Karmic partition.

NB: I can access my Karmic installation via mounting on LiveCD / New installation, but it won't boot at all.

I'm open to any suggestions.

Cheers

---

### Post by audiomick on 2010-01-12
Hallo.

> 1)Do I need so many Swap partitions?

- no you don't need 3 swap partitions. Swap is only temporary storage, only in use by the currently booted installation, and can be mounted to all installations without a problem.


> 2)My Karmic installation resides on /dev/hda6. Is there a way I can set it so that hda6 is the parition that is booted off?

- yes you can, although I am not too sure about how.:(


> 3)If no to #2, is there anyway I can use the current grub config to boot the Karmic partition.

- also possible...

I think what has happened, is that the newer installation of the older Ubuntu has "taken over" the boot process.

> I've tried editing the grub configuration file (menu.lst) but the problem persists.


Was the 9.10 a fresh install or and updated older version? 9.10 uses grub2, but it is only installed via a fresh install. If it is an upgrade from an older install, it will still be grub legacy.

Here are some links that might help you sort out what is going on.

To find out what is installed where:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

for info about grub
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

for grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Hope that helps;)

---

### Post by oldfred on 2010-01-12
Reinstall the appropriate grub as audiomick linked to.

If you delete swap files, you will probably have to edit the fstab of which ever install uses that swap to use the swap you keep.

use this to see the UUID  of the swap partitions.
sudo blkid 

Then edit the fstab in the linux partitions to match.

---

### Post by exuro1 on 2010-01-13
Thanks for all the help :)

I tried all the options mentioned here, plus a few more from research. None of them gave any results so I backed up all the required data and will start with a fresh installation of each (hopefully it'll be cleaner / functional this time ;))

Cheers

---

