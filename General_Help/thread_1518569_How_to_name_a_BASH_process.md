---
title: "How to name a BASH process?"
date: 2010-06-26
forum: General Help
---

### Post by jason50146 on 2010-06-26
I am having a problem identifying a BASH script process that I run at startup.  When I use "ps -e", I see a few BASH and SH processes running, but I don't know if any of these are my script. 
Is there a way to give a BASH script a specific name when run that I could see as the process name.  That would make it easier to identify and kill when needed.

BTW - there is a reason for this, but I didn't want to bore you with the details.

Thanks!

---

### Post by renkinjutsu on 2010-06-26
The name of the process should be the same as the name you saved as your script.

---

### Post by jason50146 on 2010-06-26
> **renkinjutsu said:**
> The name of the process should be the same as the name you saved as your script.

Hmmm.  The script name is "server_sleep.sh", but does not show up with ps -e.  There is a process named "sleep", but the PID changes every time I run ps -e, so I don't know what that is.

Output below...

```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 cpuset
   20 ?        00:00:00 khelper
   21 ?        00:00:00 netns
   22 ?        00:00:00 async/mgr
   23 ?        00:00:00 pm
   25 ?        00:00:00 sync_supers
   26 ?        00:00:00 bdi-default
   27 ?        00:00:00 kintegrityd/0
   28 ?        00:00:00 kintegrityd/1
   29 ?        00:00:00 kintegrityd/2
   30 ?        00:00:00 kintegrityd/3
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kblockd/2
   34 ?        00:00:00 kblockd/3
   35 ?        00:00:00 kacpid
   36 ?        00:00:00 kacpi_notify
   37 ?        00:00:00 kacpi_hotplug
   38 ?        00:00:03 ata/0
   39 ?        00:00:04 ata/1
   40 ?        00:00:01 ata/2
   41 ?        00:00:03 ata/3
   42 ?        00:00:00 ata_aux
   43 ?        00:00:00 ksuspend_usbd
   44 ?        00:00:00 khubd
   45 ?        00:00:00 kseriod
   46 ?        00:00:00 kmmcd
   51 ?        00:00:00 khungtaskd
   52 ?        00:00:00 kswapd0
   53 ?        00:00:00 ksmd
   54 ?        00:00:00 aio/0
   55 ?        00:00:00 aio/1
   56 ?        00:00:00 aio/2
   57 ?        00:00:00 aio/3
   58 ?        00:00:00 ecryptfs-kthrea
   59 ?        00:00:00 crypto/0
   60 ?        00:00:00 crypto/1
   61 ?        00:00:00 crypto/2
   62 ?        00:00:00 crypto/3
   76 ?        00:00:00 kstriped
   77 ?        00:00:00 kmpathd/0
   78 ?        00:00:00 kmpathd/1
   79 ?        00:00:00 kmpathd/2
   80 ?        00:00:00 kmpathd/3
   81 ?        00:00:00 kmpath_handlerd
   82 ?        00:00:00 ksnapd
   83 ?        00:00:00 kondemand/0
   84 ?        00:00:00 kondemand/1
   85 ?        00:00:00 kondemand/2
   86 ?        00:00:00 kondemand/3
   87 ?        00:00:00 kconservative/0
   88 ?        00:00:00 kconservative/1
   89 ?        00:00:00 kconservative/2
   90 ?        00:00:00 kconservative/3
  247 ?        00:00:00 scsi_eh_0
  279 ?        00:00:00 scsi_eh_1
  300 ?        00:00:00 scsi_eh_2
  301 ?        00:00:00 scsi_eh_3
  306 ?        00:00:00 scsi_eh_4
  307 ?        00:00:28 scsi_eh_5
  315 ?        00:00:00 usbhid_resumer
  362 ?        00:00:00 kdmflush
  394 ?        00:00:00 flush-8:48
  395 ?        00:00:01 jbd2/sdd1-8
  396 ?        00:00:00 ext4-dio-unwrit
  397 ?        00:00:00 ext4-dio-unwrit
  398 ?        00:00:00 ext4-dio-unwrit
  399 ?        00:00:00 ext4-dio-unwrit
  440 ?        00:00:00 upstart-udev-br
  445 ?        00:00:00 udevd
  635 ?        00:00:00 udevd
  659 ?        00:00:00 edac-poller
  667 ?        00:00:00 kpsmoused
  881 ?        00:00:00 hd-audio0
  982 ?        00:00:00 jbd2/sdd6-8
  983 ?        00:00:00 ext4-dio-unwrit
  984 ?        00:00:00 ext4-dio-unwrit
  985 ?        00:00:00 ext4-dio-unwrit
  986 ?        00:00:00 ext4-dio-unwrit
 1007 ?        00:00:00 jbd2/sdd3-8
 1008 ?        00:00:00 ext4-dio-unwrit
 1009 ?        00:00:00 ext4-dio-unwrit
 1010 ?        00:00:00 ext4-dio-unwrit
 1011 ?        00:00:00 ext4-dio-unwrit
 1027 ?        00:00:00 jbd2/dm-0-8
 1028 ?        00:00:00 ext4-dio-unwrit
 1029 ?        00:00:00 ext4-dio-unwrit
 1030 ?        00:00:00 ext4-dio-unwrit
 1031 ?        00:00:00 ext4-dio-unwrit
 1046 ?        00:00:00 smbd
 1052 ?        00:00:00 rsyslogd
 1067 ?        00:00:00 dbus-daemon
 1073 ?        00:00:00 gdm-binary
 1078 ?        00:00:00 NetworkManager
 1079 ?        00:00:00 avahi-daemon
 1080 ?        00:00:00 avahi-daemon
 1082 ?        00:00:00 modem-manager
 1088 ?        00:00:00 smbd
 1099 ?        00:00:00 wpa_supplicant
 1144 ?        00:00:00 console-kit-dae
 1212 ?        00:00:00 gdm-simple-slav
 1217 tty4     00:00:00 getty
 1221 tty5     00:00:00 getty
 1229 tty2     00:00:00 getty
 1230 tty3     00:00:00 getty
 1234 tty6     00:00:00 getty
 1241 ?        00:00:00 acpid
 1242 ?        00:00:00 irqbalance
 1270 ?        00:00:00 dnsmasq
 1283 ?        00:00:00 cron
 1284 ?        00:00:00 atd
 1286 tty7     00:05:56 Xorg
 1289 ?        00:00:00 nmbd
 1290 ?        00:00:00 powernapd
 1310 ?        00:00:00 udevd
 1340 ?        00:00:00 cupsd
 1452 tty1     00:00:00 getty
 1455 ?        00:00:00 gdm-session-wor
 1464 ?        00:00:00 gnome-session
 1498 ?        00:00:00 ssh-agent
 1501 ?        00:00:00 dbus-launch
 1502 ?        00:00:00 dbus-daemon
 1505 ?        00:00:03 gconfd-2
 1511 ?        00:00:00 gnome-keyring-d
 1514 ?        00:00:10 gnome-settings-
 1516 ?        00:00:00 gvfsd
 1521 ?        00:00:00 gvfs-fuse-daemo
 1524 ?        00:00:48 compiz
 1529 ?        00:00:04 gnome-panel
 1534 ?        00:00:00 polkit-gnome-au
 1537 ?        00:00:00 gnome-power-man
 1540 ?        00:01:59 nautilus
 1545 ?        00:01:32 wally
 1548 ?        00:00:00 bluetooth-apple
 1551 ?        00:00:01 nm-applet
 1557 ?        00:00:00 polkitd
 1558 ?        00:01:13 conky
 1559 ?        00:00:00 upowerd
 1563 ?        00:00:00 dhclient
 1574 ?        00:00:00 gvfs-gdu-volume
 1576 ?        00:00:02 udisks-daemon
 1577 ?        00:00:01 udisks-daemon
 1579 ?        00:00:00 gvfsd-trash
 1581 ?        00:00:00 bonobo-activati
 1583 ?        00:00:00 sh
 1584 ?        00:00:02 gtk-window-deco
 1592 ?        00:00:00 trashapplet
 1593 ?        00:00:03 wnck-applet
 1599 ?        00:00:00 gvfs-gphoto2-vo
 1601 ?        00:00:01 gvfs-afc-volume
 1613 ?        00:00:00 indicator-apple
 1616 ?        00:00:00 notification-ar
 1629 ?        00:00:05 clock-applet
 1666 ?        00:00:00 hald
 1671 ?        00:00:00 hald-runner
 1676 ?        00:00:00 gvfsd-metadata
 1677 ?        00:00:00 indicator-me-se
 1680 ?        00:00:00 indicator-sessi
 1711 ?        00:00:00 hald-addon-inpu
 1724 ?        00:00:00 hald-addon-cpuf
 1725 ?        00:00:00 hald-addon-acpi
 1735 ?        00:00:00 gvfsd-burn
 1740 ?        00:00:10 hald-addon-stor
 1744 ?        00:00:03 hald-addon-stor
 1754 ?        00:01:48 pulseaudio
 1756 ?        00:00:00 rtkit-daemon
 1765 ?        00:00:00 gconf-helper
 1768 ?        00:00:05 gnome-screensav
 1777 ?        00:00:01 notify-osd
 1846 ?        00:00:00 gdu-notificatio
 1889 ?        00:00:00 python
 1890 ?        00:00:00 evolution-alarm
 1900 ?        00:00:00 evolution-data-
 1904 ?        00:00:00 evolution-excha
 1976 ?        00:00:01 update-notifier
 1987 ?        00:00:00 system-service-
 3000 ?        00:00:00 sh
 3001 ?        00:00:00 sh
 3003 ?        00:00:00 sh <defunct>
 3004 ?        00:00:00 cat
 3005 ?        00:00:00 cat
 3179 pts/1    00:00:01 sh
 3675 pts/2    00:00:00 bash
 7378 ?        00:00:27 smbd
 7379 ?        00:00:00 smbd
17708 pts/1    00:00:00 sh
17709 pts/1    00:00:00 sh
17710 pts/1    00:00:00 wc
17711 pts/1    00:00:00 sh
17712 pts/1    00:00:00 cat
17713 pts/1    00:00:00 cat
17714 pts/1    00:00:00 sleep
17715 pts/2    00:00:00 ps
24774 ?        00:00:00 firefox
24779 ?        00:00:00 run-mozilla.sh
24783 ?        00:03:26 firefox-bin
25249 ?        00:02:38 npviewer.bin
28389 ?        00:00:05 gnome-terminal
28390 ?        00:00:00 gnome-pty-helpe
29494 ?        00:00:00 dbus-launch
29495 ?        00:00:00 dbus-daemon
30316 ?        00:00:00 sh
31404 pts/1    00:00:00 bash

```

---

### Post by jason50146 on 2010-06-26
Using "ps -ef" solved the issue.

```
root     30316     1  0 17:50 ?        00:00:00 sh /home/jason/server_sleep.sh
```

---

