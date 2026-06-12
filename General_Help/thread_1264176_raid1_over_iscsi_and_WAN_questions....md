---
title: "raid1 over iscsi and WAN questions..."
date: 2009-09-11
forum: General Help
---

### Post by syadnom on 2009-09-11
I am unsure of something for doing a raid1 over a WAN link via iScsi.

There are some obvious performance issues but I am aware of those.

How does a raid resync work?  If the connection drops and the raid mirror loses the remote member, when it comes back what is synced?  Does the array litterally resync from sectore a to sector z or is there some mechanism to sync from the point the raid was degraded?

I am ok with link performance as I can maintain 1.2MBytes per second between the two sites but what I cant manage is syncing up a nested terabyte array over 1.2MB/s whenever the connection drops.  if the connection dropped once every 10 days for just moments then I would be syncing constantly.

anyone know how the resync works?

Thanks in advance

---

### Post by kidders on 2009-09-13
> **syadnom said:**
> Does the array litterally resync from sectore a to sector zYes. If you think about it, there's no other way to get all disks back in sync.

Unfortunately, you'd probably find it would take quite a bit longer than 10 days to complete a sync operation in practice, assuming the array would not be left idle during that time. On top of that, even with a link tens of times faster than yours, filesystem performance would be severely degraded during that time.

I know this is exactly what you *don't* want to hear. Sorry.

---

### Post by syadnom on 2009-09-13
thats what I suspected but wasnt sure. thanks

---

