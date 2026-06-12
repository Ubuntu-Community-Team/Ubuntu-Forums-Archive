---
title: "Can someone help me make a rule to rotate a log file"
date: 2011-08-24
forum: General Help
---

### Post by MechaMechanism on 2011-08-24
I tried reading the logrotate man page and didn't understand any of it.  Seems very complex to me.  I have a log file called bind9-query.log and it needs to be rotated weekly.  Using the existing log apport to start with, can I just change the log file name to bind9-query.log and have it just work.  I'm trying to create a config file from the ones in logrotate.d.

from

/var/log/apport.log {
       daily
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}

to

/var/log/bind9-query.log {
       weekly
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}

Any help is greatly appreciated.

---

### Post by dino99 on 2011-08-24
might help: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by aeiah on 2011-08-24
> **MechaMechanism said:**
> I tried reading the logrotate man page and didn't understand any of it.  Seems very complex to me.  I have a log file called bind9-query.log and it needs to be rotated weekly.  Using the existing log apport to start with, can I just change the log file name to bind9-query.log and have it just work.  I'm trying to create a config file from the ones in logrotate.d.

from

/var/log/apport.log {
       daily
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}

to

/var/log/bind9-query.log {
       weekly
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}

Any help is greatly appreciated.

yea that should work i think, providing your bind9-query.log is in /var/log/ of course.

---

### Post by MechaMechanism on 2011-08-26
> **aeiah said:**
> yea that should work i think, providing your bind9-query.log is in /var/log/ of course.
Yes it did work.

---

