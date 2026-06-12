---
title: "Serious Kernel Problem 9.10"
date: 2009-11-04
forum: General Help
---

### Post by Cowan283 on 2009-11-04
I've just updated to karmic from Jaunty; a couple of minutes after turning on my Acer Aspire one a little orange starburst with a black exclamation mark nearly always pops up in the panel. On clicking it I get the following warning [B]

Your system encountered a serious kernel problem.[/B]

Your system might become unstable now and might need to be restarted.

You can help the developers to fix the problem by reporting it.

Unlike this thread
[http://ubuntuforums.org/showthread.php?t=1308544](http://ubuntuforums.org/showthread.php?t=1308544)
My internet doesn't disconnect, in fact everything continues working fine except for the error messages. I checked the system log viewer which reported that it can't open the following files

auth.log.0
daemon.log.0
debug.0
syslog.0
messages.0
kern.log.0

but then always freezes up and has to be force quitted. Any ideas?

---

### Post by Giblet5 on 2009-11-04
The upgrade was not completely successful.

This can be due to many many things.

You can spend the next three months tracking down problems and fixing them (you will learn much from this, even if you're already a guru), or you can save the list of installed packages, backup your /home filesystem, reinstall, and restore the backup.

If you want to track all of the problems down, then let's begin with file permissions. Open a terminal window and post the output of these two commands: ```
sudo ls -ld /var/log
sudo ls -lR /var/log
```

This might be as easy as creating that directory and rebooting, but Santa Clause and the Easter bunny might remove it again. ;)

(ie, easy fixes like that are stuff of fairy tales)

---

### Post by Cowan283 on 2009-11-04
Well lets try the tracking problems option, then if it takes flipping ages i'll just back up and do a clean install.

doug@doug-laptop:~$ sudo ls -ld /var/log
[sudo] password for doug: 
drwxr-xr-x 17 root root 4096 2009-11-04 14:25 /var/log
doug@doug-laptop:~$ 

doug@doug-laptop:~$ sudo ls -lR /var/log
/var/log:
total 1253376
drwxr-x--- 2 root              adm            4096 2009-11-03 12:45 apache2
drwxr-xr-x 2 root              root           4096 2009-04-08 15:54 apparmor
-rw-r----- 1 root              adm               0 2009-11-03 12:45 apport.log
-rw-r----- 1 root              adm             805 2009-11-02 14:45 apport.log.1
drwxr-xr-x 2 root              root           4096 2009-11-03 12:45 apt
-rw-r--r-- 1 root              root              0 2009-06-04 12:41 aptitude
-rw-r--r-- 1 root              root            311 2009-05-10 13:28 aptitude.1.gz
-rw-r----- 1 syslog            adm           83480 2009-11-04 15:55 auth.log
-rw-r----- 1 syslog            adm           46795 2009-10-27 13:01 auth.log.1
-rw-r----- 1 syslog            adm            5130 2009-10-07 17:33 auth.log.2.gz
-rw-r----- 1 syslog            adm            3078 2009-09-30 17:00 auth.log.3.gz
-rw-r----- 1 syslog            adm            6060 2009-09-23 13:44 auth.log.4.gz
-rw-r----- 1 root              adm              31 2009-04-21 02:01 boot
-rw-r--r-- 1 root              root          38779 2009-04-21 02:01 bootstrap.log
-rw-rw---- 1 root              utmp              0 2009-11-03 12:45 btmp
-rw-rw---- 1 root              utmp             20 2009-10-01 18:07 btmp.1.gz
-rw-r--r-- 1 root              root              0 2009-05-11 09:09 checkbox.log
-rw-r--r-- 1 root              root           8355 2009-05-11 09:09 checkbox.log.1
drwxr-xr-x 2 root              root           4096 2009-05-06 00:44 ConsoleKit
drwxr-xr-x 2 root              root           4096 2009-11-04 14:25 cups
-rw-r----- 1 syslog            adm          575308 2009-11-04 15:55 daemon.log
-rw-r----- 1 syslog            adm          370928 2009-10-27 11:38 daemon.log.1
-rw-r----- 1 syslog            adm           27760 2009-10-07 17:34 daemon.log.2.gz
-rw-r----- 1 syslog            adm           18684 2009-09-30 16:47 daemon.log.3.gz
-rw-r----- 1 syslog            adm           47282 2009-09-23 13:30 daemon.log.4.gz
-rw-r----- 1 syslog            adm          493873 2009-11-04 14:09 debug
-rw-r----- 1 syslog            adm          318081 2009-10-27 11:38 debug.1
-rw-r----- 1 syslog            adm           40538 2009-10-07 17:34 debug.2.gz
-rw-r----- 1 syslog            adm           22923 2009-09-30 16:47 debug.3.gz
-rw-r----- 1 syslog            adm           49817 2009-09-23 13:30 debug.4.gz
drwxr-xr-x 2 root              root           4096 2009-10-30 16:20 dist-upgrade
-rw-r----- 1 root              adm           43769 2009-11-04 13:50 dmesg
-rw-r----- 1 root              adm           45380 2009-11-04 12:57 dmesg.0
-rw-r----- 1 root              adm           11971 2009-11-03 14:36 dmesg.1.gz
-rw-r----- 1 root              adm           13079 2009-11-03 14:00 dmesg.2.gz
-rw-r----- 1 root              adm           11982 2009-11-03 12:10 dmesg.3.gz
-rw-r----- 1 root              adm           12954 2009-11-02 22:53 dmesg.4.gz
-rw-r--r-- 1 root              root              0 2009-11-03 12:45 dpkg.log
-rw-r--r-- 1 root              root        1294878 2009-11-03 12:45 dpkg.log.1
-rw-r----- 1 root              adm            4443 2009-09-30 18:26 dpkg.log.2.gz
-rw-r----- 1 root              adm            5869 2009-08-27 18:35 dpkg.log.3.gz
-rw-r----- 1 root              adm            5965 2009-08-02 09:18 dpkg.log.4.gz
-rw-r----- 1 root              adm            6779 2009-06-29 11:14 dpkg.log.5.gz
-rw-r----- 1 root              adm           73711 2009-05-20 14:18 dpkg.log.6.gz
-rw-r--r-- 1 root              root          24024 2009-11-02 15:50 faillog
-rw-r--r-- 1 root              root           3201 2009-10-30 15:49 fontconfig.log
drwxr-xr-x 2 root              root           4096 2009-04-21 02:01 fsck
drwxrwx--T 2 root              gdm            4096 2009-11-04 13:50 gdm
drwxr-xr-x 2 gnump3d           nogroup        4096 2009-11-03 12:45 gnump3d
drwxr-xr-x 2 root              root           4096 2009-05-05 23:43 installer
-rw-r--r-- 1 root              root              0 2009-11-03 12:45 jockey.log
-rw-r--r-- 1 root              root          25570 2009-11-03 12:45 jockey.log.1
-rw-r--r-- 1 root              root           2566 2009-09-19 20:25 jockey.log.2.gz
-rw-r--r-- 1 root              root           4837 2009-08-07 14:24 jockey.log.3.gz
-rw-r--r-- 1 root              root           2635 2009-05-12 18:48 jockey.log.4.gz
-rw-r--r-- 1 root              root           9632 2009-05-11 09:09 jockey.log.5.gz
-rw-r--r-- 1 root              root          23695 2009-05-10 12:45 jockey.log.6.gz
-rw-r----- 1 syslog            adm       281578679 2009-11-04 15:39 kern.log
-rw-r----- 1 syslog            adm       125496470 2009-10-29 11:25 kern.log.1
-rw-r----- 1 syslog            adm        11123370 2009-10-28 06:58 kern.log.2.gz
-rw-r----- 1 syslog            adm        14691515 2009-10-27 13:02 kern.log.3.gz
-rw-r----- 1 syslog            adm        10766855 2009-10-08 11:29 kern.log.4.gz
-rw-r----- 1 syslog            adm        25092417 2009-10-07 17:32 kern.log.5.gz
-rw-r----- 1 syslog            adm          205943 2009-09-30 16:55 kern.log.6.gz
-rw-r----- 1 syslog            adm          212422 2009-09-23 13:30 kern.log.7.gz
-rw-rw-r-- 1 root              utmp         292292 2009-11-02 15:50 lastlog
-rw-r----- 1 syslog            adm           58223 2009-11-04 13:50 lpr.log
-rw-r----- 1 syslog            adm               0 2009-04-21 02:01 mail.err
-rw-r----- 1 syslog            adm               0 2009-04-21 02:01 mail.info
-rw-r----- 1 syslog            adm               0 2009-04-21 02:01 mail.log
-rw-r----- 1 syslog            adm               0 2009-04-21 02:01 mail.warn
-rw-r--r-- 1 mediatomb         mediatomb      2224 2009-11-04 13:50 mediatomb.log
-rw-r--r-- 1 mediatomb         mediatomb     23963 2009-11-03 12:10 mediatomb.log.1
-rw-r--r-- 1 mediatomb         mediatomb     44480 2009-10-01 17:17 mediatomb.log.2
-rw-r--r-- 1 mediatomb         mediatomb     72288 2009-09-02 16:35 mediatomb.log.3
-rw-r----- 1 syslog            adm       281235263 2009-11-04 15:39 messages
-rw-r----- 1 syslog            adm       125381152 2009-10-29 11:45 messages.1
-rw-r----- 1 syslog            adm        11116260 2009-10-28 07:48 messages.2.gz
-rw-r----- 1 syslog            adm        14650570 2009-10-27 13:02 messages.3.gz
-rw-r----- 1 syslog            adm        10760792 2009-10-08 11:29 messages.4.gz
-rw-r----- 1 syslog            adm        25041887 2009-10-07 17:32 messages.5.gz
-rw-r----- 1 syslog            adm          168732 2009-09-30 16:59 messages.6.gz
-rw-r----- 1 syslog            adm          166807 2009-09-23 13:48 messages.7.gz
drwxr-sr-x 2 news              news           4096 2009-04-21 02:01 news
drwxr-xr-x 2 ntp               ntp            4096 2009-10-22 22:58 ntpstats
-rw-r--r-- 1 root              root           8677 2009-11-04 14:09 pm-powersave.log
-rw-r--r-- 1 root              root           5880 2009-10-10 21:44 pm-suspend.log
-rw-r--r-- 1 root              root              0 2009-04-21 02:04 pycentral.log
drwxr-x--- 2 root              adm            4096 2009-03-27 16:18 samba
-rw-r--r-- 1 root              root              0 2009-11-03 12:45 scrollkeeper.log
-rw-r--r-- 1 root              root          33319 2009-10-30 15:22 scrollkeeper.log.1
-rw-r--r-- 1 root              root         156190 2009-10-04 14:44 scrollkeeper.log.2
drwxr-xr-x 2 speech-dispatcher root           4096 2009-10-13 06:27 speech-dispatcher
-rw-r----- 1 syslog            adm        18096839 2009-11-04 15:55 syslog
-rw-r----- 1 syslog            adm       263832003 2009-11-04 14:25 syslog.1
-rw-r----- 1 syslog            adm           34915 2009-10-30 11:17 syslog.2.gz
-rw-r----- 1 syslog            adm        31460746 2009-10-29 11:50 syslog.3.gz
-rw-r----- 1 syslog            adm        11129376 2009-10-28 07:50 syslog.4.gz
-rw-r----- 1 syslog            adm        14640109 2009-10-27 13:02 syslog.5.gz
-rw-r----- 1 syslog            adm           34886 2009-10-10 14:24 syslog.6.gz
-rw-r----- 1 syslog            adm           67533 2009-10-09 12:40 syslog.7.gz
-rw-r--r-- 1 root              root         184477 2009-11-04 13:50 udev
drwxr-xr-x 2 root              root           4096 2009-03-02 10:07 unattended-upgrades
-rw-r----- 1 syslog            adm            9705 2009-11-04 13:31 user.log
-rw-r----- 1 syslog            adm            2010 2009-10-04 21:41 user.log.1
-rw-r----- 1 syslog            adm             304 2009-09-25 23:47 user.log.2.gz
-rw-r----- 1 syslog            adm             323 2009-09-22 18:55 user.log.3.gz
-rw-r----- 1 syslog            adm          239877 2009-09-18 12:18 user.log.4.gz
-rw-r----- 1 syslog            adm             718 2009-08-10 12:04 user.log.5.gz
-rw-r----- 1 syslog            adm             286 2009-07-05 13:57 user.log.6.gz
-rw-r--r-- 1 root              root              0 2009-11-04 14:25 wpa_supplicant.log
-rw-r--r-- 1 root              root             20 2009-11-03 12:45 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root              root            398 2009-10-30 16:20 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root              root            397 2009-10-30 11:16 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root              root            526 2009-10-29 11:50 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root              root            434 2009-10-28 07:52 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root              utmp          17664 2009-11-04 15:53 wtmp
-rw-rw-r-- 1 root              utmp           4666 2009-11-03 12:10 wtmp.1.gz
-rw-r--r-- 1 root              root          40903 2009-11-04 13:51 Xorg.0.log
-rw-r--r-- 1 root              root          41427 2009-11-04 13:50 Xorg.0.log.old
-rw-r--r-- 1 root              root          18421 2009-05-19 21:53 Xorg.20.log

/var/log/apache2:
total 56
-rw-r----- 1 root adm     0 2009-08-27 18:33 access.log
-rw-r----- 1 root adm   408 2009-08-26 12:12 access.log.1
-rw-r----- 1 root adm   117 2009-08-08 16:07 access.log.2.gz
-rw-r----- 1 root adm   698 2009-11-04 13:51 error.log
-rw-r----- 1 root adm  3477 2009-11-03 12:45 error.log.1
-rw-r----- 1 root adm   887 2009-08-16 11:41 error.log.10.gz
-rw-r----- 1 root adm   619 2009-08-09 10:57 error.log.11.gz
-rw-r----- 1 root adm   575 2009-10-27 13:05 error.log.2.gz
-rw-r----- 1 root adm   479 2009-10-04 14:29 error.log.3.gz
-rw-r----- 1 root adm   544 2009-09-28 16:55 error.log.4.gz
-rw-r----- 1 root adm   686 2009-09-20 14:47 error.log.5.gz
-rw-r----- 1 root adm   556 2009-09-13 19:02 error.log.6.gz
-rw-r----- 1 root adm   512 2009-09-06 01:44 error.log.7.gz
-rw-r----- 1 root adm   728 2009-08-31 11:40 error.log.8.gz
-rw-r----- 1 root adm   819 2009-08-23 16:33 error.log.9.gz
-rw-r--r-- 1 root root    0 2009-08-01 20:55 other_vhosts_access.log

/var/log/apparmor:
total 0

/var/log/apt:
total 180
-rw------- 1 root root      0 2009-11-03 12:45 term.log
-rw------- 1 root root   4487 2009-11-03 12:45 term.log.1.gz
-rw------- 1 root root   2542 2009-09-30 18:26 term.log.2.gz
-rw------- 1 root root   4130 2009-08-27 18:35 term.log.3.gz
-rw------- 1 root root   3982 2009-08-02 09:18 term.log.4.gz
-rw------- 1 root root   4097 2009-06-29 11:14 term.log.5.gz
-rw------- 1 root root 146409 2009-05-20 14:18 term.log.6.gz

/var/log/ConsoleKit:
total 2956
-rw-r--r-- 1 root root 3022165 2009-11-04 13:51 history

/var/log/cups:
total 60
-rw-r----- 1 root lpadmin   0 2009-11-03 12:45 access_log
-rw-r----- 1 root adm     316 2009-11-02 00:03 access_log.1.gz
-rw-r----- 1 root adm     120 2009-10-30 11:10 access_log.2.gz
-rw-r----- 1 root adm     148 2009-10-29 10:26 access_log.3.gz
-rw-r----- 1 root adm     161 2009-10-27 21:09 access_log.4.gz
-rw-r----- 1 root adm     157 2009-10-27 11:38 access_log.5.gz
-rw-r----- 1 root adm     188 2009-10-10 14:16 access_log.6.gz
-rw-r----- 1 root adm     140 2009-10-09 12:33 access_log.7.gz
-rw-r----- 1 root lpadmin   0 2009-11-04 14:24 error_log
-rw-r----- 1 root adm     153 2009-11-04 13:50 error_log.1.gz
-rw-r----- 1 root adm     160 2009-11-03 12:10 error_log.2.gz
-rw-r----- 1 root adm      82 2009-09-18 16:48 error_log.3.gz
-rw-r----- 1 root adm      96 2009-09-18 12:20 error_log.4.gz
-rw-r----- 1 root adm     107 2009-09-17 10:32 error_log.5.gz
-rw-r----- 1 root adm     111 2009-08-31 12:24 error_log.6.gz
-rw-r----- 1 root adm     119 2009-08-29 14:23 error_log.7.gz
-rw-r----- 1 root lpadmin   0 2009-07-29 10:40 page_log
-rw-r----- 1 root adm      98 2009-07-05 13:59 page_log.1.gz

/var/log/dist-upgrade:
total 960
-rw-r--r-- 1 root root  62374 2009-10-30 16:09 apt.log
-rw------- 1 root root 380445 2009-10-30 16:19 apt-term.log
-rw-r--r-- 1 root root 147152 2009-10-30 16:20 main.log
-rw-r--r-- 1 root root 368541 2009-10-30 16:19 term.log
-rw-r--r-- 1 root root    239 2009-10-30 16:20 xorg_fix_intrepid.log

/var/log/fsck:
total 8
-rw-r----- 1 root adm 121 2009-10-30 11:51 checkfs
-rw-r----- 1 root adm 197 2009-10-30 11:51 checkroot

/var/log/gdm:
total 248
-rw-r--r-- 1 root root 40502 2009-11-04 15:35 :0.log
-rw-r--r-- 1 root root 37082 2009-11-04 13:50 :0.log.1
-rw-r--r-- 1 root root 37082 2009-11-03 14:57 :0.log.2
-rw-r--r-- 1 root root 50624 2009-11-03 14:07 :0.log.3
-rw-r--r-- 1 root root 43599 2009-11-03 13:58 :0.log.4
-rw-r--r-- 1 root root   198 2009-11-04 13:51 :0-slave.log
-rw-r--r-- 1 root root   198 2009-11-04 12:58 :0-slave.log.1
-rw-r--r-- 1 root root   286 2009-11-03 14:57 :0-slave.log.2
-rw-r--r-- 1 root root   286 2009-11-03 14:07 :0-slave.log.3
-rw-r--r-- 1 root root   198 2009-11-03 12:10 :0-slave.log.4
-rw-r--r-- 1 root root  1183 2009-05-19 21:53 :20.log
-rw-r--r-- 1 gdm  gdm   1863 2009-11-04 13:51 xsplash-user.log

/var/log/gnump3d:
total 48
-rw-r--r-- 1 root adm     0 2009-08-09 10:57 access.log
-rw-r--r-- 1 root root  539 2009-08-02 09:11 access.log.1
-rw-r--r-- 1 root adm     0 2009-11-03 12:45 error.log
-rw-r--r-- 1 root adm  1574 2009-11-02 13:20 error.log.1
-rw-r--r-- 1 root adm   443 2009-08-16 11:41 error.log.10.gz
-rw-r--r-- 1 root root  468 2009-08-09 10:57 error.log.11.gz
-rw-r--r-- 1 root adm   314 2009-10-27 13:05 error.log.2.gz
-rw-r--r-- 1 root adm   243 2009-10-04 14:30 error.log.3.gz
-rw-r--r-- 1 root adm   265 2009-09-28 16:55 error.log.4.gz
-rw-r--r-- 1 root adm   352 2009-09-20 14:47 error.log.5.gz
-rw-r--r-- 1 root adm   279 2009-09-13 19:02 error.log.6.gz
-rw-r--r-- 1 root adm   281 2009-09-06 01:44 error.log.7.gz
-rw-r--r-- 1 root adm   357 2009-08-31 11:41 error.log.8.gz
-rw-r--r-- 1 root adm   400 2009-08-23 16:33 error.log.9.gz

/var/log/installer:
total 864
-rw------- 1 root   root   5594 2009-05-05 23:29 casper.log
-rw-r--r-- 1 root   root 324601 2009-05-05 23:43 initial-status.gz
-rw------- 1 root   root 100720 2009-05-05 23:36 partman
-rw------- 1 syslog adm  428702 2009-05-05 23:43 syslog
-rw------- 1 root   root     17 2009-05-05 23:29 version

/var/log/news:
total 0
-rw-r----- 1 syslog adm 0 2009-04-21 02:01 news.crit
-rw-r----- 1 syslog adm 0 2009-04-21 02:01 news.err
-rw-r----- 1 syslog adm 0 2009-04-21 02:01 news.notice

/var/log/ntpstats:
total 0

/var/log/samba:
total 0

/var/log/speech-dispatcher:
total 0

/var/log/unattended-upgrades:
total 0
doug@doug-laptop:~$ 





Hows this?

Cheers for your time.

---

### Post by Giblet5 on 2009-11-04
Can you please post the output of ```
df /
```


Six hours of chirping crickets says / was out of free space...

---

### Post by Cowan283 on 2009-11-05
Here we go...

doug@doug-laptop:~$ df /
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113946372  30048928  78109228  28% /
doug@doug-laptop:~$

---

### Post by Cowan283 on 2009-11-05
I gave up and did a clean install in the end, this version hasn't done anything to hurt me so far.. Cheers for your effort in trying to help anyway.

---

### Post by ram130 on 2009-11-11
I keep getting this error alot and its from a clean install. I don't what the matter is, can anyone help me??

---

### Post by 3rdalbum on 2009-11-11
If it merely says that you've had a kernel problem, but you don't actually feel any effects from it, then you don't need to do anything.

If the message bothers you, just run the Update Manager. The latest updates stop the errors being reported.

---

