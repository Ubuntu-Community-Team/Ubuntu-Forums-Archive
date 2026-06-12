---
title: "creating an sshd.log"
date: 2010-11-10
forum: General Help
---

### Post by knightofthesun on 2010-11-10
I want to log sshd separately from auth.log.

I understand that we now use rsyslog, so in /etc/rsyslog.d/50-default.conf I added a sshd facility (at the bottom):

```
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log
sshd                            /var/log/sshd.log
```

Then, I also changed the log facility in /etc/ssh/sshd_config from AUTH to SSHD:

```
# Logging
SyslogFacility SSHD
LogLevel VERBOSE
```

The sshd logs are still showing up in auth.log. Is there a different syslog file I should edit?


Jeff


Ubuntu 10.04 (64 bit)
Wubi install in Windows 7

---

### Post by andygauvin.ee on 2011-03-28
bump!

---

### Post by btindie on 2011-03-28
*SSHD* isn't a valid [syslog]("http://en.wikipedia.org/wiki/Syslog") facility, try using one of the *local* ones. Alternatively as you're using rsyslog, it should be possible to [filter]("http://www.rsyslog.com/doc/rsyslog_conf_filter.html") on the [programname.]("http://www.rsyslog.com/doc/property_replacer.html")

---

