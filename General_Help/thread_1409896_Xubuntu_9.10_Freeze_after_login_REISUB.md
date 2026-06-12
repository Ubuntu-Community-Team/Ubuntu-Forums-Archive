---
title: "Xubuntu 9.10 Freeze after login REISUB"
date: 2010-02-18
forum: General Help
---

### Post by cd-r80 on 2010-02-18
HI! Xubuntu 9.10 freezes sometimes after login. Also  I Cannot switch to console When it freezes. REISUB & boot again I can do. No freezing has happened inside. Where from to look cause? From syslog I cannot find... 

What are these in syslog:
 Feb 18 09:22:59 ubuntu avahi-daemon[2430]: WARNING: Failed to contact D-Bus daemon.
Feb 18 09:22:59 ubuntu init: avahi-daemon main process (2430) terminated with status 255

Feb 18 09:23:13 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb 18 09:23:13 ubuntu init: gdm main process (1127) killed by KILL signal
Feb 18 09:23:13 ubuntu init: gdm main process ended, respawning

---

### Post by rnerwein on 2010-02-18
hi
i don't know if that will help you.
there is only one config file in /etc/rsyslog.d/50-default.conf where the /dev/xcnosole (that's a named pipe and is not present on my box too - karmic koala 9.10 ).
this pipe is look for me is only called by deamon and ! mail via xconsole.
i have no problems  i haven't configured mail on my ubuntu box.
have a look into your ~/.xsession-errors for further information.
hope it will help you
ciao

---

