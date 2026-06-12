---
title: "Cron.daily Not working"
date: 2010-08-31
forum: General Help
---

### Post by bundy75 on 2010-08-31
I have a backup script that I would like cron.daily to run. the reason I want cron.daily to run it instead of in a crontab is so anacron with insure it runs each day.

I place script in cron.daily and run with "run-parts --report {nameofscriipt}" and it runs fine. Next day nothing happens. I can't seem to get the mail feature working so don't know where its going wrong :-(

Looked in /var/log/syslog

Sep  1 01:35:02 waiora-desktop anacron[2389]: Job `cron.daily' terminated
Sep  1 01:35:02 waiora-desktop anacron[2389]: Normal exit (1 job run)
Sep  1 01:35:11 waiora-desktop postfix/smtp[2569]: 44E41180A88: to=<tokomairiro.waiora@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.127.27]:25, delay=8.9, delays=0.13/0.01/2/6.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1283261710 r31si14367260qcs.0)
Sep  1 01:35:11 waiora-desktop postfix/qmgr[1183]: 44E41180A88: removed
Sep  1 02:17:01 waiora-desktop CRON[2622]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 03:17:01 waiora-desktop CRON[2628]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 04:17:01 waiora-desktop CRON[2635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 05:00:01 waiora-desktop CRON[2640]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Sep  1 05:17:01 waiora-desktop CRON[2644]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 06:17:01 waiora-desktop CRON[2651]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 06:52:01 waiora-desktop CRON[2656]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ))
Sep  1 07:09:16 waiora-desktop kernel: [131368.985993] psmouse serio1: ID: 10 00 64
Sep  1 07:09:30 waiora-desktop kernel: [131383.168164] [drm] nouveau 0000:00:0d.0: Setting dpms mode 0 on vga encoder (output 0)
Sep  1 07:17:01 waiora-desktop CRON[3126]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 07:19:23 waiora-desktop crontab[3128]: (root) BEGIN EDIT (root)
Sep  1 07:19:26 waiora-desktop crontab[3128]: (root) END EDIT (root)
Sep  1 07:19:30 waiora-desktop crontab[3140]: (alistair) BEGIN EDIT (alistair)
Sep  1 07:19:42 waiora-desktop crontab[3140]: (alistair) REPLACE (alistair)
Sep  1 07:19:42 waiora-desktop crontab[3140]: (alistair) END EDIT (alistair)
Sep  1 07:19:43 waiora-desktop crontab[3151]: (root) BEGIN EDIT (root)
Sep  1 07:19:55 waiora-desktop crontab[3151]: (root) REPLACE (root)
Sep  1 07:19:55 waiora-desktop crontab[3151]: (root) END EDIT (root)
Sep  1 07:20:01 waiora-desktop cron[858]: (alistair) RELOAD (crontabs/alistair)
Sep  1 07:26:00 waiora-desktop kernel: [132373.608078] [drm] nouveau 0000:00:0d.0: Load detected on output A
Sep  1 07:41:01 waiora-desktop cron[858]: (*system*) RELOAD (/etc/crontab)
Sep  1 07:45:01 waiora-desktop CRON[3755]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Sep  1 07:45:58 waiora-desktop anacron[3761]: Can't open timestamp file for job cron.daily: Permission denied
Sep  1 07:45:58 waiora-desktop anacron[3761]: Aborted
Sep  1 07:46:28 waiora-desktop anacron[3932]: Updated timestamp for job `cron.daily' to 2010-09-01
Sep  1 07:48:03 waiora-desktop anacron[4310]: Updated timestamp for job `cron.daily' to 2010-09-01

Noticed that cron.daily terminated don't know why :-(
Also noticed anacron couldn't open timestamp seems strange?
Added a acript to run the backup and pipe output to file

{nameofscript} > "outputfile" 2>&1

and get nothing so guessing cron.daily not running script
I have no . in script name

script is executable and owned by root.

Any suggestions?
Which user does cron.daily run as? my script needs to run as root.(is this the problem?)


thanks

---

### Post by dlepiane on 2010-08-31
Can you show us an ls -a of /etc/cron.daily and then maybe head of your backup script file?

---

### Post by dlepiane on 2010-08-31
> **dlepiane said:**
> Can you show us an ls -a of /etc/cron.daily and then maybe head of your backup script file?

Maybe crontab -l for yourself, root, and ls -la of /etc/cron.* too.

Thanks

---

### Post by bundy75 on 2010-08-31
---------------------ls -a /etc/cron.daily/ -----------------------

.         apport    automysqlbackup  logrotate  .placeholder
..        apt       bsdmainutils     man-db     popularity-contest
0anacron  aptitude  dpkg             mlocate    standard

-----------------------head of backupscript----------------------------

#!/bin/bash

-------------------- ls -la of /etc/cron.* ----------------------------
ls: cannot access of: No such file or directory
/etc/cron.d:
total 24
drwxr-xr-x   2 root root  4096 2010-09-01 08:27 .
drwxr-xr-x 131 root root 12288 2010-09-01 12:33 ..
-rw-r--r--   1 root root   288 2010-08-30 18:45 anacron
-rw-r--r--   1 root root   102 2010-04-15 11:29 .placeholder

/etc/cron.daily:
total 76
drwxr-xr-x   2 root root  4096 2010-09-01 07:56 .
drwxr-xr-x 131 root root 12288 2010-09-01 12:33 ..
-rwxr-xr-x   1 root root   311 2010-03-05 15:29 0anacron
-rwxr-xr-x   1 root root   189 2010-04-19 20:56 apport
-rwxr-xr-x   1 root root 15690 2010-04-15 16:33 apt
-rwxr-xr-x   1 root root   314 2010-04-10 00:16 aptitude
lrwxrwxrwx   1 root root    36 2010-08-25 14:36 automysqlbackup -> /etc/automysqlbackup/automysqlbackup
-rwxr-xr-x   1 root root   502 2009-11-11 05:12 bsdmainutils
-rwxr-xr-x   1 root root   256 2010-04-16 05:23 dpkg
-rwxr-xr-x   1 root root    89 2010-03-07 16:00 logrotate
-rwxr-xr-x   1 root root  1327 2010-03-02 23:31 man-db
-rwxr-xr-x   1 root root   606 2010-03-24 23:16 mlocate
-rw-r--r--   1 root root   102 2010-04-15 11:29 .placeholder
-rwxr-xr-x   1 root root  2149 2009-06-17 01:12 popularity-contest
-rwxr-xr-x   1 root root  3349 2010-04-15 11:29 standard

/etc/cron.hourly:
total 20
drwxr-xr-x   2 root root  4096 2010-04-30 00:18 .
drwxr-xr-x 131 root root 12288 2010-09-01 12:33 ..
-rw-r--r--   1 root root   102 2010-04-15 11:29 .placeholder

/etc/cron.monthly:
total 28
drwxr-xr-x   2 root root  4096 2010-04-30 00:26 .
drwxr-xr-x 131 root root 12288 2010-09-01 12:33 ..
-rwxr-xr-x   1 root root   313 2010-03-05 15:29 0anacron
-rw-r--r--   1 root root   102 2010-04-15 11:29 .placeholder
-rwxr-xr-x   1 root root   129 2010-04-15 11:29 standard

/etc/cron.weekly:
total 32
drwxr-xr-x   2 root root  4096 2010-04-30 00:27 .
drwxr-xr-x 131 root root 12288 2010-09-01 12:33 ..
-rwxr-xr-x   1 root root   312 2010-03-05 15:29 0anacron
-rwxr-xr-x   1 root root   203 2010-03-31 04:31 apt-xapian-index
-rwxr-xr-x   1 root root   887 2010-03-02 23:31 man-db
-rw-r--r--   1 root root   102 2010-04-15 11:29 .placeholder

-----------------------crontab -l "myself"----------------------------

# m h  dom mon dow   command

-----------------------crontab -l "root"----------------------------
# m h  dom mon dow   command
00 8 * * * root /etc/automysqlbackup/automysqlbackup

--------------------------------------------------------------------
NOTE the automysql backup is in daily and root crontab as I was trying to get it to work in either


Thanks

---

### Post by bundy75 on 2010-08-31
I did notice that it was only the link that was own by root and not the script but that still doesn't seemed to of fixed it


on a different note I now have sendmail working from the command line and have set MAILTO variable in /etc/crontab and /etc/anacrontab and still receive no email 

whats the best way to check if they even trying to run??

---

### Post by bundy75 on 2010-08-31
Another update 

when I tried running it that time I checked /var/log/syslog again and found

Sep  1 13:10:01 waiora-desktop CRON[1542]: (root) CMD (root /etc/automysqlbackup/automysqlbackup)
Sep  1 13:10:01 waiora-desktop postfix/pickup[1218]: D62B7181B4D: uid=0 from=<root>
Sep  1 13:10:01 waiora-desktop postfix/cleanup[1545]: D62B7181B4D: message-id=<20100901011001.D62B7181B4D@waiora-desktop>
Sep  1 13:10:01 waiora-desktop postfix/qmgr[1220]: D62B7181B4D: from=<root@waiora-desktop>, size=554, nrcpt=1 (queue active)
Sep  1 13:10:02 waiora-desktop postfix/local[1547]: D62B7181B4D: to=<root@waiora-desktop>, orig_to=<root>, relay=local, delay=0.34, delays=0.19/0.06/0/0.09, dsn=2.0.0, status=sent (delivered to mailbox)
Sep  1 13:10:02 waiora-desktop postfix/qmgr[1220]: D62B7181B4D: removed

Which looks like it did run and send me the email I expected, but I didn't get it and i do if I run it manually????????????????

---

### Post by bundy75 on 2010-09-01
I think I know the problem. 

I have a configuration file for mutt .muttrc in my home directory that allow mail from mutt to be sent via gmail. I guess root user wouldn't have this configuration.

Where would one place a configuration file for root user??????

---

