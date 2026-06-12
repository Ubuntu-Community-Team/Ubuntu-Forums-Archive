---
title: "Can't have a partition outside the disk!"
date: 2012-03-01
forum: General Help
---

### Post by jrutherfordt on 2012-03-01
When I try to run gparted my disk shows up as unallocated and gparted says "Can't have a partition outside the disk!"  I've looked into this and it seems this is caused by a problem with the partition table.  I had deleted a partition and then recovered it with testdisk immediately before this happened, so I am guessing testdisk wrote a bad partition table or something.  I've looked into common problems with partition tables and can't seem to find any of the common problems, but I am not overly familiar with partition tables myself.  Here is my partition table as shown from fdisk -lu:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013b21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19531776   405454847   192961536   83  Linux
/dev/sda3       405454848   444517336    19531244+   7  HPFS/NTFS/exFAT
/dev/sda4       444518550   488408129    21944790    f  W95 Ext'd (LBA)
/dev/sda5       446924800   488396799    20736000    7  HPFS/NTFS/exFAT


As I've said I can't find anything wrong with this partition table, but again I'm not an expert at these things.  So after being using these forums for a long time for help I am finally posting my first post here.  Thanks in advance.

---

### Post by clausrei on 2012-03-01
Did you start Gparted from LiveCD ?

---

### Post by jrutherfordt on 2012-03-01
No, will that make a difference?  I can try it.

---

### Post by 23dornot23d on 2012-03-01
sda total ...... 488397168

sda4 ............   488408129

sda4 goes beyond your total number of sectors .....

Testdisk ..... will probably work out what is wrong ...... but backup ..... all important
data before attempting to use it ......

---

### Post by jrutherfordt on 2012-03-01
Aha, I looked for that but missed it.  Thanks for the keen eye 23dornot23d.  I've run testdisk and re-wrote that partition table and it didn't correct this but I've dug around the man pages of a enough commands in the last hour so to fix this manually.  Thanks again for spotting what I missed.  Now if I can just figure out how to mark this thread as solved...

---

