---
title: "Softwear Center, Applying Changes Stuck"
date: 2012-07-31
forum: General Help
---

### Post by shaquille110 on 2012-07-31
Hi there.

Basically in Software Center "Searching" appears and underneh it says "applying changes" and it basically doesn't do anything. So i canceled it and now it just says canceling and i can't do anything.

I found on the forum someone with the same issue in the archives and it was fixed by killing the process "Natulias-Drop" (missed spelt i know!)  well no luck its still there.

I have tried restarting but no luck same issue occurs. I can't install anything in Terminal or in Software center. In terminal  i get "Process is being used by another application".

Below are my current system processes

```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 kworker/0:0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 migration/1
   10 ?        00:00:00 ksoftirqd/1
   11 ?        00:00:01 kworker/0:1
   12 ?        00:00:00 watchdog/1
   13 ?        00:00:00 cpuset
   14 ?        00:00:00 khelper
   15 ?        00:00:00 kdevtmpfs
   16 ?        00:00:00 netns
   18 ?        00:00:00 sync_supers
   19 ?        00:00:00 bdi-default
   20 ?        00:00:00 kintegrityd
   21 ?        00:00:00 kblockd
   22 ?        00:00:00 ata_sff
   23 ?        00:00:00 khubd
   24 ?        00:00:00 md
   25 ?        00:00:00 kworker/1:1
   27 ?        00:00:00 khungtaskd
   28 ?        00:00:00 kswapd0
   29 ?        00:00:00 ksmd
   30 ?        00:00:00 khugepaged
   31 ?        00:00:00 fsnotify_mark
   32 ?        00:00:00 ecryptfs-kthrea
   33 ?        00:00:00 crypto
   41 ?        00:00:00 kthrotld
   43 ?        00:00:00 scsi_eh_0
   44 ?        00:00:00 scsi_eh_1
   45 ?        00:00:00 scsi_eh_2
   46 ?        00:00:00 scsi_eh_3
   47 ?        00:00:00 scsi_eh_4
   48 ?        00:00:00 scsi_eh_5
   51 ?        00:00:00 kworker/u:5
   72 ?        00:00:00 devfreq_wq
  280 ?        00:00:00 jbd2/sda1-8
  281 ?        00:00:00 ext4-dio-unwrit
  365 ?        00:00:00 upstart-udev-br
  380 ?        00:00:00 udevd
  438 ?        00:00:00 irq/43-mei
  516 ?        00:00:00 cfg80211
  534 ?        00:00:00 udevd
  535 ?        00:00:00 udevd
  589 ?        00:00:00 scsi_eh_7
  608 ?        00:00:00 kpsmoused
  648 ?        00:00:00 hd-audio0
  694 ?        00:00:00 rsyslogd
  695 ?        00:00:00 rts_pstor
  700 ?        00:00:00 rtsx-polling
  714 ?        00:00:00 dbus-daemon
  759 ?        00:00:00 bluetoothd
  788 ?        00:00:00 krfcommd
  802 ?        00:00:00 modem-manager
  809 ?        00:00:00 avahi-daemon
  810 ?        00:00:00 avahi-daemon
  813 ?        00:00:00 NetworkManager
  816 ?        00:00:00 polkitd
  820 ?        00:00:00 upstart-socket-
  876 ?        00:00:00 cupsd
  915 ?        00:00:00 wpa_supplicant
  929 tty4     00:00:00 getty
  947 ?        00:00:00 vnstatd
  952 tty5     00:00:00 getty
  977 tty2     00:00:00 getty
  982 tty3     00:00:00 getty
  986 tty6     00:00:00 getty
 1011 ?        00:00:00 whoopsie
 1013 ?        00:00:00 acpid
 1015 ?        00:00:00 irqbalance
 1016 ?        00:00:00 lightdm
 1020 ?        00:00:00 cron
 1021 ?        00:00:00 atd
 1025 ?        00:00:00 winbindd
 1062 tty7     00:01:05 Xorg
 1094 ?        00:00:00 winbindd
 1245 ?        00:00:00 accounts-daemon
 1258 tty1     00:00:00 getty
 1275 ?        00:00:00 console-kit-dae
 1342 ?        00:00:00 kdmflush
 1351 ?        00:00:00 kcryptd_io
 1352 ?        00:00:00 kcryptd
 1407 ?        00:00:00 upowerd
 1463 ?        00:00:00 scsi_eh_8
 1464 ?        00:00:00 usb-storage
 1465 ?        00:00:00 scsi_eh_9
 1466 ?        00:00:00 usb-storage
 1560 ?        00:00:00 dhclient
 1572 ?        00:00:00 colord
 1578 ?        00:00:00 lightdm
 1612 ?        00:00:00 rtkit-daemon
 1635 ?        00:00:00 flush-8:0
 1650 ?        00:00:00 dnsmasq
 1785 ?        00:00:00 gnome-keyring-d
 1796 ?        00:00:00 gnome-session
 1831 ?        00:00:00 ssh-agent
 1834 ?        00:00:00 dbus-launch
 1835 ?        00:00:00 dbus-daemon
 1847 ?        00:00:02 gnome-settings-
 1853 ?        00:00:00 gvfsd
 1855 ?        00:00:00 gvfs-fuse-daemo
 1862 ?        00:00:46 compiz
 1865 ?        00:00:00 gconfd-2
 1871 ?        00:00:00 syndaemon
 1876 ?        00:00:00 pulseaudio
 1878 ?        00:00:00 gvfsd-metadata
 1881 ?        00:00:00 polkit-gnome-au
 1882 ?        00:00:00 gnome-fallback-
 1883 ?        00:00:00 gconf-helper
 1887 ?        00:00:00 bluetooth-apple
 1888 ?        00:00:00 nm-applet
 1901 ?        00:00:00 gvfs-gdu-volume
 1903 ?        00:00:00 udisks-daemon
 1904 ?        00:00:00 udisks-daemon
 1910 ?        00:00:00 gvfs-gphoto2-vo
 1912 ?        00:00:00 gvfs-afc-volume
 1926 ?        00:00:00 gvfsd-trash
 1931 ?        00:00:01 bamfdaemon
 1936 ?        00:00:00 gvfsd-burn
 1938 ?        00:00:00 flush-ecryptfs-
 1944 ?        00:00:00 sh
 1945 ?        00:00:00 gtk-window-deco
 1951 ?        00:00:00 unity-panel-ser
 1953 ?        00:00:00 hud-service
 1968 ?        00:00:00 indicator-messa
 1969 ?        00:00:00 indicator-appli
 1978 ?        00:00:00 indicator-sessi
 1980 ?        00:00:00 indicator-datet
 1981 ?        00:00:00 indicator-print
 1983 ?        00:00:00 indicator-sound
 2017 ?        00:00:00 geoclue-master
 2019 ?        00:00:00 ubuntu-geoip-pr
 2029 ?        00:00:00 gdu-notificatio
 2033 ?        00:00:00 telepathy-indic
 2039 ?        00:00:00 mission-control
 2044 ?        00:00:00 goa-daemon
 2049 ?        00:00:00 gnome-screensav
 2050 ?        00:00:00 zeitgeist-datah
 2057 ?        00:00:00 zeitgeist-daemo
 2064 ?        00:00:00 zeitgeist-fts
 2066 ?        00:00:00 cat
 2085 ?        00:00:00 unity-applicati
 2089 ?        00:00:00 unity-lens-vide
 2090 ?        00:00:00 unity-files-dae
 2092 ?        00:00:00 unity-music-dae
 2123 ?        00:00:00 dconf-service
 2128 ?        00:00:00 unity-musicstor
 2156 ?        00:00:53 software-center
 2174 ?        00:00:00 unity-scope-vid
 2194 ?        00:00:00 aptd
 2213 ?        00:00:00 update-notifier
 2238 pts/0    00:00:00 dpkg
 2240 pts/0    00:00:00 update-notifier
 2242 pts/0    00:00:00 package-data-do
 2244 ?        00:01:39 firefox
 2260 ?        00:00:00 at-spi-bus-laun
 2304 ?        00:00:00 deja-dup-monito
 2329 ?        00:00:01 gnome-terminal
 2337 ?        00:00:00 gnome-pty-helpe
 2338 pts/1    00:00:00 bash
 2424 ?        00:00:07 xchat
 2436 ?        00:00:00 kworker/u:0
 2449 ?        00:00:00 kworker/1:2
 2459 ?        00:00:00 kworker/0:3
 2462 ?        00:00:00 kworker/u:1
 2469 ?        00:00:00 kworker/1:0
 2473 ?        00:00:00 kworker/0:2
 2475 pts/1    00:00:00 ps
```

Any ideas on how to fix this?

I'm using Ubuntu 12.04 LTS with last updates ran yesterday night!

---

### Post by shaquille110 on 2012-07-31
Killing software center doesn't help, same issue when i run Software Center again!

---

