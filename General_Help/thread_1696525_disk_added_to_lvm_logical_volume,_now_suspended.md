---
title: "disk added to lvm logical volume, now suspended"
date: 2011-02-27
forum: General Help
---

### Post by soulburn on 2011-02-27
Dear people,

I have the following problem.

I have a Ubuntu server running at home serving as NAS.
My mediaserving logical volume ran out of space.
To fix that I bought a harddisk and did the following.

1. run pvcreate to create a physical volume.
2. run vgextend to add the new physical volume.
3. run lvextend to let the specific logical volume use the space.

I now have the following situation.

- I see the physical volumes including the new one.
- The volumegroup is also showing 2 physical volumes.
-  The logical volume is also showing the all the allocated physical extents.

The problem is that I can't mount it as the logical volume is marked as suspended.

I probably did something stupid but what am I missing.
Is there some way to recover the data from that logical volume.
Regarding manuals and googling, I have already spent some time googling the internet.

Maybe someone has gone through this before and knows something that can be done.

---

