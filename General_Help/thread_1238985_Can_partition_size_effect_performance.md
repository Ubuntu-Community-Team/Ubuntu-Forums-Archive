---
title: "Can partition size effect performance"
date: 2009-08-13
forum: General Help
---

### Post by ade234uk on 2009-08-13
Got an acer 8930g laptop. Ubuntu seems quite sluggish on this. I have done all the general tweaks, but I was wondering if partitions sizes can also have an effect on the performance?

The laptop shipped with 4GB memory, however since I am using Ubuntu 32bit I am not using the full allocation. This laptop should fly.

---

### Post by mcduck on 2009-08-13
No, partition size should not have any effect on performance.

If things feel sluggish the first thing to check would be graphics drivers. (and of course it makes a lot of difference if you mean sluggish as in "the interface is slow" or as in "programs work slow".)

---

### Post by madhavhmk on 2009-08-13
From my present experience I can surely say it does not have any considerable effect on performance if your HDD partition for linux is low


Whatever you manage to install on the partition will function seamlessly...


I have just abt 50 MB left on my partition and am franctically searching to improve it...still the software is going on fine.....Its just that I wont be able to do any more upgrades or installation

---

### Post by Post Monkeh on 2009-08-13
it's not like windows where a full partition means a smaller amount of virtual memory. on linux, your swap areas are normally on their own partition, although in saying that, with 4 gig of memory, you shouldn't be using swap too often anyway.

i'd guess either something isn't set up right with your graphics, or something is hogging your system resources.

---

### Post by XCan on 2009-08-13
In principle, if you put the system files on the outer parts of your drive you would get slightly higher data-transfer speeds compared with them being in the inner parts. However, if you merely are referring to if the system slows down when the drive becomes full, the answer would be hardly. Although if the drive is really full, stuff will become fragmented (yes even in ext3).

---

