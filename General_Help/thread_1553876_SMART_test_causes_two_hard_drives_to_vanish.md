---
title: "SMART test causes two hard drives to vanish"
date: 2010-08-15
forum: General Help
---

### Post by black_raven2525 on 2010-08-15
I ran the command ```
smartctl -a /dev/sdc
``` to look up the SMART info on my drive and the drive instantly stopped responding (music playing from it stopped and ktorrent seeding from it threw errors). The test still came back from the drive as PASSED with no errors, everything looked fine. The only problem was I still couldn't access the drive.

I rebooted the machine and that drive as well as a second drive I had ran the above command on did not mount, nor do they appear in my /dev folder. I shut the machine off and went into the bios and both of my drives are missing there too. I have rebooted several times but the bios still does not see these drives.

What about that command would cause two healthy drives to go completely dark? Any ideas to get them back?

---

### Post by Karl1982 on 2010-08-15
If you connect those drives to another computer, are they visible?  Also, fully power off your computer, if you haven't already.

---

### Post by black_raven2525 on 2010-08-15
I unplugged it for about 10 mins and plugged it back in, now the drives show up...I had already done a full power down but I guess the unplug fixed it?? This is going to make me paranoid for the next couple days T_T

---

