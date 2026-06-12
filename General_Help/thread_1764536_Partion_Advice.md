---
title: "Partion Advice"
date: 2011-05-21
forum: General Help
---

### Post by wetzeldc on 2011-05-21
I installed Ubuntu 11.04 on a new machine with two 500GB drives in a Raid 1 configuration.  Then setup VMware to run XP.  When things didn't connect I started looking for answers in the forum and realised I should have created partitions.  Since this is a new system I thought I would just start over however I obviously am naive about how to set this up.
How do I start over?
What partitions and size would you recommend.
There is about 30GB of Windows files to be loaded.
The biggest directory to be loaded is currently at 70GB.  It is used for digital pictures and could easily grow to 3 or 4 times that over the life of this computer.
If possible I would like to be able to access all files from Ubuntu and XP.  I really need this capability for the digital pictures.

---

### Post by oldfred on 2011-05-22
I do not know RAID and how you do partitions in RAID. It is different than just using gparted to create partitions.

To share data with windows & Ubuntu you need to create a shared NTFS partition which can have all you data from Windows & Ubuntu if you want. Normally we suggest a separate /home for user settings & data, but the settings are less than 1GB and all the rest of /home would be for user data. If all your data is in your NTFS data partition you can just leave /home in the / (root) partition and make root a little larger to have room for some data that creeps in. I do move some usually hidden data folders like thunderbird & Firefox profiles to NTFS so I can use the same profile in both windows & Ubuntu.

You could get by with 50 to 100GB for both windows & Ubuntu system partitions, swap slightly larger than RAM and all the rest as the shared NTFS partition. If using VM some put that into a separate partition, but I have not done any VMs so do not know.

Post this so we can see what you currently have:

sudo fdisk -lu

---

### Post by wetzeldc on 2011-05-23
Result of sudo fdisk -lu

david@David2:~$ sudo fdisk -lu
[sudo] password for david: 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc089

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   960178175   480088064   83  Linux
/dev/sdb2       960180222   976766975     8293377    5  Extended
/dev/sdb5       960180224   976766975     8293376   82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc089

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   960178175   480088064   83  Linux
/dev/sda2       960180222   976766975     8293377    5  Extended
/dev/sda5       960180224   976766975     8293376   82  Linux swap / Solaris

Disk /dev/dm-0: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc089

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1            2048   960178175   480088064   83  Linux
/dev/dm-0p2       960180222   976766975     8293377    5  Extended
/dev/dm-0p5       960180224   976766975     8293376   82  Linux swap / Solaris

Disk /dev/dm-1: 491.6 GB, 491610177536 bytes
255 heads, 63 sectors/track, 59768 cylinders, total 960176128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-3: 8492 MB, 8492417024 bytes
255 heads, 63 sectors/track, 1032 cylinders, total 16586752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table
david@David2:~$ ^C
david@David2:~$

---

### Post by oldfred on 2011-05-23
I do not know RAID. But I do know the standard tools do not work for some types. You need to find specific advice on your type of RAID. 

You may do better in the server sub forum.

---

