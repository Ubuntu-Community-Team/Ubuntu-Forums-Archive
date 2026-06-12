---
title: "CUPSd and Apache won't start at boot"
date: 2010-11-07
forum: General Help
---

### Post by NCLI on 2010-11-07
Despite both having put files in the various rc*.d folders and init.d, they don't run at boot. I have to start them manually.

Here's the output of ls -l /etc/init.d:
```
total 228
lrwxrwxrwx 1 root root   21 2010-05-22 14:07 alsa-mixer-save -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 6157 2010-04-13 22:20 apache2
-rwxr-xr-x 1 root root 3541 2010-03-31 00:03 apparmor
lrwxrwxrwx 1 root root   21 2010-05-22 13:49 apport -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:48 atd -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-09-30 06:51 avahi-daemon -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2341 2009-09-07 20:58 bootlogd
lrwxrwxrwx 1 root root   21 2010-05-22 13:49 bridge-network-interface -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 8727 2010-10-12 10:03 clamav-daemon
-rwxr-xr-x 1 root root 7981 2010-10-12 10:03 clamav-freshclam
lrwxrwxrwx 1 root root   21 2010-05-22 13:34 console-setup -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:34 cron -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3095 2010-04-09 18:59 cups
lrwxrwxrwx 1 root root   21 2010-05-22 13:47 dbus -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:35 dmesg -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1235 2009-02-20 18:56 dns-clean
-rwxr-xr-x 1 root root 6604 2009-03-15 17:01 exim4
lrwxrwxrwx 1 root root   21 2010-05-22 13:48 failsafe-x -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1623 2010-02-15 18:16 fancontrol.dpkg-bak
-rwxr-xr-x 1 root root 1105 2010-04-29 10:04 grub-common
-rwxr-xr-x 1 root root 1329 2009-09-07 20:58 halt
-rwxr-xr-x 1 root root 2908 2008-11-06 15:55 hddtemp
lrwxrwxrwx 1 root root   21 2010-05-22 13:30 hostname -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:33 hwclock -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:33 hwclock-save -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:48 irqbalance -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 1293 2009-09-07 20:58 killprocs
-rwxr-xr-x 1 root root  866 2010-02-15 18:18 lm-sensors
-rwxr-xr-x 1 root root 1908 2009-12-12 15:41 mdadm
lrwxrwxrwx 1 root root   21 2010-05-22 13:31 module-init-tools -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2778 2009-10-20 20:13 monit
-rwxr-xr-x 1 root root 2256 2009-12-03 17:04 networking
lrwxrwxrwx 1 root root   21 2010-08-25 06:47 network-interface -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-08-25 06:47 network-interface-security -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-09-15 06:44 nmbd -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3054 2010-06-14 15:56 nscd
-rwxr-xr-x 1 root root 1818 2010-02-03 01:19 ntp
-rwxr-xr-x 1 root root  882 2009-09-07 20:58 ondemand
lrwxrwxrwx 1 root root   21 2010-05-22 13:32 plymouth -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:32 plymouth-log -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:32 plymouth-splash -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:32 plymouth-stop -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 4695 2010-02-19 11:24 postfix
-rwxr-xr-x 1 root root  420 2010-03-07 06:36 pppd-dns
lrwxrwxrwx 1 root root   21 2010-05-22 13:32 procps -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-07-08 06:42 qemu-kvm -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 8863 2009-09-07 20:58 rc
-rwxr-xr-x 1 root root  801 2009-09-07 20:58 rc.local
-rwxr-xr-x 1 root root  117 2009-09-07 20:58 rcS
-rw-r--r-- 1 root root 1510 2009-09-07 20:58 README
-rwxr-xr-x 1 root root  639 2009-09-07 20:58 reboot
-rwxr-xr-x 1 root root 4400 2010-03-30 17:14 rsync
lrwxrwxrwx 1 root root   21 2010-05-22 13:35 rsyslog -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2271 2010-04-15 09:16 saned
-rwxr-xr-x 1 root root 8065 2010-03-31 11:29 saslauthd
lrwxrwxrwx 1 root root   21 2010-10-05 06:52 screen-cleanup -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3200 2010-03-30 02:20 sendsigs
-rwxr-xr-x 1 root root  590 2009-09-07 20:58 single
-rw-r--r-- 1 root root 4271 2009-09-07 20:58 skeleton
-rwxr-xr-x 1 root root 3521 2010-03-07 09:40 smartmontools
lrwxrwxrwx 1 root root   21 2010-09-15 06:44 smbd -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 3899 2010-03-08 17:11 ssh
-rwxr-xr-x 1 root root   23 2010-05-22 14:15 start-fah
-rwxr-xr-x 1 root root  519 2009-09-07 20:58 stop-bootlogd
-rwxr-xr-x 1 root root 1095 2009-09-07 20:58 stop-bootlogd-single
lrwxrwxrwx 1 root root   21 2010-09-02 06:36 udev -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-09-02 06:36 udev-finish -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-09-02 06:36 udevmonitor -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-09-02 06:36 udevtrigger -> /lib/init/upstart-job
lrwxrwxrwx 1 root root   21 2010-05-22 13:49 ufw -> /lib/init/upstart-job
-rwxr-xr-x 1 root root 2787 2009-11-05 14:03 umountfs
-rwxr-xr-x 1 root root 2075 2009-10-14 06:16 umountnfs.sh
-rwxr-xr-x 1 root root 1683 2009-10-14 06:20 umountroot
-rwxr-xr-x 1 root root  810 2010-04-29 16:46 unattended-upgrades
-rwxr-xr-x 1 root root 1997 2009-09-07 20:58 urandom
-rwxr-xr-x 1 root root 1342 2010-03-19 22:16 winbind
-rwxr-xr-x 1 root root 2327 2010-03-07 10:53 wpa-ifupdown
-rwxr-xr-x 1 root root 1777 2008-07-01 19:41 x11-common

```

And ls -l /etc/rc2.d
```
total 4
-rw-r--r-- 1 root root 677 2010-03-30 09:17 README
lrwxrwxrwx 1 root root  23 2010-06-07 09:51 S20clamav-daemon -> ../init.d/clamav-daemon
lrwxrwxrwx 1 root root  26 2010-06-07 09:50 S20clamav-freshclam -> ../init.d/clamav-freshclam
lrwxrwxrwx 1 root root  15 2010-06-07 10:52 S20exim4 -> ../init.d/exim4
lrwxrwxrwx 1 root root  17 2010-09-19 17:48 S20hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root  14 2010-09-03 20:15 S20nscd -> ../init.d/nscd
lrwxrwxrwx 1 root root  17 2010-05-22 13:36 S20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  19 2010-06-07 10:59 S20saslauthd -> ../init.d/saslauthd
lrwxrwxrwx 1 root root  23 2010-09-01 21:49 S20smartmontools -> ../init.d/smartmontools
lrwxrwxrwx 1 root root  19 2010-05-22 14:23 S20start-fah -> ../init.d/start-fah
lrwxrwxrwx 1 root root  19 2010-05-22 14:23 S20start-pms -> ../init.d/start-pms
lrwxrwxrwx 1 root root  17 2010-05-22 13:54 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  13 2010-06-20 18:16 S23ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  15 2010-05-22 13:36 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx 1 root root  14 2010-05-22 13:53 S50cups -> ../init.d/cups
lrwxrwxrwx 1 root root  15 2010-05-22 13:54 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2010-05-22 13:54 S50saned -> ../init.d/saned
lrwxrwxrwx 1 root root  19 2010-05-22 13:54 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2010-05-22 13:54 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  17 2010-05-27 17:40 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  21 2010-05-22 13:56 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  15 2010-09-03 20:30 S99monit -> ../init.d/monit
lrwxrwxrwx 1 root root  18 2010-05-22 13:33 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-05-22 13:33 S99rc.local -> ../init.d/rc.local

```

Am I missing something, or does this look totally normal to you guys too?

---

