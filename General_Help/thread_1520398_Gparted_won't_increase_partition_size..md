---
title: "Gparted won't increase partition size."
date: 2010-06-29
forum: General Help
---

### Post by Ububtubobl on 2010-06-29
I copied 10.4 from a 20gig hd. onto an 80 gig hd with Clonezilla and now I can't get Gparted to expand the partition to include the 50 gig that is unallocated. Obviously I cloned the drive incorrectly. Can any one suggest how I might move the partition without losing the data? Thanks in advance.

---

### Post by dino99 on 2010-06-29
[http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live](http://www.howtoforge.com/back-up-restore-hard-drives-and-partitions-with-clonezilla-live)

---

### Post by Mark Phelps on 2010-06-29
> **Ububtubobl said:**
> I copied 10.4 from a 20gig hd. onto an 80 gig hd with Clonezilla and now I can't get Gparted to expand the partition to include the 50 gig that is unallocated. Obviously I cloned the drive incorrectly. 
No ... when you "clone" a partition, it is supposed to make a copy the same size as the original... which is apparently what it did.  It will leave the unused space as unallocated.

> Can any one suggest how I might move the partition without losing the data? Thanks in advance.
You can't "move" a partition from one device to another, but you can copy it from one device to another and then remove it from the original device.

---

### Post by drs305 on 2010-06-29
As was mentioned, the cloned partition will be the same size as the original unless special steps are taken.

That does not mean that you cannot expand the new partition to incorporate the unallocated space. However, you cannot do it while running Ubuntu normally. You must run Gparted from a LiveCD, gparted CD, system rescue CD, etc. Additionally, even when run in this manner you will need to unmount the swap partition, which is mounted even when using the LiveCD.

There are some guidelines on changing the size of the / partition, if that is what you are trying to do, about half way down the first post of this thread:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by Ububtubobl on 2010-06-29
Thanks all for your input. I am running gparted from a live gparted cd. I have relocated the linux swap file to the end. The unalocated partition is enclosed in a blue box, the ubuntu partition is enclosed in a broken yellow and green box. None of the partitions seem to be mounted (They are grayed out). Neither dragging box sides or entering new partition sizes in appropriate boxes will allow an increase in the partition size. This is the first time I have used gparted and I understood that it would allow me to absorb the allocated space into the primary partition. I am obviously not intuitive enough.

---

### Post by plucky on 2010-06-29
> **Ububtubobl said:**
> Thanks all for your input. I am running gparted from a live gparted cd. I have relocated the linux swap file to the end. The unalocated partition is enclosed in a blue box, the ubuntu partition is enclosed in a broken yellow and green box. None of the partitions seem to be mounted (They are grayed out). Neither dragging box sides or entering new partition sizes in appropriate boxes will allow an increase in the partition size. This is the first time I have used gparted and I understood that it would allow me to absorb the allocated space into the primary partition. I am obviously not intuitive enough.

If you can please post a screen shot of your gparted window.

---

