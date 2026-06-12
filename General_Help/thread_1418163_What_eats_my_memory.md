---
title: "What eats my memory?"
date: 2010-02-28
forum: General Help
---

### Post by overander on 2010-02-28
After a fresh 9.10 installation and some configuration on my Dell inspiron 6400 laptop i noticed that almost 1/2 of my memory in use (and i don't count the memory chache/buffer use here), while if i check the running processes on my gnome-system-monitor (all process included), i counted around 200 Mb memory usage only.

My questions are:

  - Where can i list that part of the memory whitch not shown on the system monitor (top, ect ...)
  - How can i reduce my memory usage (i have only 1 Gb memory in this laptop, so i don't want to waste it).

Here is the output of thee 'free-m' command:

              total       used       free     shared    buffers     cached
Mem:           993        926         66          0         58        417
-/+ buffers/cache:        451        542
Swap:         1051          4       1046

---

### Post by chuina on 2010-02-28
Welcome in Ubuntu forums.

I use **htop** for memory watching.
In my opinion,It gives much more verbose stats display than **top** or **free**. 

To install it, give the command from a terminal:
```
sudo apt-get install htop
```

From a terminal type **htop** and press *Enter*.

---

### Post by Richard1979 on 2010-02-28
It's cache memory, nothing to worry about really.
In fact Ubuntu is helping you because it keeps frequently-accessed data in RAM so your apps and documents load faster.

If an app (i.e. a 3D game) needs the RAM, Ubuntu will give the memory space to it.

EDIT: Didn't really understand the question but the title was wayyyy off base to the post.

---

### Post by overander on 2010-02-28
> **Richard1979 said:**
> It's cache memory, nothing to worry about really.
In fact Ubuntu is helping you because it keeps frequently-accessed data in RAM so your apps and documents load faster.

If an app (i.e. a 3D game) needs the RAM, Ubuntu will give the memory space to it.

EDIT: Didn't really understand the question but the title was wayyyy off base to the post.

Thanks for the fast response, althrough you are actualy wrong. As i said before, i haven't counted cache memory there.

Currently (from free -m):

977 Mb physical memory in use:

  - 430 Mb for cache: thats okay.
  - 457 Mb for programs, kernel, etc ...: now, thats not okay.

I only run 1 firefox (<40 Mb memory usage) and 1 terminal. I think something is seriously wrong here.

---

### Post by overander on 2010-02-28
Thanks for the tip! Yes, it is more detailed, but sadly it havent listed the culpit(s) for this high memory usage.

---

### Post by Richard1979 on 2010-02-28
I don't think it's that high really.
I'm at 32% ATM with 2GB RAM and basically everything running: Apache2, MySQL, Gnome+Compiz+transparency, etc.

Take a look at my "ps aux"!

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  19452  1688 ?        Ss   10:46   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   10:46   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   10:46   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   10:46   0:02 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   10:46   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   10:46   0:03 [events/0]
root         7  0.0  0.0      0     0 ?        S<   10:46   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   10:46   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   10:46   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   10:46   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   10:46   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   10:46   0:00 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   10:46   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   10:46   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   10:46   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   10:46   0:00 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   10:46   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   10:46   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   10:46   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   10:46   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   10:46   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   10:46   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    10:46   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    10:46   0:00 [pdflush]
root        25  0.0  0.0      0     0 ?        S    10:46   0:00 [pdflush]
root        26  0.0  0.0      0     0 ?        S<   10:46   0:00 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   10:46   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   10:46   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   10:46   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_0]
root        37  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_3]
root        44  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_4]
root        46  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_5]
root        52  0.0  0.0      0     0 ?        S<   10:46   0:00 [kstriped]
root        53  0.0  0.0      0     0 ?        S<   10:46   0:00 [kmpathd/0]
root        54  0.0  0.0      0     0 ?        S<   10:46   0:00 [kmpath_handlerd]
root        55  0.0  0.0      0     0 ?        S<   10:46   0:00 [ksnapd]
root        56  0.0  0.0      0     0 ?        R<   10:46   0:05 [kondemand/0]
root        57  0.0  0.0      0     0 ?        S<   10:46   0:00 [kconservative/0]
root        58  0.0  0.0      0     0 ?        S<   10:46   0:00 [krfcommd]
root       202  0.0  0.0      0     0 ?        S<   10:46   0:00 [khpsbpkt]
root       249  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_8]
root       283  0.0  0.0      0     0 ?        S<   10:46   0:00 [usb-storage]
root       285  0.0  0.0      0     0 ?        S<   10:46   0:00 [scsi_eh_9]
root       286  0.0  0.0      0     0 ?        S<   10:46   0:01 [usb-storage]
root       303  0.0  0.0      0     0 ?        S<   10:46   0:00 [knodemgrd_0]
root       306  0.0  0.0      0     0 ?        S<   10:46   0:00 [usbhid_resumer]
root       407  0.0  0.0      0     0 ?        S<   10:46   0:00 [kjournald]
root       473  0.0  0.0  12636   692 ?        S    10:46   0:00 upstart-udev-bridge --daemon
root       475  0.0  0.0  17584  1128 ?        S<s  10:46   0:00 udevd --daemon
root       721  0.0  0.0  17580  1112 ?        S<   10:46   0:00 udevd --daemon
root       809  0.0  0.0      0     0 ?        S<   10:46   0:00 [edac-poller]
root      1004  0.0  0.0      0     0 ?        S<   10:46   0:00 [hd-audio0]
root      1040  0.0  0.0      0     0 ?        S<   10:46   0:00 [kjournald]
root      1086  0.0  0.0   8192   608 ?        Ss   10:46   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
102       1088  0.0  0.0  24308  1856 ?        Ss   10:46   0:01 dbus-daemon --system --fork
root      1099  0.0  0.1  89368  4040 ?        Ssl  10:46   0:00 NetworkManager
syslog    1100  0.0  0.1  60852  2064 ?        Sl   10:46   0:00 rsyslogd -c4
107       1104  0.0  0.2  34156  4736 ?        Ss   10:46   0:00 hald --daemon=yes
avahi     1106  0.0  0.0  31892  1556 ?        Ss   10:46   0:00 avahi-daemon: running [lara.local]
avahi     1112  0.0  0.0  31760   548 ?        Ss   10:46   0:00 avahi-daemon: chroot helper
root      1122  0.0  0.1  51508  2608 ?        S    10:46   0:00 /usr/sbin/modem-manager
root      1131  0.0  0.1  54680  3200 ?        Ssl  10:46   0:00 /usr/sbin/console-kit-daemon
root      1219  0.0  0.0  20056  1320 ?        S    10:46   0:00 hald-runner
root      1226  0.0  0.0  28216  2032 ?        S    10:46   0:00 /sbin/wpa_supplicant -u -s
root      1343  0.0  0.0  22172  1212 ?        S    10:46   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1381  0.0  0.1  74948  3736 ?        Ss   10:46   0:03 gdm-binary
root      1408  0.0  0.0  22180  1248 ?        S    10:46   0:09 hald-addon-input: Listening on /dev/input/event3 /dev/input/event5 /dev/input/event4 /dev/input/event1 /dev/input/event0
root      1409  0.0  0.0   5988   600 tty4     Ss+  10:46   0:00 /sbin/getty -8 38400 tty4
root      1411  0.0  0.0   5988   604 tty5     Ss+  10:46   0:00 /sbin/getty -8 38400 tty5
root      1439  0.0  0.0  22180  1332 ?        S    10:46   0:01 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1441  0.0  0.0   5988   604 tty2     Ss+  10:46   0:00 /sbin/getty -8 38400 tty2
root      1442  0.0  0.0   5988   600 tty3     Ss+  10:46   0:00 /sbin/getty -8 38400 tty3
root      1444  0.0  0.0   5988   604 tty6     Ss+  10:46   0:00 /sbin/getty -8 38400 tty6
root      1447  0.0  0.0   4352  1120 ?        Ss   10:46   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1449  0.0  0.0  16512   464 ?        Ss   10:46   0:00 atd
root      1450  0.0  0.0  18708   992 ?        Ss   10:46   0:00 cron
root      1469  0.0  0.0  22188  1212 ?        S    10:46   0:00 /usr/lib/hal/hald-addon-cpufreq
107       1477  0.0  0.0  26080  1212 ?        S    10:46   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1501  0.0  0.0   4004   620 ?        S    10:46   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1609  0.0  1.1 177928 24144 ?        Sl   10:46   0:08 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1611  0.0  0.0   3908   620 ?        S    10:46   0:00 logger -t mysqld -p daemon.error
root      1626  0.0  0.1  76872  3940 ?        S    10:46   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1627  7.8  2.9 670784 61708 tty7     Ss+  10:46  20:12 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-6toxsY/database -nolisten tcp vt7
clamav    1791  0.0  0.0  30084  1580 ?        Ss   10:46   0:00 /usr/bin/freshclam -d --quiet
gdm       2053  0.0  0.0  26156   780 ?        S    10:46   0:00 /usr/bin/dbus-launch --exit-with-session
root      2075  0.0  0.1  46992  2752 ?        S    10:46   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      2330  0.0  0.1 114032  3980 ?        S    10:46   0:00 /usr/lib/gdm/gdm-session-worker
root      2366  0.0  0.1  37012  2208 ?        Ss   10:46   0:00 /usr/lib/postfix/master
root      2399  0.0  0.0  17580  1100 ?        S<   10:46   0:00 udevd --daemon
root      2437  0.0  0.0  63564  1996 ?        Ss   10:46   0:00 /usr/sbin/winbindd
root      2438  0.0  0.0  63464  1428 ?        S    10:46   0:00 /usr/sbin/winbindd
root      2446  0.0  0.0  20176  1724 ?        S<s  10:46   0:00 /usr/sbin/bluetoothd --udev
root      2471  0.0  0.1  75152  2860 ?        Ss   10:46   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      2591  0.0  0.5 171664 10348 ?        Ss   10:46   0:00 /usr/sbin/apache2 -k start
root      2628  0.0  0.3  55896  6376 ?        Sl   10:47   0:02 /usr/bin/python /usr/bin/fail2ban-server -b -s /var/run/fail2ban/fail2ban.sock
root      2668  0.0  0.0   5988   600 tty1     Ss+  10:47   0:00 /sbin/getty -8 38400 tty1
richard   2686  0.0  0.1  96816  3876 ?        Sl   10:47   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
richard   2701  0.0  0.3 166724  7604 ?        Ssl  10:47   0:00 gnome-session
richard   2759  0.0  0.0  36060   708 ?        Ss   10:47   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
richard   2762  0.0  0.0  26156   776 ?        S    10:47   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
richard   2763  0.0  0.0  24088  1608 ?        Ss   10:47   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
richard   2767  1.3  0.2 272104  5512 ?        Ssl  10:47   3:34 /usr/bin/pulseaudio --start
richard   2770  0.0  0.1  94308  3416 ?        S    10:47   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
richard   2772  0.0  0.2  46276  6100 ?        S    10:47   0:07 /usr/lib/libgconf2-4/gconfd-2
richard   2780  0.0  0.5 307032 10604 ?        Ssl  10:47   0:07 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
richard   2788  0.0  0.1  43220  2384 ?        S    10:47   0:00 /usr/lib/gvfs/gvfsd
richard   2791  0.0  0.4 192848  8384 ?        Ss   10:47   0:00 seahorse-daemon
richard   2794  0.0  0.6 204344 14160 ?        S    10:47   0:03 /usr/lib/notify-osd/notify-osd
richard   2796  0.0  0.1  75492  2800 ?        Ssl  10:47   0:04 /usr/lib/gvfs//gvfs-fuse-daemon /home/richard/.gvfs
richard   2802  0.0  0.0   4004   640 ?        S    10:47   0:00 /bin/sh /usr/bin/compiz
richard   2870  1.7  3.0 328876 61884 ?        S    10:47   4:33 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 104b02f7075b5f7dc9126735402882404200000027010028 --loose-binding move resize place decoration animation
richard   2871  0.1  1.7 371540 36104 ?        S    10:47   0:26 gnome-panel
richard   2872  0.1  1.9 529932 40612 ?        Sl   10:47   0:27 nautilus
richard   2874  0.0  0.1  86844  3964 ?        Ssl  10:47   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
richard   2881  0.0  0.6 226448 12696 ?        S    10:47   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
richard   2882  0.5  1.3 266124 28304 ?        S    10:47   1:28 python -u /usr/share/screenlets/Netmonitor/NetmonitorScreenlet.py
richard   2884  1.9  1.8 278408 38620 ?        S    10:47   5:02 python -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py
richard   2887  0.0  0.6 273976 13816 ?        S    10:47   0:00 gnome-volume-control-applet
richard   2890  0.0  0.9 221800 19508 ?        S    10:47   0:00 python /usr/share/system-config-printer/applet.py
richard   2896  0.0  0.1  49876  3136 ?        S    10:47   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
richard   2897  0.0  0.4 157164  8800 ?        S    10:47   0:00 gnome-power-manager
richard   2899  0.0  0.8 217948 17968 ?        S    10:47   0:00 nm-applet --sm-disable
richard   2904  0.0  0.3 147328  6496 ?        S    10:47   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
richard   2905  0.0  0.6 195748 14108 ?        S    10:47   0:00 update-notifier --startup-delay=60
richard   2906  0.0  0.3 162724  7920 ?        S    10:47   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
richard   2907  0.0  0.0   4004   560 ?        Ss   10:47   0:00 /bin/sh -c /usr/bin/compiz-decorator
richard   2908  0.0  0.5 178196 11208 ?        S    10:47   0:03 /usr/bin/gtk-window-decorator
richard   2910  0.0  0.1  70732  3704 ?        S    10:47   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      2913  0.0  0.1  53708  3940 ?        S    10:47   0:00 /usr/lib/policykit-1/polkitd
richard   2914  0.0  0.1 170884  3164 ?        Ss   10:47   0:00 gnome-screensaver
root      2916  0.0  0.1  42560  3200 ?        S    10:47   0:02 /usr/lib/devicekit-disks/devkit-disks-daemon
root      2919  0.0  0.0  42180   828 ?        S    10:47   0:01 devkit-disks-daemon: polling /dev/sr0 /dev/sr1 /dev/sdd
richard   2924  0.0  0.1  50504  2492 ?        S    10:47   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
richard   2938  0.0  1.1 246384 23900 ?        S    10:47   0:00 python /usr/share/screenlets-manager/screenlets-daemon.py
richard   2975  0.3  0.6 232272 12904 ?        S    10:47   0:55 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=19
richard   2977  0.0  0.6 211420 12556 ?        S    10:47   0:03 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIID:GNOME_CPUFreqApplet_Factory --oaf-ior-fd=26
richard   2981  0.0  0.7 240920 15400 ?        S    10:47   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=32
richard   3099  0.0  0.1  43224  2484 ?        S    10:47   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
richard   3112  0.0  0.1  35440  2660 ?        S    10:47   0:00 /usr/lib/gvfs/gvfsd-metadata
richard   3131  0.0  0.1  95384  3732 ?        S    10:47   0:00 /usr/lib/indicator-session/indicator-status-service
richard   3133  0.0  0.1  42172  2372 ?        S    10:47   0:00 /usr/lib/indicator-session/indicator-users-service
richard   3135  0.0  0.1  51092  3052 ?        S    10:47   0:00 /usr/lib/indicator-session/indicator-session-service
root      4762  0.0  0.4  72108  9732 ?        S    10:48   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
richard   6364  4.8  1.1 246384 23456 ?        Sl   15:02   0:07 gnome-system-monitor
richard   6638  3.3  0.7 218912 16116 ?        Sl   15:04   0:00 gnome-terminal
richard   6641  0.0  0.0  14396   780 ?        S    15:04   0:00 gnome-pty-helper
richard   6642  0.9  0.2  21508  4276 pts/0    Ss   15:04   0:00 bash
root      6665  0.3  0.1  72300  2284 pts/0    S    15:04   0:00 su
root      6681  0.1  0.1  19104  2092 pts/0    S    15:04   0:00 bash
root      6707  0.0  0.0  15164  1136 pts/0    R+   15:04   0:00 ps aux
richard  18562  0.1  1.3 117036 27664 ?        Sl   11:02   0:25 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
root     18610  0.0  0.1  62772  2876 ?        S    11:02   0:00 /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugi
postfix  18893  0.0  0.1  39232  2296 ?        S    11:02   0:00 qmgr -l -t fifo -u
richard  19641  3.7  2.5 765036 51620 ?        Sl   13:08   4:17 vlc /home/richard/Music/90's Dance Hits-2009(split tracks+cover's)barney's rg/CD2/19 - Insomnia.mp3
www-data 24599  0.0  0.2 171664  5116 ?        S    11:07   0:00 /usr/sbin/apache2 -k start
www-data 24600  0.0  0.2 171664  5116 ?        S    11:07   0:00 /usr/sbin/apache2 -k start
www-data 24601  0.0  0.2 171664  5116 ?        S    11:07   0:00 /usr/sbin/apache2 -k start
www-data 24602  0.0  0.2 171664  5116 ?        S    11:07   0:00 /usr/sbin/apache2 -k start
www-data 24603  0.0  0.2 171664  5116 ?        S    11:07   0:00 /usr/sbin/apache2 -k start
postfix  28643  0.0  0.1  39072  2124 ?        S    14:20   0:00 pickup -l -t fifo -u -c
richard  30011  0.0  0.0   4004   592 ?        S    12:16   0:00 /bin/sh /usr/lib/firefox-3.6/firefox
richard  30016  0.0  0.0   4004   612 ?        S    12:16   0:00 /bin/sh /usr/lib/firefox-3.6/run-mozilla.sh /usr/lib/firefox-3.6/firefox-bin
richard  30020  7.5  8.0 798736 165440 ?       Sl   12:16  12:38 /usr/lib/firefox-3.6/firefox-bin
richard  30334  2.7  1.0  82092 20932 ?        S    12:16   4:37 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/30020-1

```

---

