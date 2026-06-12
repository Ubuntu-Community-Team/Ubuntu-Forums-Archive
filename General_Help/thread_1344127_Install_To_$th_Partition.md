---
title: "Install To $th Partition"
date: 2009-12-02
forum: General Help
---

### Post by jawadahmed on 2009-12-02
I have one sata 320 Harddisk. I have three primary partitions and left some free space (about 10 gb).
My question is that will Ubuntu install into this only free space creating its own partitions for swap etc (i am newbie).

The free space is between xp (first) partition and other partitions.
The final harddisk condition will be like
Xp==Ubuntu==Partition3==partition4

---

### Post by bodhi.zazen on 2009-12-02
Should be able to install Ubuntu into that space. Ubuntu does need two partitions, one for "root" or / and another for swap.

Personally I use gparted (it is on the desktop CD) to make partitions , then install into those partitions.

To have more then 4 partitions you will need an extended partition.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

