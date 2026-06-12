---
title: "How to get a RAID-1 back ?"
date: 2010-05-27
forum: General Help
---

### Post by parc on 2010-05-27
I had a working RAID-1 (software raid) under 9.10 and the update to 10.04 failed totally. Now I did a new installation of 9.10 and wanted to have my RAID-1 back ... but how can that be done ?

The first partition has the ID "83", the second one "fd". I was able to create a degraded RAID and was able to get a backup from the "83" disc - but whatever I do with the second disc: its busy and nothing can be done with that.

My question: how can I build the original RAID-1 from these two discs using mdadm ? Actually I've read the documentation, but the documentation also says, that both partitions should have the "fd" ID.

---

### Post by dcstar on 2010-05-27
> **parc said:**
> I had a working RAID-1 (software raid) under 9.10 and the update to 10.04 failed totally. Now I did a new installation of 9.10 and wanted to have my RAID-1 back ... but how can that be done ?

The first partition has the ID "83", the second one "fd". I was able to create a degraded RAID and was able to get a backup from the "83" disc - but whatever I do with the second disc: its busy and nothing can be done with that.

My question: how can I build the original RAID-1 from these two discs using mdadm ? Actually I've read the documentation, but the documentation also says, that both partitions should have the "fd" ID.

One would imagine that you follow the steps in the many HOWTOs on how to create a new RAID 1 array:

[http://www.google.com/search?client=ubuntu&channel=fs&q=mdadm+create+raid+1&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=mdadm+create+raid+1&ie=utf-8&oe=utf-8)

---

