---
title: "&quot;Out of Space&quot;"
date: 2012-06-26
forum: General Help
---

### Post by Ubun2to on 2012-06-26
I was given an error on VirtualBox today, and it claimed that, since the hard drive was full, it could no longer run. According to GParted, only 223.40/919.90 GB of space is used.
However, my home folder says there is 3.8 GB of data stored there, and 108.5 KB of free space.
Is the issue that the Home folder has too little space available? If so, how do I resize it?
Edit-I've done some searching, and it appears I need to resize partitions via a live CD, as Wubi only gave me 32 GB. However, I want to know how I am supposed to copy my data.

---

### Post by wildmanne39 on 2012-06-26
Hi, I am not sure if running virtual box is a good idea in wubi but here is a link to resize a wubi partition.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

Also you could use an external drive for data.

I recommend doing a normal install of ubuntu.
Thanks

---

### Post by Mark Phelps on 2012-06-27
> **Ubun2to said:**
> I was given an error on VirtualBox today, and it claimed that, since the hard drive was full, it could no longer run. According to GParted, only 223.40/919.90 GB of space is used.
However, my home folder says there is 3.8 GB of data stored there, and 108.5 KB of free space.
Is the issue that the Home folder has too little space available? If so, how do I resize it?
You can't resize folders as they are not allocated actual sizes.  They grow and shrink as needed.
> Edit-I've done some searching, and it appears I need to resize partitions via a live CD, as Wubi only gave me 32 GB. However, I want to know how I am supposed to copy my data.
Wubi is NOT a partition; instead, it is basically a file installed INTO an existing MS Windows partition.  It isn't the partition size that matters, it's the size of the file (root.disk).  The link provided earlier tells you how to resize the space that a Wubi install uses.

---

### Post by Ubun2to on 2012-06-28
I forgot to mention that I have successfully migrated from Wubi to a new partition (that is much bigger, might I add). I have space for all the stuff I want now.
[http://ubuntuforums.org/showthread.php?t=2011306](http://ubuntuforums.org/showthread.php?t=2011306)

---

### Post by wildmanne39 on 2012-06-28
Hi, I am glad you got it sorted.
Enjoy!!!

---

