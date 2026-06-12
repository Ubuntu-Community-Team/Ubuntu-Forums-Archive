---
title: "IO tuning for multiple parallel DVD readings"
date: 2010-04-29
forum: General Help
---

### Post by mmerlone on 2010-04-29
Hi all,

Objective: copy old backups from 600+ CD/DVD media to a hard disk. 

Machine: A desktop with 4 DVD drivers, mainboard has 4 SATA conectors and only one PATA conector.

My questions are:

1. What tuning can I do to the kernel on a Ubuntu Lucid Desktop to achieve maximum IO to dd/cp/rsync/whatever those medias to hd?
2. What's the best scenario regarding HD/DVD drive connections to mainboard regarding IO/throughput?

The intention is to insert 4 medias at a time and copy them all in parallel to a local hard disk.

Any thoughts, hints, insights? I confess I am completely lost where to begin, or if this should work out-of-the-box without any tuneup (will try this).

Thanks and best regards.

---

### Post by sulekha on 2010-07-16
> **mmerlone said:**
> Hi all,

Objective: copy old backups from 600+ CD/DVD media to a hard disk. 

Machine: A desktop with 4 DVD drivers, mainboard has 4 SATA conectors and only one PATA conector.

My questions are:

1. What tuning can I do to the kernel on a Ubuntu Lucid Desktop to achieve maximum IO to dd/cp/rsync/whatever those medias to hd?
2. What's the best scenario regarding HD/DVD drive connections to mainboard regarding IO/throughput?

The intention is to insert 4 medias at a time and copy them all in parallel to a local hard disk.

Any thoughts, hints, insights? I confess I am completely lost where to begin, or if this should work out-of-the-box without any tuneup (will try this).

Thanks and best regards.


for IO tuning start from here:-

[www.redhat.com/docs/wp/performancetuning/iotuning/index.html](www.redhat.com/docs/wp/performancetuning/iotuning/index.html)

---

### Post by dcstar on 2010-07-16
> **mmerlone said:**
> 
...........
Any thoughts, hints, insights? I confess I am completely lost where to begin, or if this should work out-of-the-box without any tuneup (will try this).


The best advice will be to stop imagining problems that may never exist and try it first.

If you want high disk write performance then that will be controlled mostly by the capabilities of the particular drive and not by any potential tweaking of something already designed to be as efficient as possible.

---

