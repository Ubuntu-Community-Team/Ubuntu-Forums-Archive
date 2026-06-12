---
title: "aptitude via cron not updating packages"
date: 2010-01-12
forum: General Help
---

### Post by YetAnother on 2010-01-12
Hi,
I am running following command as part of root's crontab.
```
0 1 * * * (/usr/bin/aptitude -y update && /usr/bin/aptitude -y safe-upgrade) 2>&1 >> /var/log/auto_update.log
```aptitude has run and downloaded the packages, but it hasn't upgraded the packages. Last lines of /var/log/auto_update.log are

```

The following packages will be upgraded:
  gnome-screensaver libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
  libc6-dev-i386 libc6-i386 libc6-pic libc6-prof libsmbclient libwbclient0
  samba-common samba-common-bin smbclient
15 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,186kB/51.1MB of archives. After unpacking 8,192B will be used.
Writing extended state information...
Get:1 http://xxxx karmic-updates/main gnome-screensaver 2.28.0-0ubuntu3.3 [4,186kB]
Fetched 4,186kB in 0s (5,553kB/s)
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
```

---

