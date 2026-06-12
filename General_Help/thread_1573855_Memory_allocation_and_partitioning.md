---
title: "Memory allocation and partitioning"
date: 2010-09-13
forum: General Help
---

### Post by Optimus_Jazz on 2010-09-13
I can't seem to figure this one out..I'm attempting to partition ubuntu 10 with windows 7(which was already previously installed).

However when I run the ubuntu disk, and select "install side by side" in the installation menu the max I can give for windows is 10.GB, but I am trying to partition so windows has access to half the hard drive.Has anyone got any clues to what might be the problem?

---

### Post by Optimus_Jazz on 2010-09-13
bumps

---

### Post by Mark Phelps on 2010-09-13
First of all QUIT BUMPING!  The polite rule around here is bumping at most once a day; not once an hour!

Second, use the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. And then, select the "largest free space" option when installing Ubuntu to allow it to do the necessary partitioning.  Do NOT use the Ubuntu installer to shrink the Win7 OS partition.

Also, do you know how many partitions you already have on your machine? IF not, open a terminal (when in LiveCD mode) and run the command "sudo fdisk -lu" (that's a lowercase L, not a one).

If you see four partitions, you already have the maximum number allocated and can't create any.  You will then be faced with a LOT of work to install Ubuntu because you will have to repartition your drive.

Oh, and by the way ... you need to get your terms straight.  Partitioning deals with disk usage, not memory allocation.

---

