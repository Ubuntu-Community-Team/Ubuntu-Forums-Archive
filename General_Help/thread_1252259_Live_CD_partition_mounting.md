---
title: "Live CD partition mounting???"
date: 2009-08-28
forum: General Help
---

### Post by nunrgguy on 2009-08-28
Trying to resize some partitions. If running Ubuntu live CD why would Ubuntu hdd partitions be locked?

Have tried running gparted live cd rather than Ubuntu live cd but it doesn't even see the drive (Esata, bootable controller card).

---

### Post by bodhi.zazen on 2009-08-28
The Ubuntu Desktop (live) CD will mount a swap partition if it finds it. If the swap is in an Extended partition, the extended partition will be locked as well.

It is a trade off, makes it hard when running gparted, easier for most everything else.

---

### Post by nunrgguy on 2009-08-28
So I'd need to swapoff and then unount partition?

---

### Post by P4man on 2009-08-28
partitions wont be mounted automatically in a live cd, so you only need to unmount it,... if you mounted it earlier :) For the swap, swapping off is enough. I guess its like "unmounting" swap.

One more thing that might be the problem: if  the ubuntu and/or swap partitions are inside an extended partition, then you need to resize that extended partition first. An extended partition is like a container for other partitions.

---

### Post by nunrgguy on 2009-08-28
OK. That's great. Thanks

---

