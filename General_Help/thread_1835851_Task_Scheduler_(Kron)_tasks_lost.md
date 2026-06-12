---
title: "Task Scheduler (Kron?) tasks lost"
date: 2011-08-30
forum: General Help
---

### Post by AugustinMa on 2011-08-30
Hello,

I recently did a fresh install, now running kubuntu 11.04. I have an image of my old install (9.10).

I just noticed that all my user scheduled tasks have disappeared. (K-menu => system settings => Task scheduler). 

Since those are user data, I expected them to be saved somewhere in the /home/user/ directory, which has not changed. If they are saved somewhere under /etc/, I can still access the file of my old system via the image I made. 

Questions:
Why have the schedule tasks disappeared after the upgrade?
Where are the tasks saved?
What's kcron? I installed the kcron but there is no executable. Is it the back end for the Task Scheduler?

Thanks.

---

### Post by AugustinMa on 2011-09-01
It turns out that scheduled tasks are stored in the user crontab at:
/var/spool/cron/crontabs/username

Many people advise not to do upgrades but to do fresh installs, reformatting / and keeping /home/ . However, I am starting to make a comprehensive list and backup of important config files held under / (/etc, /var, etc). 

See the following wiki page for a list of things to remember to include in your backups:

[http://linux.overshoot.tv/wiki/system/what_backup](http://linux.overshoot.tv/wiki/system/what_backup)

---

