---
title: "Cron jobs don't run after reboot"
date: 2009-12-04
forum: General Help
---

### Post by crouchingturbo on 2009-12-04
Hi, I have an Ubuntu karmic system.  I recently upgraded it from hardy -> intrepid -> jaunty -> karmic (that was a fun night).

Since the upgrade, after a reboot, a user's normal cron jobs don't run.  Crontab -l shows his cron file and it looks fine.  I found that editing the crontab with crontab -e causes it to magically start working again (even when I make no changes to the crontab).

Yesterday, a power outage forced a reboot (clean shutdown, via UPS), and again, last night, that user's cron jobs did not run.

Anyone know why cron jobs wouldn't run after a reboot?

---

### Post by floatingworld on 2009-12-10
I had the same problem when trying to run @reboots from a file in /etc/cron.d but for me moving the entries into the main /etc/crontab resulted in them working properly.

However, I found this thread which might be the solution to the problem although I haven't tested it out: 

[http://ubuntuforums.org/showthread.php?t=1228072](http://ubuntuforums.org/showthread.php?t=1228072)

---

