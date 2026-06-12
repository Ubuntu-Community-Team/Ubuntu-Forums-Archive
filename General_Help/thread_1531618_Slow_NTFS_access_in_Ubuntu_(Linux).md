---
title: "Slow NTFS access in Ubuntu (Linux)"
date: 2010-07-15
forum: General Help
---

### Post by kapetr on 2010-07-15
I'm often cutting video files (dumped from DVDs) in AVIDEMUX - without reencoding (copy A/V).

So it can be very fast by saving file.

**The problem is:**

When I use NTFS partition to save file (especially if source is on this partition too), then the "frames per second" is **up to 4x slower** then if I use ext3/4 partition.

The system is totally loaded from **/sbin/mount.ntfs** - system and user time - not device waiting.

Does anybody know, why is disk access to NTFS in Linux **so terrrrrrible  SLOW** ?

Thanks

--kapetr

---

