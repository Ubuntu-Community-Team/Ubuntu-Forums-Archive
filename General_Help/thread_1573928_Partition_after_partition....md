---
title: "Partition after partition..."
date: 2010-09-13
forum: General Help
---

### Post by onako on 2010-09-13
Primarily I assigned around 30GB to Ubuntu and 130GB to another OS. Now, I need more space for external memory computations in Ubuntu, and the amount I primarily allocated is not sufficient. Is there a way to "translate" some unused memory from the other OS to Ubuntu? It would be good not to everything from the beginning.
Thanks

---

### Post by TeoBigusGeekus on 2010-09-13
Boot up with a live cd and use gparted (gnome partition manager). Just be very carefull not to interrupt the procedure or power off your pc.

---

### Post by Mark Phelps on 2010-09-13
> **onako said:**
> Primarily I assigned around 30GB to Ubuntu and 130GB to another OS. Now, I need more space for external memory computations in Ubuntu, and the amount I primarily allocated is not sufficient. Is there a way to "translate" some unused memory from the other OS to Ubuntu? It would be good not to everything from the beginning.
Thanks

First of all, I think you're asking about "disk space" not "memory".

Second, and this is IMPORTANT, if your Other OS is Win7 (or, shudder, Vista), do NOT use GParted to shrink its OS partition.  Doing so runs the risk of partition corruption and rendering the Other OS unbootable.  Instead, use the Vista/Win7 Disk Management utility to shrink the OS partition.  If your Other OS is XP, you should be OK using GParted on it.

---

### Post by onako on 2010-09-14
Yes, I think disk space. The other OS is Windows 7. Thanks

---

