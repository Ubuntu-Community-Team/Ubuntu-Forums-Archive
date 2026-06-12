---
title: "Another &quot;my cron won't run&quot; question"
date: 2009-12-03
forum: General Help
---

### Post by plaine on 2009-12-03
I can't get my cron job to run properly.  I'm using the latest version of Ubuntu and here is some info:

sudo crontab -e shows:
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h  dom mon dow   command
29 21 * * * root /etc/cron.daily/backup

My /var/log/syslog shows:
Dec  3 21:29:01 my-username-here CRON[20977]: (root) CMD (root /etc/cron.daily/backup)

My script is working fine, because when I run it manually, it works, so no problems there.
I've stopped cron and started it back up again which didn't fix anything.
I've tried moving the backup script to another directory as well with no luck.

Where am I going wrong?  Thank you.

---

### Post by mo.reina on 2009-12-03
> **plaine said:**
> I can't get my cron job to run properly.  I'm using the latest version of Ubuntu and here is some info:

sudo crontab -e shows:
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h  dom mon dow   command
29 21 * * * **_root_** /etc/cron.daily/backup

My /var/log/syslog shows:
Dec  3 21:29:01 my-username-here CRON[20977]: (root) **_CMD (root_** /etc/cron.daily/backup)

My script is working fine, because when I run it manually, it works, so no problems there.
I've stopped cron and started it back up again which didn't fix anything.
I've tried moving the backup script to another directory as well with no luck.

Where am I going wrong?  Thank you.

format of crontab is

* * * * * /command/here

you have the word *root* included there.  remove it and it should work fine

---

### Post by plaine on 2009-12-03
I removed it and restarted cron, but still nothing.  Other suggestions?

---

### Post by dcstar on 2009-12-03
> **plaine said:**
> I removed it and restarted cron, but still nothing.  Other suggestions?

Wait until the actual time you have set it to run?

---

### Post by mo.reina on 2009-12-04
set cron to run the script a few minutes from now.  use syslog to check the output and post it here

---

### Post by plaine on 2009-12-04
Yes, I did set it a few minutes ahead as I have been all through troubleshooting, but it didn't run.  Output of syslog was:

Dec  3 22:15:01 my-username-here CRON[21286]: (root) CMD (/etc/cron.daily/backup)

---

### Post by plaine on 2009-12-05
Could there be any permissions issues at play here?  I'm at a loss why my script will run when i do a "./backup", and the syslog looks like its running at the proper time when I schedule it, but nothing happens.  No files are transferred in my rsync (the contents of my script).

---

### Post by mo.reina on 2009-12-06
are you root when running crontab -e? or is the script executable for root only? where is the script located?

---

