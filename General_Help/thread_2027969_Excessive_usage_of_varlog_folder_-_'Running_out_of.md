---
title: "Excessive usage of var/log folder - 'Running out of disk space'"
date: 2012-07-17
forum: General Help
---

### Post by Esau on 2012-07-17
HI All

I've been running Ubuntu on this computer, HP DV1000, for a number of years and all has been fine until yesterday when it displayed the 'running out of disk space" window. I ran Disk Usage Analyzer and found that the var/log folder is using 7.7 GB of space, which  seems a bit excessive. 

I don't want to just delete that folder, since it seems to be a system folder, but am unsure of how to go about finding out what the problem is with the log, generating and analyzing the log file, and then how to go about fixing it.

I'm running 12.04, using Gnome Classic.

Any help would be greatly appreciated.

Thanks

---

### Post by Cheesemill on 2012-07-17
Can you please post the output of:
```
sudo du -h --max-depth=1 /var/log
```and
```
ls -lhS /var/log
```Can you post the output surrounded by [NOPARSE]```
   
```[/NOPARSE] tags to make it easier to read.

---

### Post by Esau on 2012-07-17
[QUOTE=Cheesemill;12109866]Can you please post the output of:
```
64K    /var/log/cups
4.0K    /var/log/samba
4.0K    /var/log/speech-dispatcher
372K    /var/log/upstart
4.0K    /var/log/hp
4.0K    /var/log/news
1.5M    /var/log/dist-upgrade
1.2M    /var/log/installer
148K    /var/log/apt
36K    /var/log/lightdm
800K    /var/log/ConsoleKit
4.0K    /var/log/unattended-upgrades
12K    /var/log/fsck
7.3G    /var/log

``````
total 7.3G
-rw-r----- 1 syslog            adm  2.9G Jul 16 06:30 kern.log.1
-rw-r----- 1 syslog            adm  2.1G Jul 17 08:28 kern.log
-rw-r----- 1 syslog            adm  1.8G Jul 17 06:48 syslog.1
-rw-r----- 1 syslog            adm  294M Jul 17 08:28 syslog
-rw-r----- 1 syslog            adm   53M Jun 25 09:45 kern.log.4.gz
-rw-r----- 1 syslog            adm   50M Jul  8 11:02 kern.log.2.gz
-rw-r----- 1 syslog            adm   30M Jul  1 13:45 kern.log.3.gz
-rw-r----- 1 syslog            adm   23M Jul 13 06:44 syslog.4.gz
-rw-r----- 1 syslog            adm   23M Jul  9 18:39 syslog.7.gz
-rw-r----- 1 syslog            adm   15M Jul 11 07:56 syslog.5.gz
-rw-r----- 1 syslog            adm   12M Jul 16 06:32 syslog.2.gz
-rw-r----- 1 syslog            adm   11M Jul 14 08:52 syslog.3.gz
-rw-r----- 1 syslog            adm  6.1M Jul 10 06:29 syslog.6.gz
-rw-r--r-- 1 root              root 347K Jul 16 17:03 pm-suspend.log
-rw-r--r-- 1 root              root 342K Jul  1 13:33 pm-suspend.log.1
-rw-r--r-- 1 root              root 291K Jun 29 08:23 dpkg.log.1
-rw-rw-r-- 1 root              utmp 286K May 20 19:38 lastlog
-rw-r--r-- 1 root              root 262K Jul 17 07:35 pm-powersave.log
-rw-r--r-- 1 root              root 258K Jul 17 07:15 dpkg.log
-rw-r--r-- 1 root              root 227K Jul 17 07:35 udev
-rw-r--r-- 1 root              root 213K Jul  1 13:33 pm-powersave.log.1
-rw-r----- 1 syslog            adm  194K Jul 16 06:25 auth.log.1
-rw-r--r-- 1 root              root 186K May 31 09:24 dpkg.log.2.gz
-rw-rw-r-- 1 root              utmp 109K Jul 17 08:24 wtmp
-rw-r----- 1 root              adm   49K Jul 17 07:35 dmesg
-rw-r----- 1 root              adm   49K Jul 17 07:03 dmesg.0
-rw-r--r-- 1 root              root  48K Oct 12  2011 bootstrap.log
-rw-rw-r-- 1 root              utmp  46K Jun 28 06:44 wtmp.1
-rw-r--r-- 1 root              root  34K May 21 07:44 jockey.log.1
-rw-r----- 1 syslog            adm   30K Jul 17 08:24 auth.log
-rw-r--r-- 1 root              root  27K Jul 17 07:34 Xorg.0.log.old
-rw-r--r-- 1 root              root  26K Jul 17 07:36 Xorg.0.log
-rw-r--r-- 1 root              root  24K May 20 19:38 faillog
-rw-r----- 1 root              adm   21K Jul 14 08:56 dmesg.2.gz
-rw-r----- 1 root              adm   15K Jul 17 06:42 dmesg.1.gz
-rw-r----- 1 root              adm   14K Jul 12 07:47 dmesg.3.gz
-rw-r----- 1 root              adm   14K Jul 12 07:32 dmesg.4.gz
-rw------- 1 root              root  13K Jul 17 07:35 preload.log
-rw-r----- 1 syslog            adm  7.0K Jun 25 09:45 auth.log.4.gz
-rw-r----- 1 syslog            adm  6.9K Jul  8 10:59 auth.log.2.gz
-rw-r--r-- 1 root              root 5.0K May 31 09:24 alternatives.log.2.gz
-rw-r----- 1 syslog            adm  4.9K Jul  1 13:36 auth.log.3.gz
-rw-r--r-- 1 root              root 4.2K Jul 13 09:14 alternatives.log
drwxr-xr-x 2 root              root 4.0K Jul  1 14:08 apt
drwxr-xr-x 2 root              root 4.0K Jul  1 14:08 ConsoleKit
drwxr-xr-x 2 root              root 4.0K Jul 17 06:47 cups
drwxr-xr-x 2 root              root 4.0K May 20 19:47 dist-upgrade
drwxr-xr-x 2 root              root 4.0K Oct 12  2011 fsck
drwxr-xr-x 2 root              root 4.0K Apr  4 05:18 hp
drwxr-xr-x 2 root              root 4.0K May 20 19:39 installer
drwxr-xr-x 2 root              root 4.0K Jul 17 07:35 lightdm
drwxr-xr-x 2 root              root 4.0K May 20 18:14 news
drwxr-xr-x 2 root              root 4.0K Sep 30  2011 samba
drwx------ 2 speech-dispatcher root 4.0K Jun  5  2011 speech-dispatcher
drwxr-xr-x 2 root              root 4.0K Jul 19  2011 unattended-upgrades
drwxr-xr-x 2 root              root 4.0K Jul 17 07:03 upstart
-rw-r--r-- 1 root              root 3.6K May 31 08:58 pm-suspend.log.2.gz
-rw-r--r-- 1 root              root 3.0K Jun 29 08:23 alternatives.log.1
-rw-r--r-- 1 root              root 2.8K Jul 12 20:46 fontconfig.log
-rw-r--r-- 1 root              root 1.5K May 31 09:25 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root 1.3K Jul 17 07:35 boot.log
-rw-r----- 1 root              adm   853 Jul 16 17:41 apport.log.1
-rw-r----- 1 root              adm   381 Jul 14 13:40 apport.log.2.gz
-rw-r----- 1 root              adm   303 Jul  9 18:36 apport.log.5.gz
-rw-r----- 1 root              adm   278 Jul  5 20:46 apport.log.7.gz
-rw-r----- 1 root              adm   261 Jul 12 07:10 apport.log.3.gz
-rw-r----- 1 root              adm   241 Jul  6 08:10 apport.log.6.gz
-rw-r----- 1 root              adm   206 Jul 10 10:01 apport.log.4.gz
-rw-r----- 1 root              adm    31 Oct 12  2011 boot
-rw-r----- 1 root              adm     0 Jul 17 06:47 apport.log
-rw-rw---- 1 root              utmp    0 Jul  1 14:09 btmp
-rw-rw---- 1 root              utmp    0 Jun  1 07:55 btmp.1
-rw-r--r-- 1 root              root    0 May 21 07:44 jockey.log
-rw-r----- 1 syslog            adm     0 May 20 18:14 mail.err
-rw-r----- 1 syslog            adm     0 May 20 18:14 mail.log
-rw-r--r-- 1 root              root    0 May 24 08:57 pycentral.log
-rw-r----- 1 syslog            adm     0 May 20 18:14 ufw.log

```Hi CheeseMill. Thank you for your reply. Let me know if you need any other report on my end here.

---

### Post by Cheesemill on 2012-07-17
There is definitely something wrong with kern.log and syslog, there has to be a problem somewhere if they are filling up that quickly.

Can you post the output of the following:
```
sudo tail -n 100 /var/log/kern.log
```
```
sudo tail -n 100 /var/log/syslog
```

This will give us the last 100 lines of each file.

---

### Post by Esau on 2012-07-17
This is what I got, and your hunch is correct. The ERROR can't be good.

```
 Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133848] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133856] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133861] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133869] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133877] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133885] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133893] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133900] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133908] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133913] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133921] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133929] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133937] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133945] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133953] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133961] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133966] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133974] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133982] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133990] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133998] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134006] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134014] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134019] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134027] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134035] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134042] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134050] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134058] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134066] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134071] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134079] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134087] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134095] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134103] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134111] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134119] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134124] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134132] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134140] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134148] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134156] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134164] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134171] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134176] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134184] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134192] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134200] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134208] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134216] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134224] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134232] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134240] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134248] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134256] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134264] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134272] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134280] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134285] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134293] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134301] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134308] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134316] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134324] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134332] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134337] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134350] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134359] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134368] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134376] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134384] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134389] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134398] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134406] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134414] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134422] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134431] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134440] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134448] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134456] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134464] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134473] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134481] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134489] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134494] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134502] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134510] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134518] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134526] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134534] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134542] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134547] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134556] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134565] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134573] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134584] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134593] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134601] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134609] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134618] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
    
``` ```
 Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499851] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499856] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499864] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499872] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499879] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499888] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499896] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499904] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499909] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499917] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499925] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499934] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499942] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499949] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499958] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499963] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499971] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499979] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499987] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499995] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500016] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500022] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500031] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500039] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500047] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500055] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500063] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500072] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500080] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500089] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500096] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500104] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500113] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500121] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500126] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500134] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500143] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500151] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500159] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500168] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500176] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500185] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500193] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500201] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500210] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500217] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500225] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500230] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500238] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500246] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500255] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500263] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500271] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500280] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500285] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500293] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500301] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500310] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500318] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500326] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500335] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500343] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500352] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500360] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500368] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500377] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500385] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500390] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500398] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500406] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500414] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500422] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500430] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500438] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500443] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500451] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500459] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500467] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500475] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500483] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500492] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500497] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500504] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500512] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500520] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500528] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500537] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500545] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500554] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500562] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500570] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500578] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500586] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500595] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500600] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500608] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500615] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500624] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500632] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500640] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times 
```

---

### Post by redmk2 on 2012-07-17
> **Esau said:**
> This is what I got, and your hunch is correct. The ERROR can't be good.

```
 Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133848] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133856] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133861] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133869] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133877] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133885] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133893] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133900] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133908] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133913] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133921] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133929] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133937] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133945] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133953] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133961] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133966] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133974] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133982] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133990] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.133998] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134006] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134014] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134019] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134027] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134035] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134042] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134050] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134058] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134066] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134071] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134079] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134087] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134095] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134103] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134111] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134119] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134124] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134132] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134140] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134148] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134156] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134164] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134171] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134176] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134184] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134192] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134200] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134208] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134216] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134224] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134232] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134240] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134248] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134256] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134264] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134272] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134280] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134285] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134293] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134301] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134308] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134316] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134324] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134332] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134337] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134350] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134359] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134368] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134376] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134384] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134389] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134398] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134406] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134414] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134422] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134431] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134440] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134448] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134456] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134464] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134473] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134481] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134489] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134494] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134502] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134510] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134518] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134526] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134534] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134542] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134547] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134556] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134565] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134573] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134584] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134593] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134601] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134609] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:47:29 Bingo-Ubuntu kernel: [ 4340.134618] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
    
``` ```
 Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499851] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499856] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499864] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499872] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499879] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499888] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499896] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499904] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499909] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499917] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499925] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499934] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499942] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499949] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499958] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499963] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499971] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499979] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499987] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.499995] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500016] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500022] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500031] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500039] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500047] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500055] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500063] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500072] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500080] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500089] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500096] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500104] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500113] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500121] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500126] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500134] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500143] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500151] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500159] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500168] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500176] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500185] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500193] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500201] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500210] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500217] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500225] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500230] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500238] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500246] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500255] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500263] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500271] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500280] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500285] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500293] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500301] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500310] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500318] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500326] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500335] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500343] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500352] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500360] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500368] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500377] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500385] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500390] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500398] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500406] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500414] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500422] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500430] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500438] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500443] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500451] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500459] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500467] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500475] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500483] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500492] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500497] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500504] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500512] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500520] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500528] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500537] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500545] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500554] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500562] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500570] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500578] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500586] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500595] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500600] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500608] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500615] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500624] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500632] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Jul 17 08:48:50 Bingo-Ubuntu kernel: [ 4421.500640] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times 
```


These appear to be video errors or there is a bug in the video app.  See [**_[COLOR="Blue"]here[/COLOR]_**.]("https://www.google.com/search?q=*ERROR*+Prepared+flip+multiple+times&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs").

---

### Post by Cheesemill on 2012-07-17
There is a known bug in the Intel video drivers that causes this constant flooding of the logs.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813)

As a workaround you can try creating the following file:
```
gksudo gedit /etc/X11/xorg.conf.d/10-intel.conf
```and adding the following content to it:
```
Section "Device"
    Identifier "card0"
    Driver "intel"
    Option "DRI" "false"
EndSection
```Then reboot your machine, and then delete the log files:
```
sudo rm /var/log/syslog
sudo rm /var/log/syslog.1
sudo rm /var/log/kern.log
sudo rm /var/log/kern.log.1
```Let your machine run for a while and then check the log files again with the tail commands I posted earlier.
Hopefully the errors will have gone.

---

### Post by Esau on 2012-07-17
> **Cheesemill said:**
> There is a known bug in the Intel video drivers that causes this constant flooding of the logs.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765813)

As a workaround you can try creating the following file:
```
gksudo gedit /etc/X11/xorg.conf.d/10-intel.conf
```and adding the following content to it:
```
Section "Device"
    Identifier "card0"
    Driver "intel"
    Option "DRI" "false"
EndSection
```Then reboot your machine, and then delete the log files:
```
sudo rm /var/log/syslog
sudo rm /var/log/syslog.1
sudo rm /var/log/kern.log
sudo rm /var/log/kern.log.1
```Let your machine run for a while and then check the log files again with the tail commands I posted earlier.
Hopefully the errors will have gone.

Unfortunately when I tried that my computer graphics went a little crazy, i.e. choppy black blocks in screen, slow frame rates, etc., so I had to delete that file and go back to the way it was.  But having also implemented your last suggestion of removing the var/log files after the restart has given me back the space on my drive. I've also implemented post #2 from this thread, [http://ubuntuforums.org/showthread.php?t=1873014](http://ubuntuforums.org/showthread.php?t=1873014), so not sure if that's helped out or not but no warnings of yet. I'll keep you posted if anything changes.

Thank you kindly for all of your help. :D

---

### Post by Esau on 2012-07-17
> **redmk2 said:**
> These appear to be video errors or there is a bug in the video app.  See [**_[COLOR=Blue]here[/COLOR]_**.]("https://www.google.com/search?q=*ERROR*+Prepared+flip+multiple+times&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs").

Thank you as well for the link.

---

