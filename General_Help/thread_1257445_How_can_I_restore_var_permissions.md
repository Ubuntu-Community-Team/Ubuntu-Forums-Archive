---
title: "How can I restore /var permissions?"
date: 2009-09-03
forum: General Help
---

### Post by millibyte on 2009-09-03
Hi, 
I wanted to restrict the permissions for /var/www a bit and did a "sudo chmod -R o-rwx *" 
A millisecond after hitting enter I realized I accidentally was in /var and not /var/www, so I set the permissions for all of /var... #-o

Can anyone tell me a trick to restore the default permissions of /var (or something close to it)? So far everything works for me, but I dare not reboot or log off....

Ubuntu 9.04

Cheers!

---

### Post by blueridgedog on 2009-09-03
The default permissions on var are 755 (drwxr-xr-x).  You can restore with the same command you issued with a plus sign in place of a minus (adding the permissions, versus removing them for the owner).  Just for your efforts, here are the additional permissions of the contents of a standard /var:

```
drwxr-xr-x  2 root root  4096 2009-08-29 08:33 backups
drwxr-xr-x 18 root root  4096 2009-02-21 08:24 cache
drwxr-xr-x  2 root root  4096 2008-10-24 01:57 crash
drwxr-xr-x  2 root root  4096 2008-10-29 19:12 games
drwxr-xr-x 57 root root  4096 2009-07-12 08:11 lib
drwxrwsr-x  2 root staff 4096 2008-10-20 08:27 local
drwxrwxrwt  2 root root    60 2009-09-03 07:45 lock
drwxr-xr-x 15 root root  4096 2009-09-03 07:45 log
drwxrwsr-x  2 root mail  4096 2009-02-22 08:23 mail
drwxr-xr-x  2 root root  4096 2008-10-29 18:53 opt
drwxr-xr-x 18 root root   880 2009-08-28 22:35 run
drwxr-xr-x  9 root root  4096 2009-02-22 08:04 spool
drwxrwxrwt  5 root root  4096 2009-09-03 21:23 tmp
```

---

### Post by millibyte on 2009-09-05
Thanks a lot, blueridgedog!! :D
This helps a lot. I think I've set the permissions somewhat functionally and safe for 90% of /var now by giving o+rx recursively to most of the dirs in /var and then removing it again for all files and dirs where the group permissions were set to ---

I'm still in doubt of a few directories:

/var/log : It might be a security risk to give users read access to all logs...

/var/spool : Users should have write access to some subdirectories here, right? Like being able to add user-level cron jobs etc?

Would somebody mind giving me the output of the following for me:
sudo ls -alR /var/spool/ /var/log/

Or is there an easy way to reinstall the contents of /var (or the whole system) without having to reinstall and reconfigure the already painstakingly configured services that are running?

Cheers!

---

### Post by imhotep59 on 2009-09-05
Here it is.
```
/var/spool:
total 56
drwxr-xr-x 10 root   root    4096 2009-05-15 01:04 .
drwxr-xr-x 17 root   root    4096 2009-04-19 21:48 ..
drwxr-xr-x  2 root   root    4096 2009-01-01 17:01 anacron
drwxr-xr-x  5 daemon daemon  4096 2008-07-02 12:20 cron
drwx--x---  3 root   lp      4096 2009-09-04 20:00 cups
drwxr-xr-x  4 root   root    4096 2009-01-07 20:36 cups-pdf
lrwxrwxrwx  1 root   root       7 2009-01-01 16:48 mail -> ../mail
drwxr-s---  2 smmta  smmsp  12288 2009-08-14 20:25 mqueue
drwxrws---  2 smmsp  smmsp  12288 2009-09-05 22:21 mqueue-client
drwxr-xr-x  3 root   root    4096 2009-05-15 01:04 openoffice
drwxrwxrwt  2 root   root    4096 2008-10-10 18:55 samba

/var/spool/anacron:
total 20
drwxr-xr-x  2 root root 4096 2009-01-01 17:01 .
drwxr-xr-x 10 root root 4096 2009-05-15 01:04 ..
-rw-------  1 root root    9 2009-09-05 20:08 cron.daily
-rw-------  1 root root    9 2009-09-03 13:50 cron.monthly
-rw-------  1 root root    9 2009-08-30 13:19 cron.weekly

/var/spool/cron:
total 20
drwxr-xr-x  5 daemon daemon  4096 2008-07-02 12:20 .
drwxr-xr-x 10 root   root    4096 2009-05-15 01:04 ..
drwxrwx--T  2 daemon daemon  4096 2008-07-02 12:28 atjobs
drwxrwx--T  2 daemon daemon  4096 2007-02-20 14:41 atspool
drwx-wx--T  2 root   crontab 4096 2009-04-19 21:48 crontabs

/var/spool/cron/atjobs:
total 12
drwxrwx--T 2 daemon daemon 4096 2008-07-02 12:28 .
drwxr-xr-x 5 daemon daemon 4096 2008-07-02 12:20 ..
-rw------- 1 daemon daemon    2 2008-07-02 12:28 .SEQ

/var/spool/cron/atspool:
total 8
drwxrwx--T 2 daemon daemon 4096 2007-02-20 14:41 .
drwxr-xr-x 5 daemon daemon 4096 2008-07-02 12:20 ..

/var/spool/cron/crontabs:
total 12
drwx-wx--T 2 root   crontab 4096 2009-04-19 21:48 .
drwxr-xr-x 5 daemon daemon  4096 2008-07-02 12:20 ..
-rw------- 1 root   crontab  243 2009-04-19 21:48 root

/var/spool/cups:
total 136
drwx--x---  3 root lp   4096 2009-09-04 20:00 .
drwxr-xr-x 10 root root 4096 2009-05-15 01:04 ..
-rw-------  1 root lp    803 2009-01-07 20:36 c00001
-rw-------  1 root lp    746 2009-01-29 13:39 c00003
-rw-------  1 root lp    761 2009-01-29 21:58 c00004
-rw-------  1 root lp    781 2009-01-29 22:04 c00005
-rw-------  1 root lp    817 2009-02-02 22:45 c00006
-rw-------  1 root lp    761 2009-02-05 19:25 c00007
-rw-------  1 root lp    946 2009-02-05 19:43 c00008
-rw-------  1 root lp    800 2009-02-12 19:36 c00009
-rw-------  1 root lp    946 2009-02-15 21:30 c00010
-rw-------  1 root lp    827 2009-03-11 21:58 c00011
-rw-------  1 root lp    827 2009-03-11 21:58 c00012
-rw-------  1 root lp    873 2009-04-01 13:05 c00013
-rw-------  1 root lp    946 2009-04-01 13:06 c00014
-rw-------  1 root lp    789 2009-04-05 21:23 c00015
-rw-------  1 root lp    971 2009-04-08 22:09 c00016
-rw-------  1 root lp    781 2009-05-17 19:00 c00017
-rw-------  1 root lp    946 2009-05-17 19:05 c00018
-rw-------  1 root lp    946 2009-05-17 19:20 c00019
-rw-------  1 root lp    946 2009-05-17 19:23 c00020
-rw-------  1 root lp    946 2009-05-17 19:26 c00021
-rw-------  1 root lp    792 2009-06-10 21:37 c00022
-rw-------  1 root lp    946 2009-07-01 19:12 c00023
-rw-------  1 root lp    962 2009-07-01 19:12 c00024
-rw-------  1 root lp    946 2009-07-01 20:49 c00025
-rw-------  1 root lp    759 2009-07-05 18:51 c00026
-rw-------  1 root lp    793 2009-07-26 16:38 c00027
-rw-------  1 root lp    747 2009-07-27 21:33 c00028
-rw-------  1 root lp    946 2009-08-30 15:02 c00029
-rw-------  1 root lp    913 2009-08-30 15:07 c00030
-rw-------  1 root lp    946 2009-08-30 15:08 c00031
-rw-------  1 root lp    946 2009-09-04 20:00 c00032
drwxrwx--T  2 root lp   4096 2009-09-04 20:00 tmp

/var/spool/cups/tmp:
total 8
drwxrwx--T 2 root lp 4096 2009-09-04 20:00 .
drwx--x--- 3 root lp 4096 2009-09-04 20:00 ..

/var/spool/cups-pdf:
total 16
drwxr-xr-x  4 root   root    4096 2009-01-07 20:36 .
drwxr-xr-x 10 root   root    4096 2009-05-15 01:04 ..
drwxrwxrwt  2 nobody nogroup 4096 2008-01-24 13:47 ANONYMOUS
drwxr-x--x  2 root   lpadmin 4096 2009-08-30 15:07 SPOOL

/var/spool/cups-pdf/ANONYMOUS:
total 8
drwxrwxrwt 2 nobody nogroup 4096 2008-01-24 13:47 .
drwxr-xr-x 4 root   root    4096 2009-01-07 20:36 ..

/var/spool/cups-pdf/SPOOL:
total 8
drwxr-x--x 2 root lpadmin 4096 2009-08-30 15:07 .
drwxr-xr-x 4 root root    4096 2009-01-07 20:36 ..

/var/spool/mqueue:
total 16
drwxr-s---  2 smmta smmsp 12288 2009-08-14 20:25 .
drwxr-xr-x 10 root  root   4096 2009-05-15 01:04 ..

/var/spool/mqueue-client:
total 52
drwxrws---  2 smmsp smmsp 12288 2009-09-05 22:21 .
drwxr-xr-x 10 root  root   4096 2009-05-15 01:04 ..
-rw-rw----  1 smmsp smmsp  2989 2009-09-02 13:41 dfn82Bf566006900
-rw-rw----  1 smmsp smmsp  1566 2009-09-02 13:41 dfn82Bf567006900
-rw-rw----  1 smmsp smmsp  3178 2009-09-02 19:21 dfn82HL1pU010304
-rw-rw----  1 smmsp smmsp  4615 2009-09-02 19:21 dfn82HL1pV010304
-rw-rw----  1 smmsp smmsp   880 2009-09-05 22:21 qfn82Bf566006900
-rw-rw----  1 smmsp smmsp   875 2009-09-05 22:21 qfn82Bf567006900
-rw-rw----  1 smmsp smmsp   880 2009-09-05 22:21 qfn82HL1pU010304
-rw-rw----  1 smmsp smmsp   880 2009-09-05 22:21 qfn82HL1pV010304

/var/spool/openoffice:
total 12
drwxr-xr-x  3 root root 4096 2009-05-15 01:04 .
drwxr-xr-x 10 root root 4096 2009-05-15 01:04 ..
drwxr-xr-x  3 root root 4096 2009-05-15 01:04 uno_packages

/var/spool/openoffice/uno_packages:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:04 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:04 ..
drwxr-xr-x 4 root root 4096 2009-05-15 01:05 cache

/var/spool/openoffice/uno_packages/cache:
total 32
drwxr-xr-x 4 root root  4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root  4096 2009-05-15 01:04 ..
-rw-r--r-- 1 root root   194 2009-05-15 01:05 log.txt
drwxr-xr-x 8 root root  4096 2009-05-15 01:05 registry
-rw-r--r-- 1 root root     1 2009-05-15 01:05 stamp.sys
drwxr-xr-x 3 root root  4096 2009-05-15 01:05 uno_packages
-rw-r--r-- 1 root root 12288 2009-05-15 01:05 uno_packages.db

/var/spool/openoffice/uno_packages/cache/registry:
total 32
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 4 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.component.PackageRegistryBackend
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.configuration.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.executable.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.help.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.script.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 com.sun.star.comp.deployment.sfwk.PackageRegistryBackend

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend:
total 28
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 ..
-rw-r--r-- 1 root root 8192 2009-05-15 01:05 common.rdb
-rw-r--r-- 1 root root   36 2009-05-15 01:05 Linux_x86rc
-rw-r--r-- 1 root root 2048 2009-05-15 01:05 Linux_x86.rdb
-rw-r--r-- 1 root root  220 2009-05-15 01:05 unorc

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend:
total 20
drwxr-xr-x 3 root root  4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root  4096 2009-05-15 01:05 ..
-rw-r--r-- 1 root root 12288 2009-05-15 01:05 registered_packages.db
drwxr-xr-x 3 root root  4096 2009-05-15 01:05 registry

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 data

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 org

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 openoffice

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 TypeDetection

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice/TypeDetection:
total 20
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
-rw-r--r-- 1 root root 5647 2009-05-15 01:05 Filter.xcu
-rw-r--r-- 1 root root 2329 2009-05-15 01:05 Types.xcu

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend:
total 8
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 ..

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend:
total 8
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 ..

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend:
total 8
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 ..

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend:
total 8
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 8 root root 4096 2009-05-15 01:05 ..

/var/spool/openoffice/uno_packages/cache/uno_packages:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 4 root root 4096 2009-05-15 01:05 ..
-rw------- 1 root root    0 2009-05-15 01:05 MoC83E
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 MoC83E_

/var/spool/openoffice/uno_packages/cache/uno_packages/MoC83E_:
total 12
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 writer2latex.uno.pkg

/var/spool/openoffice/uno_packages/cache/uno_packages/MoC83E_/writer2latex.uno.pkg:
total 412
drwxr-xr-x 3 root root   4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root   4096 2009-05-15 01:05 ..
drwxr-xr-x 2 root root   4096 2009-05-15 01:05 META-INF
-rw-r--r-- 1 root root   5731 2009-05-15 01:05 w2l_filters.xcu
-rw-r--r-- 1 root root   2915 2009-05-15 01:05 w2l_types.xcu
-rw-r--r-- 1 root root 391986 2009-05-15 01:05 writer2latex.jar

/var/spool/openoffice/uno_packages/cache/uno_packages/MoC83E_/writer2latex.uno.pkg/META-INF:
total 12
drwxr-xr-x 2 root root 4096 2009-05-15 01:05 .
drwxr-xr-x 3 root root 4096 2009-05-15 01:05 ..
-rw-r--r-- 1 root root  600 2009-05-15 01:05 manifest.xml

/var/spool/samba:
total 8
drwxrwxrwt  2 root root 4096 2008-10-10 18:55 .
drwxr-xr-x 10 root root 4096 2009-05-15 01:04 ..
```
```
/var/log:
total 10856
drwxr-xr-x 18 root       root    4096 2009-09-05 20:08 .
drwxr-xr-x 17 root       root    4096 2009-04-19 21:48 ..
-rw-r-----  1 root       adm    31193 2009-06-11 14:11 acpid
-rw-r-----  1 root       adm      787 2009-06-07 21:11 acpid.1.gz
-rw-r-----  1 root       adm     6334 2009-06-04 19:07 acpid.2.gz
-rw-r-----  1 root       adm      749 2009-05-24 07:32 acpid.3.gz
-rw-r-----  1 root       adm     2338 2009-05-17 18:20 acpid.4.gz
drwxr-x---  2 root       adm     4096 2009-08-30 13:18 apache2
drwxr-xr-x  2 root       root    4096 2008-05-02 22:41 apparmor
drwxr-xr-x  2 root       root    4096 2009-09-01 02:05 apt
-rw-r-----  1 syslog     adm   218557 2009-09-05 22:33 auth.log
-rw-r-----  1 syslog     adm   246542 2009-08-30 13:18 auth.log.0
-rw-r-----  1 syslog     adm    13479 2009-08-23 08:36 auth.log.1.gz
-rw-r-----  1 syslog     adm     9918 2009-08-16 10:36 auth.log.2.gz
-rw-r-----  1 syslog     adm    13058 2009-08-08 07:48 auth.log.3.gz
-rw-r-----  1 root       adm       31 2008-07-02 12:16 boot
-rw-r--r--  1 root       root   40690 2008-07-02 12:16 bootstrap.log
-rw-rw-r--  1 root       utmp     384 2009-09-03 19:28 btmp
-rw-rw-r--  1 root       utmp    2304 2009-08-12 13:29 btmp.1
drwxr-xr-x  2 root       root    4096 2009-09-05 20:07 cups
-rw-r-----  1 syslog     adm     1677 2009-09-05 22:11 daemon.log
-rw-r-----  1 syslog     adm  1051200 2009-09-05 20:04 daemon.log.0
-rw-r-----  1 syslog     adm    47717 2009-08-30 13:15 daemon.log.1.gz
-rw-r-----  1 syslog     adm    22479 2009-08-23 08:23 daemon.log.2.gz
-rw-r-----  1 syslog     adm    62186 2009-08-16 10:36 daemon.log.3.gz
-rw-r-----  1 syslog     adm   102752 2009-08-08 07:22 daemon.log.4.gz
-rw-r-----  1 syslog     adm    15372 2009-07-16 12:50 daemon.log.5.gz
-rw-r-----  1 syslog     adm    36680 2009-07-02 06:52 daemon.log.6.gz
-rw-r-----  1 syslog     adm   346980 2009-09-05 22:11 debug
-rw-r-----  1 syslog     adm   215500 2009-08-30 13:10 debug.0
-rw-r-----  1 syslog     adm    12443 2009-08-23 08:18 debug.1.gz
-rw-r-----  1 syslog     adm    19792 2009-08-16 10:29 debug.2.gz
-rw-r-----  1 syslog     adm    29843 2009-08-08 07:18 debug.3.gz
drwxr-xr-x  2 root       root    4096 2009-05-07 13:17 dist-upgrade
-rw-r-----  1 root       adm    30521 2009-09-05 19:58 dmesg
-rw-r-----  1 root       adm    30525 2009-09-04 19:10 dmesg.0
-rw-r-----  1 root       adm     9486 2009-09-04 12:38 dmesg.1.gz
-rw-r-----  1 root       adm     9624 2009-09-03 19:27 dmesg.2.gz
-rw-r-----  1 root       adm     9467 2009-09-03 13:22 dmesg.3.gz
-rw-r-----  1 root       adm     9486 2009-09-02 18:18 dmesg.4.gz
-rw-r-----  1 root       adm    11174 2009-09-05 22:11 dpkg.log
-rw-r-----  1 root       adm   196948 2009-08-30 13:27 dpkg.log.1
-rw-r-----  1 root       adm     5395 2009-07-23 21:12 dpkg.log.2.gz
-rw-r-----  1 root       adm     4580 2009-06-29 18:53 dpkg.log.3.gz
-rw-r-----  1 root       adm    19370 2009-05-25 19:38 dpkg.log.4.gz
-rw-r-----  1 root       adm     9710 2009-04-30 13:47 dpkg.log.5.gz
-rw-r-----  1 root       adm      164 2009-03-31 22:42 dpkg.log.6.gz
-rw-r-----  1 root       adm     8999 2009-03-29 22:31 dpkg.log.7.gz
-rw-r-----  1 root       adm     5244 2009-02-20 08:47 dpkg.log.8.gz
-rw-r-----  1 root       adm    93125 2009-01-31 19:03 dpkg.log.9.gz
-rw-r--r--  1 root       root   24024 2009-08-04 20:58 faillog
-rw-r--r--  1 root       root    2171 2008-07-02 12:31 fontconfig.log
drwxr-xr-x  2 root       root    4096 2008-07-02 12:16 fsck
drwxr-xr-x  2 root       root    4096 2009-09-05 19:58 gdm
drwxr-xr-x  2 root       root    4096 2009-01-01 17:50 installer
-rw-r-----  1 syslog     adm   211289 2009-09-05 19:59 kern.log
-rw-r-----  1 syslog     adm  1127131 2009-09-03 13:28 kern.log.0
-rw-r-----  1 syslog     adm   204843 2009-08-30 13:10 kern.log.1.gz
-rw-r-----  1 syslog     adm   162499 2009-08-23 08:18 kern.log.2.gz
-rw-r-----  1 syslog     adm   188911 2009-08-16 10:29 kern.log.3.gz
-rw-r-----  1 syslog     adm    44867 2009-08-08 07:18 kern.log.4.gz
-rw-r-----  1 syslog     adm   229578 2009-07-29 19:18 kern.log.5.gz
-rw-r-----  1 syslog     adm    96487 2009-07-16 12:50 kern.log.6.gz
-rw-rw-r--  1 root       utmp  292292 2009-08-04 20:58 lastlog
-rw-r-----  1 syslog     adm     1188 2009-09-04 20:00 lpr.log
-rw-r-----  1 syslog     adm     1188 2009-07-01 20:49 lpr.log.0
-rw-r-----  1 syslog     adm      246 2009-06-10 21:37 lpr.log.1.gz
-rw-r-----  1 syslog     adm      298 2009-05-17 19:25 lpr.log.2.gz
-rw-r-----  1 syslog     adm      245 2009-04-01 13:06 lpr.log.3.gz
-rw-r-----  1 syslog     adm    38144 2009-09-05 22:21 mail.err
-rw-r-----  1 syslog     adm    31623 2009-08-30 13:10 mail.err.0
-rw-r-----  1 syslog     adm     2035 2009-08-23 08:21 mail.err.1.gz
-rw-r-----  1 syslog     adm     2179 2009-08-16 10:21 mail.err.2.gz
-rw-r-----  1 syslog     adm     2215 2009-08-08 07:45 mail.err.3.gz
-rw-r-----  1 syslog     adm   139185 2009-09-05 22:21 mail.info
-rw-r-----  1 syslog     adm    87428 2009-08-30 13:10 mail.info.0
-rw-r-----  1 syslog     adm     2213 2009-08-23 08:21 mail.info.1.gz
-rw-r-----  1 syslog     adm      890 2009-08-16 10:21 mail.info.2.gz
-rw-r-----  1 syslog     adm    34922 2009-08-13 08:41 mail.info.3.gz
-rw-r-----  1 syslog     adm    17061 2009-07-23 13:41 mail.info.4.gz
-rw-r-----  1 syslog     adm    25802 2009-07-16 12:46 mail.info.5.gz
-rw-r-----  1 syslog     adm    25292 2009-07-05 16:21 mail.info.6.gz
-rw-r-----  1 syslog     adm   139185 2009-09-05 22:21 mail.log
-rw-r-----  1 syslog     adm    87428 2009-08-30 13:10 mail.log.0
-rw-r-----  1 syslog     adm     2212 2009-08-23 08:21 mail.log.1.gz
-rw-r-----  1 syslog     adm      889 2009-08-16 10:21 mail.log.2.gz
-rw-r-----  1 syslog     adm    34921 2009-08-13 08:41 mail.log.3.gz
-rw-r-----  1 syslog     adm    17060 2009-07-23 13:41 mail.log.4.gz
-rw-r-----  1 syslog     adm    25801 2009-07-16 12:46 mail.log.5.gz
-rw-r-----  1 syslog     adm    25291 2009-07-05 16:21 mail.log.6.gz
-rw-r-----  1 syslog     adm    38144 2009-09-05 22:21 mail.warn
-rw-r-----  1 syslog     adm    31787 2009-08-30 13:10 mail.warn.0
-rw-r-----  1 syslog     adm     2036 2009-08-23 08:21 mail.warn.1.gz
-rw-r-----  1 syslog     adm     2180 2009-08-16 10:21 mail.warn.2.gz
-rw-r-----  1 syslog     adm     2216 2009-08-08 07:45 mail.warn.3.gz
-rw-r-----  1 syslog     adm  1040634 2009-09-05 22:18 messages
-rw-r-----  1 syslog     adm   861284 2009-08-30 13:19 messages.0
-rw-r-----  1 syslog     adm   140159 2009-08-23 08:36 messages.1.gz
-rw-r-----  1 syslog     adm   156313 2009-08-16 10:37 messages.2.gz
-rw-r-----  1 syslog     adm    40157 2009-08-08 07:48 messages.3.gz
-rw-r-----  1 syslog     adm   158437 2009-07-09 06:21 messages.4.gz
-rw-r-----  1 syslog     adm   131142 2009-07-02 06:56 messages.5.gz
-rw-r-----  1 syslog     adm    46582 2009-01-15 13:38 messages.6.gz
drwxr-s---  2 mysql      adm     4096 2009-04-15 21:26 mysql
-rw-r-----  1 mysql      adm        0 2009-04-15 21:26 mysql.err
-rw-r-----  1 mysql      adm        0 2009-09-05 20:07 mysql.log
-rw-r-----  1 mysql      adm       20 2009-09-04 13:01 mysql.log.1.gz
-rw-r-----  1 mysql      adm       20 2009-09-03 13:49 mysql.log.2.gz
-rw-r-----  1 mysql      adm       20 2009-09-02 01:58 mysql.log.3.gz
-rw-r-----  1 mysql      adm       20 2009-09-01 02:05 mysql.log.4.gz
-rw-r-----  1 mysql      adm       20 2009-08-31 07:47 mysql.log.5.gz
-rw-r-----  1 mysql      adm       20 2009-08-30 13:18 mysql.log.6.gz
-rw-r-----  1 mysql      adm       20 2009-08-29 20:11 mysql.log.7.gz
drwxr-sr-x  2 news       news    4096 2009-01-01 17:01 news
drwxr-xr-x  2 ntp        ntp     4096 2009-05-13 23:06 ntpstats
drwxr-xr-x  2 root       root    4096 2009-04-23 22:49 partimage
-rw-r--r--  1 root       root    2307 2009-04-23 20:03 pm-suspend.log
-rw-r--r--  1 root       root       0 2009-04-07 19:04 ppp-connect-errors
drwxr-x---  2 privoxy    adm     4096 2009-08-30 13:18 privoxy
-rw-r--r--  1 root       root       0 2008-07-02 12:18 pycentral.log
drwxr-x---  3 root       adm     4096 2009-09-02 10:29 samba
-rw-r--r--  1 root       root  121114 2009-09-03 13:54 scrollkeeper.log
-rw-r--r--  1 root       root   51518 2009-08-26 23:21 scrollkeeper.log.1
-rw-r--r--  1 root       root       0 2009-08-16 10:36 scrollkeeper.log.2
-rw-r-----  1 syslog     adm    12509 2009-09-05 22:21 syslog
-rw-r-----  1 syslog     adm   184304 2009-09-05 20:04 syslog.0
-rw-r-----  1 syslog     adm    33699 2009-09-04 13:01 syslog.1.gz
-rw-r-----  1 syslog     adm   105006 2009-09-03 13:41 syslog.2.gz
-rw-r-----  1 syslog     adm   103128 2009-09-02 01:58 syslog.3.gz
-rw-r-----  1 syslog     adm    67714 2009-09-01 02:05 syslog.4.gz
-rw-r-----  1 syslog     adm    75360 2009-08-31 07:46 syslog.5.gz
-rw-r-----  1 syslog     adm    16816 2009-08-30 13:17 syslog.6.gz
drwxr-s---  2 debian-tor adm     4096 2009-09-05 20:07 tor
-rw-r--r--  1 root       root  383231 2009-09-05 19:57 udev
drwxr-xr-x  2 root       root    4096 2008-03-10 16:24 unattended-upgrades
-rw-r-----  1 syslog     adm    25266 2009-09-05 19:59 user.log
-rw-r-----  1 syslog     adm    20778 2009-08-30 13:10 user.log.0
-rw-r-----  1 syslog     adm      939 2009-08-23 08:18 user.log.1.gz
-rw-r-----  1 syslog     adm     2720 2009-08-16 10:21 user.log.2.gz
-rw-r-----  1 syslog     adm     5444 2009-08-08 07:17 user.log.3.gz
-rw-rw-r--  1 root       utmp   76032 2009-09-05 22:31 wtmp
-rw-rw-r--  1 root       utmp  510336 2009-09-01 01:30 wtmp.1
-rw-r--r--  1 root       root     308 2008-07-02 12:32 wvdialconf.log
-rw-r--r--  1 root       root   24163 2009-09-05 21:44 Xorg.0.log
-rw-r--r--  1 root       root   24108 2009-09-04 20:53 Xorg.0.log.old
-rw-r--r--  1 root       root   23999 2009-01-22 22:18 Xorg.20.log

/var/log/apache2:
total 320
drwxr-x---  2 root adm   4096 2009-08-30 13:18 .
drwxr-xr-x 18 root root  4096 2009-09-05 20:08 ..
-rw-r-----  1 root adm  17760 2009-09-04 22:54 access.log
-rw-r-----  1 root adm  31076 2009-08-30 13:18 access.log.1
-rw-r-----  1 root adm    432 2009-06-28 18:49 access.log.10.gz
-rw-r-----  1 root adm    466 2009-06-21 14:56 access.log.11.gz
-rw-r-----  1 root adm    340 2009-06-14 22:32 access.log.12.gz
-rw-r-----  1 root adm    230 2009-06-07 21:46 access.log.13.gz
-rw-r-----  1 root adm    514 2009-06-04 19:26 access.log.14.gz
-rw-r-----  1 root adm    340 2009-05-24 07:51 access.log.15.gz
-rw-r-----  1 root adm   4144 2009-05-17 18:51 access.log.16.gz
-rw-r-----  1 root adm   7289 2009-05-10 15:01 access.log.17.gz
-rw-r-----  1 root adm  15308 2009-05-03 18:05 access.log.18.gz
-rw-r-----  1 root adm   4087 2009-04-26 15:36 access.log.19.gz
-rw-r-----  1 root adm   4885 2009-04-19 16:18 access.log.20.gz
-rw-r-----  1 root adm   1674 2009-08-23 08:36 access.log.2.gz
-rw-r-----  1 root adm    363 2009-08-16 10:36 access.log.3.gz
-rw-r-----  1 root adm    406 2009-08-09 08:48 access.log.4.gz
-rw-r-----  1 root adm    316 2009-08-02 07:53 access.log.5.gz
-rw-r-----  1 root adm    429 2009-07-27 07:39 access.log.6.gz
-rw-r-----  1 root adm  11486 2009-07-19 21:10 access.log.7.gz
-rw-r-----  1 root adm  57852 2009-07-13 18:51 access.log.8.gz
-rw-r-----  1 root adm    405 2009-07-05 16:28 access.log.9.gz
-rw-r-----  1 root adm   5052 2009-09-05 19:58 error.log
-rw-r-----  1 root adm   5081 2009-08-30 13:18 error.log.1
-rw-r-----  1 root adm    551 2009-06-28 18:49 error.log.10.gz
-rw-r-----  1 root adm    515 2009-06-21 14:56 error.log.11.gz
-rw-r-----  1 root adm    446 2009-06-14 22:32 error.log.12.gz
-rw-r-----  1 root adm    306 2009-06-07 21:46 error.log.13.gz
-rw-r-----  1 root adm    686 2009-06-04 19:26 error.log.14.gz
-rw-r-----  1 root adm    462 2009-05-24 07:51 error.log.15.gz
-rw-r-----  1 root adm    790 2009-05-17 18:51 error.log.16.gz
-rw-r-----  1 root adm    784 2009-05-10 15:01 error.log.17.gz
-rw-r-----  1 root adm    938 2009-05-03 18:05 error.log.18.gz
-rw-r-----  1 root adm    906 2009-04-26 15:36 error.log.19.gz
-rw-r-----  1 root adm    678 2009-04-19 16:18 error.log.20.gz
-rw-r-----  1 root adm    514 2009-08-23 08:36 error.log.2.gz
-rw-r-----  1 root adm    479 2009-08-16 10:36 error.log.3.gz
-rw-r-----  1 root adm    570 2009-08-09 08:48 error.log.4.gz
-rw-r-----  1 root adm    420 2009-08-02 07:53 error.log.5.gz
-rw-r-----  1 root adm    605 2009-07-27 07:39 error.log.6.gz
-rw-r-----  1 root adm    607 2009-07-19 21:10 error.log.7.gz
-rw-r-----  1 root adm    865 2009-07-13 18:51 error.log.8.gz
-rw-r-----  1 root adm    552 2009-07-05 16:28 error.log.9.gz

/var/log/apparmor:
total 8
drwxr-xr-x  2 root root 4096 2008-05-02 22:41 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..

/var/log/apt:
total 60
drwxr-xr-x  2 root root 4096 2009-09-01 02:05 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..
-rw-------  1 root root 4256 2009-09-05 22:11 term.log
-rw-------  1 root root 9052 2009-08-30 13:27 term.log.1.gz
-rw-------  1 root root 3859 2009-07-23 21:12 term.log.2.gz
-rw-------  1 root root 3079 2009-06-29 18:53 term.log.3.gz
-rw-------  1 root root 7366 2009-05-25 19:38 term.log.4.gz
-rw-------  1 root root 9175 2009-04-30 13:47 term.log.5.gz
-rw-------  1 root root  242 2009-03-31 22:42 term.log.6.gz

/var/log/cups:
total 76
drwxr-xr-x  2 root root    4096 2009-09-05 20:07 .
drwxr-xr-x 18 root root    4096 2009-09-05 20:08 ..
-rw-r-----  1 root lpadmin    0 2009-09-05 20:07 access_log
-rw-r-----  1 root lp       318 2009-09-05 19:58 access_log.1.gz
-rw-r-----  1 root lp       157 2009-09-04 12:38 access_log.2.gz
-rw-r-----  1 root lp       310 2009-09-03 13:23 access_log.3.gz
-rw-r-----  1 root lp       339 2009-09-02 01:46 access_log.4.gz
-rw-r-----  1 root lp       274 2009-09-01 01:28 access_log.5.gz
-rw-r-----  1 root lp       565 2009-08-31 07:36 access_log.6.gz
-rw-r-----  1 root lp       154 2009-08-30 13:09 access_log.7.gz
-rw-------  1 root lpadmin    0 2008-07-02 12:22 cups-pdf_log
-rw-r-----  1 root lpadmin    0 2009-07-29 19:17 error_log
-rw-r-----  1 root lp        80 2009-07-27 21:29 error_log.1.gz
-rw-r-----  1 root lp        95 2009-07-26 16:38 error_log.2.gz
-rw-r-----  1 root lp       188 2009-01-29 13:39 error_log.3.gz
-rw-r-----  1 root lpadmin    0 2009-09-05 20:07 page_log
-rw-r-----  1 root lp        76 2009-09-04 20:00 page_log.1.gz
-rw-r-----  1 root lp       116 2009-08-30 15:08 page_log.2.gz
-rw-r-----  1 root lp        75 2009-07-27 21:33 page_log.3.gz
-rw-r-----  1 root lp        87 2009-07-26 16:38 page_log.4.gz
-rw-r-----  1 root lp        74 2009-07-05 18:51 page_log.5.gz
-rw-r-----  1 root lp       124 2009-07-01 20:49 page_log.6.gz
-rw-r-----  1 root lp        77 2009-06-10 21:37 page_log.7.gz

/var/log/dist-upgrade:
total 80
drwxr-xr-x  2 root root  4096 2009-05-07 13:17 .
drwxr-xr-x 18 root root  4096 2009-09-05 20:08 ..
-rw-r--r--  1 root root 68525 2009-05-14 23:24 apt.log

/var/log/fsck:
total 16
drwxr-xr-x  2 root root 4096 2008-07-02 12:16 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..
-rw-r-----  1 root adm   182 2009-09-05 19:57 checkfs
-rw-r-----  1 root adm   215 2009-09-05 19:58 checkroot

/var/log/gdm:
total 40
drwxr-xr-x  2 root root  4096 2009-09-05 19:58 .
drwxr-xr-x 18 root root  4096 2009-09-05 20:08 ..
-rw-r--r--  1 root root  1945 2009-09-05 21:44 :0.log
-rw-r--r--  1 root root 10678 2009-09-04 21:58 :0.log.1
-rw-r--r--  1 root root  1780 2009-09-04 12:38 :0.log.2
-rw-r--r--  1 root root  1890 2009-09-03 21:19 :0.log.3
-rw-r--r--  1 root root  1780 2009-09-03 13:23 :0.log.4
-rw-r--r--  1 root root  1781 2009-01-22 22:18 :20.log

/var/log/installer:
total 1280
drwxr-xr-x  2 root   root   4096 2009-01-01 17:50 .
drwxr-xr-x 18 root   root   4096 2009-09-05 20:08 ..
-rw-------  1 root   root   5358 2009-01-01 16:31 casper.log
-rw-r--r--  1 root   root 308592 2009-01-01 17:50 initial-status.gz
-rw-------  1 root   root 650657 2009-01-01 16:38 partman
-rw-------  1 syslog adm  313649 2009-01-01 17:50 syslog
-rw-------  1 root   root     16 2009-01-01 16:32 version

/var/log/mysql:
total 8
drwxr-s---  2 mysql adm  4096 2009-04-15 21:26 .
drwxr-xr-x 18 root  root 4096 2009-09-05 20:08 ..

/var/log/news:
total 8
drwxr-sr-x  2 news news 4096 2009-01-01 17:01 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..
-rw-r--r--  1 root news    0 2009-01-01 17:01 news.crit
-rw-r--r--  1 root news    0 2009-01-01 17:01 news.err
-rw-r--r--  1 root news    0 2009-01-01 17:01 news.notice

/var/log/ntpstats:
total 8
drwxr-xr-x  2 ntp  ntp  4096 2009-05-13 23:06 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..

/var/log/partimage:
total 4896
drwxr-xr-x  2 root root    4096 2009-04-23 22:49 .
drwxr-xr-x 18 root root    4096 2009-09-05 20:08 ..
-rw-------  1 root root 4989770 2009-04-23 22:52 partimage-debug.log
lrwxrwxrwx  1 root root      38 2009-04-23 22:49 partimage-debug.log_latest -> /var/log/partimage/partimage-debug.log

/var/log/privoxy:
total 68
drwxr-x---  2 privoxy adm  4096 2009-08-30 13:18 .
drwxr-xr-x 18 root    root 4096 2009-09-05 20:08 ..
-rw-r-----  1 privoxy adm  3408 2009-09-05 19:58 errorfile
-rw-r-----  1 privoxy adm   485 2009-08-30 13:09 errorfile.1.gz
-rw-r-----  1 privoxy adm   417 2009-08-23 08:17 errorfile.2.gz
-rw-r-----  1 privoxy adm   420 2009-08-16 10:20 errorfile.3.gz
-rw-r-----  1 privoxy adm   510 2009-08-09 08:13 errorfile.4.gz
-rw-r-----  1 privoxy adm   348 2009-08-02 07:33 errorfile.5.gz
-rw-r-----  1 privoxy adm   551 2009-07-27 07:22 errorfile.6.gz
-rw-r-----  1 privoxy adm   303 2009-07-19 20:50 errorfile.7.gz
-rw-r-----  1 privoxy adm     0 2009-08-30 13:18 logfile
-rw-r-----  1 privoxy adm    20 2009-08-23 08:36 logfile.1.gz
-rw-r-----  1 privoxy adm    20 2009-08-16 10:36 logfile.2.gz
-rw-r-----  1 privoxy adm    20 2009-08-09 08:48 logfile.3.gz
-rw-r-----  1 privoxy adm    20 2009-08-02 07:54 logfile.4.gz
-rw-r-----  1 privoxy adm    20 2009-07-27 07:39 logfile.5.gz
-rw-r-----  1 privoxy adm    20 2009-07-19 21:10 logfile.6.gz
-rw-r-----  1 privoxy adm    20 2009-07-13 18:51 logfile.7.gz

/var/log/samba:
total 2680
drwxr-x---  3 root adm     4096 2009-09-02 10:29 .
drwxr-xr-x 18 root root    4096 2009-09-05 20:08 ..
drwx------  5 root root    4096 2009-01-28 13:50 cores
-rw-r--r--  1 root root    1468 2009-04-07 21:55 log.0.0.0.0
-rw-r--r--  1 root root       0 2009-02-07 17:09 log.10.13.6.4
-rw-r--r--  1 root root       0 2009-02-23 11:02 log.10.141.26.128
-rw-r--r--  1 root root  147775 2009-09-05 20:05 log.127.0.0.1
-rw-r--r--  1 root root    2234 2009-08-23 23:02 log.127.0.1.1
-rw-r--r--  1 root root       0 2009-01-27 22:16 log.169.254.4.231
-rw-r--r--  1 root root       0 2009-04-21 21:20 log.172.16.1.114
-rw-r--r--  1 root root       0 2009-04-21 20:05 log.172.16.1.166
-rw-r--r--  1 root root       0 2009-04-21 20:32 log.172.16.1.199
-rw-r--r--  1 root root       0 2009-04-21 20:44 log.172.16.1.209
-rw-r--r--  1 root root       0 2009-04-21 22:01 log.172.16.1.210
-rw-r--r--  1 root root       0 2009-04-21 20:11 log.172.16.1.54
-rw-r--r--  1 root root       0 2009-04-21 20:46 log.172.16.1.89
-rw-r--r--  1 root root       0 2009-08-31 19:04 log.172.21.16.106
-rw-r--r--  1 root root       0 2009-08-31 19:01 log.172.21.16.119
-rw-r--r--  1 root root       0 2009-08-31 07:55 log.172.21.16.189
-rw-r--r--  1 root root       0 2009-08-31 00:01 log.172.21.16.196
-rw-r--r--  1 root root       0 2009-08-30 23:49 log.172.21.16.204
-rw-r--r--  1 root root       0 2009-08-31 00:12 log.172.21.16.215
-rw-r--r--  1 root root       0 2009-08-31 19:27 log.172.21.16.226
-rw-r--r--  1 root root       0 2009-09-02 10:29 log.172.21.16.230
-rw-r--r--  1 root root       0 2009-08-31 19:11 log.172.21.16.232
-rw-r--r--  1 root root       0 2009-08-31 00:28 log.172.21.16.51
-rw-r--r--  1 root root       0 2009-08-31 17:27 log.172.21.16.58
-rw-r--r--  1 root root       0 2009-08-30 23:51 log.172.21.16.63
-rw-r--r--  1 root root       0 2009-03-04 19:11 log.192.168.0.1
-rw-r--r--  1 root root     600 2009-04-07 19:15 log.192.168.0.2
-rw-r--r--  1 root root       0 2009-01-27 22:22 log.192.168.0.3
-rw-r--r--  1 root root       0 2009-03-04 12:47 log.192.168.0.41
-rw-r--r--  1 root root       0 2009-02-20 20:21 log.192.168.0.5
-rw-r--r--  1 root root       0 2009-01-28 20:34 log.192.168.0.9
-rw-r--r--  1 root root       0 2009-09-01 14:18 log.192.168.1.101
-rw-r--r--  1 root root       0 2009-09-01 14:15 log.192.168.1.104
-rw-r--r--  1 root root       0 2009-07-03 09:28 log.192.168.200.24
-rw-r--r--  1 root root       0 2009-07-03 09:41 log.192.168.200.25
-rw-r--r--  1 root root       0 2009-07-03 10:51 log.192.168.200.26
-rw-r--r--  1 root root       0 2009-06-24 00:11 log.192.168.2.10
-rw-r--r--  1 root root    1028 2009-09-01 10:07 log.adrian
-rw-r--r--  1 root root   19930 2009-08-16 11:00 log.bureau
-rw-r--r--  1 root root     771 2009-08-31 08:36 log.chna-19b7e5ada5
-rw-r--r--  1 root root     514 2009-08-31 08:25 log.drmona
-rw-r--r--  1 root root     257 2009-04-21 22:01 log.goldael-khou-pc
-rw-r--r--  1 root root     257 2009-03-04 12:47 log.jcthc
-rw-r--r--  1 root root   12593 2009-07-03 13:08 log.mac001124d87d10
-rw-r--r--  1 root root    1542 2009-09-01 14:33 log.mac0017f2ccf8f7
-rw-r--r--  1 root root     514 2009-02-23 11:02 log.mac001b6398085e
-rw-r--r--  1 root root    1028 2009-04-21 20:55 log.mac001ec217736f
-rw-r--r--  1 root root   43176 2009-09-01 10:20 log.mac001f5b83c1a1
-rw-r--r--  1 root root    4626 2009-04-23 09:18 log.mac001f5bd31784
-rw-r--r--  1 root root    3084 2009-04-21 20:38 log.mac001f5bea3af4
-rw-r--r--  1 root root     771 2009-08-31 19:32 log.mac002241352afa
-rw-r--r--  1 root root     771 2009-07-03 10:57 log.mac002332c5cbdc
-rw-r--r--  1 root root     514 2009-08-31 19:13 log.mac002332d80944
-rw-r--r--  1 root root   25700 2009-09-02 09:55 log.mac0023df82d1be
-rw-r--r--  1 root root     257 2009-04-21 21:20 log.mac0023df8422d6
-rw-r--r--  1 root root     771 2009-09-02 10:35 log.mac002608047816
-rw-r--r--  1 root root   15163 2009-09-02 08:57 log.macbook-air
-rw-r--r--  1 root root    3855 2009-09-01 14:22 log.macbookpro
-rw-r--r--  1 root root   10280 2009-07-03 12:57 log.macbook-pro
-rw-r--r--  1 root root   13364 2009-09-02 02:35 log.macintosh-2
-rw-r--r--  1 root root    1285 2009-03-04 19:17 log.macintosh-3
-rw-r--r--  1 root root    1324 2009-02-05 20:55 log.marc-desktop
-rw-r--r--  1 root root   42533 2009-08-28 13:47 log.marc-laptop
-rw-r--r--  1 root root     257 2009-08-31 19:04 log.new-host
-rw-r--r--  1 root root   44115 2009-09-05 21:51 log.nmbd
-rw-r--r--  1 root root    1285 2009-08-30 13:15 log.nmbd.1.gz
-rw-r--r--  1 root root    2507 2009-08-23 08:34 log.nmbd.2.gz
-rw-r--r--  1 root root    1771 2009-08-16 10:26 log.nmbd.3.gz
-rw-r--r--  1 root root    1906 2009-08-09 08:20 log.nmbd.4.gz
-rw-r--r--  1 root root    1597 2009-08-02 07:40 log.nmbd.5.gz
-rw-r--r--  1 root root    2556 2009-07-27 07:29 log.nmbd.6.gz
-rw-r--r--  1 root root    1745 2009-07-19 21:07 log.nmbd.7.gz
-rw-r--r--  1 root root    1028 2009-09-02 09:43 log.olguita-pc
-rw-r--r--  1 root root  245947 2009-09-02 21:28 log.pcceline
-rw-r--r--  1 root root    2570 2009-02-20 22:09 log.pc-de-cecile
-rw-r--r--  1 root root    3432 2009-09-05 19:58 log.smbd
-rw-r--r--  1 root root     337 2009-08-30 13:09 log.smbd.1.gz
-rw-r--r--  1 root root     388 2009-08-23 08:17 log.smbd.2.gz
-rw-r--r--  1 root root     381 2009-08-16 10:20 log.smbd.3.gz
-rw-r--r--  1 root root     349 2009-08-09 08:13 log.smbd.4.gz
-rw-r--r--  1 root root     258 2009-08-02 07:33 log.smbd.5.gz
-rw-r--r--  1 root root     362 2009-07-27 07:22 log.smbd.6.gz
-rw-r--r--  1 root root     437 2009-07-19 20:50 log.smbd.7.gz
-rw-r--r--  1 root root    1285 2009-04-21 22:14 log.user-1865306f54
-rw-r--r--  1 root root    2056 2009-04-23 09:05 log.vincent
-rw-r--r--  1 root root       0 2009-01-28 20:07 log.wb-BUILTIN
-rw-r--r--  1 root root  578382 2009-09-05 20:05 log.wb-MARC-LAPTOP
-rw-r--r--  1 root root    7199 2009-09-05 19:58 log.winbindd
-rw-r--r--  1 root root     431 2009-08-30 13:09 log.winbindd.1.gz
-rw-r--r--  1 root root     390 2009-08-23 08:17 log.winbindd.2.gz
-rw-r--r--  1 root root     393 2009-08-16 10:20 log.winbindd.3.gz
-rw-r--r--  1 root root     454 2009-08-09 08:13 log.winbindd.4.gz
-rw-r--r--  1 root root     348 2009-08-02 07:33 log.winbindd.5.gz
-rw-r--r--  1 root root     475 2009-07-27 07:22 log.winbindd.6.gz
-rw-r--r--  1 root root     332 2009-07-19 20:50 log.winbindd.7.gz
-rw-r--r--  1 root root  241349 2009-09-05 20:05 log.winbindd-idmap
-rw-r--r--  1 root root 1026984 2009-08-31 00:06 log.winbindd-idmap.old
-rw-r--r--  1 root root     514 2009-09-01 19:19 log.yannlemeur

/var/log/samba/cores:
total 20
drwx------ 5 root root 4096 2009-01-28 13:50 .
drwxr-x--- 3 root adm  4096 2009-09-02 10:29 ..
drwx------ 2 root root 4096 2009-01-27 21:52 nmbd
drwx------ 2 root root 4096 2009-01-27 21:52 smbd
drwx------ 2 root root 4096 2009-01-28 13:50 winbindd

/var/log/samba/cores/nmbd:
total 8
drwx------ 2 root root 4096 2009-01-27 21:52 .
drwx------ 5 root root 4096 2009-01-28 13:50 ..

/var/log/samba/cores/smbd:
total 8
drwx------ 2 root root 4096 2009-01-27 21:52 .
drwx------ 5 root root 4096 2009-01-28 13:50 ..

/var/log/samba/cores/winbindd:
total 8
drwx------ 2 root root 4096 2009-01-28 13:50 .
drwx------ 5 root root 4096 2009-01-28 13:50 ..

/var/log/tor:
total 32
drwxr-s---  2 debian-tor adm  4096 2009-09-05 20:07 .
drwxr-xr-x 18 root       root 4096 2009-09-05 20:08 ..
-rw-r-----  1 debian-tor adm    73 2009-09-05 20:07 log
-rw-r-----  1 debian-tor adm  2076 2009-09-05 20:07 log.1
-rw-r-----  1 debian-tor adm   495 2009-09-04 13:01 log.2.gz
-rw-r-----  1 debian-tor adm   624 2009-09-03 13:49 log.3.gz
-rw-r-----  1 debian-tor adm  1027 2009-09-02 01:58 log.4.gz
-rw-r-----  1 debian-tor adm   425 2009-09-01 02:05 log.5.gz

/var/log/unattended-upgrades:
total 8
drwxr-xr-x  2 root root 4096 2008-03-10 16:24 .
drwxr-xr-x 18 root root 4096 2009-09-05 20:08 ..
```

---

### Post by millibyte on 2009-09-05
Thanks a bunch! :D

---

