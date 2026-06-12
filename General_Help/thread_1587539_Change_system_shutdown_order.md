---
title: "Change system shutdown order"
date: 2010-10-03
forum: General Help
---

### Post by wesg on 2010-10-03
My Ubuntu file server sits under a desk and shares files with the network without a hitch, and in a perfect world I wouldn't ever need to shut it down (I reached 6 months uptime once). However, since it occasionally needs service, or additions and needs to be moved, I need to shut down.

The trouble is, the power management system is borked, so whenever I issue "sudo powerff now", the system halts, but the PSU stays on. I usually wait a few minutes after and flip the PSU switch, but I'm never sure if the system is already down. 

Is there a way to reorder the way services shut down so that I put SSH last, and therefore know when the system is down when my session is disconnected? Is defaults.rc or whatever responsible for that?

---

### Post by dcstar on 2010-10-04
> **wesg said:**
> 
..........
Is there a way to reorder the way services shut down so that I put SSH last, and therefore know when the system is down when my session is disconnected? Is defaults.rc or whatever responsible for that?

Networking would be shut down long before the other remaining services, so it would be a pointless exercise.

---

### Post by wesg on 2010-10-04
Any suggestions about how to get some feedback when the system is shutdown?

---

### Post by dcstar on 2010-10-05
> **wesg said:**
> Any suggestions about how to get some feedback when the system is shutdown?

Why not ping the box and when it doesn't respond, it is down?

---

