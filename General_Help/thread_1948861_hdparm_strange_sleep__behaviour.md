---
title: "hdparm strange sleep  behaviour"
date: 2012-03-29
forum: General Help
---

### Post by djevlen on 2012-03-29
Hello

I want hdparm to put wd 3 tb to spleep on ubuntu 10.04

When hdparm.conf is set to spindown_time = 180 @ 15 minutes it works.

When hdparm.conf is set to spindown_time = 242 @ 1 hour it does not work.

Why some values work some not ?? is this because of the wd disk ?

In case it is the disk, how do i find out which values it will accept ?

Greets
Djevlen

---

### Post by dcstar on 2012-03-30
> **djevlen said:**
> Hello

I want hdparm to put wd 3 tb to spleep on ubuntu 10.04

When hdparm.conf is set to spindown_time = 180 @ 15 minutes it works.

When hdparm.conf is set to **spindown_time = 242** @ 1 hour it does not work.


242 is 20 minutes using the "-S" command:

```
man hdparm
```

---

