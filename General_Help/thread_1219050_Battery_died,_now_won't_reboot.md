---
title: "Battery died, now won't reboot"
date: 2009-07-21
forum: General Help
---

### Post by jewpiter on 2009-07-21
I unplugged my Dell Latitude D630 with 9.04 without noticing. The battery ran down and the system didn't get to shut down properly. When I restart, GRUB loads but ends with a blank screen. If I boot in recovery mode I get the following message:

***
Begin: running /scripts/init-bottom
mount: mounting /dev on /root/dev failed: No Such file or directory
mount: mounting /sys on /root/sys failed. No such file or directory
mount: mounting /proc on /root/proc failed. No such file or directory

Target file system doesn't have /sbin/init
No init found. Try passing init = bootarg
***

Then BusyBox 1.10.2 comes into line.

I guess Ubuntu doesn't handle low battery shut downs very well. It didn't get a chance to do whatever it does when it shuts down normally. This ([http://bit.ly/14Ou6E](http://bit.ly/14Ou6E)) seems to address the issue, but I get lost after booting from the install disc. 

Please advise. Thanks!

---

