---
title: "GParted doesnt regognize my table!"
date: 2010-10-31
forum: General Help
---

### Post by tommihl on 2010-10-31
Im trying to do a new install(32bit to 64bit) but Ubuntu installer doesnt see my partitions nor does this installation. "Disk utility" sees them fine and im running my Ubuntu and XP on that disk. I dont wanna lose my XP and /home(Koti) partition so help needed. 

Theres my fdisk -l:

```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1ced1ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12749   102406311    7  HPFS/NTFS
/dev/sdb2           12750       19457    53881979+   f  W95 Ext'd (LBA)
/dev/sdb5           12750       16061    26603608+   b  W95 FAT32
/dev/sdb6           19061       19457     3188871   82  Linux swap / Solaris
/dev/sdb7           16061       19060    24087552   83  Linux

```

And heres "Disk Utility":
[IMG]http://dl.dropbox.com/u/8278927/gparted.png[/IMG]
Theres supposed to be 1 NTFS, 2 EXT4 and SWAP partition. Weird thing is theres nothing wrong with the system :S Even the swap is running fine.

THANKS!

---

### Post by tommihl on 2010-10-31
Another strange thing!

[IMG]http://dl.dropbox.com/u/8278927/gparted2.jpg[/IMG]
Is it FAT32 or EXT4 :S I formatted it yesterday to EXT4 for sure...

---

### Post by srs5694 on 2010-11-01
First, partitions have type codes stored in the partition table, and these are independent of the data inside the partitions. The issue with your second post is that the filesystem in the partition does not match the type code for the partition. This is easily corrected in fdisk by using the "t" option to change the type code. Change it to "83" for a Linux partition, then use "w" to write the changes.

There's a slim chance that this mis-match is what's causing the problem you report in your first post; however, I think that's unlikely. I recommend you begin by posting the output of "sudo fdisk -lu"; this increases the precision of the fdisk output from the cylinder values in the output you've already reported to sector values. I don't see anything obviously wrong at cylinder resolution, but a small enough problem might require sector resolution to become obvious.

I think it's more likely that you've got another problem, such as old RAID data on the disk or a BIOS configured to use software RAID.

---

### Post by tommihl on 2010-11-01
Thanks for answering! Here is my "sudo fdisk -lu":
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd1ced1ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204812684   102406311    7  HPFS/NTFS
/dev/sdb2       204812746   312576704    53881979+   f  W95 Ext'd (LBA)
/dev/sdb5       204812748   258019964    26603608+   b  W95 FAT32
/dev/sdb6       306198963   312576704     3188871   82  Linux swap / Solaris
/dev/sdb7       258015232   306190335    24087552   83  Linux

Partition table entries are not in disk order

```

> I think it's more likely that you've got another problem, such as old RAID data on the disk or a BIOS configured to use software RAID.
This isn't a possibility. I checked BIOS(never changed anything else than Boot Order) and RAID was disabled. Never done RAID and Disk was new when I bought it...

---

### Post by psusi on 2010-11-01
Your partition table is corrupt.  sdb5 and sdb7 overlap slightly.  Backup any data you can get to and try running testdisk to repair it.

---

### Post by tommihl on 2010-11-01
> **psusi said:**
> Your partition table is corrupt.  sdb5 and sdb7 overlap slightly.  Backup any data you can get to and try running testdisk to repair it.


I was just going to post this when I saw your answer:
[IMG]http://dl.dropbox.com/u/8278927/gparted3.jpg[/IMG]


I bought a new Western Digital today so I'm on the safe side now :) But can anybody explain why this is happening? What did I do wrong?

---

### Post by srs5694 on 2010-11-01
Psusi is correct in his diagnosis. If either partition is unused at the moment, though, you could delete it, run Linux fsck or Windows CHKDSK (as appropriate) on the remaining partition, and create a new partition in place of the one you've deleted. That would probably be simpler and safer than using TestDisk, IMHO. Using TestDisk might be the best, or at least the simplest, solution if you need to recover data from both the affected partitions, but if you can discard one of the partitions, IMHO that's a simpler and safer solution.

As to what you did wrong, the answer is almost certainly "nothing," or at worst, you picked the wrong disk utility at some point. The sort of problem you've got can only result because of a bug in a disk utility, because of sloppy use of very low-level disk access tools (hex editors), or because of random data errors. Chances are you weren't using hex editors on your partition table (if you were, chances are you'd know enough to fix the problem yourself), so that leaves bugs or random data errors. If you know the precise history of what disk utilities you've used and precisely what you did with each, it's conceivable you could narrow the field to figure out which utility did the damage, but there's a good chance there'd be two or three candidates. The best approach is probably to just fix the damage and move on. Also, try to use as few disk partitioning programs as possible in the future. Don't use some random utility just for kicks, since it could be buggy and produce such problems. Of course, you might *need* to use a specialized tool, but you should use such tools only if you really do need to use them, not just because you want to try something different.

---

### Post by efflandt on 2010-11-01
What tool did you use to create the partitions in the wrong order and overlapping (and one with wrong type)?  Only you can answer that.

---

### Post by tommihl on 2010-11-03
> **efflandt said:**
> What tool did you use to create the partitions in the wrong order and overlapping (and one with wrong type)?  Only you can answer that.

"Disk Utility". I didn't create new partition but reformatted it

---

