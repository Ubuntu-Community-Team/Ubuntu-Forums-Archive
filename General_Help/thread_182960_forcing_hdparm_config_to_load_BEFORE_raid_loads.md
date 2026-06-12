---
title: "forcing hdparm config to load BEFORE raid loads"
date: 2006-05-27
forum: General Help
---

### Post by bobdazzla on 2006-05-27
hi there,

I'm trying to force the settings inside my /etc/hdparm.conf file to load BEFORE kubuntu loads RAID at startup. 

Right now, the system beings boot, raid loads, and then the hdparm.conf file loads (in that order). Before hdparm.conf loads, the hard disks which the raid is comprised of are loading with DMA off and 32-bit IO off. 6 disks accessing my system via PIO and 16-bit is INCREDIBLY slow, eating up all my cpu and forcing read speeds of about 2MB/s.

If anyone knows how to force the hdparm.conf file to load earlier, or to force the raid to load later, i'd appreciate the info. thanks in advance

---

### Post by hw-tph on 2006-05-27
Configurations of runlevels and what scripts run in which level is on Debian systems (Ubuntu included of course) done by creating specially named symlinks in the /etc/rc?.d/ directories. They can be manipulated by using the **update-rc.d** command or manually created, renamed or deleted.

This is described in [the Debian Reference](http://www.us.debian.org/doc/manuals/reference/ch-system.en.html#s-boot) (package name *debian-reference-en* if you would like to install it), chapter 2.4.

Cut short, you might want to rename the startup symlinks for RAID management and hdparm in /etc/rcS.d/.


Håkan

---

