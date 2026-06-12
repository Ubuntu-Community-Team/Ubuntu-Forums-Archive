---
title: "Multiple active partitions"
date: 2010-06-18
forum: General Help
---

### Post by m005k on 2010-06-18
In an effort to install something to my usb I ended up with a computer that won't boot.  I have a dual boot Ubuntu 10.4/ vista laptop. When I turn it on it gives the error "multiple active partitions" and won't go past that. If I put a Ubuntu live cd in the laptop it appears that everything is still there. Could I somehow use a partition manager to "unactivate" a partition?

Mike

---

### Post by dcstar on 2010-06-19
> **m005k said:**
> In an effort to install something to my usb I ended up with a computer that won't boot.  I have a dual boot Ubuntu 10.4/ vista laptop. When I turn it on it gives the error "multiple active partitions" and won't go past that. If I put a Ubuntu live cd in the laptop it appears that everything is still there. Could I somehow use a partition manager to "unactivate" a partition?

Mike

Use gparted to set the **single** boot flag.

---

