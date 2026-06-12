---
title: "Adding Partition to Existing Mount Point"
date: 2011-11-15
forum: General Help
---

### Post by coltsfanatic07 on 2011-11-15
Is there a way I can add a new partition's space to an already existed mount point?

For instance my main bootable mountpoint is "/" and is running out of space. I have another 15GB partition available and I would like to add that storage to the mountpoint so I don't run out of space.

I think this has to do with a Logical Volume Group, but I am pretty new to this level or work on a Linux box.

Any help would be much appreciated!

---

### Post by oldfred on 2011-11-15
Welcome to the forums.

I consider LVM more advanced. If the partitions are next to each other you should be able to create a LVM.
lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

But I prefer to keep my system (root) small at 20 to 25GB and mount data partitions either directly into /home or mount somewhere and link folders into /home.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by coltsfanatic07 on 2011-11-15
Thanks OldFred. I will try and work on this sometime this evening and see if I can get it to work as you suggested.

------------

After reading through these, I guess I still don't know what the exact best option is. Below you can see my issue. I have /dev/sda1 which is an ext4 partition where I installed Ubuntu. I just mounted another ext4 partition, /dev/sda6, which has plenty of room (well at least for what I need to use the server for, and yes, it is just a 20GB hard drive).

What would your suggestion be so that I do not run out of space? At this point I can barely install anymore packages on this box as I only have 468MiB left.


coltsfanatic@Ubuntu-Garage:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda1                 4050      3377       468  88% /
udev                       210         1       210   1% /dev
tmpfs                       87         1        86   1% /run
none                         5         0         5   0% /run/lock
none                       217         1       217   1% /run/shm
/dev/sda6                14171       164     13288   2% /mnt/data
coltsfanatic@Ubuntu-Garage:~$

---

### Post by coltsfanatic07 on 2011-11-15
Oops, I accidentally edited my post instead of replying. What are your suggestions on the above disk space situation?

---

### Post by oldfred on 2011-11-15
Having / (root) at only 4GB is tiny. New installs want a minimum of 4.4GB and that is before you add anything. Generally you only want to use about 25% of root so you have room. And with only a 20GB drive your options are limited. I assume sda6 is nowhere near sda1 on the drive. Post this or a screen shot from gparted.
```

sudo fdisk -lu
```

---

### Post by coltsfanatic07 on 2011-11-15
So in theory, can I just remove the entire extended partition, delete everything from /dev/sda6 so that it is unallocated space, and the grow the primary partition?


Disk /dev/sda: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders, total 40020624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000078db

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     8427519     4212736   83  Linux
/dev/sda2         8429566    40019967    15795201    5  Extended
/dev/sda5        37926912    40019967     1046528   82  Linux swap / Solaris
/dev/sda6         8439808    37924863    14742528   83  Linux

Partition table entries are not in disk order

---

### Post by coltsfanatic07 on 2011-11-15
I went ahead and backed the partitions so they are touching each other, and both are ext4.

Would I need to boot with a LiveUSB so that I could make sure neither partition was mounted to extend the primary partition?

---

### Post by oldfred on 2011-11-15
You do not have an extended anymore, just sda1 & sda2. Yes you need to work from a liveCD or liveUSB to edit partitions, so they are not mounted.

I would just make one larger / partition and then have swap. If you add another drive then you can mount that into your system for even more data. But one large partition allows each folder to grow and not run out of space until you have totally run out of space.

In the old days you had a partition for every folder, but it was difficult to manage partition sizes. Part of why some like LVM. But with drives so large now, there is little reason for small partitions.

---

### Post by coltsfanatic07 on 2011-11-15
Alright, booting to GParted LiveUSB was able to clear it up pretty easily. I was able to extend to just include a single partition, and then create a manual swap file instead of adding a swamp partition. Looks like I am good to go. Thanks.

---

### Post by oldfred on 2011-11-15
Glad it worked out.:)

---

