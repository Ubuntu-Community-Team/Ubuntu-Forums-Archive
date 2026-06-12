---
title: "Merge NTFS partitions without formatting?"
date: 2010-04-23
forum: General Help
---

### Post by kahlil88 on 2010-04-23
My friend has a 1TB external hard drive with two NTFS partitions and he wants to combine them into one. Is it possible to merge them together?

---

### Post by Revolutionary101 on 2010-04-23
I don't think you can merge them. 

What you should do is resize partition #1 to as big a size as you can get it. Copy files from partition #2 to partition number #1. Once you have copied all of your files over just delete partition #2 and resize partition #1 to take up the whole drive.

This may take a while because you might have to resize one partition several times.

---

### Post by Mark Phelps on 2010-04-23
If you use GParted to do this, be prepared to wait a LONG TIME -- I mean, into several HOURS for this to complete.  If you lose patience and turn the machine off before it's done, you will corrupt your partition tables and risk losing everything in the partition(s).

---

### Post by kahlil88 on 2010-04-23
I was hoping to avoid doing it that way, especially because the larger partition is toward the "right" side and is basically full. It seems like it would be possible somehow to merge them since they use the same filesystem and there aren't any partitions in between them. Is there at least a way to resize "left" without it spending hours moving the data over?

---

### Post by john newbuntu on 2010-04-24
Wow, 1TB drive and using Gparted to shrink and grow.  Are we talking days here for the operation to complete?  I hope someone who has done this can pitch in.

If you decide to go the gparted way, are you better off backing up the files some place (compressed of course) and then just deleting the 2 partitions, create a new one and then restoring the files?  Does anyone think this would be a bit faster?
I am assuming there are no OS's involved in the partitions.

---

### Post by dcstar on 2010-04-24
> **kahlil88 said:**
> 
.......
It seems like it would be possible somehow to merge them since they use the same filesystem and there aren't any partitions in between them.

No. Disk Partitions of any type are stand-alone databases that are not - and never have been - designed to be "merged".

They have their own individual structures and any "merge" would probably require space on one filesystem to be used by the other before all the data was would moved off.

Shrink the smallest partition to minimum then expand the other partition as much as you can. Then copy all (or as much as possible) data from the small to the large partition. Repeat the procedure until the small partition is empty and then delete it.

---

### Post by coffeecat on 2010-04-24
Just to add a thought:

Personally I would never shrink or expand a partition unless I had already backed up all the data. As others have pointed out - this could take hours, even days, on such large partitions. Can you be sure that you won't suffer a power cut in that time?

So - if the data is backed up, one might just as well reformat the whole drive and then copy everything back on again, as john newbuntu has suggested. If your friend doesn't have/can't afford a backup drive large enough, ask them: which is more valuable, the data or the cost of a spare drive?

Sorry to be so blunt, but this issue of the relative cost of personal files and hardware is important.

---

