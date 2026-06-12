---
title: "MySQL Problem"
date: 2010-09-08
forum: General Help
---

### Post by Red Parrot on 2010-09-08
Hey, I'm having a problem getting MySQL to start.  It's worked fine in the past, but it won't start now.  I pasted in what my syslog is telling me.  I'm pretty new to all this, so hopefully my problem is pretty obvious (just not to me).  Any help would be appreciated.  I've tried some of the other recommendations in other posts like this, but nothing seems to work.  Thanks.


Sep  8 11:46:01 Drupal-02 kernel: [51514.622436] type=1503 audit(1283964361.096:97): operation="open" pid=5508 parent=5507 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:01 Drupal-02 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Sep  8 11:46:01 Drupal-02 mysqld: 100908 11:46:01 [Warning] One can only use the --user switch if running as root
Sep  8 11:46:01 Drupal-02 kernel: [51514.830570] type=1503 audit(1283964361.306:9 operation="open" pid=5628 parent=5514 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:01 Drupal-02 mysqld: 
Sep  8 11:46:01 Drupal-02 mysqld: #007/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Sep  8 11:46:01 Drupal-02 mysqld: 100908 11:46:01 [ERROR] Aborting
Sep  8 11:46:01 Drupal-02 mysqld: 
Sep  8 11:46:01 Drupal-02 mysqld: 100908 11:46:01 [Note] /usr/sbin/mysqld: Shutdown complete
Sep  8 11:46:01 Drupal-02 mysqld: 
Sep  8 11:46:01 Drupal-02 mysqld_safe: mysqld from pid file /var/run/mysqld/mysqld.pid ended
Sep  8 11:46:02 Drupal-02 kernel: [51515.671343] type=1503 audit(1283964362.146:99): operation="open" pid=5636 parent=5635 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:03 Drupal-02 kernel: [51516.723724] type=1503 audit(1283964363.206:100): operation="open" pid=5646 parent=5645 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:04 Drupal-02 kernel: [51517.764179] type=1503 audit(1283964364.246:101): operation="open" pid=5656 parent=5655 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:05 Drupal-02 kernel: [51518.807498] type=1503 audit(1283964365.286:102): operation="open" pid=5666 parent=5665 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:06 Drupal-02 kernel: [51519.839628] type=1503 audit(1283964366.316:103): operation="open" pid=5676 parent=5675 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:07 Drupal-02 kernel: [51520.920201] type=1503 audit(1283964367.406:104): operation="open" pid=5686 parent=5685 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:08 Drupal-02 kernel: [51521.958167] type=1503 audit(1283964368.446:105): operation="open" pid=5696 parent=5695 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:09 Drupal-02 kernel: [51523.006904] type=1503 audit(1283964369.496:106): operation="open" pid=5706 parent=5705 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:10 Drupal-02 kernel: [51524.046142] type=1503 audit(1283964370.536:107): operation="open" pid=5716 parent=5715 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:11 Drupal-02 kernel: [51525.093990] type=1503 audit(1283964371.586:108): operation="open" pid=5726 parent=5725 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:12 Drupal-02 kernel: [51526.135120] type=1503 audit(1283964372.626:109): operation="open" pid=5736 parent=5735 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:13 Drupal-02 kernel: [51527.173543] type=1503 audit(1283964373.666:110): operation="open" pid=5746 parent=5745 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:14 Drupal-02 kernel: [51528.216489] type=1503 audit(1283964374.706:111): operation="open" pid=5756 parent=5755 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:15 Drupal-02 kernel: [51529.265211] type=1503 audit(1283964375.756:112): operation="open" pid=5766 parent=5765 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:15 Drupal-02 kernel: [51529.305187] type=1503 audit(1283964375.796:113): operation="open" pid=5775 parent=5774 profile="/usr/sbin/mysqld" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: Could not open required defaults file: /etc/mysql/debian.cnf
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: Fatal error in defaults handling. Program aborted
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: #007/usr/bin/mysqladmin: connect to server at 'localhost' failed
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Sep  8 11:46:15 Drupal-02 /etc/init.d/mysql[5782]:

---

### Post by spjackson on 2010-09-08
Two things strike me:
1. "Errcode: 13" is Permission denied.
2. "Could not open required defaults file: /etc/mysql/debian.cnf" . This file is present on a default install (on Lucid at any rate).

Compare
```

$ ls -ld /var/log/mysql
drwxr-s--- 2 mysql adm 4096 2010-09-08 07:46 /var/log/mysql

$ ls -lR /etc/mysql
/etc/mysql:
total 16
drwxr-xr-x 2 root root 4096 2010-08-05 10:55 conf.d
-rw------- 1 root root  333 2010-06-10 15:42 debian.cnf
-rwxr-xr-x 1 root root 1198 2010-06-07 20:55 debian-start
-rw-r--r-- 1 root root 3594 2010-07-14 15:28 my.cnf

/etc/mysql/conf.d:
total 4
-rw-r--r-- 1 root root 21 2010-06-07 20:54 mysqld_safe_syslog.cnf

```What do you have?

---

### Post by bodhi.zazen on 2010-09-08
Those error messages are from apparmor.

Put your mysql apparmor profile into complain mode and try again. If it works we need to debug your apparmor profile and you should report this as a bug.

If mysql does not start, then we need to debug mysql.

---

