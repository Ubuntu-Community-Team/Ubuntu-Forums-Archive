---
title: "Extra Storage Partition"
date: 2009-12-07
forum: General Help
---

### Post by tom.swartz07 on 2009-12-07
Hi everyone!

I have a rather simple question:

I recently upgraded my HDD, and after cloning my old disk to my new one, I have around 100gb of extra space on the drive.

Ideally, I would like to set this up with a file system that both my Windows 7 Partition (ugh) and my 2 Linux Partitions could all read from - I was thinking NTFS? I would like to use it as a supplement to my external drive, and offload my iTunes Music, .iso files, and other space intensive files directly to the drive to reduce file transfer time when Im using them (also to get rid of the naggy bit of having an external plugged in every time i boot iTunes)

Here's the problem; I already reached the limit of primary partitions on my drive, so the new partition would have to be placed in the extended partition (sda4) with my *nix partitions.
(I just tried to run fdisk -l, but it didnt return any results-- strange.. Ill post a pic instead)

[IMG]http://lh6.ggpht.com/_tORug_uHNu4/SxyhpUP4IHI/AAAAAAAAAJQ/9bth2XWYm1o/s800/Screenshot--dev-sda%20-%20GParted.png[/IMG]

HOW would I go about setting up a purely data partition without messing up any of my current settings, and how could I set it so that it automatically mounts in my 'Buntu flavors? Also, is NTFS the best option for what I am using it for?

EDIT: Got the output from fdisk:
(sda is the internal drive, sdb is my external)

tom@ubuntu-karmic:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11904    85064175    7  HPFS/NTFS
/dev/sda4           11905       24571   101747677+   f  W95 Ext'd (LBA)
/dev/sda5           22653       22978     2618595   dd  Unknown
/dev/sda6           11905       22143    82244704+  83  Linux
/dev/sda7           22144       22652     4088511   82  Linux swap / Solaris
/dev/sda8           22979       24571    12795741   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d3a058b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
Thanks all!

---

### Post by dcstar on 2009-12-07
> **tom.swartz07 said:**
> Hi everyone!

I have a rather simple question:

I recently upgraded my HDD, and after cloning my old disk to my new one, I have around 100gb of extra space on the drive.
........

Use a Live CD to boot and increase the space of the Extended Partition.

This sort of question has been asked and answered hundreds (thousands?) of times already in the forums, do a search for detailed responses.

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
Why so many primary partitions? Anyway... I made an NTFS partition for the same thing. Everything works great. Just format it to NTFS and organize it the way you'd like. You can create a folder in /media or wherever you want it to auto-mount and then in /etc/fstab tell it to mount on boot. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) will help you with fstab. There's a GUI tool called pysdm but it doesn't use UUID so you might be better off manually editing it.

---

