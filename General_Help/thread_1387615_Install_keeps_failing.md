---
title: "Install keeps failing"
date: 2010-01-22
forum: General Help
---

### Post by Gnusboy on 2010-01-22
**unable to install initramfs-tools error in Karmic** 			 			 			 		   		 		 		Hi all

I'm having a devilish time installing Karmic on my AMD 64-bit. 
Today's missive is:
"Unable to install initramfs-tools."
"Check /var/log/syslog"

After a trying to fix a corrupted 9.04, I have attempted repeated installs of 9.10 on a completely reformatted clean drive. I can get the live CD working, but when I try the permanent install, using the guided full drive install, it stopped at "Unable to install initramfs-tools." and halts the base system install. I can't find anything on this for Karmic and Launchpad says it was superseded.

Can I skip this and go on? It showed a install list going forward, but if I can't put in the base system, how do I proceed?

  I've burned 2 9.10 disks, a new 9.04 disk, downloaded 9.10 via package manager while in Live CD and get errors on all during the install process. 
The check sums match on D/L, but I can't figure how to do a chksum after it's burned to disk. The file sizes do match, but when I go for the install *something* always halts it at different steps with different errors. No joy.

Is there anything else I can try (within the limits of a newbie)?

I've checked all hardware and memory and it's good.  If there is no base system, how do I check the syslog? What now?

Thanks in advance

---

### Post by spiderbatdad on 2010-01-22
> **Gnusboy said:**
> 
The check sums match on D/L, but I can't figure how to do a chksum after it's burned to disk. The file sizes do match, but when I go for the install *something* always halts it at different steps with different errors. No joy.


You can just select the check integrity option while booting the live cd. I had a cd that verified via md5sum /dev/cdrom yet still failed to install, so you may need to burn another at 2x or 4x.

---

### Post by zine92 on 2010-01-22
What he said is right and also before every install try to boot the liveCd and use it for a while to ensure the disc is working in good condition.

---

