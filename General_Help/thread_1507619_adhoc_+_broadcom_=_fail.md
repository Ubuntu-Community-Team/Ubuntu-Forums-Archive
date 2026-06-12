---
title: "adhoc + broadcom = fail"
date: 2010-06-11
forum: General Help
---

### Post by sandyd on 2010-06-11
Is anyone having problems where they cannot change the mode of their broadcom wireless card (using propriety drivers because b43 doesn't work with mine) with the commands ```
 sudo iwconfig eth1 mode ad-hoc
```?

---

### Post by efflandt on 2010-06-11
It could be that network manager has a lock on network devices and settings.  Have you tried using System > Preferences > Network Connections > Wireless?

---

### Post by sandyd on 2010-06-12
> **efflandt said:**
> It could be that network manager has a lock on network devices and settings.  Have you tried using System > Preferences > Network Connections > Wireless?
I already stopped networkmanager before running the command.

---

