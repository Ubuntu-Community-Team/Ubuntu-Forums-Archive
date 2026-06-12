---
title: "Check Partition State"
date: 2010-06-13
forum: General Help
---

### Post by slash86 on 2010-06-13
Hi,

how do i check my partition states without a live cd???
can i 'schedule' it so the partitions are checked before boot???
how do i proceed to check my partitions while logged and without a livecd?

tks.

---

### Post by Ozymandias_117 on 2010-06-13
If you use ```
fsck -n
``` it will only check for problems, and not actually FIX the problems, which should be safe to run while the system is up.

---

