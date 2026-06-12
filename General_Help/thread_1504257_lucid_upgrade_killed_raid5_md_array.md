---
title: "lucid upgrade killed raid5 md array?"
date: 2010-06-07
forum: General Help
---

### Post by spotter on 2010-06-07
I'm a bit sick to my stomach right now.

I had a raid5 array (5x1.5TB drives) and I upgraded to lucid and now the array no longer works.

Initially, on boot, it would try to mount it from fstab and that failed consistently as it wasn't assembling it.

then I tried to assemble it by hand (--scan) and that seemed to cause it to mount degraded (it seems md in the process tried to use on of the disks for something else!), but when I look at its partition table, it's empty.

pretty pissed at the moment (somewhat at myself, didn't really need to upgrade), any ideas what went wrong?

---

### Post by spotter on 2010-06-07
raid5 isn't dead.

it was that lvm wasn't kicking in.  still having issues adding the drive lucid killed back to it (killed because it was trying to use it by itself in an md_d0 array instead of the normal md0 array)

---

### Post by spotter on 2010-06-07
managed to add the overwritten drive back into array, now rebuilding.  going to take awhile.

then to figure out why its not being assembled on boot.

---

