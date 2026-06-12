---
title: "sysklogd and logging help"
date: 2009-11-18
forum: General Help
---

### Post by king vash on 2009-11-18
I am trying to get samba (with full_audit) to log to /var/log/samba/audit.log

/etc/samba/smb.conf
under global I have

########### Audit ############
   vfs objects = full_audit
   full_audit:facility = local7
   full_audit:priority = alert
   full_audit:prefix = %u|%I|%m|%S
   full_audit:success = pread
   full_audit:failure = none

/etc/syslog.conf


auth,authpriv.*			/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
local7.alert			-/var/log/samba/audit.log
user.*				-/var/log/user.log


I have tried several small changes but nothing is working

every time I change something I run
```

/etc/init.d/samba restart
/etc/init.d/sysklogd restart
stop rsyslog
start rsyslog
```

I just tried changing *.*  -var/log/test
and I got no test file so I am confused.

any help would be appreciated

---

