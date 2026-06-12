---
title: "Lost Local domain names after upgrade to karmic?"
date: 2010-01-19
forum: General Help
---

### Post by mac666 on 2010-01-19
Hey
before i upgrade to karmic i used to visit some local domains like freenas.local.

But after the upgrade the domains doesnt work. I can go to smb://freenas/ but in firefox / chrome or in fstab i cannot use freenas.local ...

Any ideas?

---

### Post by fsando on 2010-01-23
> **mac666 said:**
> Hey
before i upgrade to karmic i used to visit some local domains like freenas.local.

But after the upgrade the domains doesnt work. I can go to smb://freenas/ but in firefox / chrome or in fstab i cannot use freenas.local ...

Any ideas?

Perhaps you entered those domain names in your old host file and need to enter them again?

---

### Post by Iowan on 2010-01-23
At the risk of being redundant... check */etc/hosts*. Another thing to check would be the "search" line in */etc/resolv.conf*

---

