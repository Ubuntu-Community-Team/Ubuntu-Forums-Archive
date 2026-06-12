---
title: "scsi scanner requires root"
date: 2009-11-13
forum: General Help
---

### Post by satbunny on 2009-11-13
My SCSI scanner requires root to run since the scanner is at 
> /dev/sg2
and everytime I reboot it resets the permissions.

Is there an elegant solution to prevent the need to keep resetting the permissions or running as root?

I have read the threads re USB scanners and looked in 
> /lib/udev/rules.d/50-udev-default.rules


but the only scsi devices in there seem to be disks and cdroms..

---

