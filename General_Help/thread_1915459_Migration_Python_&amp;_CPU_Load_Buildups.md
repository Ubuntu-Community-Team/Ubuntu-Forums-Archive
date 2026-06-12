---
title: "Migration Python &amp; CPU Load Buildups"
date: 2012-01-26
forum: General Help
---

### Post by Mosome on 2012-01-26
Hello.  I am using Ubuntu 11.10 Oneric Ocelot 64 bit (kernel 3.0.0-15-generic).  This is a quad core machine too.  I have been experiencing some heavy load build ups on the CPUs through the migration background processes for each CPU.

I have had trouble tracking down the issue, as I understand from other threads that migration is simply necessary like kworker I presume.  It handles the background processes on the machine or something.  All I want to know is what is the build up on each migration thread.

Use the Sysmonitor tool in Screenlets, I can determine at startup that all is realitively fine.  But after a day of running, I look and there is one if not all migration threads moving closer to the 100% limit.  Nothing though is telling me what is using it.  The best I can do to determine is used ps -ely, and from the times I can only determine it is python that is possibly eating at it.

I guess that means Sysmonitor is included, though I don't know this for certain.  I also use Cairo Dock, but switched to Ubuntu 2D to see if this clarified anything to no go though.

Bye.

Here is a drop of my ps -ely:

S   UID   PID  PPID  C PRI  NI   RSS    SZ WCHAN  TTY          TIME CMD
S     0     1     0  0  80   0  2256  6042 poll_s ?        00:00:00 init
S     0     2     0  0  80   0     0     0 kthrea ?        00:00:00 kthreadd
S     0     3     2  0  80   0     0     0 run_ks ?        00:00:14 ksoftirqd/0
S     0     6     2 22 -40   -     0     0 cpu_st ?        04:02:37 migration/0
S     0     7     2  0 -40   -     0     0 cpu_st ?        00:00:00 migration/1
S     0     9     2  0  80   0     0     0 run_ks ?        00:00:01 ksoftirqd/1
S     0    11     2  0 -40   -     0     0 cpu_st ?        00:00:00 migration/2
S     0    13     2  0  80   0     0     0 run_ks ?        00:00:00 ksoftirqd/2
S     0    14     2  0 -40   -     0     0 cpu_st ?        00:00:00 migration/3
S     0    16     2  0  80   0     0     0 run_ks ?        00:00:02 ksoftirqd/3
S     0    17     2  0  60 -20     0     0 rescue ?        00:00:00 cpuset
S     0    18     2  0  60 -20     0     0 rescue ?        00:00:00 khelper
S     0    19     2  0  60 -20     0     0 rescue ?        00:00:00 netns
S     0    21     2  0  80   0     0     0 bdi_sy ?        00:00:00 sync_supers
S     0    22     2  0  80   0     0     0 bdi_fo ?        00:00:00 bdi-default
S     0    23     2  0  60 -20     0     0 rescue ?        00:00:00 kintegrityd
S     0    24     2  0  60 -20     0     0 rescue ?        00:00:00 kblockd
S     0    25     2  0  60 -20     0     0 rescue ?        00:00:00 ata_sff
S     0    26     2  0  80   0     0     0 hub_th ?        00:00:00 khubd
S     0    27     2  0  60 -20     0     0 rescue ?        00:00:00 md
S     0    30     2  0  80   0     0     0 watchd ?        00:00:00 khungtaskd
S     0    31     2  0  80   0     0     0 kswapd ?        00:00:00 kswapd0
S     0    32     2  0  85   5     0     0 ksm_sc ?        00:00:00 ksmd
S     0    33     2  0  99  19     0     0 khugep ?        00:00:00 khugepaged
S     0    34     2  0  80   0     0     0 fsnoti ?        00:00:00 fsnotify_mark
S     0    35     2  0  80   0     0     0 ecrypt ?        00:00:00 ecryptfs-kthrea
S     0    36     2  0  60 -20     0     0 rescue ?        00:00:00 crypto
S     0    44     2  0  60 -20     0     0 rescue ?        00:00:00 kthrotld
S     0   200     2  0  80   0     0     0 scsi_e ?        00:00:00 scsi_eh_0
S     0   201     2  0  80   0     0     0 scsi_e ?        00:00:01 scsi_eh_1
S     0   202     2  0  80   0     0     0 scsi_e ?        00:00:00 scsi_eh_2
S     0   203     2  0  80   0     0     0 scsi_e ?        00:00:00 scsi_eh_3
S     0   208     2  0  80   0     0     0 worker ?        00:00:00 kworker/u:2
S     0   209     2  0  80   0     0     0 worker ?        00:00:02 kworker/u:3
S     0   237     2  0  80   0     0     0 kjourn ?        00:00:01 jbd2/sda1-8
S     0   238     2  0  60 -20     0     0 rescue ?        00:00:00 ext4-dio-unwrit
S     0   294     1  0  80   0   632  4274 poll_s ?        00:00:00 upstart-udev-br
S     0   297     1  0  80   0  1640  5449 ep_pol ?        00:00:00 udevd
S     0   496     2  0   9   -     0     0 irq_th ?        00:00:00 irq/16-mei
S     0   535     2  0  60 -20     0     0 rescue ?        00:00:00 cfg80211
S     0   547     2  0  60 -20     0     0 rescue ?        00:00:00 kpsmoused
S     0   555   297  0  80   0  1192  5448 ep_pol ?        00:00:00 udevd
S     0   556   297  0  80   0  1132  5448 ep_pol ?        00:00:00 udevd
S     0   668     1  0  80   0   388  3762 poll_s ?        00:00:00 upstart-socket-
S     0   775     2  0  60 -20     0     0 rescue ?        00:00:00 hd-audio0
S     0   811     1  0  80   0  1316  5700 reques ?        00:00:16 mount.ntfs-3g
S   101   843     1  0  80   0  1736 13277 poll_s ?        00:00:00 rsyslogd
S   103   852     1  0  80   0  2412  6317 poll_s ?        00:00:06 dbus-daemon
S     0   863     1  0  80   0  3168 20205 poll_s ?        00:00:00 modem-manager
S   106   866     1  0  80   0  1780  8064 poll_s ?        00:00:00 avahi-daemon
S   106   867   866  0  80   0   472  8033 unix_s ?        00:00:00 avahi-daemon
S     0   868     1  0  80   0  5148 41116 poll_s ?        00:00:00 NetworkManager
S     0   876     1  0  80   0  4492 34753 poll_s ?        00:00:00 polkitd
S     0   920     1  0  80   0   644  1045 n_tty_ tty4     00:00:00 getty
S     0   926     1  0  80   0   640  1045 n_tty_ tty5     00:00:00 getty
S     0   933     1  0  80   0   640  1045 n_tty_ tty2     00:00:00 getty
S     0   934     1  0  80   0   644  1045 n_tty_ tty3     00:00:00 getty
S     0   936     1  0  80   0   640  1045 n_tty_ tty6     00:00:00 getty
S     0   944     1  0  80   0   800  1082 poll_s ?        00:00:00 acpid
S     0   946     1  0  80   0  4456 47468 poll_s ?        00:00:00 lightdm
S     0   948     1  0  80   0   644  3962 hrtime ?        00:00:08 irqbalance
S     0   955     1  0  80   0  1036  4744 hrtime ?        00:00:00 cron
S     1   956     1  0  80   0   384  4194 hrtime ?        00:00:00 atd
S     0   987     1  0  80   0  1760 16981 poll_s ?        00:00:00 winbindd
S     0  1030   987  0  80   0  1188 16981 poll_s ?        00:00:00 winbindd
S     0  1074     2  0  80   0     0     0 bdi_wr ?        00:00:00 flush-8:0
S     0  1079     1  0  80   0  3620 30842 poll_s ?        00:00:00 accounts-daemon
S     0  1086     1  0  80   0  3924 31852 poll_s ?        00:00:00 console-kit-dae
S     0  1230     1  0  80   0  4376 38397 poll_s ?        00:00:00 upowerd
S   110  1286     1  0  81   1  1360 25800 poll_s ?        00:00:00 rtkit-daemon
S     0  1321   868  0  80   0  1556  1782 poll_s ?        00:00:00 dhclient
S   102  1339     1  0  80   0 11464 89856 poll_s ?        00:00:00 colord
S     0  1362     1  0  80   0   640  1045 n_tty_ tty1     00:00:00 getty
S  1000  1517     1  0  69 -11  7404 75345 poll_s ?        00:03:07 pulseaudio
S  1000  1535  1517  0  80   0  3044 23711 poll_s ?        00:00:00 gconf-helper
S     0  1543     1  0  80   0  3916 32434 poll_s ?        00:00:01 udisks-daemon
S     0  1544  1543  0  80   0   824 11851 poll_s ?        00:00:04 udisks-daemon
S     0  2377   946  1  80   0 25052 40272 poll_s tty7     00:12:43 Xorg
S  1000  2480     1  0  80   0  3632 39445 poll_s ?        00:00:00 gnome-keyring-d
S  1000  2492   946  0  80   0  9848 82576 poll_s ?        00:00:00 gnome-session
S  1000  2528  2492  0  80   0   276  3066 poll_s ?        00:00:00 ssh-agent
S  1000  2531     1  0  80   0   784  6642 poll_s ?        00:00:00 dbus-launch
S  1000  2532     1  0  80   0  3752  6926 poll_s ?        00:00:59 dbus-daemon
S  1000  2534     1  0  80   0  2680 15821 poll_s ?        00:00:00 gvfsd
S  1000  2539     1  0  80   0  2732 19719 futex_ ?        00:00:12 gvfs-fuse-daemo
S  1000  2553  2492  0  80   0 18104 128780 poll_s ?       00:00:06 gnome-settings-
S  1000  2559     1  0  80   0  3644 14944 poll_s ?        00:00:00 gconfd-2
S  1000  2561     1  0  80   0  4668 59360 poll_s ?        00:00:00 gsd-printer
S  1000  2564     1  0  80   0 24168 66089 poll_s ?        00:00:00 gnome-screensav
S  1000  2565  2492  0  80   0 16244 92538 poll_s ?        00:01:02 metacity
S  1000  2567     1  0  80   0  1176  5082 hrtime ?        00:00:19 syndaemon
S  1000  2572     1  0  80   0  2904 33259 poll_s ?        00:00:00 dconf-service
S  1000  2577  2492  0  80   0 32296 139161 poll_s ?       00:00:19 unity-2d-panel
S  1000  2578  2492  0  80   0 57368 179746 poll_s ?       00:00:23 unity-2d-launch
S  1000  2583  2492  0  80   0 13332 85213 poll_s ?        00:00:00 nm-applet
S  1000  2584  2492  0  80   0 25604 123292 poll_s ?       00:00:04 nautilus
S  1000  2585  2492  0  80   0 14992 53488 poll_s ?        00:00:00 polkit-gnome-au
S  1000  2586  2492  0  80   0  8584 62365 poll_s ?        00:00:00 gnome-fallback-
S  1000  2596     1  0  80   0  4100 38552 poll_s ?        00:00:00 gvfs-gdu-volume
S  1000  2606     1  0  80   0 15056 71821 poll_s ?        00:00:02 notify-osd
S  1000  2608     1  0  80   0  2640 18937 poll_s ?        00:00:00 gvfs-afc-volume
S  1000  2611     1  0  80   0  2520 15437 poll_s ?        00:00:00 gvfs-gphoto2-vo
S  1000  2614     1  0  80   0 12240 66336 poll_s ?        00:00:09 bamfdaemon
S  1000  2622     1  0  80   0  3316 16958 poll_s ?        00:00:00 gvfsd-trash
S  1000  2628     1  0  80   0 71816 106978 poll_s ?       00:00:00 python
S  1000  2677     1  0  80   0 28892 97379 poll_s ?        00:00:15 unity-panel-ser
S  1000  2691     1  0  80   0  2832 15827 poll_s ?        00:00:00 gvfsd-burn
S  1000  2721     1  0  80   0  7460 76137 poll_s ?        00:00:00 indicator-datet
S  1000  2723     1  0  80   0  6740 83533 poll_s ?        00:00:00 indicator-sound
S  1000  2725     1  0  80   0  5696 63515 poll_s ?        00:00:01 indicator-sessi
S  1000  2727     1  0  80   0  4976 56531 poll_s ?        00:00:00 indicator-appli
S  1000  2737     1  0  80   0  6568 63547 poll_s ?        00:00:00 indicator-messa
S  1000  2748     1  0  80   0  2676 12316 poll_s ?        00:00:00 geoclue-master
S  1000  2822  2492  0  80   0  3976 35697 poll_s ?        00:00:00 telepathy-indic
S  1000  2824     1  0  80   0  3528 15099 poll_s ?        00:00:00 mission-control
S  1000  2937  2492  0  80   0  8588 45778 poll_s ?        00:00:00 gdu-notificatio
S  1000  3150  2492  0  80   0  5660 55610 poll_s ?        00:00:00 zeitgeist-datah
S  1000  3156     1  0  80   0 20968 51720 poll_s ?        00:00:00 zeitgeist-daemo
S  1000  3157  3156  0  80   0   580  2813 unix_s ?        00:00:00 cat
S  1000  3374     1  0  80   0 14348 64924 poll_s ?        00:00:03 unity-applicati
S  1000  3376     1  0  80   0  4964 44344 poll_s ?        00:00:00 unity-music-dae
S  1000  3378     1  0  80   0  5372 44352 poll_s ?        00:00:00 unity-files-dae
S  1000  3427  2492  0  80   0 23780 63451 poll_s ?        00:00:01 applet.py
S  1000  3454     1  0  80   0  3176 56203 poll_s ?        00:00:00 unity-musicstor
S  1000  4228  2492  0  80   0 12976 69370 poll_s ?        00:00:01 update-notifier
S  1000  5610  2492  0  80   0  3976 39985 poll_s ?        00:00:00 deja-dup-monito
S  1000  8031     1  0  80   0  8988 52534 poll_s ?        00:00:07 gvfsd-http
S  1000  8400     1  0  80   0  2236 11994 poll_s ?        00:00:00 gvfsd-metadata
S     0  9326     2  0  80   0     0     0 worker ?        00:00:00 kworker/3:1
S     0 10978     2  0  80   0     0     0 worker ?        00:00:00 kworker/0:0
S     0 11400     2  0  80   0     0     0 worker ?        00:00:00 kworker/2:0
S  1000 12182     1  0  80   0  8336 38706 poll_s ?        00:00:00 gsd-locate-poin
S     0 12259     2  0  80   0     0     0 worker ?        00:00:01 kworker/2:2
S     0 17661     2  0  80   0     0     0 worker ?        00:00:00 kworker/0:2
S     0 17933     2  0  80   0     0     0 worker ?        00:00:02 kworker/0:1
S     0 19175     2  0  80   0     0     0 worker ?        00:00:00 kworker/2:1
S     0 19996     2  0  80   0     0     0 worker ?        00:00:03 kworker/1:2
S  1000 22084     1  0  80   0 17220 95797 poll_s ?        00:00:00 gnome-terminal
S  1000 22088 22084  0  80   0   828  3664 unix_s ?        00:00:00 gnome-pty-helpe
S  1000 22089 22084  0  80   0  4428  7355 wait   pts/0    00:00:00 bash
R  1000 22373 22089  0  80   0   776  3450 -      pts/0    00:00:00 ps
S     0 26044     2  0  80   0     0     0 worker ?        00:00:06 kworker/3:0
S     0 31249     2  0  80   0     0     0 worker ?        00:00:00 kworker/1:1

---

