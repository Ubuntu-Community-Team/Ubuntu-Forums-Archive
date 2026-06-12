---
title: "Cron is running, but jobs aren't."
date: 2010-09-28
forum: General Help
---

### Post by jkugler on 2010-09-28
I've read a few other threads that complain that cron is not getting started by upstart in 10.04. That's this bug: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/592114](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/592114) 

That's not the problem here. Cron is running (ps -AF shows it to be so).  However, after a reboot, the user cron jobs (/var/spool/cron/crontabls) are not running.  Neither editing them (with no changes), nor touching the files gets the jobs running.

I have to restart cron, and then the jobs will run.

Ideas? Comments? Things to look for?

I'm at a total loss here!

---

