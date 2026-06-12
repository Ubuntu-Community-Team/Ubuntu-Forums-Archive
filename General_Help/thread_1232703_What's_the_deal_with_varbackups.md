---
title: "What's the deal with /var/backups?"
date: 2009-08-05
forum: General Help
---

### Post by meonkeys on 2009-08-05
Anyone know if there is any standard(s) on how /var/backups is to be used? It appears that aptitude and dpkg back up some files to these directories, but I'm curious what triggers a backup and how restores should be performed.

```
$ ls /var/backups
aptitude.pkgstates.0     dpkg.status.1.gz  dpkg.status.5.gz  infodir.bak
aptitude.pkgstates.1.gz  dpkg.status.2.gz  dpkg.status.6.gz  passwd.bak
aptitude.pkgstates.2.gz  dpkg.status.3.gz  group.bak         shadow.bak
dpkg.status.0            dpkg.status.4.gz  gshadow.bak
```

Also, for all the .bak files, what triggers a backup? vipw/vigr usage? Something else?

Closest likely reference I could find ([Debian bug 122038]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=122038")) seems to indicate that Debian doesn't have a policy for this directory.

---

### Post by michy99 on 2009-08-05
Here's what I found at [http://www.infodrom.org/Debian/doc/maint/Maintenance-pkgmaint.html](http://www.infodrom.org/Debian/doc/maint/Maintenance-pkgmaint.html). (Remember that Ubuntu is Debialn-based.)

There are two lists of installed packages available on Debian. The original file these lists are created from is /var/lib/dpkg/status. This file must not be corrupted, or otherwise your system is hosed. This is the main database for the package manager dpkg.

The Debian package system keeps an older copy from the last but one dpkg run in /var/lib/dpkg/status-old. In order to preserve the system for greater damage upon a crash or filesystem corrupting a daily backup of this file is created into /var/backups when the file differs from the last copy. The backup code is in /etc/cron.daily/standard.

---

