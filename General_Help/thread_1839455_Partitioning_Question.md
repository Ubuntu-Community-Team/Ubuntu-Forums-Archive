---
title: "Partitioning Question"
date: 2011-09-05
forum: General Help
---

### Post by Thedark7 on 2011-09-05
Let's say I have 3 partitions and unallocated space, in this order:

System
Windows Partition
Recovery Partition
Unallocated Space


How would I give the unallocated space to the Windows partition? I'm using EASEUS Partition Master Home Edition. Thanks!

---

### Post by Hugh971 on 2011-09-05
use gparted in ubuntu (you can use the live CD as it looks like you don't have an ubuntu partition by what you've said above).

In there you can move the recovery partition to the end of the disk (or remove it if you don't need it) and then expand the windows partition to use the rest of the disk.

---

