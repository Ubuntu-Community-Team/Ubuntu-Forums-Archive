---
title: "[Ubuntu] Computer hangs on login"
date: 2010-05-16
forum: General Help
---

### Post by Man From Dirt on 2010-05-16
When I login, Ubuntu 10.04 (x86_64) will hang completely, as in only the mouse will move, and the only thing that shows up is the popup asking me for the password to the default keyring. No keyboard input works for X. However, if I drop to a different tty, I can use the shell.

So I thought that maybe it was a recently installed application, and I removed beagle, gnome-do, and conky. No dice. Then I created a new user via the tty and logged in through the main Ubuntu login, and lo-and-behold it works fine, so it has to be something in my other account and its settings.

The other thing I recently did (but AFAIK know should have no effect) is remove Firefox and installed Chrome, then made a shell script, called it firefox, and stuck it is /usr/bin so if any program called Firefox at some point, at least Chrome would open.

---

### Post by Man From Dirt on 2010-05-16
Bump!

---

### Post by Man From Dirt on 2010-05-16
Can you say double bump?

---

### Post by Man From Dirt on 2010-05-16
Four posts in a row, don't I rock ;) Jk, but now to the point,

I've used Meld with both sudo ps -A (as well as just ps -A) on my new account default login with my frozen account. They are nearly identical to each other, save minor differences in the process number between 3 processes.

Any ideas? Here's what runs on a default login for my freezing account:

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
   54 ?        00:00:00 kstriped
   55 ?        00:00:00 kmpathd/0
   56 ?        00:00:00 kmpathd/1
   57 ?        00:00:00 kmpath_handlerd
   58 ?        00:00:00 ksnapd
   59 ?        00:00:00 kondemand/0
   60 ?        00:00:00 kondemand/1
   61 ?        00:00:00 kconservative/0
   62 ?        00:00:00 kconservative/1
  292 ?        00:00:00 scsi_eh_0
  293 ?        00:00:02 scsi_eh_1
  294 ?        00:00:00 scsi_eh_2
  295 ?        00:00:00 scsi_eh_3
  296 ?        00:00:00 scsi_eh_4
  297 ?        00:00:00 scsi_eh_5
  318 ?        00:00:00 usbhid_resumer
  338 ?        00:00:00 jbd2/sda5-8
  339 ?        00:00:00 ext4-dio-unwrit
  340 ?        00:00:00 ext4-dio-unwrit
  373 ?        00:00:00 flush-8:0
  399 ?        00:00:00 upstart-udev-br
  402 ?        00:00:00 udevd
  719 ?        00:00:00 kpsmoused
  722 ?        00:00:00 iwlagn
  723 ?        00:00:02 phy0
  735 ?        00:00:00 kmemstick
  736 ?        00:00:00 bluetooth
  781 ?        00:00:00 hd-audio0
  858 ?        00:00:00 jbd2/sda6-8
  859 ?        00:00:00 ext4-dio-unwrit
  860 ?        00:00:00 ext4-dio-unwrit
  886 ?        00:00:00 rsyslogd
  888 ?        00:00:02 dbus-daemon
  902 ?        00:00:01 NetworkManager
  904 ?        00:00:00 gdm-binary
  911 ?        00:00:00 modem-manager
  912 ?        00:00:00 avahi-daemon
  915 ?        00:00:00 avahi-daemon
  927 ?        00:00:00 udevd
  946 ?        00:00:00 udevd
  954 ?        00:00:00 console-kit-dae
 1046 tty4     00:00:00 getty
 1055 tty5     00:00:00 getty
 1063 tty2     00:00:00 login
 1067 tty3     00:00:00 getty
 1071 tty6     00:00:00 getty
 1073 ?        00:00:00 acpid
 1092 ?        00:00:00 cron
 1093 ?        00:00:00 atd
 1095 ?        00:00:04 icecast2
 1110 ?        00:00:00 wpa_supplicant
 1133 ?        00:00:00 dhclient
 1256 ?        00:00:00 winbindd
 1272 ?        00:00:00 bluetoothd
 1289 ?        00:00:00 krfcommd
 1296 ?        00:00:00 cupsd
 1325 ?        00:00:00 winbindd
 1485 ?        00:00:00 rtkit-daemon
 1492 ?        00:00:00 polkitd
 1500 ?        00:00:00 upowerd
 1564 ?        00:00:00 hald
 1565 ?        00:00:00 hald-runner
 1591 ?        00:00:00 hald-addon-inpu
 1594 ?        00:00:00 udisks-daemon
 1597 ?        00:00:00 udisks-daemon
 1598 ?        00:00:00 hald-addon-rfki
 1599 ?        00:00:00 hald-addon-leds
 1609 ?        00:00:00 hald-addon-gene
 1622 ?        00:00:01 hald-addon-stor
 1623 ?        00:00:00 hald-addon-cpuf
 1624 ?        00:00:00 hald-addon-acpi
 1860 ?        00:00:00 couchdb
 1888 ?        00:00:00 couchdb
 1889 ?        00:00:07 beam.smp
 1899 ?        00:00:00 heart
 1902 ?        00:00:12 desktopcouch-se
 2017 tty2     00:00:01 bash
 2341 ?        00:00:11 desktopcouch-se
 3414 ?        00:00:11 desktopcouch-se
 3504 ?        08:20:38 gnome-panel
 3564 ?        00:00:00 gdm-simple-slav
 3566 tty8     00:08:20 Xorg
 3601 ?        00:00:00 dbus-launch
 3618 ?        00:00:00 gdm-session-wor
 3637 ?        00:00:00 gnome-keyring-d
 3655 ?        00:00:00 gnome-session
 3689 ?        00:00:00 ssh-agent
 3692 ?        00:00:00 dbus-launch
 3693 ?        00:00:00 dbus-daemon
 3696 ?        00:00:00 gconfd-2
 3700 ?        00:00:02 gnome-settings-
 3705 ?        00:00:00 gvfsd
 3709 ?        00:00:01 gnome-power-man
 3713 ?        00:00:02 gnome-panel
 3715 ?        00:00:10 nautilus
 3716 ?        00:00:00 gvfs-fuse-daemo
 3717 ?        00:00:09 pulseaudio
 3719 ?        00:01:54 compiz
 3728 ?        00:00:00 bluetooth-apple
 3729 ?        00:00:00 polkit-gnome-au
 3734 ?        00:00:00 nm-applet
 3749 ?        00:00:00 gvfsd-trash
 3751 ?        00:00:00 bonobo-activati
 3764 ?        00:00:00 gvfs-gdu-volume
 3765 ?        00:00:03 wnck-applet
 3767 ?        00:00:00 trashapplet
 3768 ?        00:00:00 gconf-helper
 3771 ?        00:00:00 gvfs-gphoto2-vo
 3773 ?        00:00:00 gvfs-afc-volume
 3782 ?        00:00:00 clock-applet
 3783 ?        00:00:01 indicator-apple
 3785 ?        00:00:00 indicator-apple
 3786 ?        00:00:00 notification-ar
 3792 ?        00:00:02 syndaemon
 3795 ?        00:00:00 sh
 3796 ?        00:00:01 gtk-window-deco
 3801 ?        00:00:00 gvfsd-metadata
 3802 ?        00:00:00 indicator-me-se
 3804 ?        00:00:00 indicator-sessi
 3807 ?        00:00:00 indicator-messa
 3810 ?        00:00:00 indicator-sound
 3811 ?        00:00:00 indicator-appli
 3813 ?        00:00:00 gvfsd-burn
 3815 ?        00:00:00 gnome-screensav
 3894 ?        00:00:00 gdu-notificatio
 3903 ?        00:00:00 python
 3904 ?        00:00:00 evolution-alarm
 3925 ?        00:00:00 update-notifier
 4041 ?        00:00:00 pulseaudio
 4042 ?        00:00:00 gconf-helper
 5113 ?        00:00:00 dbus-daemon
 5486 ?        00:00:00 dbus-daemon
 5764 ?        00:00:00 dbus-daemon
 5876 ?        00:00:00 gvfsd-http
 6399 ?        00:00:00 dbus-launch
 6400 ?        00:00:00 dbus-daemon
 6480 ?        00:00:00 gnome-terminal
 6481 ?        00:00:00 gnome-pty-helpe
 6482 pts/0    00:00:00 bash
 6502 pts/0    00:00:00 su
 6510 pts/0    00:00:00 bash
 6520 pts/0    00:01:44 java
 8026 ?        00:00:00 gksu
 8027 ?        00:00:05 synaptic
 8393 ?        00:00:00 gcalctool
 8616 ?        00:01:01 chrome
 8619 ?        00:00:02 chrome
 8621 ?        00:00:00 chrome
 8772 ?        00:00:00 chrome
 9342 ?        00:00:01 chrome
 9638 tty1     00:00:00 login
 9672 ?        00:00:02 python
 9769 tty1     00:00:00 bash
 9790 tty1     00:00:00 ps

```

---

