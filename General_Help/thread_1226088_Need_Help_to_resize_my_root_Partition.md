---
title: "Need Help to resize my root Partition"
date: 2009-07-29
forum: General Help
---

### Post by Ubersci on 2009-07-29
I'm trying to increase my root partition using gparted from a live CD, i have a root, home, swap and NTFS partition on my second hdd. I want to increase the size of root but it won't let me, i can delete/re-size the NTFS partition and re-size home but i don't think i can re-size my root without deleting my home partition. Does anyone know of a way around this??

---

### Post by CatKiller on 2009-07-29
> **Ubersci said:**
> I want to increase the size of root but it won't let me,

Is your / partition inside an extended partition? It would look like a cyan box around one or more other partitions. You'll need to resize that before you can make any partitions inside it bigger.

---

### Post by Ubersci on 2009-08-18
Sorry late on replying, no its not a extended partition. Its my 2nd HDD with 4 parition. Root, Home, boot and NTFS partitions. Thanks you for your help.
 I discovered that through the GParted Live CD graphical interface you can re-size from both ends of the partition. my fault for not properly looking through the software properly.

---

