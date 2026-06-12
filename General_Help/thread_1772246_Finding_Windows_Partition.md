---
title: "Finding Windows Partition"
date: 2011-05-31
forum: General Help
---

### Post by wetzeldc on 2011-05-31
I got tired of dual booting on my old computer so on the new computer I am planning to run XP on VMware Player.  The problem is that on the new computer neither Ubuntu or XP can "see" the FAT32 partition.  I intend to use the FAT32 partition for photo images and old Windows files and need access from both Ubintu and XP.

david@No2:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6445    51769431   83  Linux
/dev/sda2            6446       35145   230532688    5  Extended
/dev/sda3           35146       60801   206081820    b  W95 FAT32
/dev/sda5           34054       35145     8771458+  82  Linux swap / Solaris
/dev/sda6            6446       31988   205174084+  83  Linux
/dev/sda7           31989       34053    16587081   83  Linux

Partition table entries are not in disk order

---

### Post by Grenage on 2011-05-31
Greetings,

While I would recommend NTFS over FAT32 (FAT32 is terrible), have you mounted the partition anywhere?  For example:

```
sudo mkdir /media/store
sudo mount /dev/sda3 /media/store
```

---

### Post by Rubi1200 on 2011-05-31
For an interesting take on the differences between FAT and NTFS, see the comments in the thread by srs5694:
[http://ubuntuforums.org/showthread.php?t=1720287&highlight=fat+ntfs](http://ubuntuforums.org/showthread.php?t=1720287&highlight=fat+ntfs)

---

### Post by wetzeldc on 2011-05-31
After reading up on FAT32 vs NTFS, I reconfigured my system.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25496   204796588+   7  HPFS/NTFS
/dev/sda2   *       25497       31870    51199155   83  Linux
/dev/sda3           31871       56729   199679887    5  Extended
/dev/sda5           31871       50992   153597433+  83  Linux
/dev/sda6           50993       55454    35840983+  83  Linux
/dev/sda7           55455       56729    10241406   82  Linux swap / Solaris

I haven't got as far as reinstalling VMware, but I still have the same question.  How do I make the Windows partition "visible" to Ubuntu and XP?  When I reinstalled, I specified the mount point for the NTFS partition as /Windows

---

### Post by Grenage on 2011-06-01
Good call on NTFS.

While my experience with VMware is fleeting (I have VMware Player on this machine), I've always used network shares to transfer data from one virtual machine to the physical machine.

---

### Post by Mark Phelps on 2011-06-01
> **wetzeldc said:**
> How do I make the Windows partition "visible" to Ubuntu and XP? 
Ubuntu will see the partition in "Places"; XP should see it -- if a drive letter is assigned.
>  When I reinstalled, I specified the mount point for the NTFS partition as /Windows
Try assigning a mount point of /Media/Windows

---

