---
title: "RAID array showing two drives?"
date: 2009-12-26
forum: General Help
---

### Post by nemesis99 on 2009-12-26
I'm in the process of building a simple server with an Adaptec 1220SA RAID card.  I have two 320GB drives configured in a RAID1 array on the card itself.  When I load a live cd of 9.10 (32bit), GParted sees two drives, /dev/sda1 and /dev/sdb1.  I'm configured here.  How is the live cd seeing the two drives?  I've always been under the impression that the RAID card will present a single logical disk to the OS based on the way I configured it.

---

### Post by QrK0 on 2009-12-28
Maybe you have to load the raid card driver?

---

