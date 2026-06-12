---
title: "USB ports not working after Resume from Standby"
date: 2010-04-24
forum: General Help
---

### Post by aki096 on 2010-04-24
I have Ubuntu 9.10 on my ThinkPad T510.  Every time I resume from standby, my USB ports would stop working.  I tried unplugging and replugging my USB peripherals, but they don't get recognized by "lsusb".  Please help, thanks!

---

### Post by P4man on 2010-04-24
There is a bug report on that here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/566149)

The fix made it into the karmic kernel just hours ago, so try running update manager. Note the last poster in that thread said it also required a BIOS update for the fix to work.

---

