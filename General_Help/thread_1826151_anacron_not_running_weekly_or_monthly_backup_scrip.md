---
title: "anacron not running weekly or monthly backup script"
date: 2011-08-16
forum: General Help
---

### Post by malapradej on 2011-08-16
Hi,

I have been trying to set up PC up to do automatic backups using a script I developed and anacron. The script runs perfectly when I run it manually in bash, but won't run through anacron. If there is anyone that could help me understand what I am doing wrong it will be much appreciated. I followed all the advice on CronHowTo etc etc and are at a loss for why this is not happening.

Here is my anacron tab (new bits in blue):


SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# These replace cron's entries
1    5    cron.daily     nice run-parts --report /etc/cron.daily
7    10    cron.weekly     nice run-parts --report /etc/cron.weekly
@monthly    15    cron.monthly nice run-parts --report /etc/cron.monthly
[COLOR=Blue]7    30    desktop_weekly_backup    /home/malapradej/run_backup_int.sh
@monthly 90     desktop_monthly_backup    /home/malapradej/run_backup_ext.sh[/COLOR]


And here is the syslog:


Aug 16 09:00:06 Malaprade-Desktop anacron[856]: Job `cron.daily' terminated
Aug 16 09:00:06 Malaprade-Desktop anacron[856]: Job `desktop_weekly_backup' started
Aug 16 09:00:06 Malaprade-Desktop anacron[856]: Job `desktop_weekly_backup' terminated (exit status: 1) (mailing output)
Aug 16 09:00:06 Malaprade-Desktop anacron[856]: Tried to mail output of job `desktop_weekly_backup', but mailer process (/usr/sbin/sendmail) exited with ststus 255
Aug 16 09:00:06 Malaprade-Desktop anacron[856]: Normal exit (2 jobs run)

---

### Post by kjohri on 2011-09-10
Try renaming your script without ".sh" extension. 

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

