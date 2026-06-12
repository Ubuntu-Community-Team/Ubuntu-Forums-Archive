---
title: "Disable cron logging to syslog"
date: 2009-12-08
forum: General Help
---

### Post by zuehls on 2009-12-08
System:  Ubuntu 9.10

I have tried appending cron.none to my 50-default.conf but cron still logs to syslog (see below).  I am interested in logging all cron activity ONLY to the cron.log but this is not happening.  Also, it does not seem like I can stop cron from logging to syslog.  How to do this?  Anyone with ideas??

*.*;auth,authpriv,cron.none             -/var/log/syslog
cron.*                         /var/log/cron.log

---

### Post by zuehls on 2009-12-10
Bump.

How about disable con from logging to any log?  My syslog is full of cron jobs that run every 3 minutes.

---

### Post by cerber0s on 2012-01-27
For the record, the log is not redirected to cron.log if the syslog has not the right permissions, solution should be (at least on Natty):

```
    
sudo touch /var/log/cron.log
sudo chown syslog:adm /var/log/cron.log
sudo service rsyslog restart

```

---

