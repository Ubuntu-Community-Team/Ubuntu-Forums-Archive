---
title: "Memory problem"
date: 2010-03-28
forum: General Help
---

### Post by whackedspinach on 2010-03-28
I'm running 9.10 and I have noticed that my computer starts to lag after a while.  I have 4 gigs of RAM, and system monitor says I'm using 3.6 gigs of it.  However, no process goes over 80 MiB.

here is the output of free -m:
```
total       used       free     shared    buffers     cached
Mem:          3962       3737        225          0        109        283
-/+ buffers/cache:       3343        618
Swap:         1302       1199        103

```

Could someone please help me find where my memory has disappeared to?

---

### Post by conradin on 2010-03-29
Can you show us the output of ps -ef or the top command? Perhaps you have zombie processes?

---

### Post by whackedspinach on 2010-03-29
Here is the output of ps -ef:
```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Mar01 ?        00:00:00 /sbin/init
root         2     0  0 Mar01 ?        00:00:00 [kthreadd]
root         3     2  0 Mar01 ?        00:00:00 [migration/0]
root         4     2  0 Mar01 ?        00:04:44 [ksoftirqd/0]
root         5     2  0 Mar01 ?        00:00:00 [watchdog/0]
root         6     2  0 Mar01 ?        00:00:00 [migration/1]
root         7     2  0 Mar01 ?        01:23:02 [ksoftirqd/1]
root         8     2  0 Mar01 ?        00:00:00 [watchdog/1]
root         9     2  0 Mar01 ?        00:00:04 [events/0]
root        10     2  0 Mar01 ?        00:04:33 [events/1]
root        11     2  0 Mar01 ?        00:00:00 [cpuset]
root        12     2  0 Mar01 ?        00:00:00 [khelper]
root        13     2  0 Mar01 ?        00:00:00 [netns]
root        14     2  0 Mar01 ?        00:00:00 [async/mgr]
root        15     2  0 Mar01 ?        00:00:00 [kintegrityd/0]
root        16     2  0 Mar01 ?        00:00:00 [kintegrityd/1]
root        17     2  0 Mar01 ?        00:00:12 [kblockd/0]
root        18     2  0 Mar01 ?        00:10:08 [kblockd/1]
root        19     2  0 Mar01 ?        00:00:00 [kacpid]
root        20     2  0 Mar01 ?        00:00:00 [kacpi_notify]
root        21     2  0 Mar01 ?        00:00:00 [kacpi_hotplug]
root        22     2  0 Mar01 ?        00:02:08 [ata/0]
root        23     2  0 Mar01 ?        00:01:40 [ata/1]
root        24     2  0 Mar01 ?        00:00:00 [ata_aux]
root        25     2  0 Mar01 ?        00:00:00 [ksuspend_usbd]
root        26     2  0 Mar01 ?        00:00:01 [khubd]
root        27     2  0 Mar01 ?        00:00:00 [kseriod]
root        28     2  0 Mar01 ?        00:00:00 [kmmcd]
root        29     2  0 Mar01 ?        00:00:00 [bluetooth]
root        30     2  0 Mar01 ?        00:00:14 [khungtaskd]
root        33     2  0 Mar01 ?        02:03:38 [kswapd0]
root        34     2  0 Mar01 ?        00:00:00 [aio/0]
root        35     2  0 Mar01 ?        00:00:00 [aio/1]
root        36     2  0 Mar01 ?        00:00:00 [ecryptfs-kthrea]
root        37     2  0 Mar01 ?        00:00:00 [crypto/0]
root        38     2  0 Mar01 ?        00:00:00 [crypto/1]
root        48     2  0 Mar01 ?        00:00:00 [scsi_eh_0]
root        49     2  0 Mar01 ?        00:00:00 [scsi_eh_1]
root        52     2  0 Mar01 ?        00:07:35 [scsi_eh_2]
root        53     2  0 Mar01 ?        00:00:00 [scsi_eh_3]
root        57     2  0 Mar01 ?        00:00:00 [scsi_eh_4]
root        58     2  0 Mar01 ?        00:00:00 [scsi_eh_5]
root        69     2  0 Mar01 ?        00:00:00 [kstriped]
root        70     2  0 Mar01 ?        00:00:00 [kmpathd/0]
root        71     2  0 Mar01 ?        00:00:00 [kmpathd/1]
root        72     2  0 Mar01 ?        00:00:00 [kmpath_handlerd]
root        73     2  0 Mar01 ?        00:00:00 [ksnapd]
root        74     2  0 Mar01 ?        00:00:00 [kondemand/0]
root        75     2  0 Mar01 ?        00:00:00 [kondemand/1]
root        76     2  0 Mar01 ?        00:00:00 [kconservative/0]
root        77     2  0 Mar01 ?        00:00:00 [kconservative/1]
root        78     2  0 Mar01 ?        00:00:00 [krfcommd]
root       269     2  0 Mar01 ?        00:00:00 [khpsbpkt]
root       305     2  0 Mar01 ?        00:00:00 [usbhid_resumer]
cole       317 32707  0 22:46 ?        00:00:00 /opt/google/chrome/chrome --type
cole       321 32707  0 22:46 ?        00:00:02 /opt/google/chrome/chrome --type
cole       325 32707  0 22:46 ?        00:00:00 /opt/google/chrome/chrome --type
root       355     2  0 Mar01 ?        00:00:00 [knodemgrd_0]
cole       370 32707  0 22:46 ?        00:00:03 /opt/google/chrome/chrome --type
root       435     2  0 Mar01 ?        00:00:15 [kjournald2]
root       499     1  0 Mar01 ?        00:00:00 upstart-udev-bridge --daemon
root       516     1  0 Mar01 ?        00:00:00 udevd --daemon
cole       612 32707  0 22:54 ?        00:00:02 /opt/google/chrome/chrome --type
cole       709 32707  0 22:56 ?        00:00:00 /opt/google/chrome/chrome --type
root       746     2  0 Mar01 ?        00:00:00 [kpsmoused]
root       767     2  0 Mar01 ?        00:00:52 [kjournald2]
cole       819     1  1 Mar25 ?        00:44:59 /usr/bin/wineserver
cole       823     1  0 Mar25 ?        00:00:00 C:\windows\system32\services.exe
cole       835     1  0 Mar25 ?        00:00:44 C:\windows\explorer.exe /desktop
root       846     1  0 Mar01 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/ru
cole       857 32707  1 23:06 ?        00:00:04 /opt/google/chrome/chrome --type
root       860     2  0 Mar01 ?        00:00:00 [hd-audio0]
syslog     862     1  0 Mar01 ?        00:00:16 rsyslogd -c4
cole       899     1  0 Mar25 ?        00:02:07 C:\Program Files\World of Warcra
root       902     1  0 Mar01 ?        04:32:31 /sbin/mount.ntfs /dev/sda1 /home
102        910     1  0 Mar01 ?        00:00:13 dbus-daemon --system --fork
cole       926 31862  0 23:10 pts/4    00:00:00 ps -ef
avahi      927     1  0 Mar01 ?        00:00:03 avahi-daemon: running [slovakia.
avahi      928   927  0 Mar01 ?        00:00:00 avahi-daemon: chroot helper
107        931     1  0 Mar01 ?        00:00:04 hald --daemon=yes
root       935     1  0 Mar01 ?        00:00:00 /usr/sbin/console-kit-daemon
root      1006   931  0 Mar01 ?        00:00:00 hald-runner
root      1008     1  0 Mar01 ?        00:00:00 NetworkManager
root      1010     1  0 Mar01 ?        00:00:00 /usr/sbin/modem-manager
root      1024     1  0 Mar01 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      1140  1006  0 Mar01 ?        00:01:55 hald-addon-input: Listening on /
root      1148  1006  0 Mar01 ?        00:04:12 hald-addon-storage: polling /dev
107       1158  1006  0 Mar01 ?        00:00:00 hald-addon-acpi: listening on ac
root      1195     1  0 Mar01 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1198     1  0 Mar01 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1210     1  0 Mar01 tty2     00:00:00 /bin/login --     
root      1211     1  0 Mar01 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1213     1  0 Mar01 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1215     1  0 Mar01 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root      1224     1  0 Mar01 ?        00:00:02 cron
daemon    1225     1  0 Mar01 ?        00:00:00 atd
cole      1403 17457  0 Mar25 tty1     00:10:03 top
root      1717     1  0 Mar01 tty1     00:00:00 /bin/login --     
root      1749     1  0 Mar01 ?        00:00:02 gdm-binary
root      1757  1749  0 Mar01 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root      1758  1757  1 Mar01 tty7     10:10:01 /usr/bin/X :0 -br -verbose -auth
root      1800  1757  0 Mar01 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
cole      1815  1800  0 Mar01 ?        00:00:02 gnome-session
cole      1856  1815  0 Mar01 ?        00:00:10 /usr/bin/ssh-agent /usr/bin/dbus
cole      1859     1  0 Mar01 ?        00:00:00 /usr/bin/dbus-launch --exit-with
cole      1862     1  0 Mar01 ?        00:03:46 /bin/dbus-daemon --fork --print-
cole      1866     1  0 Mar01 ?        02:04:20 /usr/bin/pulseaudio --start
cole      1871  1866  0 Mar01 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
cole      1873     1  0 Mar01 ?        00:00:21 /usr/lib/libgconf2-4/gconfd-2
root      1878     1  0 Mar01 ?        00:00:00 /usr/lib/devicekit-power/devkit-
cole      1912     1  0 Mar01 ?        00:02:48 /usr/lib/gnome-settings-daemon/g
cole      1916     1  0 Mar01 ?        00:00:01 gnome-keyring-daemon --start
cole      1920     1  0 Mar01 ?        00:00:01 seahorse-daemon
cole      1922     1  0 Mar01 ?        00:00:01 /usr/lib/gvfs/gvfsd
cole      1930     1  0 Mar01 ?        00:00:01 /usr/lib/gvfs//gvfs-fuse-daemon
cole      1945  1815  0 Mar01 ?        00:00:00 /bin/sh /usr/bin/compiz
cole      1950     1  0 Mar01 ?        00:03:39 syndaemon -i 0.5 -k
cole      2010  1945  0 Mar01 ?        03:26:03 /usr/bin/compiz.real --ignore-de
cole      2011  1815  0 Mar01 ?        00:14:58 gnome-panel
cole      2012  1815  0 Mar01 ?        00:08:18 nautilus
cole      2014     1  0 Mar01 ?        00:00:00 /usr/lib/bonobo-activation/bonob
cole      2018  2010  0 Mar01 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
cole      2019  2018  0 Mar01 ?        00:02:20 /usr/bin/gtk-window-decorator
cole      2021  1815  0 Mar01 ?        00:00:01 /usr/lib/evolution/2.28/evolutio
cole      2023  1815  0 Mar01 ?        00:00:03 /usr/lib/gnome-disk-utility/gdu-
cole      2024  1815  0 Mar01 ?        00:00:32 update-notifier --startup-delay=
cole      2028     1  0 Mar16 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
cole      2030  1815  0 Mar01 ?        00:00:07 nm-applet --sm-disable
cole      2038  1815  0 Mar01 ?        00:00:01 bluetooth-applet
cole      2042  1815  0 Mar01 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
cole      2043  1815  0 Mar01 ?        00:00:28 gnome-volume-control-applet
cole      2047  1815  0 Mar01 ?        00:00:11 gnome-power-manager
cole      2048     1  0 Mar01 ?        00:01:02 gnome-screensaver
root      2050     1  0 Mar01 ?        00:00:00 /usr/lib/policykit-1/polkitd
cole      2053     1  0 Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
cole      2057     1  0 Mar01 ?        00:00:01 /usr/lib/gnome-applets/trashappl
cole      2059     1  0 Mar01 ?        00:00:05 /usr/lib/gvfs/gvfs-gdu-volume-mo
cole      2064     1  0 Mar01 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
cole      2074     1  0 Mar01 ?        00:00:04 /usr/lib/indicator-applet/indica
cole      2083     1  0 Mar01 ?        00:00:45 /usr/lib/indicator-messages/indi
cole      2085     1  0 Mar01 ?        00:00:01 /usr/lib/indicator-session/indic
cole      2087     1  0 Mar01 ?        00:00:00 /usr/lib/indicator-session/indic
cole      2089     1  0 Mar01 ?        00:00:00 /usr/lib/indicator-session/indic
cole      2095     1  0 Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
cole      2162     1  0 Mar01 ?        00:00:00 /bin/sh -e /usr/bin/couchdb -n -
cole      2189  2162  0 Mar01 ?        00:00:00 /bin/sh -e /usr/bin/couchdb -n -
cole      2190  2189  0 Mar01 ?        00:52:18 /usr/lib/erlang/erts-5.7.2/bin/b
cole      2199  2190  0 Mar01 ?        00:00:03 heart -pid 2190 -ht 11
cole      2204  2190  0 Mar01 ?        00:00:00 /usr/lib/couchdb/bin/couchjs /us
cole      2229     1  0 Mar01 ?        00:48:30 /usr/bin/python /usr/lib/ubuntuo
cole      2245     1  0 Mar01 ?        00:00:00 /usr/lib/evolution/2.28/evolutio
cole      2249     1  0 Mar01 ?        00:00:00 /usr/lib/evolution/evolution-dat
cole      2265     1  0 Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
root      2315     1  0 Mar01 ?        00:00:00 /usr/sbin/system-tools-backends
root      2317     1  0 Mar01 ?        00:00:00 /usr/bin/perl /usr/share/system-
cole      3580     1  0 Mar01 ?        00:01:24 /usr/lib/gvfs/gvfsd-http --spawn
cole      3992  2010  0 Mar26 ?        00:00:00 /bin/sh -c gnome-terminal
cole      3993  3992  0 Mar26 ?        00:03:39 gnome-terminal
cole      3994  3993  0 Mar26 ?        00:00:00 gnome-pty-helper
cole      3995  3993  0 Mar26 pts/1    00:00:00 bash
cole      4126     1  3 Mar26 pts/1    02:28:01 uTorrent.exe /NOINSTALL /BRINGTO
cole      4967     1  0 Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --s
guest     5506     1  0 Mar05 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
guest     5521 16605  0 Mar05 ?        00:00:00 gnome-session
guest     5563  5521  0 Mar05 ?        00:00:11 /usr/bin/ssh-agent /usr/bin/dbus
guest     5566     1  0 Mar05 ?        00:00:00 /usr/bin/dbus-launch --exit-with
guest     5567     1  0 Mar05 ?        00:00:00 /bin/dbus-daemon --fork --print-
guest     5571     1  0 Mar05 ?        00:00:02 /usr/bin/pulseaudio --start
guest     5576  5571  0 Mar05 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
guest     5578     1  0 Mar05 ?        00:00:05 /usr/lib/libgconf2-4/gconfd-2
guest     5583     1  0 Mar05 ?        00:01:11 /usr/lib/gnome-settings-daemon/g
guest     5590     1  0 Mar05 ?        00:00:00 seahorse-daemon
guest     5595     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd
guest     5600     1  0 Mar05 ?        00:00:00 /usr/lib/notify-osd/notify-osd
guest     5604     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
guest     5608  5521  0 Mar05 ?        00:00:00 /bin/sh /usr/bin/compiz
guest     5621     1  0 Mar05 ?        00:03:13 syndaemon -i 0.5 -k
guest     5682  5608  0 Mar05 ?        00:00:44 /usr/bin/compiz.real --ignore-de
guest     5683  5521  0 Mar05 ?        00:00:21 gnome-panel
guest     5684  5521  0 Mar05 ?        00:00:01 nautilus
guest     5687     1  0 Mar05 ?        00:00:00 /usr/lib/bonobo-activation/bonob
guest     5689  5521  0 Mar05 ?        00:00:00 /usr/lib/evolution/2.28/evolutio
guest     5691  5521  0 Mar05 ?        00:00:02 /usr/lib/gnome-disk-utility/gdu-
guest     5692  5521  0 Mar05 ?        00:00:31 update-notifier --startup-delay=
guest     5701  5521  0 Mar05 ?        00:00:00 bluetooth-applet
guest     5703  5521  0 Mar05 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
guest     5704  5521  0 Mar05 ?        00:00:00 gnome-volume-control-applet
guest     5708  5521  0 Mar05 ?        00:00:05 gnome-power-manager
guest     5711     1  0 Mar05 ?        00:00:24 gnome-screensaver
guest     5712  5682  0 Mar05 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
guest     5713  5712  0 Mar05 ?        00:00:14 /usr/bin/gtk-window-decorator
guest     5716     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
guest     5720     1  0 Mar05 ?        00:00:00 /usr/lib/gnome-applets/trashappl
guest     5722     1  0 Mar05 ?        00:00:03 /usr/lib/gvfs/gvfs-gdu-volume-mo
guest     5725     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
guest     5730     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-applet/indica
guest     5732     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-applet/indica
guest     5736     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-session/indic
guest     5738     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-session/indic
guest     5740     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-session/indic
guest     5742     1  0 Mar05 ?        00:00:00 /usr/lib/indicator-messages/indi
guest     5749     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
guest     5751     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
guest     5781     1  0 Mar05 ?        00:00:00 /usr/lib/evolution/2.28/evolutio
guest     5785     1  0 Mar05 ?        00:00:00 /usr/lib/evolution/evolution-dat
cole      6054     1  0 Mar21 ?        00:00:24 /usr/lib/notify-osd/notify-osd
cole      6436     1  0 Mar19 ?        00:00:00 /usr/lib/gvfs/gvfsd-network --sp
cole      6447     1  0 Mar19 ?        00:00:00 /usr/lib/gvfs/gvfsd-dnssd --spaw
cole      6508  1210  0 Mar23 tty2     00:00:00 -bash
root      7209  1749  0 Mar05 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root      7212  7209  0 Mar05 tty9     00:00:09 /usr/bin/X :3 -br -verbose -auth
gdm       7260     1  0 Mar05 ?        00:00:00 /bin/dbus-daemon --fork --print-
gdm       7261     1  0 Mar05 ?        00:00:00 /usr/bin/dbus-launch --exit-with
gdm       7262  7209  0 Mar05 ?        00:00:00 /usr/bin/gnome-session --autosta
gdm       7265     1  0 Mar05 ?        00:00:04 /usr/lib/libgconf2-4/gconfd-2
gdm       7267     1  0 Mar05 ?        00:00:23 /usr/lib/gnome-settings-daemon/g
gdm       7272     1  0 Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd
gdm       7274     1  0 Mar05 ?        00:00:00 /usr/lib/notify-osd/notify-osd
gdm       7275  7262  0 Mar05 ?        00:00:01 metacity
gdm       7277  7262  0 Mar05 ?        00:00:08 gnome-power-manager
gdm       7278  7262  0 Mar05 ?        00:00:30 /usr/lib/gdm/gdm-simple-greeter
gdm       7282     1  0 Mar05 ?        00:00:01 /usr/bin/pulseaudio --start --lo
gdm       7294  7282  0 Mar05 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
root      7312  7209  0 Mar05 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
cole      8619  2190  0 Mar21 ?        00:01:07 /usr/lib/erlang/lib/ssl-3.10.3/p
cole      8620  2190  0 Mar21 ?        00:00:00 inet_gethost 4
cole      8621  8620  0 Mar21 ?        00:00:01 inet_gethost 4
cole      8831     1  0 Mar26 ?        00:04:07 rhythmbox
root      9963 22232  0 Mar26 ?        00:00:00 /usr/sbin/winbindd
root      9964 22232  0 Mar26 ?        00:00:00 /usr/sbin/winbindd
root     11215     1  0 Mar04 ?        00:40:22 /usr/sbin/g15daemon
cole     11519     1  0 Mar04 ?        00:00:00 g15composer
root     13557     1  0 Mar04 ?        00:00:00 /usr/bin/python /usr/lib/system-
guest    13730     1  0 Mar02 ?        00:00:00 /usr/lib/evolution/evolution-dat
root     16500  1749  0 Mar02 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root     16503 16500  0 Mar02 tty10    00:08:57 /usr/bin/X :2 -br -verbose -auth
gdm      16554     1  0 Mar02 ?        00:00:00 /usr/bin/dbus-launch --exit-with
root     16605 16500  0 Mar02 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
cole     17457  1717  0 Mar06 tty1     00:00:00 -bash
cole     19193     1  0 Mar20 ?        00:07:07 /usr/bin/python /usr/lib/desktop
root     19436     2  0 Mar04 ?        00:00:00 [xfs_mru_cache]
root     19440     2  0 Mar04 ?        00:00:00 [xfslogd/0]
root     19441     2  0 Mar04 ?        00:00:00 [xfslogd/1]
root     19443     2  0 Mar04 ?        00:00:00 [xfsdatad/0]
root     19444     2  0 Mar04 ?        00:00:00 [xfsdatad/1]
root     19445     2  0 Mar04 ?        00:00:00 [xfsconvertd/0]
root     19446     2  0 Mar04 ?        00:00:00 [xfsconvertd/1]
root     19449     2  0 Mar04 ?        00:00:00 [jfsIO]
root     19450     2  0 Mar04 ?        00:00:00 [jfsCommit]
root     19451     2  0 Mar04 ?        00:00:00 [jfsCommit]
root     19452     2  0 Mar04 ?        00:00:00 [jfsSync]
root     20417   516  0 Mar25 ?        00:00:00 udevd --daemon
root     20813     1  0 Mar04 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root     21210     2  0 Mar25 ?        00:00:04 [pdflush]
root     22179     1  0 Mar25 ?        00:00:02 /usr/sbin/nmbd -D
root     22184     1  0 Mar25 ?        00:00:00 /usr/sbin/smbd -D
root     22187 22184  0 Mar25 ?        00:00:00 /usr/sbin/smbd -D
root     22232     1  0 Mar25 ?        00:00:00 /usr/sbin/winbindd
root     22234 22232  0 Mar25 ?        00:00:00 /usr/sbin/winbindd
cole     22359     1  0 Mar02 ?        00:01:09 mono /usr/lib/tomboy/Tomboy.exe
cole     24656     1  0 Mar25 ?        00:00:02 /usr/lib/telepathy/telepathy-haz
cole     24658     1  0 Mar25 ?        00:00:04 /usr/lib/telepathy/telepathy-gab
root     24724  1008  0 Mar25 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/N
cole     25889     1  0 18:57 ?        00:00:50 filezilla
cole     26756     1  0 Mar02 ?        00:00:09 /usr/lib/telepathy/mission-contr
cole     26860     1  0 Mar02 ?        00:00:01 /usr/lib/telepathy/telepathy-idl
cole     27416     1  0 19:24 ?        00:00:00 /usr/lib/gvfs/gvfsd-gphoto2 --sp
cole     28033     1  0 19:55 ?        00:01:15 /usr/lib/openoffice/program/soff
root     28217     1  0 Mar25 ?        00:00:27 /usr/lib/devicekit-disks/devkit-
root     28218 28217  0 Mar25 ?        00:00:07 devkit-disks-daemon: polling /de
root     28246     2  0 19:59 ?        00:00:00 [pdflush]
root     28898 22184  0 20:53 ?        00:00:00 /usr/sbin/smbd -D
cole     29380     1  0 21:29 ?        00:00:48 mangler
cole     31862  3993  0 22:21 pts/4    00:00:00 bash
root     31941     1  0 Mar03 ?        00:00:00 dbus-launch --autolaunch 3245f39
root     31942     1  0 Mar03 ?        00:00:00 /bin/dbus-daemon --fork --print-
cole     32317     1  0 22:40 ?        00:00:01 /usr/bin/empathy
cole     32702     1  3 22:46 ?        00:00:49 /opt/google/chrome/google-chrome
cole     32705 32702  0 22:46 ?        00:00:00 /opt/google/chrome/google-chrome
cole     32707     1  0 22:46 ?        00:00:00 /opt/google/chrome/chrome --type
cole     32741 32707  0 22:46 ?        00:00:04 /opt/google/chrome/chrome --type
```

---

### Post by conradin on 2010-03-29
sorry, i meant ps -efl (The long listing has memory usage included and the S column will show zombie processes with a Z)

---

### Post by whackedspinach on 2010-03-29
Output of ps -efl:
```
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root         1     0  0  80   0 -  4864 poll_s Mar01 ?        00:00:00 /sbin/init
1 S root         2     0  0  75  -5 -     0 kthrea Mar01 ?        00:00:00 [kthreadd]
1 S root         3     2  0 -40   - -     0 migrat Mar01 ?        00:00:00 [migration/0]
1 S root         4     2  0  75  -5 -     0 ksofti Mar01 ?        00:04:44 [ksoftirqd/0]
5 S root         5     2  0 -40   - -     0 watchd Mar01 ?        00:00:00 [watchdog/0]
1 S root         6     2  0 -40   - -     0 migrat Mar01 ?        00:00:00 [migration/1]
1 S root         7     2  0  75  -5 -     0 ksofti Mar01 ?        01:23:05 [ksoftirqd/1]
5 S root         8     2  0 -40   - -     0 watchd Mar01 ?        00:00:00 [watchdog/1]
1 S root         9     2  0  75  -5 -     0 worker Mar01 ?        00:00:04 [events/0]
1 S root        10     2  0  75  -5 -     0 worker Mar01 ?        00:04:33 [events/1]
1 S root        11     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [cpuset]
1 S root        12     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [khelper]
1 S root        13     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [netns]
1 S root        14     2  0  75  -5 -     0 async_ Mar01 ?        00:00:00 [async/mgr]
1 S root        15     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kintegrityd/0]
1 S root        16     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kintegrityd/1]
1 S root        17     2  0  75  -5 -     0 worker Mar01 ?        00:00:12 [kblockd/0]
1 S root        18     2  0  75  -5 -     0 worker Mar01 ?        00:10:09 [kblockd/1]
1 S root        19     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kacpid]
1 S root        20     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kacpi_notify]
1 S root        21     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kacpi_hotplug]
1 S root        22     2  0  75  -5 -     0 worker Mar01 ?        00:02:08 [ata/0]
1 S root        23     2  0  75  -5 -     0 worker Mar01 ?        00:01:40 [ata/1]
1 S root        24     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [ata_aux]
1 S root        25     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [ksuspend_usbd]
1 S root        26     2  0  75  -5 -     0 hub_th Mar01 ?        00:00:01 [khubd]
1 S root        27     2  0  75  -5 -     0 serio_ Mar01 ?        00:00:00 [kseriod]
1 S root        28     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kmmcd]
1 S root        29     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [bluetooth]
1 S root        30     2  0  80   0 -     0 watchd Mar01 ?        00:00:14 [khungtaskd]
1 S root        33     2  0  75  -5 -     0 kswapd Mar01 ?        02:03:39 [kswapd0]
1 S root        34     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [aio/0]
1 S root        35     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [aio/1]
1 S root        36     2  0  75  -5 -     0 ecrypt Mar01 ?        00:00:00 [ecryptfs-kthrea]
1 S root        37     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [crypto/0]
1 S root        38     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [crypto/1]
1 S root        48     2  0  75  -5 -     0 scsi_e Mar01 ?        00:00:00 [scsi_eh_0]
1 S root        49     2  0  75  -5 -     0 scsi_e Mar01 ?        00:00:00 [scsi_eh_1]
1 S root        52     2  0  75  -5 -     0 scsi_e Mar01 ?        00:07:35 [scsi_eh_2]
1 S root        53     2  0  75  -5 -     0 scsi_e Mar01 ?        00:00:00 [scsi_eh_3]
1 S root        57     2  0  75  -5 -     0 scsi_e Mar01 ?        00:00:00 [scsi_eh_4]
1 S root        58     2  0  75  -5 -     0 scsi_e Mar01 ?        00:00:00 [scsi_eh_5]
1 S root        69     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kstriped]
1 S root        70     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kmpathd/0]
1 S root        71     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kmpathd/1]
1 S root        72     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kmpath_handlerd]
1 S root        73     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [ksnapd]
1 S root        74     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kondemand/0]
1 S root        75     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kondemand/1]
1 S root        76     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kconservative/0]
1 S root        77     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kconservative/1]
5 S root        78     2  0  70 -10 -     0 rfcomm Mar01 ?        00:00:00 [krfcommd]
1 S root       269     2  0  75  -5 -     0 hpsbpk Mar01 ?        00:00:00 [khpsbpkt]
1 S root       305     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [usbhid_resumer]
1 S cole       317 32707  0  80   0 - 215363 futex_ 22:46 ?       00:00:00 /opt/google/chrome/chrome --type=extens
1 S cole       321 32707  0  80   0 - 218554 futex_ 22:46 ?       00:00:03 /opt/google/chrome/chrome --type=extens
1 S cole       325 32707  0  80   0 - 215393 futex_ 22:46 ?       00:00:00 /opt/google/chrome/chrome --type=extens
1 S root       355     2  0  75  -5 -     0 nodemg Mar01 ?        00:00:00 [knodemgrd_0]
1 S cole       370 32707  0  80   0 - 220025 futex_ 22:46 ?       00:00:10 /opt/google/chrome/chrome --type=render
1 S root       435     2  0  75  -5 -     0 kjourn Mar01 ?        00:00:15 [kjournald2]
1 S root       499     1  0  80   0 -  3192 poll_s Mar01 ?        00:00:00 upstart-udev-bridge --daemon
5 S root       516     1  0  76  -4 -  4286 poll_s Mar01 ?        00:00:00 udevd --daemon
1 S cole       612 32707  0  80   0 - 219049 futex_ 22:54 ?       00:00:03 /opt/google/chrome/chrome --type=render
1 S cole       709 32707  0  85   5 - 215658 futex_ 22:56 ?       00:00:00 /opt/google/chrome/chrome --type=render
1 S root       746     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [kpsmoused]
1 S root       767     2  0  75  -5 -     0 kjourn Mar01 ?        00:00:52 [kjournald2]
1 S cole       819     1  1  80   0 -  1768 ep_pol Mar25 ?        00:45:06 /usr/bin/wineserver
0 S cole       823     1  0  80   0 - 660904 pipe_w Mar25 ?       00:00:00 C:\windows\system32\services.exe      
0 S cole       835     1  0  80   0 - 663517 pipe_w Mar25 ?       00:00:44 C:\windows\explorer.exe /desktop      
4 S root       846     1  0  80   0 -  2048 syslog Mar01 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/run/rsysl
1 S cole       857 32707  0  85   5 - 221274 futex_ 23:06 ?       00:00:04 /opt/google/chrome/chrome --type=render
1 S root       860     2  0  75  -5 -     0 worker Mar01 ?        00:00:00 [hd-audio0]
5 S syslog     862     1  0  80   0 - 31465 poll_s Mar01 ?        00:00:16 rsyslogd -c4
0 S cole       899     1  0  80   0 - 665408 pipe_w Mar25 ?       00:02:07 C:\Program Files\World of Warcraft\WoW-
1 S root       902     1  0  80   0 -  4557 reques Mar01 ?        04:32:31 /sbin/mount.ntfs /dev/sda1 /home/cole/T
5 S 102        910     1  0  80   0 -  6387 poll_s Mar01 ?        00:00:13 dbus-daemon --system --fork
5 S avahi      927     1  0  80   0 -  7974 poll_s Mar01 ?        00:00:03 avahi-daemon: running [slovakia.local]
1 S avahi      928   927  0  80   0 -  7940 unix_s Mar01 ?        00:00:00 avahi-daemon: chroot helper
5 S 107        931     1  0  80   0 -  8554 poll_s Mar01 ?        00:00:04 hald --daemon=yes
5 S root       935     1  0  80   0 - 30095 poll_s Mar01 ?        00:00:00 /usr/sbin/console-kit-daemon
0 S root      1006   931  0  80   0 -  5014 poll_s Mar01 ?        00:00:00 hald-runner
5 S root      1008     1  0  80   0 - 22381 poll_s Mar01 ?        00:00:00 NetworkManager
4 S root      1010     1  0  80   0 - 12869 poll_s Mar01 ?        00:00:00 /usr/sbin/modem-manager
4 S root      1024     1  0  80   0 -  7054 poll_s Mar01 ?        00:00:00 /sbin/wpa_supplicant -u -s
0 S root      1140  1006  0  80   0 -  5552 poll_s Mar01 ?        00:01:55 hald-addon-input: Listening on /dev/inp
4 S root      1148  1006  0  80   0 -  5545 poll_s Mar01 ?        00:04:12 hald-addon-storage: polling /dev/sr0 (e
4 S 107       1158  1006  0  80   0 -  6520 unix_s Mar01 ?        00:00:00 hald-addon-acpi: listening on acpid soc
0 S root      1195     1  0  80   0 -  1497 n_tty_ Mar01 tty4     00:00:00 /sbin/getty -8 38400 tty4
0 S root      1198     1  0  80   0 -  1497 n_tty_ Mar01 tty5     00:00:00 /sbin/getty -8 38400 tty5
4 S root      1210     1  0  80   0 - 25081 wait   Mar01 tty2     00:00:00 /bin/login --     
0 S root      1211     1  0  80   0 -  1497 n_tty_ Mar01 tty3     00:00:00 /sbin/getty -8 38400 tty3
0 S root      1213     1  0  80   0 -  1497 n_tty_ Mar01 tty6     00:00:00 /sbin/getty -8 38400 tty6
1 S root      1215     1  0  80   0 -  1088 poll_s Mar01 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/a
1 S cole      1217 32707  2  85   5 - 221827 futex_ 23:20 ?       00:00:03 /opt/google/chrome/chrome --type=render
5 S root      1224     1  0  80   0 -  4677 hrtime Mar01 ?        00:00:02 cron
1 S daemon    1225     1  0  80   0 -  4128 hrtime Mar01 ?        00:00:00 atd
0 R cole      1282 31862  0  80   0 -  4061 -      23:22 pts/4    00:00:00 ps -efl
0 S cole      1403 17457  0  80   0 -  4816 poll_s Mar25 tty1     00:10:05 top
4 S root      1717     1  0  80   0 - 25074 wait   Mar01 tty1     00:00:00 /bin/login --     
4 S root      1749     1  0  80   0 - 18735 poll_s Mar01 ?        00:00:02 gdm-binary
0 S root      1757  1749  0  80   0 - 19212 poll_s Mar01 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display
4 S root      1758  1757  1  80   0 - 752167 poll_s Mar01 tty7    10:10:26 /usr/bin/X :0 -br -verbose -auth /var/r
4 S root      1800  1757  0  80   0 - 29314 poll_s Mar01 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
4 S cole      1815  1800  0  80   0 - 41922 poll_s Mar01 ?        00:00:02 gnome-session
1 S cole      1856  1815  0  80   0 -  9015 poll_s Mar01 ?        00:00:10 /usr/bin/ssh-agent /usr/bin/dbus-launch
1 S cole      1859     1  0  80   0 -  6539 poll_s Mar01 ?        00:00:00 /usr/bin/dbus-launch --exit-with-sessio
1 S cole      1862     1  0  80   0 -  6282 poll_s Mar01 ?        00:03:46 /bin/dbus-daemon --fork --print-pid 7 -
1 S cole      1866     1  0  80   0 - 88756 poll_s Mar01 ?        02:04:21 /usr/bin/pulseaudio --start
0 S cole      1871  1866  0  80   0 - 23577 poll_s Mar01 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
0 S cole      1873     1  0  80   0 - 11707 poll_s Mar01 ?        00:00:21 /usr/lib/libgconf2-4/gconfd-2
4 S root      1878     1  0  80   0 - 11775 poll_s Mar01 ?        00:00:00 /usr/lib/devicekit-power/devkit-power-d
1 S cole      1912     1  0  80   0 - 86478 poll_s Mar01 ?        00:02:49 /usr/lib/gnome-settings-daemon/gnome-se
1 S cole      1916     1  0  80   0 - 80387 poll_s Mar01 ?        00:00:01 gnome-keyring-daemon --start
1 S cole      1920     1  0  80   0 - 48348 poll_s Mar01 ?        00:00:01 seahorse-daemon
0 S cole      1922     1  0  80   0 - 17032 poll_s Mar01 ?        00:00:01 /usr/lib/gvfs/gvfsd
1 S cole      1930     1  0  80   0 - 37570 futex_ Mar01 ?        00:00:01 /usr/lib/gvfs//gvfs-fuse-daemon /home/c
0 S cole      1945  1815  0  80   0 -  1001 wait   Mar01 ?        00:00:00 /bin/sh /usr/bin/compiz
0 S cole      1950     1  0  80   0 -  5009 hrtime Mar01 ?        00:03:39 syndaemon -i 0.5 -k
0 S cole      2010  1945  0  80   0 - 101199 poll_s Mar01 ?       03:26:08 /usr/bin/compiz.real --ignore-desktop-h
0 S cole      2011  1815  0  80   0 - 142430 poll_s Mar01 ?       00:14:59 gnome-panel
0 S cole      2012  1815  0  80   0 - 193040 poll_s Mar01 ?       00:08:18 nautilus
0 S cole      2014     1  0  80   0 - 38134 poll_s Mar01 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activ
0 S cole      2018  2010  0  80   0 -  1001 wait   Mar01 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
0 S cole      2019  2018  0  80   0 - 59684 poll_s Mar01 ?        00:02:20 /usr/bin/gtk-window-decorator
0 S cole      2021  1815  0  80   0 - 107546 poll_s Mar01 ?       00:00:01 /usr/lib/evolution/2.28/evolution-alarm
0 S cole      2023  1815  0  80   0 - 40281 poll_s Mar01 ?        00:00:03 /usr/lib/gnome-disk-utility/gdu-notific
0 S cole      2024  1815  0  80   0 - 48279 poll_s Mar01 ?        00:00:32 update-notifier --startup-delay=60
0 S cole      2028     1  0  80   0 - 21843 poll_s Mar16 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
0 S cole      2030  1815  0  80   0 - 95667 poll_s Mar01 ?        00:00:07 nm-applet --sm-disable
0 S cole      2038  1815  0  80   0 - 38252 poll_s Mar01 ?        00:00:01 bluetooth-applet
0 S cole      2042  1815  0  80   0 - 37066 poll_s Mar01 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome
0 S cole      2043  1815  0  80   0 - 111552 poll_s Mar01 ?       00:00:28 gnome-volume-control-applet
0 S cole      2047  1815  0  80   0 - 47083 poll_s Mar01 ?        00:00:11 gnome-power-manager
1 S cole      2048     1  0  80   0 - 43539 poll_s Mar01 ?        00:01:02 gnome-screensaver
4 S root      2050     1  0  80   0 - 13521 poll_s Mar01 ?        00:00:00 /usr/lib/policykit-1/polkitd
0 S cole      2053     1  0  80   0 - 12514 poll_s Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.
0 S cole      2057     1  0  80   0 - 58941 poll_s Mar01 ?        00:00:01 /usr/lib/gnome-applets/trashapplet --oa
0 S cole      2059     1  0  80   0 - 34069 poll_s Mar01 ?        00:00:05 /usr/lib/gvfs/gvfs-gdu-volume-monitor
0 S cole      2064     1  0  80   0 - 17672 poll_s Mar01 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monit
0 S cole      2074     1  0  80   0 - 62514 poll_s Mar01 ?        00:00:04 /usr/lib/indicator-applet/indicator-app
0 S cole      2083     1  0  80   0 - 57030 poll_s Mar01 ?        00:00:45 /usr/lib/indicator-messages/indicator-m
0 S cole      2085     1  0  80   0 - 23910 poll_s Mar01 ?        00:00:01 /usr/lib/indicator-session/indicator-st
0 S cole      2087     1  0  80   0 - 10542 poll_s Mar01 ?        00:00:00 /usr/lib/indicator-session/indicator-us
0 S cole      2089     1  0  80   0 - 12772 poll_s Mar01 ?        00:00:00 /usr/lib/indicator-session/indicator-se
0 S cole      2095     1  0  80   0 - 10803 poll_s Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9
0 S cole      2162     1  0  80   0 -  1001 pipe_w Mar01 ?        00:00:00 /bin/sh -e /usr/bin/couchdb -n -a \"/et
1 S cole      2189  2162  0  80   0 -  1001 wait   Mar01 ?        00:00:00 /bin/sh -e /usr/bin/couchdb -n -a \"/et
0 S cole      2190  2189  0  80   0 - 28512 poll_s Mar01 ?        00:52:21 /usr/lib/erlang/erts-5.7.2/bin/beam.smp
0 S cole      2199  2190  0  80   0 -   943 poll_s Mar01 ?        00:00:03 heart -pid 2190 -ht 11
0 S cole      2204  2190  0  80   0 - 18612 pipe_w Mar01 ?        00:00:00 /usr/lib/couchdb/bin/couchjs /usr/share
0 S cole      2229     1  0  80   0 - 33448 poll_s Mar01 ?        00:48:30 /usr/bin/python /usr/lib/ubuntuone-clie
0 S cole      2245     1  0  80   0 - 104735 poll_s Mar01 ?       00:00:00 /usr/lib/evolution/2.28/evolution-excha
0 S cole      2249     1  0  80   0 - 97828 poll_s Mar01 ?        00:00:00 /usr/lib/evolution/evolution-data-serve
0 S cole      2265     1  0  80   0 -  8905 poll_s Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
4 S root      2315     1  0  80   0 - 10044 poll_s Mar01 ?        00:00:00 /usr/sbin/system-tools-backends
4 S root      2317     1  0  80   0 - 14649 poll_s Mar01 ?        00:00:00 /usr/bin/perl /usr/share/system-tools-b
0 S cole      3580     1  0  80   0 - 53300 poll_s Mar01 ?        00:01:27 /usr/lib/gvfs/gvfsd-http --spawner :1.9
0 S cole      3992  2010  0  80   0 -  1001 wait   Mar26 ?        00:00:00 /bin/sh -c gnome-terminal
0 S cole      3993  3992  0  80   0 - 81404 poll_s Mar26 ?        00:03:41 gnome-terminal
0 S cole      3994  3993  0  80   0 -  3599 unix_s Mar26 ?        00:00:00 gnome-pty-helper
0 S cole      3995  3993  0  80   0 -  5713 n_tty_ Mar26 pts/1    00:00:00 bash
0 S cole      4126     1  3  80   0 - 669524 pipe_w Mar26 pts/1   02:28:18 uTorrent.exe /NOINSTALL /BRINGTOFRONT 
0 S cole      4967     1  0  80   0 - 31018 poll_s Mar01 ?        00:00:00 /usr/lib/gvfs/gvfsd-computer --spawner
1 S guest     5506     1  0  80   0 - 22150 poll_s Mar05 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemoni
4 S guest     5521 16605  0  80   0 - 41873 poll_s Mar05 ?        00:00:00 gnome-session
1 S guest     5563  5521  0  80   0 -  9015 poll_s Mar05 ?        00:00:11 /usr/bin/ssh-agent /usr/bin/dbus-launch
1 S guest     5566     1  0  80   0 -  6539 poll_s Mar05 ?        00:00:00 /usr/bin/dbus-launch --exit-with-sessio
1 S guest     5567     1  0  80   0 -  5964 poll_s Mar05 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 8 -
1 S guest     5571     1  0  80   0 - 55797 poll_s Mar05 ?        00:00:02 /usr/bin/pulseaudio --start
0 S guest     5576  5571  0  80   0 - 23577 poll_s Mar05 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
0 S guest     5578     1  0  80   0 - 11574 poll_s Mar05 ?        00:00:05 /usr/lib/libgconf2-4/gconfd-2
1 S guest     5583     1  0  80   0 - 78538 poll_s Mar05 ?        00:01:11 /usr/lib/gnome-settings-daemon/gnome-se
1 S guest     5590     1  0  80   0 - 48339 poll_s Mar05 ?        00:00:00 seahorse-daemon
0 S guest     5595     1  0  80   0 - 10803 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd
0 S guest     5600     1  0  80   0 - 41350 poll_s Mar05 ?        00:00:00 /usr/lib/notify-osd/notify-osd
1 S guest     5604     1  0  80   0 - 18873 futex_ Mar05 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/g
0 S guest     5608  5521  0  80   0 -  1001 wait   Mar05 ?        00:00:00 /bin/sh /usr/bin/compiz
0 S guest     5621     1  0  80   0 -  4943 hrtime Mar05 ?        00:03:13 syndaemon -i 0.5 -k
0 S guest     5682  5608  0  80   0 - 76837 poll_s Mar05 ?        00:00:44 /usr/bin/compiz.real --ignore-desktop-h
0 S guest     5683  5521  0  80   0 - 84478 poll_s Mar05 ?        00:00:21 gnome-panel
0 S guest     5684  5521  0  80   0 - 116773 poll_s Mar05 ?       00:00:01 nautilus
0 S guest     5687     1  0  80   0 - 38134 poll_s Mar05 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activ
0 S guest     5689  5521  0  80   0 - 107502 poll_s Mar05 ?       00:00:00 /usr/lib/evolution/2.28/evolution-alarm
0 S guest     5691  5521  0  80   0 - 40248 poll_s Mar05 ?        00:00:02 /usr/lib/gnome-disk-utility/gdu-notific
0 S guest     5692  5521  0  80   0 - 48152 poll_s Mar05 ?        00:00:31 update-notifier --startup-delay=60
0 S guest     5701  5521  0  80   0 - 38220 poll_s Mar05 ?        00:00:00 bluetooth-applet
0 S guest     5703  5521  0  80   0 - 37033 poll_s Mar05 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome
0 S guest     5704  5521  0  80   0 - 67284 poll_s Mar05 ?        00:00:00 gnome-volume-control-applet
0 S guest     5708  5521  0  80   0 - 46518 poll_s Mar05 ?        00:00:05 gnome-power-manager
1 S guest     5711     1  0  80   0 - 42950 poll_s Mar05 ?        00:00:24 gnome-screensaver
0 S guest     5712  5682  0  80   0 -  1001 wait   Mar05 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
0 S guest     5713  5712  0  80   0 - 44015 poll_s Mar05 ?        00:00:14 /usr/bin/gtk-window-decorator
0 S guest     5716     1  0  80   0 - 12458 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.
0 S guest     5720     1  0  80   0 - 58328 poll_s Mar05 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oa
0 S guest     5722     1  0  80   0 - 13585 poll_s Mar05 ?        00:00:03 /usr/lib/gvfs/gvfs-gdu-volume-monitor
0 S guest     5725     1  0  80   0 - 14969 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monit
0 S guest     5730     1  0  80   0 - 61847 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-applet/indicator-app
0 S guest     5732     1  0  80   0 - 61675 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-applet/indicator-app
0 S guest     5736     1  0  80   0 - 23845 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-session/indicator-st
0 S guest     5738     1  0  80   0 - 10542 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-session/indicator-us
0 S guest     5740     1  0  80   0 - 12772 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-session/indicator-se
0 S guest     5742     1  0  80   0 - 16214 poll_s Mar05 ?        00:00:00 /usr/lib/indicator-messages/indicator-m
0 S guest     5749     1  0  80   0 -  8681 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
0 S guest     5751     1  0  80   0 - 10803 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.1
0 S guest     5781     1  0  80   0 - 88319 poll_s Mar05 ?        00:00:00 /usr/lib/evolution/2.28/evolution-excha
0 S guest     5785     1  0  80   0 - 95673 poll_s Mar05 ?        00:00:00 /usr/lib/evolution/evolution-data-serve
0 S cole      6054     1  0  80   0 - 55243 poll_s Mar21 ?        00:00:25 /usr/lib/notify-osd/notify-osd
0 S cole      6436     1  0  80   0 - 16509 poll_s Mar19 ?        00:00:00 /usr/lib/gvfs/gvfsd-network --spawner :
0 S cole      6447     1  0  80   0 - 13164 poll_s Mar19 ?        00:00:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.
4 S cole      6508  1210  0  80   0 -  5734 n_tty_ Mar23 tty2     00:00:00 -bash
0 S root      7209  1749  0  80   0 - 19212 poll_s Mar05 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display
4 S root      7212  7209  0  80   0 - 164788 poll_s Mar05 tty9    00:00:09 /usr/bin/X :3 -br -verbose -auth /var/r
1 S gdm       7260     1  0  80   0 -  5865 poll_s Mar05 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 -
1 S gdm       7261     1  0  80   0 -  6539 poll_s Mar05 ?        00:00:00 /usr/bin/dbus-launch --exit-with-sessio
4 S gdm       7262  7209  0  80   0 - 38070 poll_s Mar05 ?        00:00:00 /usr/bin/gnome-session --autostart=/usr
0 S gdm       7265     1  0  80   0 - 11536 poll_s Mar05 ?        00:00:04 /usr/lib/libgconf2-4/gconfd-2
1 S gdm       7267     1  0  80   0 - 57796 poll_s Mar05 ?        00:00:23 /usr/lib/gnome-settings-daemon/gnome-se
0 S gdm       7272     1  0  80   0 -  8695 poll_s Mar05 ?        00:00:00 /usr/lib/gvfs/gvfsd
0 S gdm       7274     1  0  80   0 - 37080 poll_s Mar05 ?        00:00:00 /usr/lib/notify-osd/notify-osd
0 S gdm       7275  7262  0  80   0 - 72443 poll_s Mar05 ?        00:00:01 metacity
0 S gdm       7277  7262  0  80   0 - 45952 poll_s Mar05 ?        00:00:08 gnome-power-manager
0 S gdm       7278  7262  0  80   0 - 47046 poll_s Mar05 ?        00:00:30 /usr/lib/gdm/gdm-simple-greeter
1 S gdm       7282     1  0  80   0 - 56788 poll_s Mar05 ?        00:00:01 /usr/bin/pulseaudio --start --log-targe
0 S gdm       7294  7282  0  80   0 - 23577 poll_s Mar05 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
0 S root      7312  7209  0  80   0 - 14428 poll_s Mar05 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
0 S cole      8619  2190  0  80   0 -  4962 poll_s Mar21 ?        00:01:07 /usr/lib/erlang/lib/ssl-3.10.3/priv/bin
0 S cole      8620  2190  0  80   0 -  2656 poll_s Mar21 ?        00:00:00 inet_gethost 4
1 S cole      8621  8620  0  80   0 -  5266 pipe_w Mar21 ?        00:00:01 inet_gethost 4
0 S cole      8831     1  0  80   0 - 287343 poll_s Mar26 ?       00:04:08 rhythmbox
1 S root      9963 22232  0  80   0 - 16406 poll_s Mar26 ?        00:00:00 /usr/sbin/winbindd
1 S root      9964 22232  0  80   0 - 18008 poll_s Mar26 ?        00:00:00 /usr/sbin/winbindd
5 S root     11215     1  0  80   0 -  9985 pause  Mar04 ?        00:40:23 /usr/sbin/g15daemon
0 S cole     11519     1  0  80   0 -  9579 futex_ Mar04 ?        00:00:00 g15composer
4 S root     13557     1  0  80   0 - 18029 poll_s Mar04 ?        00:00:00 /usr/bin/python /usr/lib/system-service
0 S guest    13730     1  0  80   0 - 95482 poll_s Mar02 ?        00:00:00 /usr/lib/evolution/evolution-data-serve
4 S root     16500  1749  0  80   0 - 19245 poll_s Mar02 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display
4 S root     16503 16500  0  80   0 - 181593 poll_s Mar02 tty10   00:08:57 /usr/bin/X :2 -br -verbose -auth /var/r
1 S gdm      16554     1  0  80   0 -  6539 poll_s Mar02 ?        00:00:00 /usr/bin/dbus-launch --exit-with-sessio
4 S root     16605 16500  0  80   0 - 30562 poll_s Mar02 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
4 S cole     17457  1717  0  80   0 -  5370 wait   Mar06 tty1     00:00:00 -bash
0 S cole     19193     1  0  80   0 - 45741 poll_s Mar20 ?        00:07:07 /usr/bin/python /usr/lib/desktopcouch/d
1 S root     19436     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfs_mru_cache]
1 S root     19440     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfslogd/0]
1 S root     19441     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfslogd/1]
1 S root     19443     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfsdatad/0]
1 S root     19444     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfsdatad/1]
1 S root     19445     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfsconvertd/0]
1 S root     19446     2  0  75  -5 -     0 worker Mar04 ?        00:00:00 [xfsconvertd/1]
1 S root     19449     2  0  75  -5 -     0 jfsIOW Mar04 ?        00:00:00 [jfsIO]
1 S root     19450     2  0  75  -5 -     0 jfs_la Mar04 ?        00:00:00 [jfsCommit]
1 S root     19451     2  0  75  -5 -     0 jfs_la Mar04 ?        00:00:00 [jfsCommit]
1 S root     19452     2  0  75  -5 -     0 jfs_sy Mar04 ?        00:00:00 [jfsSync]
5 S root     20417   516  0  78  -2 -  4285 poll_s Mar25 ?        00:00:00 udevd --daemon
4 S root     20813     1  0  80   0 - 18807 ep_pol Mar04 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
1 S root     21210     2  0  80   0 -     0 pdflus Mar25 ?        00:00:04 [pdflush]
5 S root     22179     1  0  80   0 - 15112 poll_s Mar25 ?        00:00:02 /usr/sbin/nmbd -D
5 S root     22184     1  0  80   0 - 24080 poll_s Mar25 ?        00:00:00 /usr/sbin/smbd -D
1 S root     22187 22184  0  80   0 - 24077 poll_s Mar25 ?        00:00:00 /usr/sbin/smbd -D
1 S root     22232     1  0  80   0 - 16407 poll_s Mar25 ?        00:00:00 /usr/sbin/winbindd
1 S root     22234 22232  0  80   0 - 16406 poll_s Mar25 ?        00:00:00 /usr/sbin/winbindd
0 S cole     22359     1  0  80   0 - 106240 poll_s Mar02 ?       00:01:09 mono /usr/lib/tomboy/Tomboy.exe
0 S cole     24656     1  0  80   0 - 60392 poll_s Mar25 ?        00:00:02 /usr/lib/telepathy/telepathy-haze
0 S cole     24658     1  0  80   0 - 19186 poll_s Mar25 ?        00:00:04 /usr/lib/telepathy/telepathy-gabble
4 S root     24724  1008  0  80   0 -  1616 poll_s Mar25 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkM
0 S cole     25889     1  0  80   0 - 91755 poll_s 18:57 ?        00:00:52 filezilla
0 S cole     26756     1  0  80   0 - 11486 poll_s Mar02 ?        00:00:09 /usr/lib/telepathy/mission-control-5
0 S cole     26860     1  0  80   0 - 12255 poll_s Mar02 ?        00:00:01 /usr/lib/telepathy/telepathy-idle
0 S cole     27416     1  0  80   0 - 20875 poll_s 19:24 ?        00:00:00 /usr/lib/gvfs/gvfsd-gphoto2 --spawner :
0 S cole     28033     1  0  80   0 - 178289 poll_s 19:55 ?       00:01:16 /usr/lib/openoffice/program/soffice.bin
4 S root     28217     1  0  80   0 - 10637 poll_s Mar25 ?        00:00:27 /usr/lib/devicekit-disks/devkit-disks-d
1 S root     28218 28217  0  80   0 - 10545 poll_s Mar25 ?        00:00:07 devkit-disks-daemon: polling /dev/sr0 
1 S root     28246     2  0  80   0 -     0 pdflus 19:59 ?        00:00:00 [pdflush]
5 S root     28898 22184  0  80   0 - 24135 poll_s 20:53 ?        00:00:00 /usr/sbin/smbd -D
0 S cole     29380     1  0  80   0 - 98910 poll_s 21:29 ?        00:00:53 mangler
0 S cole     31862  3993  0  80   0 -  5817 wait   22:21 pts/4    00:00:00 bash
5 S root     31941     1  0  80   0 -  6539 poll_s Mar03 ?        00:00:00 dbus-launch --autolaunch 3245f398b8a3ae
1 S root     31942     1  0  80   0 -  5832 poll_s Mar03 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 -
0 S cole     32317     1  0  80   0 - 132043 poll_s 22:40 ?       00:00:02 /usr/bin/empathy
0 S cole     32702     1  3  80   0 - 218915 poll_s 22:46 ?       00:01:09 /opt/google/chrome/google-chrome --enab
1 S cole     32705 32702  0  80   0 - 46965 poll_s 22:46 ?        00:00:00 /opt/google/chrome/google-chrome --enab
4 S cole     32707     1  0  80   0 - 50211 wait_f 22:46 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
1 S cole     32741 32707  0  80   0 - 222519 futex_ 22:46 ?       00:00:07 /opt/google/chrome/chrome --type=extens

```

EDIT: I don't see any zombies.  Which column is memory usage?

---

### Post by linden940 on 2010-03-29
i'm about to go 2 bed..but here is something for you to try....

restart...see if that helps your memory problem...

when was the last time you restarted?

dont restart...computer lets loaded with crap..and will slow down...a restart will in that case...HELP

---

### Post by whackedspinach on 2010-03-29
I have an uptime of 27 days :).

I understand the whole reboot to fix idea, but isn't it possible to run a machine forever without this happening?  Am I just dreaming?  Because that would be beautiful.

---

### Post by conradin on 2010-03-29
1 S cole     32741 32707  0  80   0 - 222519 futex_ 22:46 ?       00:00:07 /opt/google/chrome/chrome --type=extens

1  3  80   0 - 669524 pipe_w Mar26 pts/1   02:28:18 uTorrent.exe /NOINSTALL /BRINGTOFRONT 

4 S root      1758  1757  1  80   0 - 752167 poll_s Mar01 tty7    10:10:26 /usr/bin/X :0 -br -verbose -auth /var/r


0 S cole       823     1  0  80   0 - 660904 pipe_w Mar25 ?       00:00:00 C:\windows\system32\services.exe  
    
0 S cole       835     1  0  80   0 - 663517 pipe_w Mar25 ?       00:00:44 C:\windows\explorer.exe /desktop   

0 S cole       899     1  0  80   0 - 665408 pipe_w Mar25 ?       00:02:07 C:\Program Files\World of Warcraft\WoW- 

Well, there seems to be numerous things with high memory usages, but no zombies. The collective google chrome processes seems to account for about 1
gig of memory useage, running WOW under wine seems to take up about 1.8 gig of memory. Are you running the desktop emulator? of wine? The 9th token in is the memory useage in Kilo bytes. Ill assume most of your issues are around running WOW, although there might be other things. The X server seems a little bit high also. A friend of mine recommends Cedega if youre having troubles running WOW under wine. 
[http://www.transgaming.com/](http://www.transgaming.com/)

also, Im not sure why you're running utorrent under wine, transmission runs native with lower memory usage (in my experience) Applications> Internet>  transmission Bittorent client

---

### Post by whackedspinach on 2010-03-29
WoW wasn't even running, or it wasn't supposed to be.  After killing all of the wine and chrome processes, I get this output for free -m:
```
total       used       free     shared    buffers     cached
Mem:          3962       3407        555          0         26        155
-/+ buffers/cache:       3225        736
Swap:         1302       1259         42
```
It seems better, but X still seems to be taking a lot of memory.

---

### Post by NightwishFan on 2010-03-29
Run top in a terminal, and hit shift+m to sort processes in order of memory usage.
```
top
```

---

### Post by whackedspinach on 2010-03-29
```
 
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
1758 root      20   0 2930m 1.7g 7644 S    4 43.5 612:14.09 Xorg                                                                                                     
 2083 cole      20   0  222m  80m 1140 S    0  2.0   0:45.52 indicator-messa                                                                                          
 2522 cole      20   0  710m  79m  28m S    0  2.0   0:13.44 chrome                                                                                                   
 2012 cole      20   0  754m  57m 4152 S    0  1.5   8:21.62 nautilus                                                                                                 
 8831 cole      20   0 1122m  57m 6824 S    0  1.5   4:09.41 rhythmbox                                                                                                
 2633 cole      20   0  858m  50m  14m S    0  1.3   0:03.95 chrome                                                                                                   
 2011 cole      20   0  556m  39m 5676 S    0  1.0  15:03.30 gnome-panel                                                                                              
 1866 cole      20   0  411m  36m  34m S    0  0.9 124:26.04 pulseaudio                                                                                               
28033 cole      20   0  696m  34m 5948 R    0  0.9   1:19.80 soffice.bin                                                                                              
 2010 cole      20   0  398m  22m 6684 S    1  0.6 206:31.80 compiz.real                                                                                              
 2560 cole      20   0  867m  22m  10m S    0  0.6   0:01.45 chrome                                                                                                   
 1912 cole      20   0  337m  21m 1740 S    0  0.5   2:49.92 gnome-settings-                                                                                          
 2279 cole      20   0  369m  21m 3948 S    0  0.5   0:01.23 gedit                                                                                                    
 2043 cole      20   0  435m  18m 2596 S    0  0.5   0:28.74 gnome-volume-co
```

Here are the a few results from top.  Xorg seems too high still.

---

### Post by NightwishFan on 2010-03-29
Yes, that is a lot of memory and cpu time for xorg, see mine in comparison.
```
1754 virgil    20   0  741m 104m  35m S    0  3.5   1:39.73 epiphany-browse    
 1530 virgil    20   0  752m  59m  29m S    0  2.0   0:39.95 rhythmbox          
 1442 virgil    20   0  505m  50m  25m S    0  1.7   0:03.83 empathy            
  991 root      20   0  156m  31m  13m S    5  1.0   1:17.91 Xorg
```

```
             total       used       free     shared    buffers     cached
Mem:          2985       1695       1289          0        115        847
-/+ buffers/cache:        732       2252
Swap:         4766          0       4766
```

You could log out to restart your xserver.

---

### Post by whackedspinach on 2010-03-29
Yes, I just did and xorg is using around 13m now.  Maybe there is a memory leak somewhere? Thanks for the help, everyone.

---

### Post by linden940 on 2010-03-29
u can run a computer 4ever but you have to reboot parts of the computer over time or it will lock up

---

### Post by conradin on 2010-03-30
not sure if you still have a high memory usage for your X process.
If you are, try resting the process with the kill 1 command. Kill 1 is the hangup signal that restarts the killed process with the same PID. 
(I think that will release the memory that process is taking.)
try:
```

ps -e | grep X
sudo kill 1 <PID>

```

Certainly I appreciate keeping my system up and running.

---

