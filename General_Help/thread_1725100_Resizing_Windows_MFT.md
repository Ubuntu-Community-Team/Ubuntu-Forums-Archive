---
title: "Resizing Windows MFT"
date: 2011-04-09
forum: General Help
---

### Post by stracky on 2011-04-09
I have a DELL Inspiron 1545
It has a 160 GB hard drive and 2 GB of RAM
I dual boot between Windows XP and Ubuntu 10.10
My partitions are set up as follows:

I want to shrink the windows partition because I am out of space in Ubuntu
(The unallocated space is reserved for something else)

[IMG]http://dl.dropbox.com/u/5992804/partition.png[/IMG]

[SIZE=3]**My Windows partition is mostly defragged, except for a large Master File Table at the end**[/SIZE]

[IMG]http://dl.dropbox.com/u/5992804/HDDmap.JPG[/IMG]

[SIZE=3]**What i want to know is: what is the safest way to deal with this**[/SIZE]

---

### Post by dragonfly41 on 2011-04-09
I've just gone through this process of resizing Vista partition on Dell Inspiron 1720 and then installing ubuntu.

This might be helpful .. 

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Mark Phelps on 2011-04-09
Since it's XP, not Vista or Win7, you should be able to resize the partition using GParted without problems.  You just need to ensure that the partition is NOT mounted when you launch Partition Editor.

Since Partition Editor is generally NOT installed by default in Ubuntu, you should install it.

As always, anytime you mess around with partitions, it's prudent to make a backup before doing that -- just in case.

---

### Post by dragonfly41 on 2011-04-09
Yes .. it seems that it's Vista not XP which sometimes has problems coexisting with ubuntu.   

I missed the point that you have XP.

I used this tool burned onto bootable CD for partition juggling.

[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

It contains partition editor and a bunch of other useful tools such as testdisk.   Use option 1 from menu at launch.

---

### Post by stracky on 2011-04-09
I was not aware that the XP MFT could just be moved with GParted

To be on the safe side, I used the free trial of the non-free PerfectDisk defragmenter, which is suppose to be able to move MFT

It resized from 100 GB to 50 in about 5 seconds - Defragging paid off after all :D

Thanks!

---

