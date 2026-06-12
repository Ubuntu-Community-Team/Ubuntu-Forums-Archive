---
title: "Reserving an amount of disk space for a specific folder"
date: 2011-09-06
forum: General Help
---

### Post by MG2R on 2011-09-06
I was wondering if it was possible to reserve a specific amount of disk space for a specifc folder.
i.e.: on sdc5 there is a folder *reserved* that should have 3 GB of disk space available at all times (thus limiting the amount of space given to other files on sdc5).

Is that possible, or should I create a seperate partition for folder?

---

### Post by aeiah on 2011-09-06
its possible, yea. you'd have to set up a disk quota. quotas dont reserve space though, so really you'd have to set everything except *reserved* to have a quota that is 3gb less than the total, if you understand what i mean.

it may be easier to create a partition instead though

---

### Post by MG2R on 2011-09-06
OK, thanks for the quick reply!

---

### Post by SecretCode on 2011-09-06
Without messing about with your real partitions, you might be able to achieve the same thing by creating a 3GB file, and mounting it as a loopback file system at /path/to/reserved (see [Mount - Community Ubuntu Documentation](https://help.ubuntu.com/community/Mount)).

---

### Post by SecretCode on 2011-09-06
I thought of adding "but I haven't tested it" to my post above, but instead, I tested it. Works fine.

Advantages: quick and easy. Doesn't require rebooting or using a live CD. Utilities like df report the free space and utilisation meaningfully. 

Disadvantages - basically the same as with real partitions: you can't change the space allocation on the fly (although it's a lot easier this way than with a partition). You can't exceed the allocated space. And somebody, or some tool, is bound to get confused at some point!

---

### Post by MG2R on 2011-09-06
> **SecretCode said:**
> Without messing about with your real partitions, you might be able to achieve the same thing by creating a 3GB file, and mounting it as a loopback file system at /path/to/reserved (see [Mount - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Mount")).

This is perfect! I can even move the file to different disks! Thanks a lot!

---

