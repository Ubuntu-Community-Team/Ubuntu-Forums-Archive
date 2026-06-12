---
title: "Two hard disks, one partition"
date: 2010-06-26
forum: General Help
---

### Post by fetimo on 2010-06-26
Hey there,

Is it possible to get two hard drives under one partition? I have set up Ubuntu server and would like users to be able to access the disk space of both hard drives and I'm guessing this is the way towards it. Call me crazy.

Any advice and help is much appreciated :)

---

### Post by dabl on 2010-06-26
You are crazy.

:lolflag:

No, drives have partitions -- partitions don't have drives.

Is your Ubuntu server OS on one of these drives?  I would assume what you want to do is to make directories (i.e. "folders") on the partitions that are not used by the OS.  You can assign permissions to the new folders that the users can use.

---

### Post by akakingess on 2010-06-26
I used to know more about this stuff, but you could google the terms "raid hard drives" or "striping hard drives" and probably learn a little more.

EDIT: Craziness aside, if that's what you want to do, it is your server...

---

### Post by tom.swartz07 on 2010-06-26
Actually, I think it might be possible. 

I was just looking this up the other day, as a matter of fact.

LVM is, as far as I have read so far, a way of virtually managing different partitions and directories across multiple physical devices.

[http://en.wikipedia.org/wiki/Logical_Volume_Management](http://en.wikipedia.org/wiki/Logical_Volume_Management)

Theres also a Linux version of this: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))


Hope this at least helps point you in the right direction!

---

### Post by drdos2006 on 2010-06-26
Yes, use LVM through LiveCd and GPARTED. The only issue is that if your main HDD fails in 3 or 4 years time, you may not be able to rescue the data on the second LVM drive. Make regular backups off the data drive onto your backup disks.

regards

---

### Post by fetimo on 2010-06-27
Awesome, thank you for all the advice, I did choose the LVM option when partitioning so I'll look down that route and burn a new version of Gparted and yes, drdos2006 I will definitely be backing up regularly! 

dabl, exactly! This is why I thought it couldn't be done.

If I pull it off I'll post back here so there's a bit more info on it =)

---

### Post by tom.swartz07 on 2010-06-27
> **fetimo said:**
> Awesome, thank you for all the advice, I did choose the LVM option when partitioning so I'll look down that route and burn a new version of Gparted and yes, drdos2006 I will definitely be backing up regularly! 

dabl, exactly! This is why I thought it couldn't be done.

If I pull it off I'll post back here so there's a bit more info on it =)

Please do!

Let us know any problems you face, and even what you did- 
I was looking into doing this soon with my big desktop.

---

