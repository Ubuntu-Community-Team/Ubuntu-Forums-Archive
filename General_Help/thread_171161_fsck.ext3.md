---
title: "fsck.ext3"
date: 2006-05-06
forum: General Help
---

### Post by physcsdrk on 2006-05-06
When I boot ubuntu it gives me an error message that says:

[I]fsck.ext3: No such file or directory while trying to open /dev/sdb2

/dev/sdb2
The superblock could not be read or does ot describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:

e2fsck -b 8193 <device>[/I]

Then I have to press ctrl-D to get it to continue booting.

I am not sure exactly what this means.  I cannot remember exactly how i partitioned but here is some background:
I had ubuntu installed, I played with my monitor settings and then I couldn't get it to show anything on my screen so I re-installed earlier today.  I am dual booting with windows xp.  I have three hard drives, two internal, one external. 
My hard drive that I boot form is a SATA drive and I belive ubuntu calls my windows partition (the first one on the drive as I installed windows first) sdb1.
When I reinstalled I had two partitions on the drive from the previous install of ubuntu.  I deleted both of those and then I chose to have ubuntu automatically install into the free space.  I believe it gave me two partitions, one root and one swap.  It did like 6GB of swap and then 120 of root.


Thats everything I know.  If anyone could help me I would greatly appreciate it.

---

### Post by physcsdrk on 2006-05-06
Ok, so I was poking around, found the disks manager and figured out a few things.  
My hard drive that I boot from is named sda and my backup drive is named sdb.  My ext3 partition on the backup drive is in the second partition, thus sdb2.  
Maybe there was a better way to partition it?  I don't know.  It might be worth noting...I don't always have the external on.  I usually turn it on once a week and backup.  I got the error message posted above twice when booting into ubuntu.  The first time the drive was on.  The second time it wasn't.
When I did have it on it wouldn't let me write to it.  It said it was a read only drive. 

Any ideas on how to get the drive working properly with ubuntu?

---

