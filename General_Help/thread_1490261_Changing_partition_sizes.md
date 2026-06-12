---
title: "Changing partition sizes"
date: 2010-05-22
forum: General Help
---

### Post by PepeLapiu on 2010-05-22
Okay, I have a 500 GB H.D.D. and on it, I have a 250 GB partition for windoze and a 250 GB partition for Ubuntu.

How do I shrink my windoze partition to 20 GB and expand my Ubuntu partition to 480 GB?

Thanx,
PepeLapiu :P

---

### Post by jamesisin on 2010-05-22
You can use GParted to move partition boundaries.  You cannot do this on a mounted drive so you'll have to either use the Ubuntu Live CD or get the GParted live CD.

In either case, you will first shrink the Windows partition and apply that, then you will expand the Ubuntu partition and apply that.

Oh, and be very careful as you can wipe things out.  Have you backed up recently?

---

