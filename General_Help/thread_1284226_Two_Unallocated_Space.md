---
title: "Two Unallocated Space"
date: 2009-10-06
forum: General Help
---

### Post by Mutil8r on 2009-10-06
Hi, I have one unallocated space worth 45GB and another 145GB. Is there anyway to merge them?

---

### Post by CatKiller on 2009-10-06
Why would you want to? What's the advantage of having unallocated space?

Anyway, unallocated space is just a hole where there's no partition. Move the partitions around and the hole magically moves the other way. Use Gparted from a live cd.

---

### Post by sir_cheats_a_lot on 2009-10-06
I would suggest caution here.  the fact that they listed two seperate unallocated partitions, would suggest two seperate hard drives.  if this is the case you wouldn't be able to merge them to begin with. the problem with merging partitions is, it's not always safe to do so.  since you are dealing with unallocated space(no partition), you would first need to create a partition in that space and then format it. then you can actually USE the space.
   The question is: what is on each of the drives, and how could you best put the unused space to use?  you could make one a partition for backing up files, or just use it as space to move files back and forth between windows and linux(if you still have windows installed). I did the Latter for the longest time until i discovered the ex2/3 installable file system for windows, which allowed me to move things directly from each side to the other :).  Any way, best thing to do, is **_if you have windows _**installed on the drive with the smaller unallocated space available, i'd create and format the unallocated to an ntfs partition and just merge it with the windows partition.  the other i'd probably just make your other partitions a bit bigger to use up some of the space and the rest make a backup partition just for your personal files.

---

