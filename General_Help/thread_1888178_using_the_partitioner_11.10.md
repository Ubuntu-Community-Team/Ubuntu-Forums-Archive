---
title: "?using the partitioner 11.10"
date: 2011-11-28
forum: General Help
---

### Post by sdad46 on 2011-11-28
I want to replace a window's 7 installation but I want to leave the 20g restore partition intact. Opening the installation I am directed to partitioner where I chose to set up my own partitions.  I see the restore partition and the target partition.  I want a 220 gb ext4 partition that I elect to format and set to "\" .  The original win 7 was 232+gb, so I was going to use the remaining 12 gb for swap space.  In setting up the 220gb ext4 partition I ended up with 12gb being reported as unusable!  And it is!!! How do I recover that 12 gb of space and then assign that space as swap?  

Things don't seem to be setting up as they useta did!

---

### Post by MG&amp;TL on 2011-11-28
Did you set the 12GB to be formatted as swap?

12GB is a little excessive...4GB is more than enough.

---

### Post by dabl on 2011-11-28
I like to separate partitioning from installation, for just such reasons.

Make a [Parted Magic](http://partedmagic.com/doku.php) Live CD or USB stick, and boot that.  Open the partition editor (yes, it is GParted) and take a look at your drive.  It should be fairly obviously which is the recovery partition that you need to keep, and which are the others that you want to delete.  Starting at the bottom partition in the graphic, delete the ones you don't want, and click "Apply". When the only one left is the recovery partition, then you can make a new partition for your new OS, and format it ext4, and leave enough room for a reasonable (2 GB) swap partition, plus any other partitions that you want.  Once you have done these tasks, THEN boot your Ubuntu Alternate Install CD and it will be easy and straightforward to simply install the OS.  :guitar:

---

### Post by sdad46 on 2011-11-28
Thanks guys.  #1,  I realize swap is a bit much. ...... So I went and increased the size of my ext4 partition to include the unusable space.  It did do that. Then I deleted that entire partition and that returned my space to being unused, instead of unusable.  Dialed in from there.  BTW, I ended up with just under 8 gb of swap.  I do have some huge files I play with and inside a vm environment.  I do use that swap space.

---

