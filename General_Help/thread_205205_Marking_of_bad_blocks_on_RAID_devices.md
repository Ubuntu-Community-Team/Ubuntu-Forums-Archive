---
title: "Marking of bad blocks on RAID devices?"
date: 2006-06-28
forum: General Help
---

### Post by hubick on 2006-06-28
Hi.

Let's assume what is generally a reality, that hardware is crap, and any storage device will accrue some bad blocks eventually.

So, instead of one, I buy two of equal size, and use RAID 1 to created a mirrored array.

It is my empirical observation that If the kernel fails in an attempt to write to either of these devices by encountering a bad block, it removes that device from the array and marks it as failed.

It is also my understanding that with a normal filesystem like ext3 on a drive, if a device block fails, the filesystem will mark that block as bad, write the data somewhere else, not use that block in the future, and continue happily on its merry way.

My question is this... given our previous assumption that all hardware will eventually have blocks fail, it seems as though a normal filesystem is more tolerant of this, and capable of working around this eventuality better than the RAID array.  The normal filesystem can have 10 or 100 bad blocks on a device, while continuing to be perfectly usable, but as soon as the RAID setup encounters a *single* bad block on each of it's constituant devices, you are apparently screwed?

I would guess that, given a RAID 1 array containing two devices of equal size, that the array needs all the blocks on both devices to be working, else it would have nowhere to mirror the extra working blocks from one device when blocks on the other fail?  Or...

Does a Linux software RAID array keep some extra unformatted space for marking bad blocks?

If so, why are my devices being marked failed and removed from the array when encountering what apparently by the logs is a single bad block, rather than said extra space being used?

Or... what am I missing?

Much Thanks!

---

