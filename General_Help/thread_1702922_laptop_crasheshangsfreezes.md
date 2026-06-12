---
title: "laptop crashes/hangs/freezes"
date: 2011-03-08
forum: General Help
---

### Post by aksbuntu on 2011-03-08
I am running Ubuntu 10.10 on my 2006 Dell Latitude D610 laptop. It crashes/hangs/freezes once every day. This happens sometime when left idle and sometime while working for example while browsing or working on matlab. Sometime it happens in sleep mode as well. So when it crashes the only option I have is shutting it down by power button. 

I'm doubting on the following

* low RAM : I have just 1 GB RAM
* some issue with power management code

I also tried restarting it by alt+Fn+SysRq+K and with alt+Fn+SysRq+'R','E', 'I', 'S', 'U', 'B' but did not work.

Please help me out. I'm hard rebooting my computer twice a day these days.

---

### Post by Tamlynmac on 2011-03-08
Have you checked you log file viewer - "system/administration/log file viewer"?

It may have the failure listed in one of your log files and perhaps even identify what the root cause may be.

Other logs may be viewed (other than those already displayed) in the log file viewer by selecting "file/open/select from the list of log files". I often find lock up issues in either the dmesg.log or the user.log 

Good Luck & hope this helps.

---

