---
title: "How to change the frequency of auth.log?"
date: 2010-06-25
forum: General Help
---

### Post by mokachoka on 2010-06-25
I have edited /etc/logrotate.conf to include 
 
/var/log/auth.log {
rotate 6
monthly
copytruncate
compress
}
 
To try and prevent auth.log rotating daily and change it to monthly but it doesnt seem to work.
 
Either im doing it wrong or i need to restart some service?
 
Any help would be appreciated :popcorn:

---

### Post by Bachstelze on 2010-06-25
You need to edit the entry for auth.log in /etc/logrotate.d/syslog-ng.

---

### Post by mokachoka on 2010-06-25
> **Bachstelze said:**
> You need to edit the entry for auth.log in /etc/logrotate.d/syslog-ng.
 
This file does not exist for me?
 
Im running Ubuntu Server 9.04 if that makes a difference?

---

### Post by gmargo on 2010-06-25
You probably have the **rsyslog** package installed, so the file would be /etc/logrotate.d/rsyslog.

Find which syslog package you have with:
```

dpkg -l | grep -i syslog

```

---

### Post by mokachoka on 2010-06-26
It didnt find that package, but it did find logrotate and sysklogd... Any good?

---

### Post by gmargo on 2010-06-26
Kind of strange that you have sysklogd installed since rsyslog is the default.  But anyway...

You can easily help yourself here....  Since your syslog package is sysklogd, get the contents of the package with "dpkg -L sysklogd" and you'll see that there are cron-related entries in /etc/cron.daily/sysklogd and /etc/cron.weekly/sysklogd.  If you take a look at them you'll see that these files are doing the log file rotation using the savelog command.

So all you have to do is move the weekly one over to /etc/cron.monthly/, adjust it accordingly, and remove the daily one.

Alternatively, install rsyslog and remove sysklogd; then you can deal with the log files through the logrotate.d/ configuration files.

---

