---
title: "Safe to resize home partition?"
date: 2010-08-27
forum: General Help
---

### Post by keypox on 2010-08-27
I want to resize my home partition and have other partitons before and after it.  Would it be safe to boot into live cd and use gparted to resize?

---

### Post by xjesse on 2010-08-27
In all honestly resizing a partition with data is never flawless. However, using the live CD with GParted would be the way of doing this.

I would back up any sensitive data before playing around with GParted in the case the worst happens. Maybe someone can shine some more light on this subject for you.

Over all, good luck!

---

### Post by deserthowler on 2010-08-27
Gparted works fine for that.  From what I understand, you want to shrink your partition.  I wouldn't move it as that isn't necessary.  It takes a lot of time to move the partition and could result in the partition being scrambled.  Just add the partitions after it if you can.

I use the latest gparted live CD.  I use it instead of the live Ubuntu CD.  I resized several times with the live gparted CD and shrinking partitions with data and adding partitions is no problem.  Moving them, as I said, is risky and usually unnecessary.

Earl

---

### Post by keypox on 2010-08-27
Thanks, so no UUID problems?  Does ubuntu still use UUIDs?

---

### Post by deserthowler on 2010-08-27
> **keypox said:**
> Thanks, so no UUID problems?  Does ubuntu still use UUIDs?

I haven't run into any UUID problems.  Are you going to use these partitions to run other Linux distros or as special storage?

Earl

---

### Post by keypox on 2010-08-28
> **deserthowler said:**
> I haven't run into any UUID problems.  Are you going to use these partitions to run other Linux distros or as special storage?

Earl

actually other partitions behind this home part that i want to resize are just test partitions for the 10.10 alphas.  So they can be deleted.  As I want to test the beta next week anyways.

---

### Post by keypox on 2010-08-29
Ok i did it.  I did get an UUID error, but it went away and booted fine.

---

