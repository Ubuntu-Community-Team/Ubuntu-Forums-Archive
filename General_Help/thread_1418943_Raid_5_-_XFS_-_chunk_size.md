---
title: "Raid 5 - XFS - chunk size"
date: 2010-03-01
forum: General Help
---

### Post by stek_87 on 2010-03-01
Hi!

I have set up an ubuntu server with 3*2TB sata disk, into a raid5 volume with mdadm.

This server will serve my ESX with a 4TB nfs datastore. What chunk size would be the best to use? Right now everything is default.

And what else can I do to improve performance of this raid volume?

Any help would be appreciated!

rgds
/S

---

### Post by kidders on 2010-03-02
Hi there,

> **stek_87 said:**
> What chunk size would be the best to use?In general, XFS over RAID5 tends to perform better when the chunk size and filesystem block size are equal. That said, there are other considerations to take into account (eg what your typical usage patterns are likely to be), so it's not always that straightforward. For example, supposing you'll be storing movies on your array. The natural tendency would be to pick a large block size, but if your network is fast, the corresponding large chunk size could become a bottleneck.

Anyhow, the most important thing to get right is that your XFS log writes align perfectly with the underlying stripes.

> **stek_87 said:**
> And what else can I do to improve performance of this raid volume?One tweak that can make a significant difference to XFS performance when it's sitting on top of any logical device is disabling write barriers. If you do, a UPS is _essential_ ... but then again, running XFS over RAID without a UPS is risky either way.

I hope that helps.

---

