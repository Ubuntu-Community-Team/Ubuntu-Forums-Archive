---
title: "mdadm arrays breaking with drive order change"
date: 2009-07-21
forum: General Help
---

### Post by blackcloud333 on 2009-07-21
I have a Promise controller with 4 SATA(SDA1,SDB1-SDC1,SDD1) drives attached in 2 separate mdadm software RAID 1 arrays and 1 80GB SATA drive as my boot drive.  On a reboot, sometimes the 80GB boot drive is SDA and sometimes it's SDE which breaks the 2 RAID arrays if it becomes SDA(since the mdadm RAID is setup as SDA+SDB and SDC+SDD).  Is there a way to make that 80GB boot drive(SDE) drive stay put with fstab?  I have read some but I am a bit of Linux/Ubuntu noob and I am not completely understanding how to do this with UUIDs or how it would make a difference.

---

