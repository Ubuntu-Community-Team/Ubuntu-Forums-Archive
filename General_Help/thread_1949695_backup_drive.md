---
title: "backup drive"
date: 2012-03-30
forum: General Help
---

### Post by bjje on 2012-03-30
I'd like to put another hard drive in one of my machines (10.04, will switch to 12.04) and mirror my primary disk such that if my primary drive died, I could just switch the sata cable and boot right up and not know the difference. It has a complicated configuration but not much changes on it because data is stored elsewhere. I guess I could use dd but I wonder what other better options there are?

---

### Post by kazztan0325 on 2012-03-31
Hi bjje,

You would be able to clone your hard drive with **'Clonezilla'**.

There is its Home Page here:
[http://www.clonezilla.org/]("http://www.clonezilla.org/")

Hope this helps.

---

### Post by 2F4U on 2012-03-31
Would you like the disks to be permanently in sync? Then neither dd nor some other clone technology would be the right thing and a better choice would be RAID 1. 

[http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_1](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_1)

However, I have no idea if it is possible to setup a RAID level on  an already running system, but I suspect that it would require a fresh installation.

---

### Post by bjje on 2012-03-31
No, I don't need a running backup because nothing much changes on this machine. I just want to clone it and have it bootable with the least hassle and most reliability.

---

### Post by kazztan0325 on 2012-04-02
Hi bjje,

I reconsidered about your plan, and now I would like to recommend you to follow the advice from @2F4U.
Because there would be some security updates and some bug fixes in future also, even if your machine seems to be stable enough and be reliable enough at present.

---

### Post by Adrian98 on 2012-04-02
that clonezilla method would be easy to do! Haven't you tried that?

---

### Post by bjje on 2012-04-02
I hadn't. I don't know much about it and was concerned that it carried a proprietary format but I'll look into it. 
As for RAID1 I think I have to set up a machine like that and can't after the fact.

Thanks for the help.

---

### Post by Mark Phelps on 2012-04-02
> **bjje said:**
> ... and _mirror_ my primary disk such that if my primary drive died, I could just switch the sata cable and boot right up and not know the difference...

Your own words!  

Mirroring is essentially, real-time backup, and will get you what you want.  Using Clonezilla will not -- as it is a snapshot in time, and once the backup is created, it is already "old".

First thing you need to do is decide WHAT outcome you want. Telling us you want to "mirror" and then saying you don't need real-time backup is contradicting yourself.

We can't help you if you can't specify what you want to do.

---

### Post by CharlesA on 2012-04-02
> **Mark Phelps said:**
> Your own words!  

Mirroring is essentially, real-time backup, and will get you what you want.  Using Clonezilla will not -- as it is a snapshot in time, and once the backup is created, it is already "old".

First thing you need to do is decide WHAT outcome you want. Telling us you want to "mirror" and then saying you don't need real-time backup is contradicting yourself.

We can't help you if you can't specify what you want to do.

That's what I was thinking as well..

The only thing that comes to mind that involves mirroring is RAID1, but that is not a substitute for backups.

---

### Post by bjje on 2012-04-03
As I sort of said, these machines are set up with a complicated config for a single purpose, the data is stored elsewhere but I didn't think much about updates so I guess only RAID1 will do it and I would need to start from scratch with reformatting. I need to keep working asap if I lose a disk. I was hoping to not have to wipe it but I will probably take the opportunity when the LTS release happens.
Thanks again.

---

