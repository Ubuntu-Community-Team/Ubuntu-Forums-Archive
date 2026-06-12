---
title: "script not running in cron"
date: 2011-09-19
forum: General Help
---

### Post by sn0m on 2011-09-19
Hi, is there a way to execute a script on shutdown using cron?
Regards
?Sorry about the misleading title
Sokol

---

### Post by Cheesehead on 2011-09-24
No. 
Cron, to my knowledge, is not called during shutdown. Anacron is called during startup/wake-up, but not suspend/shutdown.

To run a job at shutdown, such as backup or unmount, use Upstart. That also adds more flexibility to the range of system events you can use for your triggers. For example, my laptop automatically unmounts network drives and changes the wallpaper upon both shutdown and changing networks.

---

### Post by Habitual on 2011-09-24
[http://www.unix.com/man-page/Linux/5/crontab/](http://www.unix.com/man-page/Linux/5/crontab/)

---

