---
title: "can't create extended partition with gparted"
date: 2006-03-21
forum: General Help
---

### Post by vayu on 2006-03-21
My Ubuntu partition is filled.  I'm trying to rearrange my space.  I have 3 partitions.  One is free, one has Ubuntu on it.  The Ubuntu partition is divided into / and swap.  I'm trying to merge the free partition with the Ubuntu partition.  There is no option to to that.  So next step I've tried to break up the free partition into 3 logical partitions where I will then format them ext3 and mount some of the Ubuntu directories on them.  It won't let me create 3 logical partitions on it.  It is a primary partition.

---

### Post by akiro.yamamoto on 2006-03-21
Can you post your partition layout and attach a pic of gparted as well... ;)
So we can make some educated recommendations.

---

### Post by vayu on 2006-03-22
Here's a screenshot of gparted.  

hda1 is Windows 98, hda4 is the free space that I would like to include as part of the Breezy install which is on hda2.  I do not have anything on hda4 yet.  That partition could be freed and attached to hda2 or the swap if gparted would let me.

Since I couldn't seem to merge hda2 with hda4, what I was going to do is make it into three logical partitions.  Then each one could be mapped to the most used areas of hda2 using fstab.  /home is only taking 100MB  so I was going to use /usr/lib which is using 800MB and /usr/icantrememberrightnow which is taking 700MB.  I thought if I mapped those to new partitions then I'd have another 1.5 GB free for the whole system.  (This is for my 5 yr olds PIII computer)   

(There's a tiny little bit of free space next to hda4 that for whatever reason gparted would not let me include as part of the partition without errors.)

---

### Post by plors on 2006-03-22
not really an answer to your question, but you should start using a newer gparted. check [this]("http://gparted.sourceforge.net/livecd.php") out for example.

good luck!

---

