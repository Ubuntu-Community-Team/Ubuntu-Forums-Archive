---
title: "Re: Move unallocated space to extended partition"
date: 2012-08-01
forum: General Help
---

### Post by Ravi5kumar on 2012-08-01
Can someone help me with this:

[IMG]http://img826.imageshack.us/img826/4490/devsdagparted004.png[/IMG]

I want to add 7.01 unallocated space to my / partition? Is it possible:confused:? If yes how to do that?

---

### Post by howefield on 2012-08-01
Post moved to its own thread.

---

### Post by Cheesemill on 2012-08-02
It is possible, but it will take a long time.
First make sure you have a backup as any operations involving moving partitions carry an element of risk. Then the procedure would be:

1 - Boot from a Live CD and run gparted.
2 - Right click on sda9 and select Swapoff.
3 - Right click on sda2 and select Unmount (may not be neccesary, ignore if it's already unmounted).
4 - Move sda9 all the way to the right.
5 - Move sda6 all the way to the right.
6 - Move sda5 all the way to the right.
7 - Resize sda2 so that the unallocated space it outside the extended partition.
8 - Move sda1 all the way to the right.
9 - Resize sda3 to use the unallocated space.

---

