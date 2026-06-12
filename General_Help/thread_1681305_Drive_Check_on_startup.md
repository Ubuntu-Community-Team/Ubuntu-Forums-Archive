---
title: "Drive Check on startup"
date: 2011-02-04
forum: General Help
---

### Post by budman21901 on 2011-02-04
I am running Ubuntu 10.10.  I just purchased a 1TB external drive (USB).  I formatted it Ext4 and everything works perfectly except it checks/indexes it everytime i boot which takes forever.  I can turn it off on boot to fix the issue, but was just wondering if there was a bypass of this check on this particular drive.

---

### Post by recluce on 2011-02-04
> **budman21901 said:**
> I am running Ubuntu 10.10.  I just purchased a 1TB external drive (USB).  I formatted it Ext4 and everything works perfectly except it checks/indexes it everytime i boot which takes forever.  I can turn it off on boot to fix the issue, but was just wondering if there was a bypass of this check on this particular drive.

Are you sure the drive gets unmounted cleanly before shutdown or removal? Off the bat, I see no reason that Ubuntu would check the drive on every boot, unless the file system is not clean.

---

### Post by lisati on 2011-02-04
The usual way of avoiding a check at every boot is to let it run to completion, and make sure you shut down your system "cleanly", i.e. use the menu option to shut down. If you do this, and still get a disk check every boot, it's often a sign of some kind of problem.

---

