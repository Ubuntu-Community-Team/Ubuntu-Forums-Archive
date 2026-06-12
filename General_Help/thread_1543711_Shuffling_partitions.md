---
title: "Shuffling partitions?"
date: 2010-08-01
forum: General Help
---

### Post by kernalphage on 2010-08-01
Hey there!

I'm trying out Ubuntu as a hobby, but i think i ran into a problem:

I made the Ubuntu partition too small (only about 5 gigs), and it's  starting to pop up with warnings saying that I'm running out of room. 

I have a 1TB drive that is split into the Ubuntu partition and "Swap space" (a media dumping ground for both Linux and Windows to use)
And I've got the 300gig drive that came with my PC that houses Vista and  it's applications.


Is there  a way to expand the ubuntu partition without re-formatting the entire drive? (the terabyte drive still has about 90% free space, if that helps)

---

### Post by dv3500ea on 2010-08-01
Yes, if you insert the ubuntu live CD and reboot into a live session, you can use the partition manager (System -> Administration -> Partition Manager) to shrink the media partition then increase the size of the ubuntu partition.

---

### Post by mcduck on 2010-08-01
Yes, it is possible, but you need to do it from a live-CD (since you can't edit the partition you are actually using at the time), and the exact steps depend on your partition layout. Mainly, to resize a partition the available empty space must be next to that partition. So you may have to move some partitions around to be able to resize the one you want.

Another option, of course, is to create a new partition in the empty space and mount that as /home. That way you'd only have the system stuff on your existing partition and all the currently unused space would be used for our personal files.

Anyway, you can either use Gparted from the Ubuntu CD, or the Gparted live-CD do do the job.

---

### Post by sydbat on 2010-08-01
> **dv3500ea said:**
> Yes, if you insert the ubuntu live CD and reboot into a live session, you can use the partition manager (System -> Administration -> Partition Manager) to shrink the media partition then increase the size of the ubuntu partition.This.

However, before doing this, BACK EVERYTHING UP.

---

### Post by kernalphage on 2010-08-01
> **mcduck said:**
> 
Anyway, you can either use Gparted from the Ubuntu CD, or the Gparted live-CD do do the job.

Yup, I'm typing this from the newly re-partitioned drive.

Everything went smoothly, Ubuntu now has a comfy 100 gigs to itself.

 (The hardest part was finding the boot CD)

Thanks for the quick replies everyone!

---

