---
title: "Another karmic problem! This is one is a 'blocker' !!! HELP!!!"
date: 2009-11-01
forum: General Help
---

### Post by DexterLB on 2009-11-01
I upgraded to karmic, network upgrade. I love it except for this problem.

As I said, BLOCKER! I can hardly do anything on this system!

The problem: gnome-panel and Xorg are taking my entire CPU - their CPU usage combined gives 100%

ps aux:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2528  1488 ?        Ss   07:45   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   07:45   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   07:45   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   07:45   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   07:45   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   07:45   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   07:45   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   07:45   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   07:45   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   07:45   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   07:45   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   07:45   0:00 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   07:45   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   07:45   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   07:45   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   07:45   0:00 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   07:45   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   07:45   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   07:45   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   07:45   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   07:45   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   07:45   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    07:45   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    07:45   0:00 [pdflush]
root        25  0.0  0.0      0     0 ?        S    07:45   0:00 [pdflush]
root        26  0.0  0.0      0     0 ?        S<   07:45   0:00 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   07:45   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   07:45   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   07:45   0:00 [crypto/0]
root        33  0.0  0.0      0     0 ?        S<   07:45   0:00 [scsi_eh_0]
root        34  0.1  0.0      0     0 ?        S<   07:45   0:02 [scsi_eh_1]
root        37  0.0  0.0      0     0 ?        S<   07:45   0:00 [kstriped]
root        38  0.0  0.0      0     0 ?        S<   07:45   0:00 [kmpathd/0]
root        39  0.0  0.0      0     0 ?        S<   07:45   0:00 [kmpath_handlerd]
root        40  0.0  0.0      0     0 ?        S<   07:45   0:00 [ksnapd]
root        41  0.0  0.0      0     0 ?        S<   07:45   0:00 [kondemand/0]
root        42  0.0  0.0      0     0 ?        S<   07:45   0:00 [kconservative/0]
root        43  0.0  0.0      0     0 ?        S<   07:45   0:00 [krfcommd]
root       255  0.0  0.0      0     0 ?        S<   07:45   0:00 [scsi_eh_2]
root       256  0.0  0.0      0     0 ?        S<   07:45   0:01 [usb-storage]
root       309  0.0  0.0      0     0 ?        S<   07:45   0:00 [usbhid_resumer]
root       385  0.0  0.0      0     0 ?        S<   07:45   0:00 [kjournald]
root       454  0.0  0.0   2148   760 ?        S    07:45   0:00 upstart-udev-bridge --daemon
root       458  0.0  0.0   2768  1112 ?        S<s  07:45   0:00 udevd --daemon
root       684  0.0  0.0      0     0 ?        S<   07:45   0:00 [kgameportd]
root       806  0.0  0.0   3860  1000 ?        Ss   07:45   0:00 /sbin/mount.ntfs-3g /dev/sda2 /media/Data1 -o rw,locale=en_US.UTF-8
root       809  0.0  0.0      0     0 ?        S<   07:45   0:00 [kjournald2]
root       843  0.0  0.0   1848   544 ?        Ss   07:46   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
108        878  0.0  0.0   3144  1624 ?        Ss   07:46   0:00 dbus-daemon --system --fork
syslog    1049  0.0  0.0  33696  1660 ?        Sl   07:46   0:00 rsyslogd -c4
111       1059  0.0  0.2   6420  4144 ?        Ss   07:46   0:00 hald --daemon=yes
root      1060  0.0  0.1   8612  3404 ?        Ss   07:46   0:00 gdm-binary
avahi     1094  0.0  0.0   2820  1504 ?        Ss   07:46   0:00 avahi-daemon: running [DexterLB-home.local]
avahi     1095  0.0  0.0   2820   528 ?        Ss   07:46   0:00 avahi-daemon: chroot helper
root      1134  0.0  0.1  19472  2988 ?        Ssl  07:46   0:00 /usr/sbin/console-kit-daemon
root      1208  0.0  0.0   3336  1236 ?        S    07:46   0:00 hald-runner
root      1209  0.0  0.1  18664  3784 ?        Ssl  07:46   0:00 NetworkManager
root      1212  0.0  0.0   1700   548 tty4     Ss+  07:46   0:00 /sbin/getty -8 38400 tty4
root      1215  0.0  0.1   3900  2124 ?        S    07:46   0:00 /usr/sbin/modem-manager
root      1217  0.0  0.0   1700   540 tty5     Ss+  07:46   0:00 /sbin/getty -8 38400 tty5
root      1222  0.0  0.0   1700   544 tty2     Ss+  07:46   0:00 /sbin/getty -8 38400 tty2
root      1223  0.0  0.0   1700   548 tty3     Ss+  07:46   0:00 /sbin/getty -8 38400 tty3
root      1225  0.0  0.0   1700   544 tty6     Ss+  07:46   0:00 /sbin/getty -8 38400 tty6
root      1227  0.0  0.0   1972   864 ?        Ss   07:46   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1235  0.0  0.0   1892   808 ?        Ss   07:46   0:00 anacron -s
daemon    1238  0.0  0.0   1960   424 ?        Ss   07:46   0:00 atd
root      1239  0.0  0.0   2088   860 ?        Ss   07:46   0:00 cron
root      1279  0.0  0.0   4932  1660 ?        S    07:46   0:00 /sbin/wpa_supplicant -u -s
root      1283  0.0  0.0   2140   952 ?        S    07:46   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-7056e988-92a7-4348-87ea-8a42e444388a-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      1288  0.0  0.1   8544  3408 ?        S    07:46   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1315 32.3  1.7  49684 36324 tty7     Ss+  07:46   9:34 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-rFGHlC/database -nolisten tcp vt7
root      1331  0.0  0.0   5568  1040 ?        Ss   07:46   0:00 /usr/sbin/sshd
root      1386  0.0  0.0   3412  1144 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
111       1389  0.0  0.0   3256  1124 ?        S    07:46   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1390  0.0  0.0   3412  1140 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root      1394  0.0  0.0   3412  1140 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root      1395  0.0  0.0   3412  1144 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1396  0.0  0.0   3412  1140 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sr1 (every 2 sec)
root      1397  0.0  0.0   3412  1140 ?        S    07:46   0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
root      1404  0.0  0.0   3412  1140 ?        S    07:46   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event0 /dev/input/event1
root      1429  0.0  0.0   1748   544 ?        S    07:46   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     1537  0.0  1.2 146608 25744 ?        Sl   07:46   0:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1538  0.0  0.0   1664   540 ?        S    07:46   0:00 logger -t mysqld -p daemon.error
root      1616  0.0  0.3   9696  6764 ?        S    07:46   0:00 ddclient - sleeping for 40 seconds
root      1660  0.0  0.0   2940   688 ?        Ss   07:46   0:00 /usr/bin/dirmngr --daemon --sh
gdm       1728  0.0  0.0   3380   708 ?        S    07:46   0:00 /usr/bin/dbus-launch --exit-with-session
root      1780  0.0  0.1   5124  2476 ?        S    07:46   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      2499  0.0  0.1  11952  3480 ?        S    07:46   0:00 /usr/lib/gdm/gdm-session-worker
ntp       2543  0.0  0.0   4360  1264 ?        Ss   07:46   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 115:127 -g
human     2571  0.0  0.3  25648  6600 ?        Ssl  07:46   0:00 gnome-session
human     2620  0.0  0.0   4916   616 ?        Ss   07:47   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
human     2623  0.0  0.0   3380   712 ?        S    07:47   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
human     2624  0.0  0.0   3104  1380 ?        Ss   07:47   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
human     2628  0.0  0.2  94228  4664 ?        Ssl  07:47   0:00 /usr/bin/pulseaudio --start
human     2631  0.0  0.1  10628  2904 ?        S    07:47   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
human     2633  0.0  0.2   7836  4836 ?        S    07:47   0:00 /usr/lib/libgconf2-4/gconfd-2
human     2642  0.0  0.4  96928  9220 ?        Ssl  07:47   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
119       2645  0.0  0.0   6564   896 ?        Ss   07:47   0:00 /usr/sbin/exim4 -bd -q30m
human     2651  0.0  0.1   5884  2208 ?        S    07:47   0:00 /usr/lib/gvfs/gvfsd
human     2663  0.0  0.1  40888  3112 ?        Sl   07:47   0:00 gnome-keyring-daemon --start
human     2667  0.0  0.3  17548  6328 ?        S    07:47   0:00 /usr/lib/notify-osd/notify-osd
human     2670  0.0  0.1  29788  2452 ?        Ssl  07:47   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/human/.gvfs
kernoops  2696  0.0  0.0   3340   908 ?        Ss   07:47   0:00 /usr/sbin/kerneloops
human     2698  0.0  0.3  22728  7252 ?        Ss   07:47   0:00 seahorse-daemon
human     2703  0.2  0.6 144760 13060 ?        Sl   07:47   0:04 metacity --sm-client-id 10768506579cf9b0d8125699875886077300000034240001
lastfm    2706  0.0  0.2   8748  4420 ?        S    07:47   0:00 /usr/bin/python /usr/bin/lastfmsubmitd
root      2751  0.0  0.0  14316   812 ?        Ss   07:47   0:00 /usr/sbin/nvtvd --quiet
proxy     2754  0.0  0.0   2152   376 ?        Ss   07:47   0:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid daemonise=true logFile=/var/log/polipo/polipo.log forbiddenFile=/etc/polipo/forbidden proxyOffline=false
root      2766  0.0  0.0   3984   632 ?        Ss   07:47   0:00 pure-ftpd (SERVER)                                                                                                          
root      2782  0.0  0.0   9120  1704 ?        Ss   07:47   0:00 /usr/sbin/nmbd -D
root      2786  0.0  0.1  15288  2968 ?        Ss   07:47   0:00 /usr/sbin/smbd -D
root      2806  0.0  0.0  15288  1336 ?        S    07:47   0:00 /usr/sbin/smbd -D
root      2820  0.0  0.0   2764  1088 ?        S<   07:47   0:00 udevd --daemon
root      2821  0.0  0.0   2764  1080 ?        S<   07:47   0:00 udevd --daemon
human     2823  0.2  1.0 151848 21788 ?        Rl   07:47   0:03 nautilus --sm-client-id 10768506579cf9b0d8125699875886158900000034240003 --sm-client-state-file /home/human/.config/session-state/nautilus-1257019585.desktop
human     2829  0.0  0.1  40716  3540 ?        Ssl  07:47   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
root      2858  0.0  0.0  11744  1600 ?        Ss   07:47   0:00 /usr/sbin/winbindd
root      2865  0.0  0.0  11744  1352 ?        S    07:47   0:00 /usr/sbin/winbindd
root      2900  0.0  0.0   2420   856 ?        Ss   07:47   0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive -inetd_compat -inetd_ipv6
root      2912  0.0  0.0   2132   808 ?        Ss   07:47   0:00 /usr/sbin/dhcdbd --system
root      2926  0.0  0.0   4056  1828 ?        Ss   07:47   0:00 /usr/sbin/bluetoothd
human     2949  0.0  0.5 209628 11544 ?        Sl   07:47   0:00 gnome-volume-control-applet
human     2953  0.0  0.2  16656  5636 ?        S    07:47   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
human     2957  0.0  0.0   4488  1540 ?        S    07:47   0:00 /bin/bash /home/human/.shellScripts/tor.sh 60
root      2963  0.0  0.1   5820  3468 ?        S    07:47   0:00 /usr/lib/policykit-1/polkitd
human     2966  0.0  0.7  29596 14456 ?        S    07:47   0:00 python /usr/share/system-config-printer/applet.py
human     2970  0.0  0.5  68492 11768 ?        S    07:47   0:00 update-notifier --startup-delay=60
human     2974  0.0  0.5  67628 11428 ?        Sl   07:47   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-6o1Gaw/ --sm-client-id 10f34b584086f1b2ac125701573968605100000025530027 --screen 0
human     2977  0.0  0.0   4492  1500 ?        S    07:47   0:00 /bin/bash /home/human/.shellScripts/Network/hamachi_vnc.sh
human     2979  0.0  0.6 105484 13644 ?        S    07:47   0:00 nm-applet --sm-disable
root      2984  0.0  0.1   5080  2860 ?        S    07:47   0:00 /usr/lib/devicekit-disks/devkit-disks-daemon
human     2985  0.0  0.3  17396  7208 ?        S    07:47   0:00 gnome-power-manager
human     2987  0.0  0.3  17256  6532 ?        S    07:47   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
root      2989  0.0  0.1   6872  2536 ?        Ss   07:47   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
human     2990  0.0  0.1  17540  2628 ?        Ss   07:47   0:00 gnome-screensaver
root      2991  0.0  0.0   4820   756 ?        S    07:47   0:01 devkit-disks-daemon: polling /dev/sdd /dev/sde /dev/sr1 /dev/sdf /dev/sdc /dev/sr0
human     3000  0.0  0.2  23248  4384 ?        Ss   07:47   0:00 /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
human     3002  0.0  0.1  22904  3248 ?        S    07:47   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
human     3006  0.0  0.1   6200  2856 ?        S    07:47   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
human     3070  0.0  0.1   6524  2200 ?        S    07:47   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
human     3106  0.0  0.5  44088 11176 ?        Sl   07:47   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=22
human     3141  0.0  0.4  79560  9088 ?        Sl   07:47   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
root      3142  0.0  0.3  32240  7732 ?        Ss   07:47   0:00 /usr/sbin/apache2 -k start
www-data  3148  0.0  0.1  32240  3904 ?        S    07:47   0:00 /usr/sbin/apache2 -k start
www-data  3149  0.0  0.1  32240  3904 ?        S    07:47   0:00 /usr/sbin/apache2 -k start
www-data  3150  0.0  0.1  32240  3904 ?        S    07:47   0:00 /usr/sbin/apache2 -k start
www-data  3151  0.0  0.1  32240  3904 ?        S    07:47   0:00 /usr/sbin/apache2 -k start
www-data  3153  0.0  0.1  32240  3904 ?        S    07:47   0:00 /usr/sbin/apache2 -k start
root      3240  0.0  0.0   1700   548 tty1     Ss+  07:47   0:00 /sbin/getty -8 38400 tty1
human     3254  0.0  0.1   5756  2252 ?        S    07:47   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
root      3259  0.0  0.0   1528   328 ?        S    07:47   0:00 tuncfg
human     3268  0.0  0.0   3144   824 ?        S    07:47   0:00 hamachi start
human     3270  0.0  0.0   1748   500 ?        S    07:47   0:00 /bin/sh ./rxvnc.sh
human     3273  0.0  0.1   8440  3448 ?        S    07:47   0:00 /usr/lib/indicator-messages/indicator-messages-service
human     3275  0.0  0.1  12064  3156 ?        S    07:47   0:00 /usr/lib/indicator-session/indicator-status-service
human     3277  0.0  0.1   6324  2100 ?        S    07:47   0:00 /usr/lib/indicator-session/indicator-users-service
human     3279  0.0  0.1   6892  2672 ?        S    07:47   0:00 /usr/lib/indicator-session/indicator-session-service
human     3300  0.1  0.5  14020 11300 ?        S    07:48   0:03 tor
human     3302  0.0  0.3  23548  8056 ?        S    07:48   0:00 x11vnc -rfbauth /home/human/.vnc/passwd -once -rfbport 5431 -shared -forever -afteraccept ./vnc_connected.sh
root      3350  0.0  0.0   1748   488 ?        S    07:51   0:00 /bin/sh -c nice run-parts --report /etc/cron.daily
root      3351  0.0  0.0   1664   588 ?        SN   07:51   0:00 run-parts --report /etc/cron.daily
root      3360  0.0  0.0   1748   548 ?        SN   07:51   0:00 /bin/sh /etc/cron.daily/apt
root      3587  0.0  0.0  11744  1228 ?        S    07:57   0:00 /usr/sbin/winbindd
root      3588  0.0  0.0  11836  1988 ?        S    07:57   0:00 /usr/sbin/winbindd
human     3670 45.9  1.2  89064 24884 ?        R    08:07   3:57 gnome-panel --replace
human     3674  0.0  0.5  71364 10736 ?        S    08:07   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=20
human     3679  0.0  0.5  71196 10676 ?        S    08:07   0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activate-iid=OAFIID:GNOME_DriveMountApplet_Factory --oaf-ior-fd=21
human     3681  0.0  0.5  72236 11484 ?        S    08:07   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=30
human     3683  0.0  0.6  73412 12972 ?        S    08:07   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=26
human     3701 12.9  3.7 341428 78300 ?        Sl   08:09   0:49 /usr/lib/firefox-3.5.5pre/firefox
human     3747  0.6  0.7  80636 14968 ?        Sl   08:10   0:02 gnome-terminal
human     3748  0.0  0.0   1900   708 ?        S    08:10   0:00 gnome-pty-helper
human     3749  0.1  0.2   7152  4404 pts/0    Ss   08:10   0:00 bash
human     3788  0.0  0.0   5520  1808 ?        S    08:10   0:00 /usr/lib/gvfs/gvfsd-metadata
root      3835  0.3  0.4  15340  9816 ?        S    08:13   0:00 /usr/bin/python /usr/sbin/aptd
human     3840  1.0  0.5  33072 11708 ?        RN   08:13   0:01 /usr/bin/python /usr/lib/update-notifier/apt-check
root      3846  6.9  1.5  50404 32488 ?        RN   08:14   0:06 /usr/bin/python /usr/sbin/update-apt-xapian-index -q
root      3847  0.0  0.0   1700   416 ?        SN   08:14   0:00 /bin/cat
human     3850  0.0  0.0   2640  1016 pts/0    R+   08:15   0:00 ps aux
```

gnome-panel output shows nothing strange:
```
** (gnome-panel:3651): DEBUG: Adding applet 0.
** (gnome-panel:3651): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3651): DEBUG: Adding applet 1.
** (gnome-panel:3651): DEBUG: Adding applet 2.
** (gnome-panel:3651): DEBUG: Adding applet 3.
** (gnome-panel:3651): DEBUG: Adding applet 4.
** (gnome-panel:3651): DEBUG: Adding applet 5.
** (gnome-panel:3651): DEBUG: Adding applet 6.
** (gnome-panel:3651): DEBUG: Adding applet 7.
** (gnome-panel:3651): DEBUG: Adding applet 8.
** (gnome-panel:3651): DEBUG: Adding applet 9.
** (gnome-panel:3651): DEBUG: Adding applet 10.
** (gnome-panel:3651): DEBUG: Adding applet 11.
** (gnome-panel:3651): DEBUG: Adding applet 12.
** (gnome-panel:3651): DEBUG: Adding applet 13.
** (gnome-panel:3651): DEBUG: Adding applet 14.
```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 00000000000ec000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fff8000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff0ffff (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 base 0E0000000 mask FFC000000 write-combining
[    0.000000]   7 base 0E0000000 mask FFC000000 write-combining
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 00000000000ec000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  modified: 000000007fff0000 - 000000007fff8000 (ACPI data)
[    0.000000]  modified: 000000007fff8000 - 0000000080000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffee0000 - 00000000fff0ffff (reserved)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37807000 - 37fef3b0
[    0.000000] Allocated new RAMDISK: 008ad000 - 010953b0
[    0.000000] Move RAMDISK from 0000000037807000 - 0000000037fef3af to 008ad000 - 010953af
[    0.000000] ACPI: RSDP 000fa120 00014 (v00 AMI   )
[    0.000000] ACPI: RSDT 7fff0000 0002C (v01 AMIINT SiS645XX 00000010 MSFT 0100000B)
[    0.000000] ACPI: FACP 7fff0030 00081 (v01 AMIINT SiS645XX 00000011 MSFT 0100000B)
[    0.000000] ACPI: DSDT 7fff0120 03545 (v01    SiS      645 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 7fff8000 00040
[    0.000000] ACPI: APIC 7fff00c0 00054 (v01 AMIINT SiS645XX 00001000 MSFT 0100000B)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac108]              BRK ==> [00008a9000 - 00008ac108]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 00010953b0]      NEW RAMDISK ==> [00008ad000 - 00010953b0]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00fb960] fb960
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fff0
[    0.000000] On node 0 totalpages: 524159
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1096200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294626 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 00000000000ec000
[    0.000000] PM: Registered nosave memory: 00000000000ec000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c20a0000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520063
[    0.000000] Kernel command line: root=UUID=5f025fc0-2b9b-42e5-b775-36fb8b23d269 ro splash vga=792 quiet 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10485120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fff0)
[    0.000000] Memory: 2052240k/2097088k available (4565k kernel code, 43492k reserved, 2143k data, 540k init, 1187784k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.961 MHz processor.
[    0.000043] Console: colour dummy device 80x25
[    0.000051] console [tty0] enabled
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.92 BogoMIPS (lpj=7999844)
[    0.004050] Security Framework initialized
[    0.004089] AppArmor: AppArmor initialized
[    0.004104] Mount-cache hash table entries: 512
[    0.004334] Initializing cgroup subsys ns
[    0.004343] Initializing cgroup subsys cpuacct
[    0.004352] Initializing cgroup subsys memory
[    0.004369] Initializing cgroup subsys freezer
[    0.004375] Initializing cgroup subsys net_cls
[    0.004404] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004412] CPU: L2 cache: 512K
[    0.004417] CPU: Hyper-Threading is disabled
[    0.004425] mce: CPU supports 4 MCE banks
[    0.004443] CPU0: Thermal monitoring enabled (TM1)
[    0.004461] Performance Counters: no PMU driver, software counters only.
[    0.004474] Checking 'hlt' instruction... OK.
[    0.021163] SMP alternatives: switching to UP code
[    0.032029] Freeing SMP alternatives: 19k freed
[    0.032057] ACPI: Core revision 20090521
[    0.044379] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085021] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[    0.088001] Brought up 1 CPUs
[    0.088001] Total of 1 processors activated (3999.92 BogoMIPS).
[    0.088001] CPU0 attaching NULL sched-domain.
[    0.088001] Booting paravirtualized kernel on bare hardware
[    0.088001] regulator: core version 0.5
[    0.088001] Time:  7:45:43  Date: 11/01/09
[    0.088001] NET: Registered protocol family 16
[    0.088001] EISA bus registered
[    0.088001] ACPI: bus type pci registered
[    0.088001] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[    0.088001] PCI: Using configuration type 1 for base access
[    0.089121] bio: create slab <bio-0> at 0
[    0.089879] ACPI: EC: Look up EC in DSDT
[    0.097894] ACPI: Interpreter enabled
[    0.097902] ACPI: (supports S0 S1 S3 S4 S5)
[    0.097953] ACPI: Using IOAPIC for interrupt routing
[    0.105647] ACPI: Power Resource [URP1] (off)
[    0.105697] ACPI: Power Resource [URP2] (off)
[    0.105745] ACPI: Power Resource [FDDP] (off)
[    0.105792] ACPI: Power Resource [LPTP] (off)
[    0.106065] ACPI: No dock devices found.
[    0.106716] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.106794] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.106990] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.107057] pci 0000:00:02.1: reg 20 io port: [0xc00-0xc1f]
[    0.107138] pci 0000:00:02.5: reg 20 io port: [0xff00-0xff0f]
[    0.107209] pci 0000:00:02.7: reg 10 io port: [0xdc00-0xdcff]
[    0.107221] pci 0000:00:02.7: reg 14 io port: [0xd800-0xd87f]
[    0.107281] pci 0000:00:02.7: supports D1 D2
[    0.107286] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.107295] pci 0000:00:02.7: PME# disabled
[    0.107333] pci 0000:00:03.0: reg 10 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.107409] pci 0000:00:03.1: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.107486] pci 0000:00:03.2: reg 10 32bit mmio: [0xdfffe000-0xdfffefff]
[    0.108009] pci 0000:00:03.3: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.108073] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.108081] pci 0000:00:03.3: PME# disabled
[    0.108149] pci 0000:00:09.0: reg 10 io port: [0xd400-0xd4ff]
[    0.108161] pci 0000:00:09.0: reg 14 32bit mmio: [0xdfffbc00-0xdfffbfff]
[    0.108198] pci 0000:00:09.0: reg 30 32bit mmio: [0xdffc0000-0xdffdffff]
[    0.108227] pci 0000:00:09.0: supports D1 D2
[    0.108231] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot
[    0.108239] pci 0000:00:09.0: PME# disabled
[    0.108341] pci 0000:01:00.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.108352] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.108382] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.108465] pci 0000:00:01.0: bridge 32bit mmio: [0xddd00000-0xdfefffff]
[    0.108474] pci 0000:00:01.0: bridge 32bit mmio pref: [0xcda00000-0xddbfffff]
[    0.108489] pci_bus 0000:00: on NUMA node 0
[    0.108498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.113220] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.113395] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.113568] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.113738] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.113910] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.114081] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.114256] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.114432] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.114764] SCSI subsystem initialized
[    0.114876] libata version 3.00 loaded.
[    0.115002] usbcore: registered new interface driver usbfs
[    0.115033] usbcore: registered new interface driver hub
[    0.115074] usbcore: registered new device driver usb
[    0.115296] ACPI: WMI: Mapper loaded
[    0.115301] PCI: Using ACPI for IRQ routing
[    0.115550] Bluetooth: Core ver 2.15
[    0.115602] NET: Registered protocol family 31
[    0.115606] Bluetooth: HCI device and connection manager initialized
[    0.115612] Bluetooth: HCI socket layer initialized
[    0.115616] NetLabel: Initializing
[    0.115620] NetLabel:  domain hash size = 128
[    0.115624] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.115647] NetLabel:  unlabeled traffic allowed by default
[    0.118136] pnp: PnP ACPI init
[    0.118175] ACPI: bus type pnp registered
[    0.123298] pnp: PnP ACPI: found 13 devices
[    0.123304] ACPI: ACPI bus type pnp unregistered
[    0.123311] PnPBIOS: Disabled by ACPI PNP
[    0.123333] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.123340] system 00:01: ioport range 0x480-0x48f has been reserved
[    0.123346] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.123352] system 00:01: ioport range 0xc00-0xc1f has been reserved
[    0.123359] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[    0.123367] system 00:01: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.158182] AppArmor: AppArmor Filesystem Enabled
[    0.158215] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.158220] pci 0000:00:01.0:   IO window: disabled
[    0.158230] pci 0000:00:01.0:   MEM window: 0xddd00000-0xdfefffff
[    0.158239] pci 0000:00:01.0:   PREFETCH window: 0xcda00000-0xddbfffff
[    0.158261] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.158267] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.158273] pci_bus 0000:01: resource 1 mem: [0xddd00000-0xdfefffff]
[    0.158280] pci_bus 0000:01: resource 2 pref mem [0xcda00000-0xddbfffff]
[    0.158339] NET: Registered protocol family 2
[    0.158496] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.159031] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.160178] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.160792] TCP: Hash tables configured (established 131072 bind 65536)
[    0.160803] TCP reno registered
[    0.161004] NET: Registered protocol family 1
[    0.161124] Trying to unpack rootfs image as initramfs...
[    0.503940] Freeing initrd memory: 8096k freed
[    0.512870] cpufreq-nforce2: No nForce2 chipset.
[    0.512925] Scanning for low memory corruption every 60 seconds
[    0.513119] audit: initializing netlink socket (disabled)
[    0.513151] type=2000 audit(1257061543.512:1): initialized
[    0.524621] highmem bounce pool size: 64 pages
[    0.524632] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.526861] VFS: Disk quotas dquot_6.5.2
[    0.526957] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.527867] fuse init (API version 7.12)
[    0.528005] msgmni has been set to 1706
[    0.528347] alg: No test for stdrng (krng)
[    0.528370] io scheduler noop registered
[    0.528375] io scheduler anticipatory registered
[    0.528380] io scheduler deadline registered
[    0.528462] io scheduler cfq registered (default)
[    2.640387] pci 0000:01:00.0: Boot video device
[    2.640545] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.640590] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.640808] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.640816] ACPI: Power Button [PWRF]
[    2.640894] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.640899] ACPI: Power Button [PWRB]
[    2.641230] processor LNXCPU:00: registered as cooling_device0
[    2.644509] isapnp: Scanning for PnP cards...
[    2.712372] Switched to high resolution mode on CPU 0
[    2.998428] isapnp: No Plug & Play device found
[    3.000507] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.000643] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.000761] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.001214] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.001380] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.003011] brd: module loaded
[    3.003718] loop: module loaded
[    3.003868] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    3.004885] pata_sis 0000:00:02.5: version 0.5.2
[    3.005133] scsi0 : pata_sis
[    3.005297] scsi1 : pata_sis
[    3.006605] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.006611] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.007250] Fixed MDIO Bus: probed
[    3.007317] PPP generic driver version 2.4.2
[    3.007486] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.007526]   alloc irq_desc for 23 on node -1
[    3.007531]   alloc kstat_irqs on node -1
[    3.007544] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.007569] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.007664] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    3.007713] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    3.007739] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffff000
[    3.016014] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    3.016159] usb usb1: configuration #1 chosen from 1 choice
[    3.016212] hub 1-0:1.0: USB hub found
[    3.016228] hub 1-0:1.0: 6 ports detected
[    3.016337] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.016376]   alloc irq_desc for 20 on node -1
[    3.016381]   alloc kstat_irqs on node -1
[    3.016391] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.016413] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    3.016479] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    3.016518] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfffc000
[    3.074114] usb usb2: configuration #1 chosen from 1 choice
[    3.074161] hub 2-0:1.0: USB hub found
[    3.074175] hub 2-0:1.0: 2 ports detected
[    3.074255]   alloc irq_desc for 21 on node -1
[    3.074260]   alloc kstat_irqs on node -1
[    3.074269] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.074285] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.074352] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    3.074383] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffd000
[    3.130106] usb usb3: configuration #1 chosen from 1 choice
[    3.130153] hub 3-0:1.0: USB hub found
[    3.130174] hub 3-0:1.0: 2 ports detected
[    3.130247]   alloc irq_desc for 22 on node -1
[    3.130251]   alloc kstat_irqs on node -1
[    3.130261] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.130277] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    3.130336] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    3.130369] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfffe000
[    3.186100] usb usb4: configuration #1 chosen from 1 choice
[    3.186152] hub 4-0:1.0: USB hub found
[    3.186167] hub 4-0:1.0: 2 ports detected
[    3.186245] uhci_hcd: USB Universal Host Controller Interface driver
[    3.186393] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.186398] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.186500] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.186627] mice: PS/2 mouse device common for all mice
[    3.186777] rtc_cmos 00:03: RTC can wake from S4
[    3.186837] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.186867] rtc0: alarms up to one month, 114 bytes nvram
[    3.187040] device-mapper: uevent: version 1.0.3
[    3.187202] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    3.187329] device-mapper: multipath: version 1.1.0 loaded
[    3.187335] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.187524] EISA: Probing bus 0 at eisa.0
[    3.187565] EISA: Detected 0 cards.
[    3.187637] cpuidle: using governor ladder
[    3.187642] cpuidle: using governor menu
[    3.188463] TCP cubic registered
[    3.188676] NET: Registered protocol family 10
[    3.189342] lo: Disabled Privacy Extensions
[    3.189855] NET: Registered protocol family 17
[    3.189892] Bluetooth: L2CAP ver 2.13
[    3.189896] Bluetooth: L2CAP socket layer initialized
[    3.189902] Bluetooth: SCO (Voice Link) ver 0.6
[    3.189906] Bluetooth: SCO socket layer initialized
[    3.189960] Bluetooth: RFCOMM TTY layer initialized
[    3.189966] Bluetooth: RFCOMM socket layer initialized
[    3.189970] Bluetooth: RFCOMM ver 1.11
[    3.190028] Using IPI No-Shortcut mode
[    3.190156] PM: Resume from disk failed.
[    3.190177] registered taskstats version 1
[    3.190340]   Magic number: 1:82:773
[    3.190353] hub 2-0:1.0: hash matches
[    3.190449] rtc_cmos 00:03: setting system clock to 2009-11-01 07:45:46 UTC (1257061546)
[    3.190455] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.190459] EDD information not available.
[    3.204879] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.292739] ata1.00: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[    3.292745] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.293105] ata1.01: ATA-6: ST3160023A, 8.01, max UDMA/100
[    3.293111] ata1.01: 312581808 sectors, multi 16: LBA48 
[    3.359212] ata1.00: configured for UDMA/100
[    3.372427] ata1.01: configured for UDMA/100
[    3.372608] scsi 0:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[    3.372821] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.372947] scsi 0:0:1:0: Direct-Access     ATA      ST3160023A       8.01 PQ: 0 ANSI: 5
[    3.373107] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    3.373176] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.373255] sd 0:0:0:0: [sda] Write Protect is off
[    3.373261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.373301] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.373516]  sda: sda1 sda2
[    3.415725] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.415761] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.415834] sd 0:0:1:0: [sdb] Write Protect is off
[    3.415840] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    3.415879] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.416083]  sdb: sdb1 sdb2 sdb4
[    3.445464] sd 0:0:1:0: [sdb] Attached SCSI disk
[    3.496027] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    3.544360] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H20L, 1.00, max UDMA/33
[    3.544420] ata2.01: ATAPI: ATAPI-CD ROM-DRIVE-52MAX, VER 52GV, max UDMA/33
[    3.560386] ata2.00: configured for UDMA/33
[    3.568318] ata2.01: configured for UDMA/33
[    3.571310] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H20L 1.00 PQ: 0 ANSI: 5
[    3.576463] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.576470] Uniform CD-ROM driver Revision: 3.20
[    3.576617] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.576716] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    3.577233] scsi 1:0:1:0: CD-ROM            ATAPI-CD ROM-DRIVE-52MAX  52GV PQ: 0 ANSI: 5
[    3.579647] sr1: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[    3.579778] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    3.579857] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    3.579894] Freeing unused kernel memory: 540k freed
[    3.580540] Write protecting the kernel text: 4568k
[    3.580583] Write protecting the kernel read-only data: 1836k
[    3.704209] usb 1-6: configuration #1 chosen from 1 choice
[    3.884855] Linux agpgart interface v0.103
[    3.890166] agpgart-sis 0000:00:00.0: SiS chipset [1039/0646]
[    3.897520] Floppy drive(s): fd0 is 1.44M
[    3.901967] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[    3.916047] FDC 0 is a post-1991 82077
[    3.955773] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[    3.956119]   alloc irq_desc for 16 on node -1
[    3.956125]   alloc kstat_irqs on node -1
[    3.956138] tulip 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.956779] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
[    4.079240] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    4.083833] eth0: ADMtek Comet rev 17 at Port 0xd400, 00:08:a1:62:e2:fb, IRQ 16.
[    4.127733] Initializing USB Mass Storage driver...
[    4.127904] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.128077] usbcore: registered new interface driver usb-storage
[    4.128084] USB Mass Storage support registered.
[    4.129731] usb-storage: device found at 4
[    4.129736] usb-storage: waiting for device to settle before scanning
[    4.284367] usb 3-1: configuration #1 chosen from 1 choice
[    4.539233] vesafb: framebuffer at 0xd0000000, mapped to 0xf8100000, using 6144k, total 65536k
[    4.539241] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[    4.539246] vesafb: protected mode interface info at c000:f320
[    4.539251] vesafb: pmi: set display start = c00cf356, set palette = c00cf3c0
[    4.539255] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    4.539296] vesafb: scrolling: redraw
[    4.539304] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.539395] fb0: VESA VGA frame buffer device
[    4.550191] Console: switching to colour frame buffer device 128x48
[    4.590395] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    4.912798] usb 4-1: configuration #1 chosen from 1 choice
[    4.930771] usbcore: registered new interface driver hiddev
[    4.937829] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:03.2/usb4/4-1/4-1:1.0/input/input4
[    4.937988] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.2-1/input0
[    4.938021] usbcore: registered new interface driver usbhid
[    4.938028] usbhid: v2.6:USB HID core driver
[    4.953159] xor: automatically using best checksumming function: pIII_sse
[    4.972010]    pIII_sse  :  2540.000 MB/sec
[    4.972015] xor: using function: pIII_sse (2540.000 MB/sec)
[    5.000973] device-mapper: dm-raid45: initialized v0.2594b
[    5.287510] PM: Starting manual resume from disk
[    5.287518] PM: Resume from partition 8:20
[    5.287522] PM: Checking hibernation image.
[    5.287766] PM: Resume from disk failed.
[    5.299210] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[    5.299219] PM: Basic memory bitmaps created
[    5.315356] PM: Basic memory bitmaps freed
[    5.354706] kjournald starting.  Commit interval 5 seconds
[    5.354727] EXT3-fs: mounted filesystem with writeback data mode.
[    6.140302] type=1505 audit(1257061549.449:2): operation="profile_load" pid=412 name=/usr/share/gdm/guest-session/Xsession
[    6.161878] type=1505 audit(1257061549.469:3): operation="profile_load" pid=413 name=/sbin/dhclient3
[    6.162711] type=1505 audit(1257061549.469:4): operation="profile_load" pid=413 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.163167] type=1505 audit(1257061549.469:5): operation="profile_load" pid=413 name=/usr/lib/connman/scripts/dhclient-script
[    6.193537] type=1505 audit(1257061549.501:6): operation="profile_load" pid=414 name=/usr/bin/evince
[    6.206755] type=1505 audit(1257061549.513:7): operation="profile_load" pid=414 name=/usr/bin/evince-previewer
[    6.214484] type=1505 audit(1257061549.521:8): operation="profile_load" pid=414 name=/usr/bin/evince-thumbnailer
[    6.237329] type=1505 audit(1257061549.545:9): operation="profile_load" pid=416 name=/usr/lib/cups/backend/cups-pdf
[    6.238298] type=1505 audit(1257061549.545:10): operation="profile_load" pid=416 name=/usr/sbin/cupsd
[    6.254594] type=1505 audit(1257061549.561:11): operation="profile_load" pid=417 name=/usr/sbin/mysqld
[    8.181845] Adding 5783392k swap on /dev/sdb4.  Priority:-1 extents:1 across:5783392k 
[    9.128316] usb-storage: device scan complete
[    9.134304] scsi 2:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    9.266662] udev: starting version 147
[    9.727150] EXT3 FS on sdb1, internal journal
[   10.106434] scsi 2:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   10.116961] scsi 2:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   10.123970] scsi 2:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   10.124753] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   10.124914] sd 2:0:0:1: Attached scsi generic sg5 type 0
[   10.125071] sd 2:0:0:2: Attached scsi generic sg6 type 0
[   10.125222] sd 2:0:0:3: Attached scsi generic sg7 type 0
[   10.140838] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[   10.144437] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[   10.172607] sd 2:0:0:2: [sde] Attached SCSI removable disk
[   10.175427] sd 2:0:0:3: [sdf] Attached SCSI removable disk
[   10.299365] lp: driver loaded but no devices found
[   10.741185] parport_pc 00:0a: reported by Plug and Play ACPI
[   10.741238] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   10.802055] ppdev: user-space parallel port driver
[   10.852468] lp0: using parport0 (interrupt-driven).
[   10.883644] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.954771] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   10.954783] ACPI: I/O resource 0000:00:02.1 [0xc00-0xc1f] conflicts with ACPI region SMRG [0xc00-0xc1f]
[   10.954790] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.954803] sis96x_smbus: probe of 0000:00:02.1 failed with error -16
[   10.972443] gameport: NS558 PnP Gameport is pnp00:0b/gameport0, io 0x200, speed 764kHz
[   11.155571] Linux video capture interface: v2.00
[   11.511794] nvidia: module license 'NVIDIA' taints kernel.
[   11.511802] Disabling lock debugging due to kernel taint
[   11.769630] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.769987] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   11.980753] gspca: main v2.6.0 registered
[   12.149989] gspca: probing 046d:092f
[   12.268053] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.362659] gspca: probe ok
[   12.362699] usbcore: registered new interface driver spca561
[   12.362705] spca561: registered
[   12.656376]   alloc irq_desc for 18 on node -1
[   12.656383]   alloc kstat_irqs on node -1
[   12.656396] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   12.980029] intel8x0_measure_ac97_clock: measured 52821 usecs (2541 samples)
[   12.980036] intel8x0: clocking to 48000
[   15.680983] EXT4-fs (sdb2): barriers enabled
[   15.686321] kjournald2 starting: pid 809, dev sdb2:8, commit interval 5 seconds
[   15.686604] EXT4-fs (sdb2): internal journal on sdb2:8
[   15.686610] EXT4-fs (sdb2): delayed allocation enabled
[   15.686616] EXT4-fs: file extents enabled
[   15.687016] EXT4-fs: mballoc enabled
[   15.687041] EXT4-fs (sdb2): mounted filesystem with ordered data mode
[   17.751899] __ratelimit: 9 callbacks suppressed
[   17.751907] type=1505 audit(1257054361.057:15): operation="profile_replace" pid=937 name=/usr/share/gdm/guest-session/Xsession
[   17.755363] type=1505 audit(1257054361.061:16): operation="profile_replace" pid=938 name=/sbin/dhclient3
[   17.756271] type=1505 audit(1257054361.065:17): operation="profile_replace" pid=938 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.756751] type=1505 audit(1257054361.065:18): operation="profile_replace" pid=938 name=/usr/lib/connman/scripts/dhclient-script
[   17.765009] type=1505 audit(1257054361.073:19): operation="profile_replace" pid=939 name=/usr/bin/evince
[   17.778712] type=1505 audit(1257054361.085:20): operation="profile_replace" pid=939 name=/usr/bin/evince-previewer
[   17.787471] type=1505 audit(1257054361.093:21): operation="profile_replace" pid=939 name=/usr/bin/evince-thumbnailer
[   17.801041] type=1505 audit(1257054361.109:22): operation="profile_replace" pid=941 name=/usr/lib/cups/backend/cups-pdf
[   17.802020] type=1505 audit(1257054361.109:23): operation="profile_replace" pid=941 name=/usr/sbin/cupsd
[   17.806417] type=1505 audit(1257054361.113:24): operation="profile_replace" pid=942 name=/usr/sbin/mysqld
[   26.817840] 0000:00:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   26.817856] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   28.010255] __ratelimit: 9 callbacks suppressed
[   28.010262] type=1503 audit(1257054371.319:28): operation="open" pid=1372 parent=1371 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   28.935551] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   28.935580] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode
[   28.935632] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   29.518789] type=1503 audit(1257054372.825:29): operation="open" pid=1422 parent=1421 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   30.280942] type=1503 audit(1257054373.589:30): operation="open" pid=1537 parent=1429 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   30.920904] type=1503 audit(1257054374.229:31): operation="open" pid=1543 parent=1542 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.075069] type=1503 audit(1257054375.381:32): operation="open" pid=1565 parent=1564 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.158780] type=1503 audit(1257054375.465:33): operation="open" pid=1576 parent=1575 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.320029] eth0: no IPv6 routers present
[   85.525782] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   85.525789] vboxdrv: Successfully done.
[   85.525793] vboxdrv: Found 1 processor cores.
[   85.525988] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   85.525992] vboxdrv: Successfully loaded version 3.0.8 (interface 0x000e0000).
[   89.480250] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   89.480258] Bluetooth: BNEP filters: protocol multicast
[   89.720679] Bridge firewalling registered
[  106.104196] tun: Universal TUN/TAP device driver, 1.6
[  106.104204] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
```
cat ~/.xsession-errors:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.

(gnome-settings-daemon:2642): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2642): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
GNOME_KEYRING_SOCKET=/tmp/keyring-K7kWpm/socket
SSH_AUTH_SOCK=/tmp/keyring-K7kWpm/socket.ssh
GNOME_KEYRING_PID=2663
Unable to find a synaptics device.
** (gnome-panel:2739): DEBUG: Adding applet 0.
** (gnome-panel:2739): DEBUG: Initialized Panel Applet Signaler.

(polkit-gnome-authentication-agent-1:2953): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2953): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
Tor Starting!
gnome-session[2571]: WARNING: Could not launch application '10f34b584086f1b2ac125701577648028000000025530039.desktop': Unable to start application: Failed to execute child process "evolution-exchange-storage" (No such file or directory)
gnome-session[2571]: WARNING: Could not launch application '10f34b584086f1b2ac125701576864820600000025530038.desktop': Unable to start application: Failed to execute child process "indicator-applet-session" (No such file or directory)
** (gnome-panel:2739): DEBUG: Adding applet 1.
** (gnome-panel:2739): DEBUG: Adding applet 2.
Failure: Module initalization failed
** (gnome-panel:2739): DEBUG: Adding applet 3.

(nautilus:2823): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** (gnome-panel:2739): DEBUG: Adding applet 4.
Waiting 60 seconds...
** (gnome-panel:2739): DEBUG: Adding applet 5.
evolution-alarm-notify-Message: Setting timeout for 65563 1257120000 1257054437
evolution-alarm-notify-Message:  Mon Nov  2 02:00:00 2009

evolution-alarm-notify-Message:  Sun Nov  1 07:47:17 2009

** (gnome-panel:2739): DEBUG: Adding applet 6.
** (gnome-panel:2739): DEBUG: Adding applet 7.
** (gnome-panel:2739): DEBUG: Adding applet 8.
** (gnome-panel:2739): DEBUG: Adding applet 9.
Initializing nautilus-gdu extension

** (nautilus:2823): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2823): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2823): WARNING **: No marshaller for signature of signal 'ShareCreateError'

(nautilus:3231): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': libx264.so.67: cannot open shared object file: No such file or directory

(nautilus:3231): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstx264.so': libx264.so.67: cannot open shared object file: No such file or directory
[sudo] password for human: 
** (gnome-panel:2739): DEBUG: Adding applet 10.
** (gnome-panel:2739): DEBUG: Adding applet 11.
** (gnome-panel:2739): DEBUG: Adding applet 12.
** (gnome-panel:2739): DEBUG: Adding applet 13.
** (gnome-panel:2739): DEBUG: Adding applet 14.
evolution-alarm-notify-Message: Setting timeout for 65538 1257120000 1257054462
evolution-alarm-notify-Message:  Mon Nov  2 02:00:00 2009

evolution-alarm-notify-Message:  Sun Nov  1 07:47:42 2009


(evolution-alarm-notify:2954): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running…
```

Killing gnome-panel causes X to restart. I tried rebooting, shutting down X, remembering a new gnome-session (which probably doesn't work because I remember it with the problem), no effect!

My videocard is NVidia MX-440, I am using the proprietrary driver and I do not have compiz. My processor is Intel Pentium 4 Single Core on 2.0 GHz

Help pleeease! :(

---

### Post by DexterLB on 2009-11-01
Edit: The problem is caused by the applet 'Notification Area'. Removing it causes the CPU usage to go back to 0%.

---

### Post by DexterLB on 2009-11-01
Temporary workaround is to put the notification area on an autohiding panel. When it's hidden the cpu usage is low. But that's not a solution!

Bumpy Bumpy

---

### Post by javabean420 on 2009-11-01
do you have a reason to keep it upgraded???

if not, remove it then do a fresh install (ie not upgrade)

another thing to try is read what it would install if you do apt-get install ubuntu-desktop maybe notification area from your jaunty didn't get removed or upgraded right try removing it "apt-get remove notification-daemon" then try the "apt-get install ubuntu-desktop" again

ubuntu-desktop is the "meta-package" that installs "everything" that is on a fresh install of the standard ubuntu install..... but installing it like that "shouldn't" cause any of the other things to malfunction

---

### Post by DexterLB on 2009-11-02
Uninstalling notification daemon did not remove ubuntu-desktop. Turns out that ubuntu-desktop doesn't depend on notification daemon. Uninstalling it doesn't affect the notification area's appearance, not it's CPU usage. I tried restarting gnome-panel and rebooting the computer. problem still exists

---

### Post by Icebear on 2009-11-12
look at the following link
[http://ubuntuforums.org/showthread.php?t=1306735](http://ubuntuforums.org/showthread.php?t=1306735)

I had luck with both -sudo killall udevd
                     -or having a cd in the drive

---

