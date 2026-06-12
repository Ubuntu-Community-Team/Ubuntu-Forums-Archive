---
title: "Other software managers open?..."
date: 2010-01-31
forum: General Help
---

### Post by z0mb1e on 2010-01-31
When I try to download something from the Ubuntu Software Center, it thinks another software manager is open, and as far as I know there isn't. Is there any way to fix this? Using 9.10 x64

Screenshot attached

---

### Post by blueshiftoverwatch on 2010-01-31
Try opening up the terminal and entering **ps -e**. It will list all currently running processes. If another package manager is running, it should be listed there. If you can't find anything that looks like the culprit, post the results here. Maybe I or another forum member can take a look.

---

### Post by z0mb1e on 2010-01-31
It would be nice if I knew what half of it was. I'm new to this..lol

```
PID TTY          TIME CMD
    1 ?        00:00:01 init
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
   23 ?        00:00:00 kintegrityd/0
   24 ?        00:00:00 kintegrityd/1
   25 ?        00:00:00 kintegrityd/2
   26 ?        00:00:00 kintegrityd/3
   27 ?        00:00:00 kblockd/0
   28 ?        00:00:00 kblockd/1
   29 ?        00:00:00 kblockd/2
   30 ?        00:00:00 kblockd/3
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
   33 ?        00:00:00 kacpi_hotplug
   34 ?        00:00:00 ata/0
   35 ?        00:00:00 ata/1
   36 ?        00:00:00 ata/2
   37 ?        00:00:00 ata/3
   38 ?        00:00:00 ata_aux
   39 ?        00:00:00 ksuspend_usbd
   40 ?        00:00:00 khubd
   41 ?        00:00:00 kseriod
   42 ?        00:00:00 kmmcd
   43 ?        00:00:00 bluetooth
   44 ?        00:00:00 khungtaskd
   45 ?        00:00:00 pdflush
   46 ?        00:00:00 pdflush
   47 ?        00:00:00 kswapd0
   48 ?        00:00:00 aio/0
   49 ?        00:00:00 aio/1
   50 ?        00:00:00 aio/2
   51 ?        00:00:00 aio/3
   52 ?        00:00:00 ecryptfs-kthrea
   53 ?        00:00:00 crypto/0
   54 ?        00:00:00 crypto/1
   55 ?        00:00:00 crypto/2
   56 ?        00:00:00 crypto/3
   67 ?        00:00:00 scsi_eh_0
   68 ?        00:00:00 scsi_eh_1
   69 ?        00:00:00 scsi_eh_2
   70 ?        00:00:00 scsi_eh_3
   75 ?        00:00:00 scsi_eh_4
   76 ?        00:00:00 scsi_eh_5
   80 ?        00:00:00 scsi_eh_6
   81 ?        00:00:00 scsi_eh_7
   85 ?        00:00:00 scsi_eh_8
   86 ?        00:00:00 scsi_eh_9
   95 ?        00:00:00 kstriped
   96 ?        00:00:00 kmpathd/0
   97 ?        00:00:00 kmpathd/1
   98 ?        00:00:00 kmpathd/2
   99 ?        00:00:00 kmpathd/3
  100 ?        00:00:00 kmpath_handlerd
  101 ?        00:00:00 ksnapd
  102 ?        00:00:00 kondemand/0
  103 ?        00:00:00 kondemand/1
  104 ?        00:00:00 kondemand/2
  105 ?        00:00:00 kondemand/3
  106 ?        00:00:00 kconservative/0
  107 ?        00:00:00 kconservative/1
  108 ?        00:00:00 kconservative/2
  109 ?        00:00:00 kconservative/3
  110 ?        00:00:00 krfcommd
  345 ?        00:00:00 usbhid_resumer
  426 ?        00:00:00 kjournald2
  483 ?        00:00:00 upstart-udev-br
  485 ?        00:00:00 udevd
  642 ?        00:00:00 udevd
  660 ?        00:00:00 edac-poller
  668 ?        00:00:00 udevd
  707 ?        00:00:00 kpsmoused
  787 ?        00:00:00 hd-audio0
  817 ?        00:00:00 hd-audio1
  858 ?        00:00:00 dd
  859 ?        00:00:00 dbus-daemon
  868 ?        00:00:00 rsyslogd
  870 ?        00:00:00 hald
  871 ?        00:00:00 NetworkManager
  875 ?        00:00:00 avahi-daemon
  876 ?        00:00:00 avahi-daemon
  878 ?        00:00:00 modem-manager
  894 ?        00:00:00 console-kit-dae
  965 ?        00:00:00 hald-runner
  979 ?        00:00:00 wpa_supplicant
  984 ?        00:00:01 phy0
 1053 tty4     00:00:00 getty
 1056 tty5     00:00:00 getty
 1062 tty2     00:00:00 getty
 1064 tty3     00:00:00 getty
 1066 tty6     00:00:00 getty
 1083 ?        00:00:00 acpid
 1120 ?        00:00:00 atd
 1121 ?        00:00:00 cron
 1214 ?        00:00:00 gdm-binary
 1267 ?        00:00:00 gdm-simple-slav
 1268 tty7     00:08:36 Xorg
 1271 ?        00:00:00 firegl
 1272 ?        00:00:00 winbindd
 1275 ?        00:00:00 winbindd
 1290 ?        00:00:00 hald-addon-rfki
 1302 ?        00:00:00 atieventsd
 1317 ?        00:00:00 hald-addon-leds
 1349 ?        00:00:00 hald-addon-stor
 1361 ?        00:00:00 hald-addon-inpu
 1362 ?        00:00:00 cupsd
 1364 ?        00:00:00 hald-addon-cpuf
 1365 ?        00:00:00 hald-addon-acpi
 1566 ?        00:00:00 timidity
 1569 tty1     00:00:00 getty
 1593 ?        00:00:00 gdm-session-wor
 1608 ?        00:00:00 gnome-session
 1652 ?        00:00:00 ssh-agent
 1655 ?        00:00:00 dbus-launch
 1656 ?        00:00:01 dbus-daemon
 1660 ?        00:00:00 pulseaudio
 1692 ?        00:00:00 gconf-helper
 1694 ?        00:00:04 gconfd-2
 1699 ?        00:00:00 devkit-power-da
 1740 ?        00:00:00 gnome-keyring-d
 1743 ?        00:00:02 gnome-settings-
 1758 ?        00:00:00 seahorse-daemon
 1760 ?        00:00:00 gvfsd
 1765 ?        00:00:00 gvfs-fuse-daemo
 1798 ?        00:00:01 notify-osd
 1799 ?        00:00:00 compiz
 1884 ?        00:00:17 compiz.real
 1885 ?        00:00:16 gnome-panel
 1900 ?        00:00:04 nautilus
 1902 ?        00:00:00 bonobo-activati
 1906 ?        00:00:00 polkit-gnome-au
 1907 ?        00:00:01 python
 1909 ?        00:00:00 gnome-power-man
 1912 ?        00:00:00 evolution-alarm
 1914 ?        00:00:00 bluetooth-apple
 1920 ?        00:00:00 trashapplet
 1923 ?        00:00:00 gnome-volume-co
 1924 ?        00:00:01 update-notifier
 1925 ?        00:00:00 gdu-notificatio
 1927 ?        00:00:01 nm-applet
 1930 ?        00:00:00 polkitd
 1944 ?        00:00:00 gnome-screensav
 1946 ?        00:00:00 gvfsd-trash
 1953 ?        00:00:00 devkit-disks-da
 1954 ?        00:00:00 devkit-disks-da
 1958 ?        00:00:00 gvfs-gdu-volume
 1960 ?        00:00:00 gvfs-gphoto2-vo
 1963 ?        00:00:00 sh
 1964 ?        00:00:04 gtk-window-deco
 1973 ?        00:00:01 indicator-apple
 1975 ?        00:00:00 indicator-apple
 2006 ?        00:00:00 indicator-statu
 2009 ?        00:00:00 indicator-users
 2010 ?        00:00:00 indicator-sessi
 2012 ?        00:00:00 gvfsd-burn
 2014 ?        00:00:00 indicator-messa
 2018 ?        00:00:00 gvfsd-metadata
 2027 ?        00:00:00 dhclient
 2250 ?        00:00:01 aptd
 3489 ?        00:00:00 sh
 3490 ?        00:00:00 authatieventsd.
 4348 ?        00:00:00 gvfsd-http
 4390 ?        00:00:39 empathy
 4393 ?        00:00:00 mission-control
 4488 ?        00:00:00 telepathy-haze
 4494 ?        00:00:03 telepathy-butte
 4500 ?        00:00:00 evolution-data-
 4505 ?        00:00:00 evolution-excha
 5035 ?        00:00:12 firefox
 5072 ?        00:00:02 npviewer.bin
 5140 ?        00:00:00 gnome-terminal
 5141 ?        00:00:00 gnome-pty-helpe
 5142 pts/0    00:00:00 bash
 5161 pts/0    00:00:00 ps

```Any idea what it could be?

---

### Post by raktarok on 2010-01-31
Have a look at this thread, I encountered a similar problem a few days ago, and it was quite frustruating...

[http://ubuntuforums.org/showthread.php?t=1391546](http://ubuntuforums.org/showthread.php?t=1391546)

Good luck and if you have any trouble, post here!

---

### Post by z0mb1e on 2010-01-31
I will have to try some of the suggestions tomorrow after school. Will report back with the results.

---

### Post by raktarok on 2010-01-31
Just try this quick in the terminal and see if you have it working.

```
sudo dpkg --configure -a
```

 I don't know why but the thread I linked got longer than was necessary.

---

### Post by z0mb1e on 2010-02-01
Awesome, that worked!

---

