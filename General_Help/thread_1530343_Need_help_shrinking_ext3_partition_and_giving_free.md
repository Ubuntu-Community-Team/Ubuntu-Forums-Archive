---
title: "Need help shrinking ext3 partition and giving free space to NTFS."
date: 2010-07-13
forum: General Help
---

### Post by morbid_bean on 2010-07-13
Using a small hard drive (180 GB) dual booting windows XP for gaming and Ubuntu 9.10 for my other stuff during install I didnt know how much of each partition i would use, so i did 50-50  1 for ext3   and one for  NTFS

However after awhile it seems I have run out of space on my NTFS and have tons of unused space on my ext3.

What I am wanting to do is shrink some of that ext3 down and give it it NTFS,  I did a little searching and found a couple of old posts but I was a little sketchey on em.  Simply looking for some personal Methods or Tools you have used and a starting point of how to use them.

---

### Post by cj.surrusco on 2010-07-13
I use a [GParted]("http://gparted.sourceforge.net/") live CD because I do a lot of partitioning, but a normal Ubuntu live CD will also work once you install GParted on it.

---

### Post by Mark Phelps on 2010-07-13
The difference is that the GParted LiveCD will not automatically mount any partitions; the Ubuntu live CD will mount partitions.  

IF you use the latter, you'll have to ensure that the partition you're resizing is unmounted first.

---

### Post by morbid_bean on 2010-07-13
WOW thanks for the blazing fast replies....I was actually downloading Gparted 0.5.2-9 live  right now...have heard alot about it...thanks

---

### Post by morbid_bean on 2010-07-13
ok cool so i used GParted to shrink my EXT3 partition and now I have about 50gbs of extra space I want to give to NTFS, however I cant seem to figure out how to do it.

---

### Post by cj.surrusco on 2010-07-13
Right-click the NTFS partition and choose to resize it. Then drag the partition over the free space.

---

