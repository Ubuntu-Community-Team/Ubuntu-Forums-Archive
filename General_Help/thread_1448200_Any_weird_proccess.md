---
title: "Any weird proccess?"
date: 2010-04-06
forum: General Help
---

### Post by Lord DEA on 2010-04-06
Hello everyone
my ubuntu 9.10 has been acting strange lately...
procesor always 100% in use
pulseaudio does nod load correctly and I have to restart it every time.

I think there can be a weird process running in background consuming resources, but since I'm not very familiar with ubuntu's processes, I cannot recognize any...

please help me...
here's the ps -e output:

```

  PID TTY          TIME CMD
    1 ?        00:00:41 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 cpuset
    8 ?        00:00:00 khelper
    9 ?        00:00:00 netns
   10 ?        00:00:00 async/mgr
   11 ?        00:00:00 kintegrityd/0
   12 ?        00:00:00 kblockd/0
   13 ?        00:00:00 kacpid
   14 ?        00:00:00 kacpi_notify
   15 ?        00:00:00 kacpi_hotplug
   16 ?        00:00:00 ata/0
   17 ?        00:00:00 ata_aux
   18 ?        00:00:00 ksuspend_usbd
   19 ?        00:00:00 khubd
   20 ?        00:00:00 kseriod
   21 ?        00:00:00 kmmcd
   22 ?        00:00:00 bluetooth
   23 ?        00:00:00 khungtaskd
   24 ?        00:00:00 pdflush
   25 ?        00:00:00 pdflush
   26 ?        00:00:00 kswapd0
   27 ?        00:00:00 aio/0
   28 ?        00:00:00 ecryptfs-kthrea
   29 ?        00:00:00 crypto/0
   36 ?        00:00:00 scsi_eh_0
   37 ?        00:00:00 scsi_eh_1
   39 ?        00:00:00 kstriped
   40 ?        00:00:00 kmpathd/0
   41 ?        00:00:00 kmpath_handlerd
   42 ?        00:00:00 ksnapd
   43 ?        00:00:00 kondemand/0
   44 ?        00:00:00 kconservative/0
   45 ?        00:00:00 krfcommd
  262 ?        00:00:00 i915/0
  275 ?        00:00:00 scsi_eh_2
  276 ?        00:00:00 usb-storage
  351 ?        00:00:00 kjournald2
  352 ?        00:00:00 ext4-dio-unwrit
  374 ?        00:00:00 usbhid_resumer
  401 ?        00:00:15 mountall
  415 ?        00:00:12 upstart-udev-br
  418 ?        00:00:09 udevd
  422 ?        00:00:37 udevd
  424 ?        00:00:00 udevd
  425 ?        00:00:00 udevd
  426 ?        00:00:00 udevd
  427 ?        00:00:00 udevd
  428 ?        00:00:00 udevd
  429 ?        00:00:00 udevd
  431 ?        00:00:00 udevd
  432 ?        00:00:00 udevd
  443 ?        00:00:00 udevd
  444 ?        00:00:00 udevd
  445 ?        00:00:00 udevd
  446 ?        00:00:00 udevd
  447 ?        00:00:00 udevd
  448 ?        00:00:00 udevd
  449 ?        00:00:00 udevd
  462 ?        00:00:00 udevd
  463 ?        00:00:00 udevd
  464 ?        00:00:00 udevd
  465 ?        00:00:00 udevd
  466 ?        00:00:00 udevd
  467 ?        00:00:00 udevd
  468 ?        00:00:00 udevd
  469 ?        00:00:00 udevd
  470 ?        00:00:00 udevd
  471 ?        00:00:00 udevd
  472 ?        00:00:00 udevd
  473 ?        00:00:00 udevd
  474 ?        00:00:00 udevd
  475 ?        00:00:00 udevd
  476 ?        00:00:00 udevd
  477 ?        00:00:00 udevd
  478 ?        00:00:00 udevd
  479 ?        00:00:00 udevd
  490 ?        00:00:00 udevd
  491 ?        00:00:00 udevd
  492 ?        00:00:00 udevd
  493 ?        00:00:00 udevd
  494 ?        00:00:00 udevd
  495 ?        00:00:00 udevd
  496 ?        00:00:00 udevd
  497 ?        00:00:00 udevd
  498 ?        00:00:00 udevd
  499 ?        00:00:00 udevd
  500 ?        00:00:00 udevd
  501 ?        00:00:00 udevd
  502 ?        00:00:00 udevd
  503 ?        00:00:00 udevd
  504 ?        00:00:00 udevd
  505 ?        00:00:00 udevd
  506 ?        00:00:00 udevd
  507 ?        00:00:00 udevd
  508 ?        00:00:00 udevd
  509 ?        00:00:00 udevd
  510 ?        00:00:00 udevd
  511 ?        00:00:00 udevd
  512 ?        00:00:00 udevd
  526 ?        00:00:00 udevd
  527 ?        00:00:00 udevd
  528 ?        00:00:00 udevd
  529 ?        00:00:00 udevd
  530 ?        00:00:00 udevd
  531 ?        00:00:00 udevd
  532 ?        00:00:00 udevd
  533 ?        00:00:00 udevd
  534 ?        00:00:00 udevd
  535 ?        00:00:00 udevd
  536 ?        00:00:00 udevd
  537 ?        00:00:00 udevd
  538 ?        00:00:00 udevd
  539 ?        00:00:00 udevd
  540 ?        00:00:00 udevd
  541 ?        00:00:00 udevd
  542 ?        00:00:00 udevd
  543 ?        00:00:00 udevd
  544 ?        00:00:00 udevd
  545 ?        00:00:00 udevd
  546 ?        00:00:00 udevd
  547 ?        00:00:00 udevd
  548 ?        00:00:00 udevd
  549 ?        00:00:00 udevd
  550 ?        00:00:00 udevd
  587 ?        00:00:00 udevd
  588 ?        00:00:00 udevd
  589 ?        00:00:00 udevd
  590 ?        00:00:00 udevd
  591 ?        00:00:00 udevd
  592 ?        00:00:00 udevd
  593 ?        00:00:00 udevd
  594 ?        00:00:00 udevd
  595 ?        00:00:00 udevd
  596 ?        00:00:00 udevd
  597 ?        00:00:00 udevd
  598 ?        00:00:00 udevd
  599 ?        00:00:00 udevd
  600 ?        00:00:00 udevd
  601 ?        00:00:00 udevd
  602 ?        00:00:00 udevd
  603 ?        00:00:00 udevd
  604 ?        00:00:00 udevd
  605 ?        00:00:00 udevd
  606 ?        00:00:00 udevd
  607 ?        00:00:00 udevd
  608 ?        00:00:00 udevd
  609 ?        00:00:00 udevd
  610 ?        00:00:00 udevd
  611 ?        00:00:00 udevd
  667 ?        00:00:00 kpsmoused
  722 ?        00:00:06 phy0
  738 ?        00:00:00 hd-audio0
  771 ?        00:01:00 dbus-daemon
  781 ?        00:00:03 hald
  782 ?        00:00:00 NetworkManager
  783 ?        00:00:00 avahi-daemon
  784 ?        00:00:00 gdm-binary
  790 ?        00:00:00 dd
  795 ?        00:00:00 avahi-daemon
  797 ?        00:00:00 console-kit-dae
  861 ?        00:00:00 modem-manager
  862 ?        00:00:04 rsyslogd
  871 ?        00:00:00 hald-runner
  986 ?        00:00:00 wpa_supplicant
 1015 ?        00:00:00 hald-addon-rfki
 1019 tty4     00:00:00 getty
 1021 tty5     00:00:00 getty
 1026 tty2     00:00:00 getty
 1027 tty3     00:00:00 getty
 1029 tty6     00:00:00 getty
 1042 ?        00:00:00 acpid
 1043 ?        00:00:00 atd
 1044 ?        00:00:00 cron
 1075 ?        00:00:00 hald-addon-gene
 1095 ?        00:00:00 mount.ntfs-3g
 1096 ?        00:00:00 hald-addon-acpi
 1121 ?        00:00:00 hald-addon-inpu
 1124 ?        00:00:00 hald-addon-stor
 1140 ?        00:00:00 hald-addon-stor
 1555 ?        00:00:00 winbindd
 1577 ?        00:00:00 winbindd
 1593 ?        00:00:00 cupsd
 1947 tty1     00:00:00 getty
 1978 ?        00:00:00 devkit-power-da
 2248 ?        00:01:09 devkit-disks-da
 2249 ?        00:00:00 devkit-disks-da
 2262 ?        00:00:00 polkitd
 6872 ?        00:00:00 gdm-simple-slav
 6875 tty7     00:00:16 Xorg
 7254 ?        00:00:00 dbus-launch
 9977 ?        00:00:00 gdm-session-wor
10897 ?        00:00:00 system-service-
11089 ?        00:00:00 gnome-keyring-d
11116 ?        00:00:00 gnome-session
11169 ?        00:00:00 ssh-agent
11175 ?        00:00:00 dbus-daemon
11177 ?        00:00:00 dbus-launch
11181 ?        00:00:01 pulseaudio
11249 ?        00:00:00 gconf-helper
11254 ?        00:00:00 gconfd-2
11290 ?        00:00:00 gnome-settings-
11308 ?        00:00:00 seahorse-daemon
11316 ?        00:00:00 gvfsd
11372 ?        00:00:00 notify-osd
11379 ?        00:00:00 metacity
11393 ?        00:00:01 gnome-panel
11417 ?        00:00:00 syndaemon
11457 ?        00:00:00 nautilus
11464 ?        00:00:00 bonobo-activati
11476 ?        00:00:22 update-notifier
11478 ?        00:00:00 nm-applet
11484 ?        00:00:00 bluetooth-apple
11485 ?        00:00:01 gnome-power-man
11486 ?        00:00:00 gnome-volume-co
11490 ?        00:00:00 polkit-gnome-au
11502 ?        00:00:00 evolution-alarm
11507 ?        00:00:18 gdu-notificatio
11508 ?        00:00:00 python
11520 ?        00:00:00 trashapplet
11529 ?        00:00:42 gvfs-gdu-volume
11538 ?        00:00:00 gvfsd-trash
11545 ?        00:00:00 gnome-screensav
11559 ?        00:00:00 gvfs-gphoto2-vo
11659 ?        00:00:00 dhclient
11698 ?        00:00:00 stickynotes_app
11700 ?        00:00:00 indicator-apple
11703 ?        00:00:00 multiload-apple
11807 ?        00:00:00 gvfsd-burn
11854 ?        00:00:00 gvfsd-metadata
11863 ?        00:00:00 indicator-statu
11865 ?        00:00:00 indicator-users
11869 ?        00:00:00 indicator-sessi
18291 ?        00:00:03 chrome
18300 ?        00:00:00 chrome
18305 ?        00:00:00 chrome
18702 ?        00:00:01 chrome
22987 ?        00:00:02 gnome-terminal
23002 ?        00:00:00 gnome-pty-helpe
23004 pts/0    00:00:00 bash
29195 pts/0    00:00:00 ps

```

are all those "udevd" processes really necessary?

thx in advance...

---

### Post by spibou on 2010-04-06
Run```
top
```It will show you which processes occupy most CPU time.

---

### Post by Lord DEA on 2010-04-06
> **spibou said:**
> Run```
top
```It will show you which processes occupy most CPU time.

thx, but running top didn't reveal any suspicious process...

still, I wonder if all those udevd processes are necessary... anyone knows?

---

