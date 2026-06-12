---
title: "Help with grep command - HUGE output"
date: 2010-03-15
forum: General Help
---

### Post by smain on 2010-03-15
I am using a daemon called MicroMiser to help optimize battery life. When I want to check the amount of kWh it has saved me I can, according to the following tutorial: [http://www.ubuntugeek.com/micromiser-power-saving-software-for-ubuntu-laptopsdesktopsservers.html](http://www.ubuntugeek.com/micromiser-power-saving-software-for-ubuntu-laptopsdesktopsservers.html) issue the following command:

```
sudo grep Estimated\ energy /var/log/*
```

This however gives a huge output looking similar to this 

```
/var/log/auth.log:Mar 15 19:42:31 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/auth.log.1 /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/daemon.log.1 /var/log/debug /var/log/debug.1 /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/kern.log.1 /var/log/lastlog /var/log/lpr.log /var/log/lpr.log.1 /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.1 /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log
/var/log/auth.log:Mar 15 20:13:57 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/auth.log.1 /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/daemon.log.1 /var/log/debug /var/log/debug.1 /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/kern.log.1 /var/log/lastlog /var/log/lpr.log /var/log/lpr.log.1 /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.1 /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log
/var/log/auth.log:Mar 15 20:18:41 jens-desktop sudo:     jens : TTY=pts/1 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/auth.log.1 /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/daemon.log.1 /var/log/debug /var/log/debug.1 /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/kern.log.1 /var/log/lastlog /var/log/lpr.log /var/log/lpr.log.1 /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.1 /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log
/var/log/auth.log:Mar 15 20:26:11 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/auth.log.1 /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/daemon.log.1 /var/log/debug /var/log/debug.1 /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/kern.log.1 /var/log/lastlog /var/log/lpr.log /var/log/lpr.log.1 /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.1 /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log
/var/log/auth.log.1:Mar 12 16:34:32 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/user.log
/var/log/auth.log.1:Mar 12 16:34:41 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/user.log
/var/log/auth.log.1:Mar 12 16:34:45 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/user.log
/var/log/auth.log.1:Mar 12 17:35:44 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/user.log
/var/log/auth.log.1:Mar 12 17:49:54 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/user.log
/var/log/auth.log.1:Mar 13 17:45:34 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/
/var/log/auth.log.1:Mar 13 21:28:44 jens-desktop sudo:     jens : TTY=pts/0 ; PWD=/home/jens ; USER=root ; COMMAND=/bin/grep Estimated energy /var/log/apparmor /var/log/apt /var/log/auth.log /var/log/autokey-daemon.log /var/log/autokey-daemon.log.old /var/log/boot /var/log/bootstrap.log /var/log/btmp /var/log/ConsoleKit /var/log/cups /var/log/daemon.log /var/log/debug /var/log/dist-upgrade /var/log/dkms_autoinstaller /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/jockey.log /var/log/kern.log /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/news /var/log/pm-powersave.log /var/log/prelink.log /var/log/preload.log /var/log/pycentral.log /var/log/samba /var/log/speech-dispatcher /var/log/syslog /var/log/syslog.1 /var/log/udev /var/log/unattended-upgrades /var/log/
/var/log/daemon.log:Mar 15 16:34:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.001467kWh (23.47%)
/var/log/daemon.log:Mar 15 16:40:52 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.003368kWh (26.85%)
/var/log/daemon.log:Mar 15 16:53:40 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.008877kWh (35.29%)
/var/log/daemon.log:Mar 15 17:19:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.019866kWh (39.45%)
/var/log/daemon.log:Mar 15 18:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.045512kWh (45.16%)
/var/log/daemon.log:Mar 15 19:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.086339kWh (54.01%)
/var/log/daemon.log:Mar 15 20:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.116689kWh (53.30%)
/var/log/daemon.log.1:Mar 12 16:32:03 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/daemon.log.1:Mar 12 16:32:04 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/daemon.log.1:Mar 12 16:32:07 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000009kWh (20.37%)
/var/log/daemon.log.1:Mar 12 16:32:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000029kWh (19.67%)
/var/log/daemon.log.1:Mar 12 16:32:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000060kWh (18.06%)
/var/log/daemon.log.1:Mar 12 16:32:49 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000131kWh (17.93%)
/var/log/daemon.log.1:Mar 12 16:33:37 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000377kWh (24.77%)
/var/log/daemon.log.1:Mar 12 16:35:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000915kWh (29.53%)
/var/log/daemon.log.1:Mar 12 16:38:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.001904kWh (30.48%)
/var/log/daemon.log.1:Mar 12 16:44:49 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.004719kWh (37.64%)
/var/log/daemon.log.1:Mar 12 16:57:37 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.010762kWh (42.78%)
/var/log/daemon.log.1:Mar 12 17:23:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.023314kWh (46.27%)
/var/log/daemon.log.1:Mar 12 18:14:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.040297kWh (40.01%)
/var/log/daemon.log.1:Mar 13 13:24:56 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/daemon.log.1:Mar 13 13:24:59 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000002kWh (3.85%)
/var/log/daemon.log.1:Mar 13 13:25:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000014kWh (10.00%)
/var/log/daemon.log.1:Mar 13 13:25:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000038kWh (11.58%)
/var/log/daemon.log.1:Mar 13 13:25:41 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000101kWh (13.84%)
/var/log/daemon.log.1:Mar 13 13:26:29 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000530kWh (35.10%)
/var/log/daemon.log.1:Mar 13 13:28:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.001896kWh (61.64%)
/var/log/daemon.log.1:Mar 13 13:31:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.004649kWh (74.60%)
/var/log/daemon.log.1:Mar 13 13:37:41 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.007820kWh (62.33%)
/var/log/daemon.log.1:Mar 13 13:50:29 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.008768kWh (34.88%)
/var/log/daemon.log.1:Mar 13 14:16:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.010519kWh (20.90%)
/var/log/daemon.log.1:Mar 13 15:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.017293kWh (17.17%)
/var/log/daemon.log.1:Mar 13 16:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.029849kWh (18.69%)
/var/log/daemon.log.1:Mar 13 17:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.035707kWh (16.33%)
/var/log/daemon.log.1:Mar 13 18:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.049786kWh (17.92%)
/var/log/daemon.log.1:Mar 13 19:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.073532kWh (21.82%)
/var/log/daemon.log.1:Mar 13 20:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.097103kWh (24.52%)
/var/log/daemon.log.1:Mar 13 21:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.117141kWh (25.74%)
/var/log/daemon.log.1:Mar 13 22:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.140306kWh (27.29%)
/var/log/daemon.log.1:Mar 13 23:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.159051kWh (27.75%)
/var/log/daemon.log.1:Mar 14 00:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.186875kWh (29.56%)
/var/log/daemon.log.1:Mar 14 09:20:23 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/daemon.log.1:Mar 14 09:20:26 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000006kWh (12.79%)
/var/log/daemon.log.1:Mar 14 09:20:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000006kWh (4.33%)
/var/log/daemon.log.1:Mar 14 09:20:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000052kWh (15.23%)
/var/log/daemon.log.1:Mar 14 09:21:08 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000107kWh (14.65%)
/var/log/daemon.log.1:Mar 14 09:21:56 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000529kWh (34.99%)
/var/log/daemon.log.1:Mar 14 09:23:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.001315kWh (42.55%)
/var/log/daemon.log.1:Mar 14 09:26:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.001952kWh (31.29%)
/var/log/daemon.log.1:Mar 14 09:33:08 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.005002kWh (39.92%)
/var/log/daemon.log.1:Mar 14 09:45:56 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.009215kWh (36.72%)
/var/log/daemon.log.1:Mar 14 10:11:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.022295kWh (44.35%)
/var/log/daemon.log.1:Mar 14 11:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.039942kWh (39.65%)
/var/log/daemon.log.1:Mar 14 12:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.065838kWh (41.21%)
/var/log/daemon.log.1:Mar 14 13:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.088125kWh (40.28%)
/var/log/daemon.log.1:Mar 14 14:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.118835kWh (42.78%)
/var/log/daemon.log.1:Mar 14 15:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.142807kWh (42.40%)
/var/log/daemon.log.1:Mar 14 16:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.165418kWh (41.79%)
/var/log/daemon.log.1:Mar 14 17:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.188150kWh (41.37%)
/var/log/daemon.log.1:Mar 14 18:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.208836kWh (40.64%)
/var/log/daemon.log.1:Mar 14 19:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.234687kWh (40.96%)
/var/log/daemon.log.1:Mar 14 20:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.250418kWh (39.62%)
/var/log/daemon.log.1:Mar 15 16:28:07 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/daemon.log.1:Mar 15 16:28:10 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.00%)
/var/log/daemon.log.1:Mar 15 16:28:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000015kWh (10.97%)
/var/log/daemon.log.1:Mar 15 16:28:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000078kWh (23.53%)
/var/log/daemon.log.1:Mar 15 16:28:52 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000154kWh (20.84%)
/var/log/daemon.log.1:Mar 15 16:29:40 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000338kWh (22.17%)
/var/log/daemon.log.1:Mar 15 16:31:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000630kWh (20.34%)
/var/log/syslog:Mar 15 16:34:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.001467kWh (23.47%)
/var/log/syslog:Mar 15 16:40:52 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.003368kWh (26.85%)
/var/log/syslog:Mar 15 16:53:40 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.008877kWh (35.29%)
/var/log/syslog:Mar 15 17:19:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.019866kWh (39.45%)
/var/log/syslog:Mar 15 18:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.045512kWh (45.16%)
/var/log/syslog:Mar 15 19:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.086339kWh (54.01%)
/var/log/syslog:Mar 15 20:10:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.116689kWh (53.30%)
/var/log/syslog.1:Mar 12 16:32:03 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 12 16:32:04 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 12 16:32:07 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000009kWh (20.37%)
/var/log/syslog.1:Mar 12 16:32:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000029kWh (19.67%)
/var/log/syslog.1:Mar 12 16:32:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000060kWh (18.06%)
/var/log/syslog.1:Mar 12 16:32:49 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000131kWh (17.93%)
/var/log/syslog.1:Mar 12 16:33:37 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000377kWh (24.77%)
/var/log/syslog.1:Mar 12 16:35:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.000915kWh (29.53%)
/var/log/syslog.1:Mar 12 16:38:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.001904kWh (30.48%)
/var/log/syslog.1:Mar 12 16:44:49 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.004719kWh (37.64%)
/var/log/syslog.1:Mar 12 16:57:37 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.010762kWh (42.78%)
/var/log/syslog.1:Mar 12 17:23:13 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.023314kWh (46.27%)
/var/log/syslog.1:Mar 12 18:14:25 jens-desktop micromiser[4289]: Estimated energy saved since MicroMiser start: 0.040297kWh (40.01%)
/var/log/syslog.1:Mar 13 13:24:56 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 13 13:24:59 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000002kWh (3.85%)
/var/log/syslog.1:Mar 13 13:25:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000014kWh (10.00%)
/var/log/syslog.1:Mar 13 13:25:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000038kWh (11.58%)
/var/log/syslog.1:Mar 13 13:25:41 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000101kWh (13.84%)
/var/log/syslog.1:Mar 13 13:26:29 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.000530kWh (35.10%)
/var/log/syslog.1:Mar 13 13:28:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.001896kWh (61.64%)
/var/log/syslog.1:Mar 13 13:31:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.004649kWh (74.60%)
/var/log/syslog.1:Mar 13 13:37:41 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.007820kWh (62.33%)
/var/log/syslog.1:Mar 13 13:50:29 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.008768kWh (34.88%)
/var/log/syslog.1:Mar 13 14:16:05 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.010519kWh (20.90%)
/var/log/syslog.1:Mar 13 15:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.017293kWh (17.17%)
/var/log/syslog.1:Mar 13 16:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.029849kWh (18.69%)
/var/log/syslog.1:Mar 13 17:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.035707kWh (16.33%)
/var/log/syslog.1:Mar 13 18:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.049786kWh (17.92%)
/var/log/syslog.1:Mar 13 19:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.073532kWh (21.82%)
/var/log/syslog.1:Mar 13 20:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.097103kWh (24.52%)
/var/log/syslog.1:Mar 13 21:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.117141kWh (25.74%)
/var/log/syslog.1:Mar 13 22:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.140306kWh (27.29%)
/var/log/syslog.1:Mar 13 23:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.159051kWh (27.75%)
/var/log/syslog.1:Mar 14 00:07:17 jens-desktop micromiser[1570]: Estimated energy saved since MicroMiser start: 0.186875kWh (29.56%)
/var/log/syslog.1:Mar 14 09:20:23 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 14 09:20:26 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000006kWh (12.79%)
/var/log/syslog.1:Mar 14 09:20:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000006kWh (4.33%)
/var/log/syslog.1:Mar 14 09:20:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000052kWh (15.23%)
/var/log/syslog.1:Mar 14 09:21:08 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000107kWh (14.65%)
/var/log/syslog.1:Mar 14 09:21:56 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.000529kWh (34.99%)
/var/log/syslog.1:Mar 14 09:23:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.001315kWh (42.55%)
/var/log/syslog.1:Mar 14 09:26:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.001952kWh (31.29%)
/var/log/syslog.1:Mar 14 09:33:08 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.005002kWh (39.92%)
/var/log/syslog.1:Mar 14 09:45:56 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.009215kWh (36.72%)
/var/log/syslog.1:Mar 14 10:11:32 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.022295kWh (44.35%)
/var/log/syslog.1:Mar 14 11:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.039942kWh (39.65%)
/var/log/syslog.1:Mar 14 12:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.065838kWh (41.21%)
/var/log/syslog.1:Mar 14 13:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.088125kWh (40.28%)
/var/log/syslog.1:Mar 14 14:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.118835kWh (42.78%)
/var/log/syslog.1:Mar 14 15:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.142807kWh (42.40%)
/var/log/syslog.1:Mar 14 16:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.165418kWh (41.79%)
/var/log/syslog.1:Mar 14 17:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.188150kWh (41.37%)
/var/log/syslog.1:Mar 14 18:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.208836kWh (40.64%)
/var/log/syslog.1:Mar 14 19:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.234687kWh (40.96%)
/var/log/syslog.1:Mar 14 20:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.250418kWh (39.62%)
/var/log/syslog.1:Mar 15 16:28:07 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 15 16:28:10 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.00%)
/var/log/syslog.1:Mar 15 16:28:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000015kWh (10.97%)
/var/log/syslog.1:Mar 15 16:28:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000078kWh (23.53%)
/var/log/syslog.1:Mar 15 16:28:52 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000154kWh (20.84%)
/var/log/syslog.1:Mar 15 16:29:40 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000338kWh (22.17%)
/var/log/syslog.1:Mar 15 16:31:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000630kWh (20.34%)
```

What I want is just the very last part which states that so far have i saved, e.g. 0.000630kWh (20.34%). Does anyone know how to grep only this part? My reason for this is that it would be nice, to be able to keep an eye on this in Conky

Thank you in advance
Jens

---

### Post by srs5694 on 2010-03-15
If you want to view the last few lines of a file or another program's output, you can use the "tail" command. You can issue this directly on a file, as in "tail /var/log/messages"; however, in your case you probably want to use it in a pipeline -- that is, have tail accept another program's output as its input. In your case, it would look like this:

```

sudo grep Estimated\ energy /var/log/* | tail

```

Instead of tail, you could use less to view all the output and page through it. Another option might be to use another grep statement. For instance, you could grep on a specific date:

```

sudo grep Estimated\ energy /var/log/* | grep "Mar 12"

```

---

### Post by SPr on 2010-03-15
sudo grep Estimated\ energy /var/log/*|grep -v TTY|sed  's/.*start:\ //'

There's probably a neater way.

---

### Post by smain on 2010-03-15
hmm using tail I am able to reduce the output to:

```
/var/log/syslog.1:Mar 14 18:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.208836kWh (40.64%)
/var/log/syslog.1:Mar 14 19:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.234687kWh (40.96%)
/var/log/syslog.1:Mar 14 20:02:44 jens-desktop micromiser[1578]: Estimated energy saved since MicroMiser start: 0.250418kWh (39.62%)
/var/log/syslog.1:Mar 15 16:28:07 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.0%)
/var/log/syslog.1:Mar 15 16:28:10 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000000kWh (0.00%)
/var/log/syslog.1:Mar 15 16:28:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000015kWh (10.97%)
/var/log/syslog.1:Mar 15 16:28:28 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000078kWh (23.53%)
/var/log/syslog.1:Mar 15 16:28:52 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000154kWh (20.84%)
/var/log/syslog.1:Mar 15 16:29:40 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000338kWh (22.17%)
/var/log/syslog.1:Mar 15 16:31:16 jens-desktop micromiser[1523]: Estimated energy saved since MicroMiser start: 0.000630kWh (20.34%)
```

Now what I want from this output is the last, and only the last number, so in this case: 0.000630kWh... however since both date and number changes during time, how am I able to get this part?...

The command used was the one you suggested:

```
sudo grep Estimated\ energy /var/log/* | tail
```

---

### Post by rnerwein on 2010-03-15
hi
sudo grep Estimated\ energy /var/log/* | tail [COLOR=Red]-1
[COLOR=Black]ciao[/COLOR]
[/COLOR]

---

### Post by SPr on 2010-03-15
kWh
```

sudo grep Estimated\ energy /var/log/* | tail -1|sed  -e 's/.*start:\ //' -e 's/\ .*//'

```
Percentage
```

sudo grep Estimated\ energy /var/log/* | tail -1|sed  -e 's/.*kWh\ (//' -e 's/).*//'

```

---

### Post by djurny on 2010-03-15
also works with less pipework

```

# kilowatthours
sudo awk '/Estimated energy/ { kwh=NF-1 } END { print $kwh }' /var/log/*
# percentage
sudo awk '/Estimated energy/ { pct=$NF; gsub(/[()]/, "", pct) } END { print pct }' /var/log/*

```

---

### Post by smain on 2010-03-16
Thank you SPr those commands did the trick ^^

Hmm the ones using awk won't work for some reason :S, just gives a fatal error instead o.0...

Anyway, marking this one as solved... Thank you all for the help :D

Jens

(Now if only I was skilled enough with the terminal to understand that last command o.0)

---

### Post by jcbrown on 2010-04-20
> **rnerwein said:**
> hi
sudo grep Estimated\ energy /var/log/* | tail [COLOR=Red]-1
[COLOR=Black]ciao[/COLOR]
[/COLOR][FONT=Calibri][SIZE=3]Micro Miser seems to be a very  good daemon for optimizing battery life. We can check the amount of  kWh it has saved us by issuing the above mentioned command code. The  only problem is that the output looks full to bursting![/SIZE][/FONT]

---

