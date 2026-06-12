---
title: "I have files in /var/log which total 398 GB"
date: 2010-10-31
forum: General Help
---

### Post by NCLI on 2010-10-31
What the hell could be the cause of this??
```
-rw-r----- 1 syslog            adm       297853028 2010-10-29 08:00 syslog.2.gz
-rw-r----- 1 syslog            adm       342836706 2010-10-28 07:35 syslog.3.gz
-rw-r----- 1 syslog            adm          170650 2010-10-26 09:00 syslog.4.gz
-rw-r----- 1 syslog            adm           43067 2010-10-24 11:49 syslog.5.gz
-rw-r----- 1 syslog            adm           68636 2010-10-23 12:01 syslog.6.gz
-rw-r----- 1 syslog            adm          232173 2010-10-22 08:24 syslog.7.gz
-rw-r--r-- 1 root              root         278659 2010-10-31 12:01 udev
-rw-r----- 1 syslog            adm               0 2010-05-03 23:14 ufw.log
drwxr-xr-x 2 root              root           4096 2009-03-02 11:07 unattended-upgrades
-rw-r----- 1 syslog            adm           58530 2010-10-31 11:01 user.log
-rw-r----- 1 syslog            adm          102639 2010-10-24 11:44 user.log.1
-rw-r----- 1 syslog            adm             953 2010-10-17 12:46 user.log.2.gz
-rw-r----- 1 syslog            adm            2627 2010-10-16 03:04 user.log.3.gz
-rw-r----- 1 syslog            adm             874 2010-10-03 10:14 user.log.4.gz
-rw-r--r-- 1 root              root           2164 2010-05-21 14:00 vbox-install.log
-rw-r--r-- 1 root              root              0 2010-10-09 12:59 wpa_supplicant.log
-rw-r--r-- 1 root              root             20 2010-10-08 08:18 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root              root             20 2010-10-05 07:17 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root              root             20 2010-10-03 10:29 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root              root             20 2010-10-02 01:13 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root              root             20 2010-10-01 07:11 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root              utmp         346368 2010-10-31 11:29 wtmp
-rw-rw-r-- 1 root              utmp           8444 2010-10-01 06:54 wtmp.1.gz
-rw-r--r-- 1 root              root          18014 2010-10-31 12:01 Xorg.0.log
-rw-r--r-- 1 root              root          19434 2010-10-31 02:23 Xorg.0.log.old
-rw-r--r-- 1 root              root          16244 2010-10-04 21:21 Xorg.1.log
-rw-r--r-- 1 root              root          15676 2010-10-02 02:13 Xorg.1.log.old
-rw-r--r-- 1 root              root          15964 2010-08-07 10:44 Xorg.2.log
-rw-r--r-- 1 root              root          15689 2010-06-29 21:39 Xorg.2.log.old

```
I've deleted all the syslogs now, since it prevents me from using the system properly, and it seemed to keep expanding every time I freed space.

After deleting syslog entries:
```
drwxr-xr-x  4 root              root           4K 2010-10-15 18:39 dist-upgrade
-rw-r-----  1 syslog            adm           25K 2010-10-03 10:14 debug.4.gz
-rw-r-----  1 syslog            adm           62K 2010-10-15 18:46 debug.3.gz
-rw-r-----  1 syslog            adm            6K 2010-10-17 12:46 debug.2.gz
-rw-r-----  1 syslog            adm          437K 2010-10-24 11:44 debug.1
-rw-r-----  1 syslog            adm          298K 2010-10-31 11:01 debug
-rw-r-----  1 syslog            adm           18K 2010-10-03 10:20 daemon.log.4.gz
-rw-r-----  1 syslog            adm           45K 2010-10-16 05:34 daemon.log.3.gz
-rw-r-----  1 syslog            adm        19858K 2010-10-17 12:46 daemon.log.2.gz
-rw-r-----  1 syslog            adm          326K 2010-10-24 11:45 daemon.log.1
-rw-r-----  1 syslog            adm    279890071K 2010-10-31 11:34 daemon.log
drwxr-xr-x  2 root              root           4K 2010-10-30 08:00 cups
drwxr-xr-x  2 root              root           4K 2010-10-01 07:11 ConsoleKit
drwxr-xr-x  2 clamav            clamav         4K 2010-10-31 11:16 clamav
-rw-rw----  1 root              utmp           1K 2010-09-04 13:41 btmp.1.gz
-rw-rw----  1 root              utmp           0K 2010-10-01 07:11 btmp
-rw-r--r--  1 root              root          38K 2009-04-20 16:00 bootstrap.log
-rw-r--r--  1 root              root           1K 2010-10-31 12:01 boot.log
-rw-r-----  1 root              adm            1K 2009-04-20 15:59 boot
-rw-r-----  1 syslog            adm            3K 2010-10-03 10:17 auth.log.4.gz
-rw-r-----  1 syslog            adm            5K 2010-10-16 07:30 auth.log.3.gz
-rw-r-----  1 syslog            adm            2K 2010-10-17 12:46 auth.log.2.gz
-rw-r-----  1 syslog            adm           46K 2010-10-24 11:44 auth.log.1
-rw-r-----  1 syslog            adm           47K 2010-10-31 11:36 auth.log
drwxr-xr-x  2 root              root           4K 2010-10-01 07:11 apt
drwxr-xr-x  2 root              root           4K 2009-04-08 16:54 apparmor
-rw-r--r--  1 root              root          65K 2010-10-29 07:47 alternatives.log
drwxr-xr-x 14 root              root           4K 2010-10-15 16:28 ..
drwxr-xr-x 15 root              root           4K 2010-10-31 11:36 .

```

EDIT: Daemon.log seems to suggest it's an NTFS issue, as it's filled with copies of this entry(with different dates and times). Any suggestions?: 
```
Oct 26 17:59:42 jan-desktop ntfs-3g[2056]: ntfs_attr_pread error reading '/giga kopi/Reserve/andet/tethers/Ny mappe43/Ny mappe3/brændnu/New Folder1/New Folder/dload/isos/iso.iso' at offset 2860515328: 4096 <> -1: Input/output error
```

---

### Post by P4man on 2010-10-31
Is it always the same file?
Either way,  Id run chkdsk /f from windows at least twice. See if that solves it.

BTW, I thought my folder structure was messy at times, but I feel a lot better seeing yours now lol.

---

### Post by HermanAB on 2010-10-31
Howdy,

Modify /etc/logrotate.conf

Read the logrotate man page for details.

---

