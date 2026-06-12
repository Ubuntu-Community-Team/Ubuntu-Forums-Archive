---
title: "Mirror a partition without RAID"
date: 2010-02-11
forum: General Help
---

### Post by adam.ec on 2010-02-11
I have two hard drives inside an Ubuntu 9.10 machine, each with a data partition on. What I want to do is as I save files to one data partition partition (or delete them) I want the files copying/deleted automatically on the the other data partition. I do not want to start using RAID or end-of-day incremental backups.

Does anybody know of a solution to this?

Thanks in advance.

---

### Post by Mark Phelps on 2010-02-11
> **adam.ec said:**
> ... I want the files copying/deleted automatically on the the other data partition...

That's what RAID (redundancy version) is FOR.

---

### Post by JackRock on 2010-02-11
To do it simultaneously?  That's RAID.  However, you could do something like periodic full backups to a networked drive, and there are many third-party utilities for that.  But it won't be simultaneous.

---

### Post by adam.ec on 2010-02-11
I'd rather avoid RAID if I can as we've just had a load of problems with Ubuntu's software RAID. Also the second drive is completely removable and a colleague needs to be able to access an exact replica of the partition on the main drive.

For backup I have found Simple Backup Suite which seems to work well. As for what I am trying to do I've just completed a Python script which picks up on data being written to the 1st partition and automatically copies it to the second partition. Just got to put in the code for handling filename changes and deleting and should be good to go.

Thanks anyway guys.

---

### Post by cjhabs on 2010-02-11
How about rsync, configured for mirroring, scheduled from cron every x minutes?

---

### Post by JackRock on 2010-02-11
> **adam.ec said:**
> I'd rather avoid RAID if I can as we've just had a load of problems with Ubuntu's software RAID. Also the second drive is completely removable and a colleague needs to be able to access an exact replica of the partition on the main drive.

For backup I have found Simple Backup Suite which seems to work well. As for what I am trying to do I've just completed a Python script which picks up on data being written to the 1st partition and automatically copies it to the second partition. Just got to put in the code for handling filename changes and deleting and should be good to go.

Thanks anyway guys.

Have you considered a hardware RAID solution?

---

