---
title: "Help spinning down idle SATA drives (in RAID)"
date: 2011-02-24
forum: General Help
---

### Post by Gatorfreak on 2011-02-24
Ubuntu 10.04
Two 1TB SATA drives in software RAID 1 using mdadm. These drives do not contain the OS but just media.

I can't get hdparm to spin the drives down.  "hdparm -Y /dev/sdb" makes "hdparm -C /dev/sdb" indicate that it is in a sleep state but the drive continues to spin.  I can feel it when I touch the drive.

I can't get sg3_utils ("sg_start --stop") to spin the drives down.


I know that the drives CAN be spun down because they used to be connected to a TomatoUSB router and it used scsi-stop to spin them down.  Was not in RAID at that time.

Any ideas?  Does mdadm RAID prevent spin down commands?

---

