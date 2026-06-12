---
title: "Changing the size of my swap partition?"
date: 2010-04-25
forum: General Help
---

### Post by savaan on 2010-04-25
This is my first go around with Linux. I set my swap partition a bit high and now want to shrink it down and possibly merge it with one of my other partitions. I don't have dual boot, just have a second partition on the drive for data. Can I merge these easily?

---

### Post by nitstorm on 2010-04-25
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Maybe this could help??

---

### Post by savaan on 2010-04-25
I'm sorry, I don't find the info on that page. This is already installed...I'm looking to shrink the swap file. I see a place there to expand it, not shrink it after install

---

### Post by john newbuntu on 2010-04-25
In a sense you can not merge partitions.  You can delete one and extend the other if they are right next to each other.

Just to get a clearer picture, open a terminal (applications->accessories->terminal) and post the output of the following by typing the following and hit enter:
```
sudo fdisk -l
```

---

### Post by savaan on 2010-04-25
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  83  Linux
/dev/sda2           18237       60801   341903362+   5  Extended
/dev/sda5           18237       19452     9767488+  82  Linux swap / Solaris
/dev/sda6           19453       60801   332135811   83  Linux

---

### Post by john newbuntu on 2010-04-25
I take it that you want to reduce swap (/dev/sda5) and use the unallocated space to merge with /dev/sda6.  If this is true, just to be on the safe side, you can use gparted on the ubuntu liveCD, uncheck the swap on /dev/sda5, drop it and recreate the partition.
The longer part is going to be moving /dev/sda6 to the left to add the unallocated space.

A general suggestion would always be to backup your data before moving/resizing.

If you have not used gparted before, please familiarize yourself with some of the documentation especially the copy/move one.  They are mostly illustrations.
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by dino99 on 2010-04-25
no need a swap larger than twice your hard ram

---

### Post by srs5694 on 2010-04-25
IMHO, you should leave it alone. Your swap file is roughly 9,767,488KiB (9.3GiB) in size, which is a bit on the big size for most systems, but not ridiculously so. You could certainly shrink it to something more reasonable (say, ~5GiB if you've got 4GiB of RAM), but that will only free up ~4GiB of disk space. You'd then need to grow /dev/sda6 *to the left* -- that is, moving its start point. Shifting the start point of a partition is always riskier, and usually more time-consuming, than shifting the end point of a partition. Thus, you'd be spending a lot of time and risking all your data to recover only ~4GiB of disk space (less than 1% of your total disk space). If you really need that ~4GiB of disk space, you're better off buying another disk than risking your data in this way.

That said, depending on your needs you might be able to create a new partition between /dev/sda5 and /dev/sda6. You could then mount it somewhere to give yourself access to this ~4GiB partition. This could be worthwhile if you've got some specific use for a ~4GiB partition, such as a temporary data area if you're confident you won't exceed this size, or a partition to hold a single DVD image file. In fact, if you make it just a bit bigger than 4GiB, you could directly store a single DVD image in that partition, without even formatting it.

---

