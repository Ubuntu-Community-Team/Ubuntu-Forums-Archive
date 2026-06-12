---
title: "How to safely resize filesystem partition?"
date: 2010-08-06
forum: General Help
---

### Post by revered on 2010-08-06
I need to resize an ext4 filesystem partition, How can I do it being sure it wont get f#@ked up?

Is it safe to do it using a gparted live cd?

---

### Post by Mark Phelps on 2010-08-06
Yes, it is.  

But be aware that GParted is very s...l..o..w. So, be prepared for this to take HOURS, and make sure your machine stays powered on the whole time.  And, do NOT interrupt it.

Also, generally a good idea to take backup of anything you don't want to lose before you start.

---

### Post by revered on 2010-08-06
> **Mark Phelps said:**
> Yes, it is.  

But be aware that GParted is very s...l..o..w. So, be prepared for this to take HOURS, and make sure your machine stays powered on the whole time.  And, do NOT interrupt it.

Also, generally a good idea to take backup of anything you don't want to lose before you start.

Is there something faster (and still safe) besides GParted?

Or is there a way to backup the ext4 partition from another disk with WinXP? Because I can't read that hdd that has winxp from lucid, the disk has some errors and after ubuntu starts it changes capacity from 40 to 0 (i tried a chkdsk and some other stuff but still cant get it working) :(

I need to resize a 50gb partition to 80-100gb, my virtual machines are filling up all my disk, i have only 3.3gb of free space lol.

---

### Post by agarzon on 2010-08-06
50 Gb partition shouldn't take that long. It also depends on how full the partition is.

---

