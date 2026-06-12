---
title: "[Q] Partitioning. Move free space from sdb2 to sdb3?"
date: 2012-06-14
forum: General Help
---

### Post by mikeeey on 2012-06-14
Something that appears so simple is giving me quite the trouble. I'm just trying to take some free space from my windows ntsf partition (sdb2) and move it to my ubuntu partition (sdb3) (located in a sub-partition of sdb5).
But when I create unallocated **after** sdb2 it still remains **before** sdb3. I can't seem to get it out of sdb2 and into sdb3/sdb5.
Here's a screenshot as well:

---

### Post by carl4926 on 2012-06-14
sda3 is an extended partition, if there is free space before it, you need to resize sda3 backwards towards sda2

Can you post

```
sudo fdisk -l
```

---

### Post by xycris on 2012-06-14
hi mikeey,

since you are using gparted. try the steps found here
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by prshah on 2012-06-14
> **mikeeey said:**
> move it to my ubuntu partition (sdb3) (located in a sub-partition of sdb5).
But when I create unallocated **after** sdb2 it still remains **before** sdb3. I can't seem to get it out of sdb2 and into sdb3/sdb5.

Your ubuntu partition is /dev/sdb5; located within an extended partition /dev/sdb3.

Your windows partition /dev/sdb2, is a primary partition.

These are the steps you need to follow:

1) Close all "locked" partitions (the ones marked by a "key"). Right click the partition and choose unmount (swapoff, if a swap partition). If any of the partitions are currently in use (booted from) then you need to boot off a live CD first.
2) Reduce the partition /dev/sda2.
3) Resize / Move /dev/sda3 (backwards, into the free space AFTER sda2)
4) Resize / Move /dev/sda5 (your linux partition).
6) Apply changes.

Note that moving / resizing partitions is fraught with risks, so please have a backup. At your own risk, please.

Please post back if you need more information.

Regards,

---

### Post by Mark Phelps on 2012-06-14
Unless I'm misreading the second screenshot, you already HAVE shrunk your Win7 OS partition, right? If that is the case, do NOT mess with it again using GParted.  Doing so risks corrupting Win7 and rendering it unbootable.

All you should have to do, once booting from an Ubuntu LiveCD or LiveUSB, is to expand the beginning of the Extended partition to take up the new allocated space.

If you can do that, then expand the Linux partition to the left to take up the space in the Extended partition.

Then, reboot into Ubuntu on your hard drive.

---

### Post by mikeeey on 2012-06-23
Thanks for the replies everyone. 

[COLOR="Silver"]The process seems to have been unsucessful.
I first used Easus Partition Master to make 16GB of unalocated space from my windows partition.
I then used a GParted Live CD to drag the sdb3 extended partition backwards into the unallocated space. I was then given an error saying it was unsucessful.
I have no idea why I can't extend my partition.



If needed, here are the results for sudo fdisk -l:
> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x480a284b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              64  2930274303  1465137120    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x08f9e1f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      210943      104448    7  HPFS/NTFS/exFAT
/dev/sdb2          211680  1399628159   699708240    7  HPFS/NTFS/exFAT
/dev/sdb3      1432387530  1465147391    16379931    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sdb5      1432387584  1465147391    16379904   83  Linux
[/COLOR]

[SIZE="3"]**[COLOR="Red"]EDIT:[/COLOR]** Oh my! the solution was rediculously simple! The problem was the **Gparted Live CD** not allowing me to do this. Instead, I inserted the **Ubuntu 12.04 Live CD**, ran GParted, and everything worked as it should.
For anyone else that may run into this having the same problem as me, I did run into this startling warning messages mentioning a high change of Ubuntu not being able to boot up or Grub not working (which I've uploaded below), but all went well anyway.[/SIZE]

---

### Post by oldfred on 2012-06-24
Well, gparted may have been trying to protect you from Windows issues. NTFS likes 30% free, slows at 20% free and at 10% free just about stops working. You may not be able to defrag as there is not enough working room.

Of course, Ubuntu needs some free space also. Linux system partition has 5% hidden away to prevent you from crashing it when it runs out of room.

---

