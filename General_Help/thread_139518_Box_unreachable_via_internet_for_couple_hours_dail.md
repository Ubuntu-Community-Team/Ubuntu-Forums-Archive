---
title: "Box unreachable via internet for couple hours daily but box still running! .. ?"
date: 2006-03-04
forum: General Help
---

### Post by CzarAlex on 2006-03-04
Hello, My ubuntu box runs an apacha server as well as some other services like ftp, webmin, php, mysql. Also some MOOs (like MUDs from the 80s, 90s).

Every day, for a couple hours, the box seems unaccessable. After a bit, its all good and the system uptime has not reset, indicating that it has no restarted the box. Other computers in the house sharing the router work just fine. No connection problems. 

My /var/log/messages is all full of -- MARK -- except for every morning at 0737 when it shows:

```
Mar  4 07:37:26 czaralex exiting on signal 15
Mar  4 07:37:27 czaralex syslogd 1.4.1#16ubuntu6: restart.
```

As mentioned above, I dont think the box is restarting because the system uptime is incrementing like normal.

My /var/log/syslog 
```
czar@queeg500:/var/log$ cat syslog
Mar  4 07:37:27 czaralex syslogd 1.4.1#16ubuntu6: restart.
Mar  4 07:37:27 czaralex anacron[12387]: Job `cron.daily' terminated
Mar  4 07:37:27 czaralex anacron[12387]: Normal exit (1 job run)
Mar  4 07:39:01 czaralex /USR/SBIN/CRON[12673]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Mar  4 07:57:27 czaralex -- MARK --
Mar  4 08:09:01 czaralex /USR/SBIN/CRON[13050]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Mar  4 08:17:01 czaralex /USR/SBIN/CRON[13155]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  4 08:37:27 czaralex -- MARK --
Mar  4 08:39:01 czaralex /USR/SBIN/CRON[13422]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Mar  4 08:57:27 czaralex -- MARK --
Mar  4 09:09:01 czaralex /USR/SBIN/CRON[13804]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
czar@queeg500:/var/log$
```

Anything look strange here?

---

### Post by localzuk on 2006-03-04
You have a cron job running once a day which is causing your system to grind to a halt. Take a look for your cron jobs and see what is being ran (I am not sure how to do this...)

---

