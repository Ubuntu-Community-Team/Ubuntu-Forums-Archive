---
title: "See HDD contents; move complete contents to another HDD"
date: 2010-11-11
forum: General Help
---

### Post by RealGomer on 2010-11-11
I'm still feeling my way thru Linux, in particular Ubuntu. I have a dual boot PC with two hard drives. I believe I have WinXP Pro on the one HDD and Ubuntu 10.04 on the other. The second HDD is partitioned into two logical drives of 80 GB each. I'm hoping to use this PC as a file server for my main PC, laptop, my wife's netbook, and as a media server. Now my questions.
Is there a program that can show each HDD and logical dive with their contents no matter the underlying OS? SO if I have Ubuntu on sda1 the software will show I have sda0, sda1 and sda2 and then show WinXP is on sda0, Ubuntu on sda1 and data / files on sda2.

Second: Having already partitioned one HDD into two logical 40 GB drives, is there any software or method that will let me move the complete contents from the second HDD to the first HDD into the unused partition?

---

### Post by papibe on 2010-11-11
If you did a regular install (no the wubu) it is very simple to have access to your Windows partitions in Ubuntu.

Unfortunately, it doesn't work that well the other way around. Windows by itself does not recognize Ubuntu/Linux partitions (ext3/4). There's third party software that may be worth take a look, but I do NOT really know how well they work:

[Three Ways To Access Linux Partitions (ext2/ext3) From Windows On Dual-Boot Systems]("http://www.howtoforge.com/access-linux-partitions-from-windows").

---

### Post by dcstar on 2010-11-12
> **RealGomer said:**
> 
..........
Second: Having already partitioned one HDD into two logical 40 GB drives, is there any software or method that will let me move the complete contents from the second HDD to the first HDD into the unused partition?

gparted

---

