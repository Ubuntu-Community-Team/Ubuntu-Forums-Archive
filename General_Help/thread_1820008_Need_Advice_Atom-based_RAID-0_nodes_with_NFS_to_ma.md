---
title: "Need Advice: Atom-based RAID-0 nodes with NFS to main server RAID-1???"
date: 2011-08-07
forum: General Help
---

### Post by sunite on 2011-08-07
Salutations,

For the last 3 months I've had this idea bounce around the inside of my head.

Basically I want to buy 2 Atom ITX boards, get 2 HDDs each (so a total of 4 HDDs of pure storage) with an extra drive (probably flash based) for the OS. Each Atom node would be doing raid-0 (mdadm).

I would then have a control server (which I have already built: atom based as well) to which the nodes would connect via a Gb-switch. It would in turn use the mounted drives from the nodes to create a raid-1.

So the 2 nodes would be mirroring each other.

The thing is that I am not entirely sure if this is even possible and by what means one would do it. Would one use NFS to connect the nodes to the server to even do raid, or should I use something along the lines of GlusterFS to achieve a similar result?

Thanks

---

### Post by sunite on 2011-08-07
ok as it would seem I have answered my own question: DRBD.

sorry ;)

---

