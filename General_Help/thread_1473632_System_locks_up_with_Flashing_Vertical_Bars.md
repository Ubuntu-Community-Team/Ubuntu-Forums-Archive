---
title: "System locks up with Flashing Vertical Bars"
date: 2010-05-05
forum: General Help
---

### Post by dnguyen1963 on 2010-05-05
Hi,

In the last few days I have been experiencing some lock-up problems with 10.04.  At first I thought it was due to waking up from hibernation or the screen saver program or FireFox Add-ons.  I cleared out all the Add-ons and set all the power Management options to never shut down. This morning, 10.04 shuts down on me and gave me that flashing vertical bars again.  I am not sure what the problem might be.  As far as I know a few other users had experienced the same problem.  I searched on this forum for possible solution, but have not found any.  Any help would be greatly appreciated.

Thank you.

Ubuntu 10.04 LTS, Dell Inspiron 2400, 512 Mb RAM, 100 GB HD, Intel 82845 G/GL VGA compatible, Broadcom 4401 100Base-T, Dual Boot with XP.

---

### Post by dino99 on 2010-05-05
need to check:

- system admin hardware driver: is it well activated ?
- fans working and cpu gpu temperatures
- .Xsession-errors (/home, unhide into menu)
- system admin log viewer: logs errors

some cleaning:
- install and use gconf-cleaner (yes to all)
- sudo apt-get update
- sudo apt-get install -f
- sudo dpkg --configure -a

---

