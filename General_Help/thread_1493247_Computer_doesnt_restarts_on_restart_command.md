---
title: "Computer doesnt restarts on restart command"
date: 2010-05-25
forum: General Help
---

### Post by p.matulionis@gmail.com on 2010-05-25
Hello,

I'm using Ubuntu 10.04 on DELL inspiron 1545

When I want to restart my computer i doesnt restarts, just stops... The same is with turn off. What could it be?

---

### Post by 98cwitr on 2010-05-25
> **p.matulionis@gmail.com said:**
> Hello,

I'm using Ubuntu 10.04 on DELL inspiron 1545

When I want to restart my computer i doesnt restarts, just stops... The same is with turn off. What could it be?

if you run 

```
sudo shutdown -r now
``` does it restart then?

---

### Post by p.matulionis@gmail.com on 2010-05-26
It is trying to restart but stops on log of screen progress. 

I have no idea what could it be.

---

### Post by 98cwitr on 2010-05-27
please post output of 

```
sudo ps -A
```

---

### Post by p.matulionis@gmail.com on 2010-05-30
This is the post of sudo ps -A:
paulius@paulius-laptop:~$ sudo ps -A

[sudo] password for paulius: 

  PID TTY          TIME CMD

    1 ?        00:00:00 init

    2 ?        00:00:00 kthreadd

    3 ?        00:00:00 migration/0

    4 ?        00:00:00 ksoftirqd/0

    5 ?        00:00:00 watchdog/0

    6 ?        00:00:00 migration/1

    7 ?        00:00:00 ksoftirqd/1

    8 ?        00:00:00 watchdog/1

    9 ?        00:00:00 events/0

   10 ?        00:00:00 events/1

   11 ?        00:00:00 cpuset

   12 ?        00:00:00 khelper

   13 ?        00:00:00 netns

   14 ?        00:00:00 async/mgr

   15 ?        00:00:00 pm

   17 ?        00:00:00 sync_supers

   18 ?        00:00:00 bdi-default

   19 ?        00:00:00 kintegrityd/0

   20 ?        00:00:00 kintegrityd/1

   21 ?        00:00:00 kblockd/0

   22 ?        00:00:00 kblockd/1

   23 ?        00:00:00 kacpid

   24 ?        00:00:00 kacpi_notify

   25 ?        00:00:00 kacpi_hotplug

   26 ?        00:00:00 ata/0

   27 ?        00:00:00 ata/1

   28 ?        00:00:00 ata_aux

   29 ?        00:00:00 ksuspend_usbd

   30 ?        00:00:00 khubd

   31 ?        00:00:00 kseriod

   32 ?        00:00:00 kmmcd

   35 ?        00:00:00 khungtaskd

   36 ?        00:00:00 kswapd0

   37 ?        00:00:00 ksmd

   38 ?        00:00:00 aio/0

   39 ?        00:00:00 aio/1

   40 ?        00:00:00 ecryptfs-kthrea

   41 ?        00:00:00 crypto/0

   42 ?        00:00:00 crypto/1

   56 ?        00:00:00 kstriped

   57 ?        00:00:00 kmpathd/0

   58 ?        00:00:00 kmpathd/1

   59 ?        00:00:00 kmpath_handlerd

   60 ?        00:00:00 ksnapd

   61 ?        00:00:00 kondemand/0

   62 ?        00:00:00 kondemand/1

   63 ?        00:00:00 kconservative/0

   64 ?        00:00:00 kconservative/1

  272 ?        00:00:00 scsi_eh_0

  296 ?        00:00:00 scsi_eh_1

  297 ?        00:00:00 scsi_eh_2

  298 ?        00:00:00 scsi_eh_3

  299 ?        00:00:00 scsi_eh_4

  300 ?        00:00:00 scsi_eh_5

  306 ?        00:00:00 scsi_eh_6

  307 ?        00:00:00 usb-storage

  322 ?        00:00:00 usbhid_resumer

  344 ?        00:00:00 jbd2/sda1-8

  345 ?        00:00:00 ext4-dio-unwrit

  346 ?        00:00:00 ext4-dio-unwrit

  381 ?        00:00:00 flush-8:0

  409 ?        00:00:00 upstart-udev-br

  412 ?        00:00:00 udevd

  693 ?        00:00:00 kpsmoused

  812 ?        00:00:00 radeon/0

  815 ?        00:00:00 radeon/1

  819 ?        00:00:00 ttm_swap

  884 ?        00:00:00 hd-audio0

  947 ?        00:00:00 bluetooth

  955 ?        00:00:00 mysqld

  964 ?        00:00:00 rsyslogd

  968 ?        00:00:00 dbus-daemon

  981 ?        00:00:00 NetworkManager

  982 ?        00:00:00 gdm-binary

  987 ?        00:00:00 modem-manager

  998 ?        00:00:00 avahi-daemon

 1008 ?        00:00:00 avahi-daemon

 1040 ?        00:00:00 wpa_supplicant

 1044 ?        00:00:00 console-kit-dae

 1109 ?        00:00:00 gdm-simple-slav

 1137 tty4     00:00:00 getty

 1141 tty5     00:00:00 getty

 1148 tty2     00:00:00 getty

 1150 tty3     00:00:00 getty

 1153 tty6     00:00:00 getty

 1156 ?        00:00:00 acpid

 1162 tty7     00:08:37 Xorg

 1199 ?        00:00:00 atd

 1200 ?        00:00:00 cron

 1206 ?        00:00:00 cupsd

 1210 ?        00:00:00 krfcommd

 1285 ?        00:07:22 smfpd

 1311 ?        00:00:00 dbus-launch

 1372 tty1     00:00:00 getty

 1379 ?        00:00:00 gdm-session-wor

 1381 ?        00:00:00 upowerd

 1387 ?        00:00:00 rtkit-daemon

 1391 ?        00:00:00 polkitd

 1433 ?        00:00:00 hald

 1434 ?        00:00:00 hald-runner

 1517 ?        00:00:00 hald-addon-inpu

 1520 ?        00:00:00 hald-addon-rfki

 1535 ?        00:00:00 hald-addon-gene

 1537 ?        00:00:00 hald-addon-stor

 1541 ?        00:00:00 hald-addon-stor

 1542 ?        00:00:00 hald-addon-cpuf

 1543 ?        00:00:00 hald-addon-acpi

 1552 ?        00:00:00 gnome-keyring-d

 1570 ?        00:00:00 gnome-session

 1604 ?        00:00:00 ssh-agent

 1607 ?        00:00:00 dbus-launch

 1608 ?        00:00:03 dbus-daemon

 1611 ?        00:00:01 gconfd-2

 1618 ?        00:00:05 gnome-settings-

 1620 ?        00:00:00 gvfsd

 1625 ?        00:00:00 gvfs-fuse-daemo

 1630 ?        00:00:18 avant-window-na

 1632 ?        00:00:00 bluetooth-apple

 1634 ?        00:00:00 gnome-power-man

 1635 ?        00:05:13 pulseaudio

 1636 ?        00:00:00 polkit-gnome-au

 1637 ?        00:00:02 gnome-panel

 1638 ?        00:00:00 nm-applet

 1640 ?        00:00:13 nautilus

 1642 ?        00:00:36 compiz

 1659 ?        00:00:00 gvfsd-trash

 1661 ?        00:00:00 gvfs-gdu-volume

 1663 ?        00:00:00 udisks-daemon

 1664 ?        00:00:00 udisks-daemon

 1667 ?        00:00:00 gvfs-afc-volume

 1670 ?        00:00:00 gvfs-gphoto2-vo

 1672 ?        00:00:00 bonobo-activati

 1684 ?        00:00:00 clock-applet

 1685 ?        00:00:00 indicator-apple

 1688 ?        00:00:00 sh

 1689 ?        00:00:04 indicator-apple

 1690 ?        00:00:00 notification-ar

 1691 ?        00:00:05 gtk-window-deco

 1702 ?        00:00:00 gconf-helper

 1707 ?        00:00:01 syndaemon

 1713 ?        00:00:00 gvfsd-metadata

 1714 ?        00:00:00 indicator-sound

 1717 ?        00:00:00 indicator-appli

 1718 ?        00:00:00 indicator-messa

 1721 ?        00:00:00 indicator-me-se

 1723 ?        00:00:00 indicator-sessi

 1725 ?        00:00:00 gvfsd-burn

 1727 ?        00:00:00 gnome-screensav

 1728 ?        00:00:02 awn-applet

 1730 ?        00:00:15 awn-applet

 1731 ?        00:00:00 dhclient

 1739 ?        00:00:00 gdu-notificatio

 1744 ?        00:00:03 notify-osd

 1789 ?        00:00:03 python

 1790 ?        00:00:00 evolution-alarm

 1798 ?        00:00:00 evolution-data-

 1802 ?        00:00:00 evolution-excha

 1848 ?        00:00:00 udevd

 1849 ?        00:00:00 udevd

 1864 ?        00:00:00 update-notifier

 1869 ?        00:00:00 system-service-

 2979 ?        00:00:00 gvfsd-http

 3479 ?        00:00:14 skype

 3828 ?        00:00:01 gedit

 3831 ?        00:00:00 firefox

 3836 ?        00:00:00 run-mozilla.sh

 3840 ?        00:00:02 firefox-bin

 3857 ?        00:00:00 gnome-terminal

 3858 ?        00:00:00 gnome-pty-helpe

 3859 pts/0    00:00:00 bash

 3876 pts/0    00:00:00 ps

paulius@paulius-laptop:~$

---

