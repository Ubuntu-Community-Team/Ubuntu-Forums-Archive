---
title: "Out of space :o"
date: 2009-08-21
forum: General Help
---

### Post by SpriteSODA on 2009-08-21
Hi guys,
My ubuntu is almost out of disk space - 100MB left on the partition. I've got plenty more on the HD, but I can't seem to resize my ubuntu's ext3 partition! (trying with Gparted in a Gparted live cd - it only gives me the option to shrink it Oo)

How can I solve this hassle?

---

### Post by Bachstelze on 2009-08-21
Moved to General Help. Can you post a screenshot of your GParted?

---

### Post by eldragon on 2009-08-21
> **SpriteSODA said:**
> Hi guys,
My ubuntu is almost out of disk space - 100MB left on the partition. I've got plenty more on the HD, but I can't seem to resize my ubuntu's ext3 partition! (trying with Gparted in a Gparted live cd - it only gives me the option to shrink it Oo)

How can I solve this hassle?

is it at the end of the hdd?

how about shrinking the partition behind first?

---

### Post by P4man on 2009-08-21
I bet the ubuntu partition is contained inside an extended partition (light blue border IIRC). You'll have to unmmount all partitions, and swapoff the swap partition if its inside the extended (right click, unmount, or swapoff). Then you can grow the extended partition first (its like a container), then you can move/grow the other partitions inside it.

---

