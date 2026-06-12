---
title: "Total Silence - No more cron logging. Is it that hard?"
date: 2012-08-23
forum: General Help
---

### Post by brentrussell on 2012-08-23
I have searched all of Al Gore's internet and can not find what I want. I even RTFM but I can't find what I am looking for. I don't want to ever hear from cron again. Not in a cron log, not in the syslog, not in the auth log. I want to stop it all together. Complete darkness.

Currently, I have many cron jobs firing off wget every minute. It is a limitation in the application which I will fix another day. Each time it runs, I gotta hear about it in the syslog and the auth.log. I know I can change it and have it log to another file but I don't want that. If cron fails I will know before I even have time to open up a log file. Can I please just have some peace and quite?

Here is an example cron I have running (There are many)...
**0,10,20,30,40,50 * * * * /usr/bin/wget -nv -t 5 --connect-timeout=4 -w 4 --connect-timeout=20 -nd --no-cache --no-cookies --delete-after -U "CRON PROCESS" [http://site.com/file.php?id=6](http://site.com/file.php?id=6) >/dev/null 2>&1**

Here is what I am getting in the syslog
**Aug 23 19:16:01 ord1 CRON[1747]: (epl) CMD (/usr/bin/wget -nv -t 5 --connect-timeout=4 -w 4 --connect-timeout=20 -nd --no-cache --no-cookies --delete-after -U "CRON PROCESS" [http://site.com/file.php?id=160](http://site.com/file.php?id=160) >/dev/null 2>&1)**

Here is what I am getting in the auth.log
**Aug 23 19:16:01 ord1 CRON[1576]: pam_unix(cron:session): session closed for user epl**

I have rsyslog and here is what I have in the config
> # First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
#daemon.*                       -/var/log/daemon.log
kern.*                          -/var/log/kern.log
#lpr.*                          -/var/log/lpr.log
mail.*                          -/var/log/mail.log
#user.*                         -/var/log/user.log

It is filling up the hard drive very fast. Any suggestions?

---

