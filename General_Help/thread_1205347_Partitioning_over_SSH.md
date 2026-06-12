---
title: "Partitioning over SSH?"
date: 2009-07-05
forum: General Help
---

### Post by TheForkOfJustice on 2009-07-05
I want to format a partition on my fileserver but want to do it over SSH if I can.

Gparted doesn't recognize partitions over SSH so is there another way?

---

### Post by t4thfavor on 2009-07-05
fdisk or cfdisk 

cfdisk /dev/sdc1 etc, you get the idea, I hope.

---

### Post by TheForkOfJustice on 2009-07-06
Ah, of course.  Duh.

Wouldn't this work too?:

mkfs -t ext3 /dev/sdb3

---

