---
title: "Firewall filling syslog with error messages? (yet another case of huge log files)"
date: 2011-06-01
forum: General Help
---

### Post by jgratero on 2011-06-01
I'm having a huge issue with some old Dell OptiPlex-GX270 units I'm using in my office, running Lubuntu 11.04 (they previously ran Xubuntu 10.10. Apparently, something is filling up the sys and kern.log with repeated error messages:

```
cpfa26@cpfa26-OptiPlex-GX270:~$ ls -lhS /var/log
total 7,6G
-rw-r----- 1 syslog adm  7,6G 2011-06-01 14:20 kern.log
-rw-rw-r-- 1 root   utmp 286K 2011-05-25 07:55 lastlog
-rw-r--r-- 1 root   root 210K 2011-06-01 07:15 udev
-rw-r----- 1 syslog adm  113K 2011-06-01 14:20 syslog
-rw-r--r-- 1 root   root  41K 2010-10-09 16:27 bootstrap.log
-rw-r----- 1 root   adm   39K 2011-06-01 07:15 dmesg
-rw-r--r-- 1 root   root  30K 2011-06-01 07:49 Xorg.0.log
-rw-r--r-- 1 root   root  24K 2011-05-25 07:55 faillog
-rw-r----- 1 syslog adm   20K 2011-06-01 14:17 auth.log
-rw-r--r-- 1 root   root 6,1K 2011-06-01 10:56 jockey.log
drwxr-xr-x 2 root   root 4,0K 2010-09-27 11:00 apparmor
drwxr-xr-x 2 root   root 4,0K 2011-06-01 14:05 apt
drwxr-xr-x 2 root   root 4,0K 2011-06-01 14:05 ConsoleKit
drwxr-xr-x 2 root   root 4,0K 2011-06-01 14:05 cups
drwxr-xr-x 3 root   root 4,0K 2011-06-01 14:05 dist-upgrade
drwxr-xr-x 2 root   root 4,0K 2010-10-09 16:26 fsck
drwxr-xr-x 2 root   root 4,0K 2011-06-01 14:05 installer
drwxr-xr-x 2 root   root 4,0K 2011-05-23 15:24 news
drwxr-xr-x 2 ntp    ntp  4,0K 2010-08-06 18:20 ntpstats
drwxr-xr-x 3 root   root 4,0K 2011-06-01 14:05 samba
drwxr-xr-x 2 root   root 4,0K 2010-08-26 12:21 unattended-upgrades
-rw-r--r-- 1 root   root 3,4K 2011-05-25 16:02 fontconfig.log
-rw-rw-r-- 1 root   utmp 1,9K 2011-06-01 14:20 wtmp
-rw-r----- 1 root   root 1,4K 2011-06-01 07:17 lxdm.log
-rw-r--r-- 1 root   root  556 2011-06-01 07:15 boot.log
-rw-r--r-- 1 root   root  474 2011-05-24 07:37 wvdialconf.log
-rw-r----- 1 root   adm    31 2010-10-09 16:26 boot
-rw-r--r-- 1 root   root    0 2011-06-01 07:31 alternatives.log
-rw-rw---- 1 root   utmp    0 2011-06-01 07:31 btmp
-rw-r----- 1 syslog adm     0 2011-05-30 07:21 daemon.log
-rw-r----- 1 syslog adm     0 2011-05-30 07:21 debug
-rw-r--r-- 1 root   root    0 2011-06-01 07:31 dpkg.log
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 lpr.log
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 mail.err
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 mail.info
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 mail.log
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 mail.warn
-rw-r----- 1 syslog adm     0 2011-05-30 07:21 messages
-rw-r--r-- 1 root   root    0 2011-06-01 07:31 pm-powersave.log
-rw-r--r-- 1 root   root    0 2010-10-09 16:27 pycentral.log
-rw-r----- 1 syslog adm     0 2011-05-23 15:24 ufw.log
-rw-r----- 1 syslog adm     0 2011-05-30 07:21 user.log
cpfa26@cpfa26-OptiPlex-GX270:~$ man tee
cpfa26@cpfa26-OptiPlex-GX270:~$ sudo tail -n 30 /var/log/kern.log /var/log/syslog
[sudo] password for cpfa26: 
==> /var/log/kern.log <==
Jun  1 14:17:44 cpfa26-OptiPlex-GX270 kernel: [25359.005598] CTLX[3] error: state(Request failed)
Jun  1 14:17:44 cpfa26-OptiPlex-GX270 kernel: [25359.005605] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005664] CTLX[3] error: state(Request failed)
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005670] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005730] CTLX[3] error: state(Request failed)
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005737] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005801] CTLX[3] error: state(Request failed)
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005808] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005857] CTLX[3] error: state(Request failed)
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005864] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005919] CTLX[3] error: state(Request failed)
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005931] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005979] CTLX[3] error: state(Request failed)
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005985] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002045] CTLX[3] error: state(Request failed)
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002052] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005115] CTLX[3] error: state(Request failed)
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005121] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001160] CTLX[3] error: state(Request failed)
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001168] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001219] CTLX[3] error: state(Request failed)
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001225] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005268] CTLX[3] error: state(Request failed)
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005274] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001334] CTLX[3] error: state(Request failed)
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001341] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005381] CTLX[3] error: state(Request failed)
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005388] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005437] CTLX[3] error: state(Request failed)
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005444] getconfig(ROAMMODE) failed. result=-5

==> /var/log/syslog <==
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005664] CTLX[3] error: state(Request failed)
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005670] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005730] CTLX[3] error: state(Request failed)
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005737] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005801] CTLX[3] error: state(Request failed)
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005808] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005857] CTLX[3] error: state(Request failed)
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005864] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005919] CTLX[3] error: state(Request failed)
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005931] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005979] CTLX[3] error: state(Request failed)
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005985] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002045] CTLX[3] error: state(Request failed)
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002052] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005115] CTLX[3] error: state(Request failed)
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005121] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001160] CTLX[3] error: state(Request failed)
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001168] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001219] CTLX[3] error: state(Request failed)
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001225] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005268] CTLX[3] error: state(Request failed)
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005274] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001334] CTLX[3] error: state(Request failed)
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001341] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005381] CTLX[3] error: state(Request failed)
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005388] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005437] CTLX[3] error: state(Request failed)
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005444] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: Called
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: username = [cpfa26]
cpfa26@cpfa26-OptiPlex-GX270:~$ clear

cpfa26@cpfa26-OptiPlex-GX270:~$ sudo tail -n 30 /var/log/kern.log /var/log/syslog
[sudo] password for cpfa26: 
==> /var/log/kern.log <==
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005664] CTLX[3] error: state(Request failed)
Jun  1 14:18:44 cpfa26-OptiPlex-GX270 kernel: [25419.005670] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005730] CTLX[3] error: state(Request failed)
Jun  1 14:19:44 cpfa26-OptiPlex-GX270 kernel: [25479.005737] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005801] CTLX[3] error: state(Request failed)
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005808] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005857] CTLX[3] error: state(Request failed)
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005864] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005919] CTLX[3] error: state(Request failed)
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005931] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005979] CTLX[3] error: state(Request failed)
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005985] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002045] CTLX[3] error: state(Request failed)
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002052] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005115] CTLX[3] error: state(Request failed)
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005121] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001160] CTLX[3] error: state(Request failed)
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001168] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001219] CTLX[3] error: state(Request failed)
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001225] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005268] CTLX[3] error: state(Request failed)
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005274] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001334] CTLX[3] error: state(Request failed)
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001341] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005381] CTLX[3] error: state(Request failed)
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005388] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005437] CTLX[3] error: state(Request failed)
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005444] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 kernel: [26259.005491] CTLX[3] error: state(Request failed)
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 kernel: [26259.005498] getconfig(ROAMMODE) failed. result=-5

==> /var/log/syslog <==
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005801] CTLX[3] error: state(Request failed)
Jun  1 14:20:44 cpfa26-OptiPlex-GX270 kernel: [25539.005808] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005857] CTLX[3] error: state(Request failed)
Jun  1 14:21:44 cpfa26-OptiPlex-GX270 kernel: [25599.005864] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005919] CTLX[3] error: state(Request failed)
Jun  1 14:22:44 cpfa26-OptiPlex-GX270 kernel: [25659.005931] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005979] CTLX[3] error: state(Request failed)
Jun  1 14:23:44 cpfa26-OptiPlex-GX270 kernel: [25719.005985] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002045] CTLX[3] error: state(Request failed)
Jun  1 14:24:44 cpfa26-OptiPlex-GX270 kernel: [25779.002052] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005115] CTLX[3] error: state(Request failed)
Jun  1 14:25:44 cpfa26-OptiPlex-GX270 kernel: [25839.005121] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001160] CTLX[3] error: state(Request failed)
Jun  1 14:26:44 cpfa26-OptiPlex-GX270 kernel: [25899.001168] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001219] CTLX[3] error: state(Request failed)
Jun  1 14:27:44 cpfa26-OptiPlex-GX270 kernel: [25959.001225] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005268] CTLX[3] error: state(Request failed)
Jun  1 14:28:44 cpfa26-OptiPlex-GX270 kernel: [26019.005274] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001334] CTLX[3] error: state(Request failed)
Jun  1 14:29:44 cpfa26-OptiPlex-GX270 kernel: [26079.001341] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005381] CTLX[3] error: state(Request failed)
Jun  1 14:30:44 cpfa26-OptiPlex-GX270 kernel: [26139.005388] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005437] CTLX[3] error: state(Request failed)
Jun  1 14:31:44 cpfa26-OptiPlex-GX270 kernel: [26199.005444] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: Called
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: username = [cpfa26]
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 kernel: [26259.005491] CTLX[3] error: state(Request failed)
Jun  1 14:32:44 cpfa26-OptiPlex-GX270 kernel: [26259.005498] getconfig(ROAMMODE) failed. result=-5
Jun  1 14:33:34 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: Called
Jun  1 14:33:34 cpfa26-OptiPlex-GX270 sudo: pam_sm_authenticate: username = [cpfa26]
cpfa26@cpfa26-OptiPlex-GX270:~$
```

For what I've checked ([here]("http://ubuntuforums.org/showthread.php?t=853347&page=2"), [here]("http://ubuntuforums.org/showthread.php?t=1680105"), [here]("http://ubuntuforums.org/showthread.php?t=1053706"), and [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=583522")) this seems to be a problem related to the firewall (the configuration I set is forcing the firewall to collapse the log with repeated messages) and (or) a problem with the wireless adapter, a firmware problem reported as a bug...

What do you think? Any ideas?

---

