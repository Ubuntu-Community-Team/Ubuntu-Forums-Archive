---
title: "How to quietly skip non-ready drives during boot?"
date: 2011-02-03
forum: General Help
---

### Post by recluce on 2011-02-03
I am running a notebook that sometimes sits in a docking station that provides additional eSATA drives. I would like to auto-mount the partitions on one of these drives if and only if they are present at boot time. If not present, they should be skipped silently.

So far, I tried to add the "nofail" switch to the fstab entries for these partitions, but I still get a requester at boot time for each partition: "The drive for /media/xyz is not ready, press S to skip or M to fix manually" if the drive is not present.

Any ideas?

---

### Post by psusi on 2011-02-03
Why don't you just leave them mount automatically when you access them?

---

### Post by recluce on 2011-02-04
I found the solution on another forum.

Instead of "nofail" the option to use is "nobootwait" - and it works. I am not sure though what nofail is good for, though.

---

