---
title: "Some of Crontab Don't Run"
date: 2010-08-19
forum: General Help
---

### Post by penetal on 2010-08-19
Hey could anyone please help me figure out why this /etc/crontab won't run correctly?
Is it possible that it dont run because the cron deamon is not running?

```
~$ service cron status
cron start/running, process 1013

``````

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

# CSS restart once a day
* 6 * * *   root  sh /home/fm/HLDS/updatetool/update.sh

# CSS Rank update
45 * * * * root /home/fm/HLDS/Pstats/stats.pl

# PMS Update Check
*/1 * * * * fm php /home/fm/www/pms/pms.php
* 6 * * * * fm pms restart

# Rtorrent Check
*/1 * * * * fm /home/fm/torrent.sh

# Torrent Permissions
*/1 * * * * root chmod -R 777 /home/fm/torrent/Complete/*
*/1 * * * * root chmod -R 777 /home/fm/torrent/Incomplete/*
*/1 * * * * root chmod -R 777 /home/fm/torrent/autoloadtorrents/

# HLDS logs Permissions
*/1 * * * * root  chmod -R 777 /home/fm/HLDS/10X/orangebox/cstrike/logs/
*/1 * * * * root  chmod -R 777 /home/fm/HLDS/CSS/orangebox/cstrike/logs/
*/1 * * * * root  chmod -R 777 /home/fm/HLDS/GG/orangebox/cstrike/logs/
*/1 * * * * root  chmod -R 777 /home/fm/HLDS/SURF/orangebox/cstrike/logs/

```

---

### Post by penetal on 2010-08-25
some help please?

---

