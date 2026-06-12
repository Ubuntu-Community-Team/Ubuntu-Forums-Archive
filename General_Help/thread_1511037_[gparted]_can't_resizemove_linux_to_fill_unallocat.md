---
title: "[gparted] can't resize/move linux to fill unallocated space-- even from live cd"
date: 2010-06-16
forum: General Help
---

### Post by the pearly gates on 2010-06-16
Hello,

I installed a dual boot windows 7 and xubuntu and now decided that I would like to allocate more hard disk space to xubuntu.  I've resized the windows partition (sda2 in the screenshot) and it is now the grey unallocated.  

I'm having trouble moving this unallocated space to the linux portion (sda5).  I did my homework and found that this is done by booting off a live cd and using gparted from there, because  you can't modify a partition that you're using.  I also read that you had to turn swap off. I did both of these tasks, but as you can see from the attached screenshot, I am unable to resize the linux partition to fill the unallocated space.

Here's my "sudo fdisk -l" for reference:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2afe7258

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12625   101306888+   7  HPFS/NTFS
/dev/sda3           19537       26588    56645190    5  Extended
/dev/sda4           26589       38914    99000320    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5           19537       25615    48829536   83  Linux
/dev/sda6           25616       26588     7815591   82  Linux swap / Solaris

```

Also, the sda4 is a shared partition that I can access from both windows and linux.

Any help would be greatly appreciated. Thanks!

---

### Post by warfacegod on 2010-06-16
Select sda3 to resize first. Then do sda5.

---

### Post by oldfred on 2010-06-16
warfacegod is correct.

Just to add a little explanation on partitions. The sda3 primary partiton is the extended partition that is a container for all the logical partitions. The logicals cannot be outside the extended.  So you have to move the extended to make room to expand the logical inside the extend partition.

---

### Post by the pearly gates on 2010-06-19
> **warfacegod said:**
> Select sda3 to resize first. Then do sda5.

> **oldfred said:**
> warfacegod is correct.

Just to add a little explanation on partitions. The sda3 primary partiton is the extended partition that is a container for all the logical partitions. The logicals cannot be outside the extended.  So you have to move the extended to make room to expand the logical inside the extend partition.

Thank you both-- that worked like a charm!

---

### Post by warfacegod on 2010-06-19
Glad to be of service.

---

### Post by dancer_69 on 2011-06-11
I have a very similar problem and I cannot resize ubuntu partition.
Here is the fdisk output:
```
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1            4728        4990    39933243    f  Extended LBA
Warning: Partition 1 does not end on cylinder boundary.
/dev/sdc5            4728        4990     2104515   82  Linux swap
Warning: Partition 5 does not end on cylinder boundary.
/dev/sdc2   *        4990        9236    34105995   83  Linux
Warning: Partition 2 does not end on cylinder boundary.
/dev/sdc3            9237       19457    82092150    7  HPFS/NTFS

```

I resized the NTFS partition to make space for Ubuntu partition.
Now, here is the order that the partitions dispayed on gparted:
**    Unallocated space | Swap | Ubuntu | NTFS Drive**
I want to use the unallocated space to extend Ubuntu partition, but I cannot move any partition, and I can only resize the NTFS.
How can I do this?

---

### Post by oldfred on 2011-06-11
Partition rules still apply. You only have logical partitions inside one extended and the rest are primary partitions. You can move partitions around which may be very slow and have some risk so have good backups. If unallocated in not adjacent to partition you want to expand it requires an awful lot of shuffling and a lot of risk.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

If you are sharing with windows a shared NTFS partition is recommended or just a ext3 or ext4 data partition.

Another alternative is just to make it a data partition or move /home into a new partition which would have to be inside the extended unless you still have a primary left to assign.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by dancer_69 on 2011-06-11
Thanks for the directions.
I've a quick look on one of the links and I understood how gparted works.
So, I booted to gparted live cd and with some copying deleting, moving and resizing I've manage to resize my Ubuntu partition. It took a lot time(about 3 hours), but now I'm writing from a working system with double partition size.
Thanks again.

---

