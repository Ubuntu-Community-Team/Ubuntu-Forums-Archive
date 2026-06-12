---
title: "Simple help resizing a partition"
date: 2012-01-08
forum: General Help
---

### Post by genti on 2012-01-08
Hello all,

Anyone has 5 minutes to spare? Since the forum changes the formatting I am attaching the same thing as text to make reading easier. 

I am trying to shrink and expand two ext4 partitions on a software raid. Gparted is not picking md0 up while on bootable media, (but somehow it does see the partitions fine when I boot out of the hard drive). I did install mdadm and assembled the array while on the bootable USB.

**I think my main issue is how to tell resize2fs and fdisk exactly what I want.**

Before any changes I had this:
    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1            2048    46139391    23068672   83  Linux
/dev/md0p2        46139392    62937087     8398848   83  Linux

md0p1 is ~21G (using about 7-8G), and md0p2 is ~8G (using about 0.5G).

Since GParted is not helping my goal was:
1. resize2fs md0p1 to about 19G
2. shrink the partition of md0p1 with fdisk (delete first partition and add it with different ending)
3. expand the partition of md0p2 with fdisk
4. expand the filesystem of md0p2 with resize2fs.

I tried this:
root@ubuntu:~# resize2fs /dev/md0p1 20000M
resize2fs 1.41.14 (22-Dec-2010)
Resizing the filesystem on /dev/md0p1 to 5120000 (4k) blocks.
The filesystem on /dev/md0p1 is now 5120000 blocks long.

I am assuming that the the 5120000 blocks of resize2fs are 4k blocks so they are equal to 20480000 fdisk blocks. 

Something changed with fdisk because it displays things in sectors instead of blocks, in the past I did not have to run it as fdisk -u /dev/md0

Right now I have:
   Device Boot      Start         End      Blocks   Id  System 
/dev/md0p1               1        2553    20506941   83  Linux
/dev/md0p2            2554        3917    10948297   83  Linux

and 
Command (m for help): v                                                   
Information: 12530 unallocated sectors 

In expert fdisk mode I see:
Nr AF  Hd Sec     Cyl  Hd Sec     Cyl      Start       Size ID
 1 00  32  32       0 254  62    2552       2048   41011897 83
 2 00   0   0    2553 254  62    3916   41013945   21912660 83

Should I move the start of partition 1? Will that mess up the data? Where is the raid info stored?

* After the restart tmp would not mount so I had to recreate the filesystem and mount it with 1777 permissions.
I don't know why and not to one's self to make the tmp partition huge.

---

