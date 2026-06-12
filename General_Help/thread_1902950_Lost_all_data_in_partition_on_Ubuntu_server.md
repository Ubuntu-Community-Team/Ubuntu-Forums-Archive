---
title: "Lost all data in partition on Ubuntu server"
date: 2012-01-01
forum: General Help
---

### Post by Martin B on 2012-01-01
Hi,

The strangest thing just happened with my Ubuntu 8.04 Server...
I run a headless server as a backend for Mythtv, I have two frontends.
I am running 8 disks in two partitions, controlled by a HW raid card, running raid5.
When my daughter was watching a recorded tv show on one of the frontends today the screen went black all of a sudden.
When I logged on to the server with Putty to check what had happened the partition in question was totally empty, 1 TB of data had mysteriously vanished!

Is this a common phenomenon?
What, if anything, can I do to recover my data?

//Martin

---

### Post by 2F4U on 2012-01-01
Before attempting to recover anything I would try to find out what happened. Since you have a hardware RAID it could be a problem with the RAID controller. If that is the case, all your data is at risk and may even be corrupted. Is there any indication of a failure in the log files?

---

### Post by rsvancara on 2012-01-01
Did you have the battery backed cache turned on for your RAID controller when you did not have a battery installed?  Also it would be good to know the make and model of your RAID controller.

This is OT, but I am looking to do something similar with MythTV.  Does this solution work well for you?

Thanks,

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

