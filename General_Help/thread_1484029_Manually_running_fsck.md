---
title: "Manually running fsck"
date: 2010-05-15
forum: General Help
---

### Post by epp on 2010-05-15
I installed Ubuntu 10.04 LTS on a desktop but had to do it as an incremntal upgrade (installed 7.10, upgraded to 8.04 LTS, then a further uopgrade to 10.04 LTS) due to some changes to IDE/SCSI drivers that made it impossible to install any Linux distro released since the autumn of 2008 on this system.

Last night, when it booted up, it indicated it was doing a file system check.  It took almost no time to go from 0 to 70%, then it slowed down considerably.  At that point, it took a good half hour to go from 70% completed to 90% completed and during this time, there was next to no hard drive activity.  I finally decided to press "C" to cancel the file system check, but pressing that did nothing.  I ended up doing a manual power down of the system.  When I powered it back on, it came up fine.

A suggestion to run fsck in another thread on the site, mentioned using a GParted LiveCD and running a check that way, which seems easier, I have this running the file system check right now.  On the assumption that it will complete the task faster than Ubuntu itself and if this is done periodically, would it prevent Ubuntu from doing its own file system check (e.g. does GParted place something on it indicating when the last file system check was performed?)

Thank you for any information.

---

