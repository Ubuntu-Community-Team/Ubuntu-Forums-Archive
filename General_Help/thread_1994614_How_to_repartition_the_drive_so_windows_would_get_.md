---
title: "How to repartition the drive so windows would get more space?"
date: 2012-06-03
forum: General Help
---

### Post by orange2k on 2012-06-03
As the title says I'm trying to repartition my drive so windows would get more space. Right now my windows partition has 68 GB of space and ubuntu 12.04 about 160 GB. Total disk size is 250 GB.

I hope I don't have to reinstall...

---

### Post by carl4926 on 2012-06-03
show us

```
sudo fdisk -l
```

---

### Post by orange2k on 2012-06-03
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa84fa84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   133114589    66557263+   7  HPFS/NTFS/exFAT
/dev/sda2       133114590   137018384     1951897+  82  Linux swap / Solaris
/dev/sda3       137019390   488394751   175687681    5  Extended
/dev/sda5       137019392   488394751   175687680   83  Linux

Disk /dev/mapper/cryptswap1: 1998 MB, 1998743040 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3903795 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xae797476
Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
```

---

### Post by carl4926 on 2012-06-03
It would be messy and tricky.
I'd backup your user file in Ubuntu
Delete all linux partitions, resize Windows
Repartition for Linux
Re-install Ubuntu

Windows will do a file system check at next boot, let it run.

---

### Post by orange2k on 2012-06-03
> **carl4926 said:**
> It would be messy and tricky.
I'd backup your user file in Ubuntu
Delete all linux partitions, resize Windows
Repartition for Linux
Re-install Ubuntu

Windows will do a file system check at next boot, let it run.

Just as I thought, tricky problem...

Well, I'll enjoy another reinstalling session...

Of course I'll backup my files first...):P

---

### Post by Mark Phelps on 2012-06-03
You could shrink Ubuntu using GParted from a LiveCD.  Problem is that GParted is notoriously S...L...O...W.  It's not just the shrinking that will take time, you will also have to move the shrunk partition to the right to make some room to the left.  After shrinking the Extended partition, you will also have to move the other Liniux partition to the right.

I don't remember if GParted will let you move a partition to the right.

And then, you will need to grow the Windows partition to take up the space.  IF you have Win7, you should do this using the Disk Management utility.  That won't take long as all you're doing is adding some free space.

All-in-all, it probably would be much faster just removing Ubuntu, expanding Windows, and reinstalling Ubuntu.

---

### Post by orange2k on 2012-06-03
> **Mark Phelps said:**
> All-in-all, it probably would be much faster just removing Ubuntu, expanding Windows, and reinstalling Ubuntu.

I did that, and I did that properly, so I reinstalled Windows (had lot of junk on it, anyways), deleted all partitions, gave windows 118 GB, installed it, then installed Ubuntu, gave it 120 GB, and voila...:guitar:

It took 3,5 hours...:KS

---

