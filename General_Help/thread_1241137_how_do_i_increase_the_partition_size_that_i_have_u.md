---
title: "how do i increase the partition size that i have ubuntu installed on?"
date: 2009-08-15
forum: General Help
---

### Post by rhythmiccycle on 2009-08-15
i have ubuntu 9 installed with in xp.

I want to take some of the space from the xp partition, and give it to the ubuntu partition.

how is this done.

---

### Post by yeeeev on 2009-08-15
You can do this using gparted/partition-editor from a live CD.
Using that you can resize partitions. A backup and windows "chkdsk -f" is highly recommended before any partition resizing (even though I never had any problems with it)

---

### Post by cmost on 2009-08-15
Use your Ubuntu Live CD to boot your machine.  Then use Gparted to shrink the XP partition by X GB.  Then, simply expand the Ubuntu partition by the same X GB.  Be careful!  Make sure you backup any important data before you attempt this!!

*** Edit:  Yeeev, you beat me to the punch!  ***

---

