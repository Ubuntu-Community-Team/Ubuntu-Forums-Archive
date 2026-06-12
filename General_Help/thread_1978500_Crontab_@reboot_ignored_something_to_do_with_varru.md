---
title: "Crontab @reboot ignored something to do with /var/run/crond.reboot"
date: 2012-05-11
forum: General Help
---

### Post by YWELLC on 2012-05-11
Annoying issue trying to run a script at reboot on headless machine running Ubuntu 11.10 64bit (running LXDE on top).  I have sorted through (I think) all permission issues:

Tried calling script from user's crontab
Tried calling script from root's crontab
Moved script to /usr/bin from /home to prevent issues with encrypted /home, then chown to user and tried calling script from user's crontab,  then tried again from root's crontab.  I then performed all above steps again with a different script.  FWIW any script I tested works when called directly, ie outside of cron, OR when called by cron as a usual job such as:
0 5 * * 1 tar -zcf /var/backups/home.tgz /home/

I have read elsewhere that cron will ignore @reboot jobs if file /var/run/crond.reboot exists.  That file DOES exist on my system.  It is a link to /run/crond.reboot.  Both files attributes are: 
---------- 1 root       root 

I have manually rm'd both files multiple times, and they are recreated each time cron is restarted.

Any help would be greatly appreciated!

---

