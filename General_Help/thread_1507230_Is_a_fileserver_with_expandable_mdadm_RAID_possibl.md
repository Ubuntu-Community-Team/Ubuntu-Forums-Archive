---
title: "Is a fileserver with expandable mdadm RAID possible?"
date: 2010-06-11
forum: General Help
---

### Post by bobbob1016 on 2010-06-11
I am looking to build a fileserver with a RAID that can be expanded, if at all possible.  I have seen and used FreeNAS, but I want something with a GUI incase I want to have this machine do a batch encode overnight or something.

I would like to be able to add storage to a "storage pool" for the files as well.  I have Windows Home Server at the moment which can add storage on the fly, but WHS only protects data with duplication, which halves my storage space.  WHS is also giving me fragmentation issues, so I would like switch.

The machine itself is a Dual Xeon (I think Xeon) HT.  Dual physical CPU's, with 1gig RAM at the moment.  I know mdadm is CPU bound but would I be correct in assuming that a Dual Physical Xeon HyperThreaded 2.8ghz machine should be able to handle a lot of mdadm requests at once?

Basically my questions are:


Is there a Soft-RAID that can be expanded?
If yes, can I install Ubuntu on said Soft-RAID or do I need another drive to install to?
How tolerant is said Soft-RAID if I lose a drive?
Would a Dual-Physical-Xeon Hyper-Threaded at 2.8ghz with 1gig ram (I can buy more if needed) be able to handle said Soft-RAID well?

Thanks in advance for the help.

---

### Post by parisv on 2011-07-22
did you find a solution to this? I'm looking for the same thing.

I've found flexraid. Just having a bit of trouble configuring it.

---

### Post by i.r.id10t on 2011-07-22
You want RAID plus LVM

---

### Post by psusi on 2011-07-22
Yes, mdadm can add a new disk and expand the array on the fly, and yes, LVM on top of raid is quite handy.  See [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm).

---

