---
title: "dd if=/dev/sda  of=/dev/sdb"
date: 2011-09-15
forum: General Help
---

### Post by deniro on 2011-09-15
dd if=/dev/sda of=/dev/sdb
 
is it copying whole sda bit by bit(including free space) or just copy data on /dev/sda?

---

### Post by Slim Odds on 2011-09-15
> **deniro said:**
> dd if=/dev/sda of=/dev/sdb
 
is it copying whole sda bit by bit(including free space) or just copy data on /dev/sda?

everything including free space

---

### Post by deniro on 2011-09-15
very good.. thx
can I use  rsync   after  dd copy (to sync after some time)?

---

### Post by Slim Odds on 2011-09-15
> **deniro said:**
> very good.. thx
can I use  rsync   after  dd copy (to sync after some time)?

That should work fine once you mount /dev/sdb? somewhere

---

### Post by dcstar on 2011-09-16
> **deniro said:**
> very good.. thx
can I use  rsync   after  dd copy (to sync after some time)?

Not until you change the UUID of the partitions in the copied disk so that they are different from the originals.

---

