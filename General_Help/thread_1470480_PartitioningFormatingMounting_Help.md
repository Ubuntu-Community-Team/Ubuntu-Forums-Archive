---
title: "Partitioning/Formating/Mounting Help?"
date: 2010-05-02
forum: General Help
---

### Post by jtdeloach10 on 2010-05-02
I have this nice 500 GB Hard drive that I recently upgraded in my computer. ( It is an additional and did not replace any )
I would like to mount it in all 500 gb or 2x250's, but utilizing all space.

Problem: When I mount it I only get 250 gb. space.


Data:
fdisk -l
```
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?         410      119791   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      121585      234786   909287957+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

```

I can't mount sdb1 or sdb2, just sdb and it mounts as 250 gb. ( 231 acctually ).

Please help :D It sucks not getting all I deserve.

---

### Post by srs5694 on 2010-05-03
Chances are the disk came set up with a "raw" filesystem without a partition table, but I'm not sure why it's showing up as 250GB rather than 500GB. If you haven't already copied files to the hard disk, the simple solution is to partition it and set up filesystem(s) on the partition(s). You can partition the disk with fdisk, gdisk, GNU Parted, GParted, or other tools; and you can set up filesystems with mkfs, GNU Parted, GParted, or other tools. GParted is the easiest of these tools to use, but it may be thrown by the existing filesystem. You should be able to delete enough of it to make GParted happy as follows:

```

sudo dd if=/dev/zero of=/dev/sdb bs=512 count=100

```

This command erases the first 100 sectors of the disk (100 is a somewhat arbitrary value; 1 would probably be sufficient, but 100 ensures that other possibly misinterpreted data will also be wiped). GParted should then interpret the disk as empty. You can use it to create one or more partitions, which it can also fill with filesystems.

---

