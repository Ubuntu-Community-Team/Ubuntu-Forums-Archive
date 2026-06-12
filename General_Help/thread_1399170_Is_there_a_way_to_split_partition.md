---
title: "Is there a way to split partition?"
date: 2010-02-05
forum: General Help
---

### Post by drabina on 2010-02-05
I have Ubuntu (command line only) installed as a part of XBMC Live installation. My disk is 1TB that's currently partitioned like this:

10GB root
2GB swap
950GB media

Is there a way to split the existing 950GB partition into two (900GB and 50GB) without altering or moving the data that's currently on it?

Thanks.

---

### Post by Teunis on 2010-02-05
The problem is a partition needs to be unmounted before splitting, you cannot split a mounted partition.

Start up from a Gparted Live CD and do the repartitioning.

---

### Post by audiomick on 2010-02-05
The easiest way would be to boot into the live CD.
start gparted
system> administration> gparted
Shrink down your media partition, create a new partition in the resulting empty space.
If you want to have the new partition mounted at boot, you will have to change fstab, I think, but I am not sure on how to do that.

You should back up anything critical before you start any partitioning operations. It shouldn't cause any problems, but there is always a small risk of data loss.

---

### Post by drabina on 2010-02-05
Unmounting the partition shouldn't be any problem. It contains only movies and music. XBMC and Ubuntu are installed on the 10GB root partition.

I will try to do it with gparted. Hopefully, I will not mess anything up.

---

### Post by audiomick on 2010-02-05
> **drabina said:**
> Unmounting the partition shouldn't be any problem. It contains only movies and music. XBMC and Ubuntu are installed on the 10GB root partition.

I will try to do it with gparted. Hopefully, I will not mess anything up.

I think a right click after selecting the partition in gparted will offer you the option to unmount.

I think you will still have to add the new partition to fstab when you are finished, but I am not sure.

Good luck!

---

