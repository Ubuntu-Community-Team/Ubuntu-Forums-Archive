---
title: "Alsa Issue"
date: 2010-09-10
forum: General Help
---

### Post by linuxguy5 on 2010-09-10
Hi,
I am currently writing a program in Python using BASS. I'm not a Linux guru, and am getting the following error:
```
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
```I am running Ubuntu 10.04, with all the latest updates installed. Can you help me fix it? 
Thank you in advance.

---

### Post by lilmike2 on 2010-09-10
Hi,
A quick google search turns up many posts on this topic, some from this very forum.
May I suggest you try:
[http://ubuntuforums.org/showthread.php?t=601522](http://ubuntuforums.org/showthread.php?t=601522)
If that doesn't help, you may try googling the exact error you received, that's what i did.
Oh yes, and even though this post is from a while back I think it might still be relevant.
Hth,
-Michael.

---

### Post by linuxguy5 on 2010-09-10
Hi,
Thank you. I installed:

libsdl1.2debian-all
and modified my .bashrc to remove all lines containing  SDL_AUDIODRIVER (there weren't any).
I'm not sure what to do from here.
Thanks.

---

### Post by lilmike2 on 2010-09-10
from what i saw it seems like it should just work now.
-Michael.

---

### Post by linuxguy5 on 2010-09-10
Hi Michael,
No, I do not have it working.
Thank you.

---

### Post by sandyd on 2010-09-10
> **linuxguy5 said:**
> Hi,
I am currently writing a program in Python using BASS. I'm not a Linux guru, and am getting the following error:
```
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
```I am running Ubuntu 10.04, with all the latest updates installed. Can you help me fix it? 
Thank you in advance.
what Desktop Environment are you using.
and you got any other programs running?

---

### Post by linuxguy5 on 2010-09-10
Hi,
I'm running GNOME 2.30.2. I just have Firefox and gedit open. Here is my ps -A log:
```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:03 ksoftirqd/1
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
   26 ?        00:00:05 ata/0
   27 ?        00:00:01 ata/1
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
  250 ?        00:00:00 scsi_eh_0
  256 ?        00:00:15 scsi_eh_1
  274 ?        00:00:00 khpsbpkt
  275 ?        00:00:00 scsi_eh_2
  278 ?        00:00:00 scsi_eh_3
  285 ?        00:00:00 scsi_eh_4
  286 ?        00:00:00 scsi_eh_5
  291 ?        00:00:00 scsi_eh_6
  292 ?        00:00:12 usb-storage
  301 ?        00:00:00 knodemgrd_0
  317 ?        00:00:16 mount.ntfs
  324 ?        00:00:05 loop0
  326 ?        00:00:00 jbd2/loop0-8
  327 ?        00:00:00 ext4-dio-unwrit
  328 ?        00:00:00 ext4-dio-unwrit
  365 ?        00:00:00 flush-8:0
  398 ?        00:00:00 upstart-udev-br
  400 ?        00:00:00 udevd
  725 ?        00:00:00 edac-poller
  726 ?        00:00:00 kpsmoused
  737 ?        00:00:00 zd1211rw
  782 ?        00:00:00 hd-audio0
  783 ?        00:00:16 phy0
  841 ?        00:00:00 rsyslogd
  850 ?        00:00:03 dbus-daemon
  860 ?        00:00:00 gdm-binary
  868 ?        00:00:05 NetworkManager
  875 ?        00:00:00 modem-manager
  877 ?        00:00:00 avahi-daemon
  881 ?        00:00:00 console-kit-dae
  883 ?        00:00:00 avahi-daemon
  957 ?        00:00:00 udevd
  958 ?        00:00:00 gdm-simple-slav
 1005 tty4     00:00:00 getty
 1012 tty5     00:00:00 getty
 1017 tty2     00:00:00 getty
 1018 tty3     00:00:00 getty
 1021 tty6     00:00:00 getty
 1022 ?        00:00:00 acpid
 1023 ?        00:00:00 irqbalance
 1028 ?        00:00:00 cron
 1029 ?        00:00:00 atd
 1065 ?        00:00:00 winbindd
 1068 ?        00:00:00 winbindd
 1082 ?        00:00:00 wpa_supplicant
 1095 ?        00:00:00 cupsd
 1096 tty7     00:10:42 Xorg
 1201 tty1     00:00:00 getty
 1221 ?        00:00:00 dbus-launch
 1238 ?        00:00:00 gdm-session-wor
 1242 ?        00:00:00 upowerd
 1248 ?        00:00:00 rtkit-daemon
 1252 ?        00:00:00 polkitd
 1291 ?        00:00:00 hald
 1292 ?        00:00:00 hald-runner
 1324 ?        00:00:02 hald-addon-inpu
 1325 ?        00:00:00 hald-addon-rfki
 1337 ?        00:00:01 hald-addon-stor
 1338 ?        00:00:02 hald-addon-stor
 1339 ?        00:00:02 hald-addon-stor
 1340 ?        00:00:02 hald-addon-stor
 1344 ?        00:00:06 hald-addon-stor
 1345 ?        00:00:00 hald-addon-cpuf
 1346 ?        00:00:00 hald-addon-acpi
 1375 ?        00:00:00 flush-7:0
 1386 ?        00:00:00 gnome-keyring-d
 1404 ?        00:00:00 gnome-session
 1438 ?        00:00:00 ssh-agent
 1441 ?        00:00:00 dbus-launch
 1442 ?        00:00:00 dbus-daemon
 1445 ?        00:00:07 gconfd-2
 1452 ?        00:00:10 gnome-settings-
 1454 ?        00:00:00 gvfsd
 1459 ?        00:00:00 gvfs-fuse-daemo
 1463 ?        00:04:42 compiz
 1466 ?        00:03:40 pulseaudio
 1476 ?        00:00:00 bluetooth-apple
 1478 ?        00:00:28 nautilus
 1482 ?        00:00:18 gnome-panel
 1483 ?        00:00:00 gnome-power-man
 1484 ?        00:00:00 polkit-gnome-au
 1485 ?        00:00:04 nm-applet
 1489 ?        00:00:00 gvfsd-trash
 1491 ?        00:00:00 gconf-helper
 1493 ?        00:00:00 bonobo-activati
 1499 ?        00:00:00 gvfs-gdu-volume
 1502 ?        00:00:00 udisks-daemon
 1503 ?        00:00:00 dhclient
 1505 ?        00:00:19 udisks-daemon
 1506 ?        00:00:00 sh
 1507 ?        00:00:14 gtk-window-deco
 1511 ?        00:00:01 gvfs-afc-volume
 1514 ?        00:00:00 gvfs-gphoto2-vo
 1518 ?        00:01:03 wnck-applet
 1522 ?        00:00:00 trashapplet
 1535 ?        00:00:00 indicator-apple
 1536 ?        00:00:01 clock-applet
 1537 ?        00:00:00 indicator-apple
 1538 ?        00:00:00 notification-ar
 1541 ?        00:00:00 gvfsd-metadata
 1543 ?        00:00:00 indicator-sound
 1549 ?        00:00:00 indicator-messa
 1551 ?        00:00:00 indicator-appli
 1556 ?        00:00:00 indicator-sessi
 1558 ?        00:00:00 indicator-me-se
 1562 ?        00:00:02 gnome-screensav
 1564 ?        00:00:00 gvfsd-burn
 1577 ?        00:00:06 notify-osd
 1627 ?        00:00:00 gdu-notificatio
 1630 ?        00:00:00 python
 1631 ?        00:00:00 evolution-alarm
 1633 ?        00:00:17 gwibber-service
 1635 ?        00:00:51 desktopcouch-se
 1708 ?        00:00:00 couchdb
 1736 ?        00:00:00 couchdb
 1737 ?        00:01:07 beam.smp
 1747 ?        00:00:00 heart
 1750 ?        00:01:07 desktopcouch-se
 1787 ?        00:00:05 couchjs
 1819 ?        00:00:00 update-notifier
 1879 ?        00:00:26 sd_espeak
 1883 ?        00:00:00 sd_dummy
 1885 ?        00:00:00 speech-dispatch
 2538 ?        00:00:00 gvfsd-computer
 3652 ?        00:00:16 gedit
 3831 ?        00:00:00 firefox
 3836 ?        00:00:00 run-mozilla.sh
 3840 ?        00:05:05 firefox-bin
 4059 ?        00:02:40 npviewer.bin
 4241 ?        00:00:01 gnome-terminal
 4246 ?        00:00:00 gnome-pty-helpe
 4247 pts/0    00:00:00 bash
 4417 ?        00:00:00 usbmuxd
 4418 ?        00:00:00 udevd
 4423 ?        00:00:00 gvfsd-afc
 4552 pts/0    00:00:00 ps

```
Thank you.

---

### Post by lilmike2 on 2010-09-10
From what I've seen on most topics that I have read on the matter, firefox causes this problem, or possibly a plugin inside firefox.
Try closing firefox.
-Michael.

---

### Post by sandyd on 2010-09-10
> **linuxguy5 said:**
> Hi,
I'm running GNOME 2.30.2. I just have Firefox and gedit open. Here is my ps -A log:
```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:03 ksoftirqd/1
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
   26 ?        00:00:05 ata/0
   27 ?        00:00:01 ata/1
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
  250 ?        00:00:00 scsi_eh_0
  256 ?        00:00:15 scsi_eh_1
  274 ?        00:00:00 khpsbpkt
  275 ?        00:00:00 scsi_eh_2
  278 ?        00:00:00 scsi_eh_3
  285 ?        00:00:00 scsi_eh_4
  286 ?        00:00:00 scsi_eh_5
  291 ?        00:00:00 scsi_eh_6
  292 ?        00:00:12 usb-storage
  301 ?        00:00:00 knodemgrd_0
  317 ?        00:00:16 mount.ntfs
  324 ?        00:00:05 loop0
  326 ?        00:00:00 jbd2/loop0-8
  327 ?        00:00:00 ext4-dio-unwrit
  328 ?        00:00:00 ext4-dio-unwrit
  365 ?        00:00:00 flush-8:0
  398 ?        00:00:00 upstart-udev-br
  400 ?        00:00:00 udevd
  725 ?        00:00:00 edac-poller
  726 ?        00:00:00 kpsmoused
  737 ?        00:00:00 zd1211rw
  782 ?        00:00:00 hd-audio0
  783 ?        00:00:16 phy0
  841 ?        00:00:00 rsyslogd
  850 ?        00:00:03 dbus-daemon
  860 ?        00:00:00 gdm-binary
  868 ?        00:00:05 NetworkManager
  875 ?        00:00:00 modem-manager
  877 ?        00:00:00 avahi-daemon
  881 ?        00:00:00 console-kit-dae
  883 ?        00:00:00 avahi-daemon
  957 ?        00:00:00 udevd
  958 ?        00:00:00 gdm-simple-slav
 1005 tty4     00:00:00 getty
 1012 tty5     00:00:00 getty
 1017 tty2     00:00:00 getty
 1018 tty3     00:00:00 getty
 1021 tty6     00:00:00 getty
 1022 ?        00:00:00 acpid
 1023 ?        00:00:00 irqbalance
 1028 ?        00:00:00 cron
 1029 ?        00:00:00 atd
 1065 ?        00:00:00 winbindd
 1068 ?        00:00:00 winbindd
 1082 ?        00:00:00 wpa_supplicant
 1095 ?        00:00:00 cupsd
 1096 tty7     00:10:42 Xorg
 1201 tty1     00:00:00 getty
 1221 ?        00:00:00 dbus-launch
 1238 ?        00:00:00 gdm-session-wor
 1242 ?        00:00:00 upowerd
 1248 ?        00:00:00 rtkit-daemon
 1252 ?        00:00:00 polkitd
 1291 ?        00:00:00 hald
 1292 ?        00:00:00 hald-runner
 1324 ?        00:00:02 hald-addon-inpu
 1325 ?        00:00:00 hald-addon-rfki
 1337 ?        00:00:01 hald-addon-stor
 1338 ?        00:00:02 hald-addon-stor
 1339 ?        00:00:02 hald-addon-stor
 1340 ?        00:00:02 hald-addon-stor
 1344 ?        00:00:06 hald-addon-stor
 1345 ?        00:00:00 hald-addon-cpuf
 1346 ?        00:00:00 hald-addon-acpi
 1375 ?        00:00:00 flush-7:0
 1386 ?        00:00:00 gnome-keyring-d
 1404 ?        00:00:00 gnome-session
 1438 ?        00:00:00 ssh-agent
 1441 ?        00:00:00 dbus-launch
 1442 ?        00:00:00 dbus-daemon
 1445 ?        00:00:07 gconfd-2
 1452 ?        00:00:10 gnome-settings-
 1454 ?        00:00:00 gvfsd
 1459 ?        00:00:00 gvfs-fuse-daemo
 1463 ?        00:04:42 compiz
 1466 ?        00:03:40 pulseaudio
 1476 ?        00:00:00 bluetooth-apple
 1478 ?        00:00:28 nautilus
 1482 ?        00:00:18 gnome-panel
 1483 ?        00:00:00 gnome-power-man
 1484 ?        00:00:00 polkit-gnome-au
 1485 ?        00:00:04 nm-applet
 1489 ?        00:00:00 gvfsd-trash
 1491 ?        00:00:00 gconf-helper
 1493 ?        00:00:00 bonobo-activati
 1499 ?        00:00:00 gvfs-gdu-volume
 1502 ?        00:00:00 udisks-daemon
 1503 ?        00:00:00 dhclient
 1505 ?        00:00:19 udisks-daemon
 1506 ?        00:00:00 sh
 1507 ?        00:00:14 gtk-window-deco
 1511 ?        00:00:01 gvfs-afc-volume
 1514 ?        00:00:00 gvfs-gphoto2-vo
 1518 ?        00:01:03 wnck-applet
 1522 ?        00:00:00 trashapplet
 1535 ?        00:00:00 indicator-apple
 1536 ?        00:00:01 clock-applet
 1537 ?        00:00:00 indicator-apple
 1538 ?        00:00:00 notification-ar
 1541 ?        00:00:00 gvfsd-metadata
 1543 ?        00:00:00 indicator-sound
 1549 ?        00:00:00 indicator-messa
 1551 ?        00:00:00 indicator-appli
 1556 ?        00:00:00 indicator-sessi
 1558 ?        00:00:00 indicator-me-se
 1562 ?        00:00:02 gnome-screensav
 1564 ?        00:00:00 gvfsd-burn
 1577 ?        00:00:06 notify-osd
 1627 ?        00:00:00 gdu-notificatio
 1630 ?        00:00:00 python
 1631 ?        00:00:00 evolution-alarm
 1633 ?        00:00:17 gwibber-service
 1635 ?        00:00:51 desktopcouch-se
 1708 ?        00:00:00 couchdb
 1736 ?        00:00:00 couchdb
 1737 ?        00:01:07 beam.smp
 1747 ?        00:00:00 heart
 1750 ?        00:01:07 desktopcouch-se
 1787 ?        00:00:05 couchjs
 1819 ?        00:00:00 update-notifier
 1879 ?        00:00:26 sd_espeak
 1883 ?        00:00:00 sd_dummy
 1885 ?        00:00:00 speech-dispatch
 2538 ?        00:00:00 gvfsd-computer
 3652 ?        00:00:16 gedit
 3831 ?        00:00:00 firefox
 3836 ?        00:00:00 run-mozilla.sh
 3840 ?        00:05:05 firefox-bin
 4059 ?        00:02:40 npviewer.bin
 4241 ?        00:00:01 gnome-terminal
 4246 ?        00:00:00 gnome-pty-helpe
 4247 pts/0    00:00:00 bash
 4417 ?        00:00:00 usbmuxd
 4418 ?        00:00:00 udevd
 4423 ?        00:00:00 gvfsd-afc
 4552 pts/0    00:00:00 ps

```Thank you.
please close firefox, and any other programs (just do a restart) and try again.

There is a issue with flash and other open programs accessing the sound card directly, and as a default, it blocks other programs from using it.

Oh, and another thought. You got pulseaudio installed?
Because if you do, you will have to push the output through pulseaudio, not alsa in order for it to work

---

### Post by linuxguy5 on 2010-09-11
Hi,
Yes, I do have PulseAudio installed. I don't believe there is a way to do this in BASS, but I've posted to their forums, and we'll see if I can make it use PulseAudio rather than ALSA.
Thank you.

---

