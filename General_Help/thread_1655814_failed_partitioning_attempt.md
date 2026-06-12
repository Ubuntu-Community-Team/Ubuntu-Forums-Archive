---
title: "failed partitioning attempt"
date: 2010-12-30
forum: General Help
---

### Post by fibrebiz on 2010-12-30
I have a 500GB external hard drive. It originally had 2 partitions,

the first was EXT4, about 100GB in size, the second was FAT32, filling the rest of the disk.

I attempted to delete the EXT4 partition and grow the FAT32 partition to full size but when I tried this, GParted returned an error.

The end result leaves 1 500GB EXT4 partition. Ubuntu reads the partition as EXT4 and can see the data that was originally on the EXT4 partition slated for deletion.
The data on the FAT32 partition is still there, according to GParted, but it cannot recognise the FAT32 section of data.
Windows cannot find the FAT32 data and offers to reformat it - an offer I will not take up. I want that data back.

Any suggestions?

---

### Post by dasan on 2010-12-30
give one try with gparted live CD

---

### Post by fibrebiz on 2010-12-30
The Gparted Live CD does not help. I could repartition the Disk, but there's no indication that I would get to keep the data of the hidden FAT32 partition.

Interestingly, in the disk utility, for my 500GB Iomega hard drive, it show 1 partition.
Partition type: W95 FAT32 (0x0b)
Partition flags: - 
Type: EXT4 (version 1.0)

If I choose to edit the partition, it refers to it as Partition 2. Strange.

Any more ideas?

---

### Post by Quackers on 2010-12-30
testdisk?
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by fibrebiz on 2010-12-30
TestDisk seems like it'll do the job nicely. 
I'm not quite sure how to use it but I'll try anyway.

---

### Post by fibrebiz on 2010-12-30
VICTORY!

I'd recommend that program to anyone who has a partitioning mishap.

---

### Post by Quackers on 2010-12-31
I'm glad you managed to get things sorted out :-)

---

### Post by dasan on 2010-12-31
It was a good info for mee tooo
Thankz...lot

---

