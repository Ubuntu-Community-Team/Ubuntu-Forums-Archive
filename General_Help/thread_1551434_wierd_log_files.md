---
title: "wierd log files"
date: 2010-08-12
forum: General Help
---

### Post by shadow120 on 2010-08-12
ok i woke up this morning and my pc had been restarted.  i looked at the log files and saw some thing that i dont know what they are. im more curious than anything.  if someone can tell me what is going on here that would be great thanks

auth.log
```
Aug 12 07:35:05 allen-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=allen ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session opened for user allen by (uid=0)
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session closed for user allen
Aug 12 07:35:05 allen-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=allen ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session opened for user allen by (uid=0)
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session closed for user allen
Aug 12 07:35:05 allen-desktop sudo:     root : TTY=unknown ; PWD=/ ; USER=allen ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session opened for user allen by (uid=0)
Aug 12 07:35:05 allen-desktop sudo: pam_unix(sudo:session): session closed for user allen
```

and this line from syslog
Aug 12 07:39:51 allen-desktop syslogd 1.5.0#1ubuntu1: restart.

---

### Post by Fludizz on 2010-08-12
gconftool is the gnome config tool. Seems to me that the gconftool periodically checks for (changed) settings. Do these messages pop up at a regular interval?

---

### Post by shadow120 on 2010-08-12
from today theses were the only one the thing that has me wondering is why my system log was reset

edit: if it was schedueled wouldnt it have cron it the log?

---

### Post by Fludizz on 2010-08-12
Just got home and checked my laptop... I don't have a cronjob for gconftool and I don't have this entry appearing in my syslog. (then again, I also don't leave any computer except my server running 24/7 ;))

---

### Post by shadow120 on 2010-08-12
well everything seems to be fine now so it was most likely normal.  it just bothered me that the system log was restarted.

---

