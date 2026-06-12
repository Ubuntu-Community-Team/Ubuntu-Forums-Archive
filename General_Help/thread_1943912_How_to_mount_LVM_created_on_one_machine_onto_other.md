---
title: "How to mount LVM created on one machine onto other machine"
date: 2012-03-20
forum: General Help
---

### Post by kkpal on 2012-03-20
Hi,

I have created two Ubuntu10.04 VMs and attached a iscsi target on one of them created a logical volume(/dev/volgroup/volume) and format it as ext4.
Both machine are same. Now I want to add same iscsi target(in case of first machine goes down) on other machine and mount that logical volume onto other machine.
So how can it is possible?


Thanks & Regards
Komal K Pal

---

### Post by blind2314 on 2012-03-20
Unless you use a clustering filesystem of some sort (or NFS/other networked options), this isn't possible. If you want both machines to be able to access the same filesystem that is shared between them, you'll need a CFS (clustered filesystem). If you want the filesystem to automatically "failover" to the second machine when the first one goes down, you'll need some sort of clustering solution (whether homemade or third party).

---

