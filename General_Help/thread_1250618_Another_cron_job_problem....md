---
title: "Another cron job problem..."
date: 2009-08-26
forum: General Help
---

### Post by Peck49 on 2009-08-26
I've seen others with cron problems, but I'm not sure where mine is.
My crons look like this:
 
```
 
* 2 * * * find /backup/daily/* -mtime +7 -exec rm -r {} \;
 
* 2 * * * /usr/local/bin/backup-moodle -f /backup/daily/moodle_backup_`date +%Y_%m_%d`.tgz -m /var/www
 
* 2 * * * /usr/local/bin/backup-moodle -f /backup/daily/mahara_backup_`date +%Y_%m_%d`.tgz -m /var/www/mahara

```
 
None of the three run.
 
They work from the CLI manually using sudo, but won't run from crontab.
 
I DID install it using root's crontab. sudo crontab -e.
 
I tried pumping the output to a log, but the log never gets created. I tried greping through the system log, and there are no entries for cron related to these three commands. Other cronjobs in the same crontab ARE running.
 
ANY AND ALL HELP WOULD BE GREATLY APPRECIATED!!

---

### Post by Peck49 on 2009-08-30
OK, I figured it out. If anyone comes across this and cares, I'll post what I found out... [LIST=1]
[*]Apparently, The cronjob can't handle the % characters in the date command, without them being escaped with a backslash (\) before each one.
[*]My format (* 2 * * *) was causing the script to attempt to run during every minute of the hour of 2 AM. I guess it should be (0 2 * * *)
[/LIST]```
 
0 2 * * * find /backup/daily/* -mtime +7 -exec rm -r {} \;
 
0 2 * * * /usr/local/bin/backup-moodle -f /backup/daily/moodle_backup_`date +\%Y_\%m_\%d`.tgz -m /var/www
 
0 2 * * * /usr/local/bin/backup-moodle -f /backup/daily/mahara_backup_`date +\%Y_\%m_\%d`.tgz -m /var/www/mahara

```
 
Posted the functional one in case anyone cares.

---

