---
title: "best way to span 2 drives"
date: 2010-12-03
forum: General Help
---

### Post by MonsterMaxx on 2010-12-03
I have two 1TB drives I want to span for the storage area of mythtv.

Not for swap, system or anything else, just storage of myth's files.

My mythserver died and I'm rebuilding from scratch, in a previous life I'd used mdadm and a software raid 0.  But this was always a bit of a pita and I'm told it's not necssary.

What's the most efficient method of using two drives and could someone point me towards a how to on the subject?

Thanks in advance.

---

### Post by galvatron408 on 2010-12-03
You should definitely look in to LVM (logical volume manager).

It will allow you to do exactly what you want and more... 

First, install the lvm2 package via "apt-get install lvm2" and then read this guide.

[http://linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager](http://linuxconfig.org/Linux_lvm_-_Logical_Volume_Manager)

---

