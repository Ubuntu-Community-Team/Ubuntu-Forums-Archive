---
title: "Rapidly Decreasing Disk Space?"
date: 2012-09-02
forum: General Help
---

### Post by Sudarson4 on 2012-09-02
I was running Ubuntu 10.04 just fine for about a year. Yesterday i upgraded to 12.04. The disk space is decreasing at an alarming rate, about 9 gigabytes per hour. Im not downloading anything or running any programs in the background. I fear i may have the Rotinom worm, but ClamTK antivirus showed nothing of the sort. Eventually disk space is going to hit 0 and I wont be able to use the system at all. Help!

---

### Post by steeldriver on 2012-09-02
maybe you have a log file that's filling up? prime candidates are

- your ~/.xsession-errors file

- /var/log/syslog

- var/log/kern.log

or you can use a search to find 'big' files e.g. for files bigger than 100MB

```
sudo find / -type f -size +100M 2>/dev/null
```or use the 'du' command (or the GUI Disk Usage analyzer)

---

### Post by Sudarson4 on 2012-09-03
My log files are definitely full. There are over 11000 lines of code in each.
Im not sure what this means. Is it supposed to be like that?
Ive used the command you suggested before, but there arent any hits.

---

### Post by SlugSlug on 2012-09-03
post output of 

```
sudo du -sch /
```

---

### Post by Sudarson4 on 2012-09-03
I found two files in /var/log/cups which are 20gb and 70 gb respectively!
they are 'error_log' and 'error_log.1' 
what should i do with these??

---

### Post by SlugSlug on 2012-09-03
post output of

tail /var/log/cups/error_log

---

### Post by Sudarson4 on 2012-09-03
Here you go :

E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!

---

### Post by SlugSlug on 2012-09-03
> **Sudarson4 said:**
> Here you go :

E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!
E [03/Sep/2012:17:41:10 +0530] Directory "/usr/lib/cups/notifier" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:41:10 +0530] Notifier for subscription 462 (dbus://) went away, retrying!


```
sudo chmod 755 /usr/lib/cups/notifier
sudo chown root.root /usr/lib/cups/notifier
sudo rm /var/log/cups/error*
sudo /etc/init.d/cups restart
```

post output of

```
tail /var/log/cups/error_log
```

---

### Post by Sudarson4 on 2012-09-03
this is what i get for sudo /etc/init.d/cups restart -

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 13847


and for 
tail /var/log/cups/error_log
E [03/Sep/2012:17:50:30 +0530] EPSON-T13-T22E: Directory "/usr/lib/cups/filter" has insecure permissions (040777/uid=0/gid=0).
E [03/Sep/2012:17:50:30 +0530] EPSON-T13-T22E: Directory "/usr/lib/cups/filter" has insecure permissions (040777/uid=0/gid=0).
W [03/Sep/2012:17:50:30 +0530] no access to /System/Library/ColorSync/Profiles/sRGB Profile.icc
W [03/Sep/2012:17:50:30 +0530] no access to /System/Library/ColorSync/Profiles/sRGB Profile.icc
W [03/Sep/2012:17:50:30 +0530] no access to /System/Library/ColorSync/Profiles/Generic CMYK Profile.icc

---

### Post by Sudarson4 on 2012-09-03
all those 8) are '8' followed by ')'

---

### Post by SlugSlug on 2012-09-03
```
sudo chmod 755 /usr/lib/cups -R
sudo chown root.root /usr/lib/cups -R
```


restart cups and post tail command again

---

