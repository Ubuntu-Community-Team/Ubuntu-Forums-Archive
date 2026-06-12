---
title: "Concern about Duplicate Processes"
date: 2009-12-27
forum: General Help
---

### Post by crazyness003 on 2009-12-27
Hi All.
Just to state: Im running Ubuntu 9.10 x86_64 kernel 2.6.31-17-generic.

Using HTOP, I recently discovered that i have over 250 total processes on my machine (although CONKY reports 350). When I investigated a little further, I noticed that some processes were duplicated or listed more than once ('/usr/sbin/console-kit-daemon' is listed 64 times!).

I also have a lot of google-chrome listings (some for extensions, 4  of them are part of the renderer, 2 as '--type=zygote' [???] and 15 more just plain '/opt/google/chrome/google-chrome')

I'm not sure if this is a normal occurance (or even if /opt is the normal place Google Chrome installs to)

If anyone can give me a heads up as to what is going on, or how to fix this, if it is a bad thing. Over 1gb of memory is being used and all I have actively running is Chrome, Conky and some applets.

Also, Xorg is shooting my CPU usage up sometimes (probably unrelated)

Sorry for the bizarre post and Thanks in advance.

If anyone can tell me how to list all of my processes and post them here, I'm more than willing to do it.

---

### Post by alphabravoxxx on 2009-12-27
Can you post ps aux?

---

### Post by crazyness003 on 2009-12-27
```
selmani@main-pc:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  19444  1660 ?        Ss   Dec25   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Dec25   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Dec25   0:18 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Dec25   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   Dec25   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Dec25   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   Dec25   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   Dec25   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   Dec25   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   Dec25   0:33 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   Dec25   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   Dec25   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    Dec25   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    Dec25   0:03 [pdflush]
root        25  0.0  0.0      0     0 ?        S    Dec25   0:02 [pdflush]
root        26  0.0  0.0      0     0 ?        S<   Dec25   0:34 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   Dec25   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   Dec25   0:00 [crypto/0]
root        38  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_1]
root        42  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_2]
root        43  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_3]
root        46  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_4]
root        48  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_5]
root        51  0.0  0.0      0     0 ?        S<   Dec25   1:15 [scsi_eh_6]
root        53  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_7]
root        61  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kstriped]
root        62  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kmpathd/0]
root        63  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kmpath_handlerd]
root        64  0.0  0.0      0     0 ?        S<   Dec25   0:00 [ksnapd]
root        65  0.0  0.0      0     0 ?        S<   Dec25   0:11 [kondemand/0]
root        66  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kconservative/0]
root        67  0.0  0.0      0     0 ?        S<   Dec25   0:00 [krfcommd]
root       243  0.0  0.0      0     0 ?        S<   Dec25   0:00 [khpsbpkt]
root       324  0.0  0.0      0     0 ?        S<   Dec25   0:00 [knodemgrd_0]
root       359  0.0  0.0      0     0 ?        S<   Dec25   0:00 [usbhid_resumer]
root       365  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_8]
root       366  0.0  0.0      0     0 ?        S<   Dec25   0:34 [usb-storage]
root       368  0.0  0.0      0     0 ?        S<   Dec25   0:00 [scsi_eh_9]
root       369  0.0  0.0      0     0 ?        S<   Dec25   0:17 [usb-storage]
root       503  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kjournald]
root       565  0.0  0.0  12904   768 ?        S    Dec25   0:00 upstart-udev-bridge --daemon
root       592  0.0  0.0  17716   388 ?        S<s  Dec25   0:00 udevd --daemon
root       892  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kjournald]
root       926  0.0  0.0      0     0 ?        S<   Dec25   0:00 [edac-poller]
root       936  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kpsmoused]
root       947  0.0  0.0      0     0 ?        S<   Dec25   0:01 [kjournald]
root       991  0.0  0.0   8192   484 ?        Ss   Dec25   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog    1005  0.0  0.0  60984  1212 ?        Sl   Dec25   0:00 rsyslogd -c4
102       1025  0.0  0.0  24908  2084 ?        Ss   Dec25   0:10 dbus-daemon --system --fork
avahi     1040  0.0  0.0  31916  1324 ?        Ss   Dec25   0:01 avahi-daemon: running [main-pc.local]
avahi     1041  0.0  0.0  31760   252 ?        Ss   Dec25   0:00 avahi-daemon: chroot helper
103       1043  0.0  0.0  34296  2664 ?        Ss   Dec25   0:02 hald --daemon=yes
root      1044  0.0  0.1  74924  3124 ?        Ss   Dec25   0:16 gdm-binary
root      1056  0.0  0.0  54844  2632 ?        Ssl  Dec25   0:00 /usr/sbin/console-kit-daemon
root      1061  0.0  0.0  89392  2804 ?        Ssl  Dec25   0:00 NetworkManager
root      1129  0.0  0.0  51476  1776 ?        S    Dec25   0:00 /usr/sbin/modem-manager
root      1138  0.0  0.0  20184  1024 ?        S    Dec25   0:00 hald-runner
root      1199  0.0  0.0  28216   880 ?        S    Dec25   0:00 /sbin/wpa_supplicant -u -s
root      1202  0.0  0.0   6464   632 ?        S    Dec25   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/n
root      1246  0.0  0.0  22180  1064 ?        S    Dec25   0:00 hald-addon-input: Listening on /dev/input/event
root      1249  0.0  0.0  22180  1112 ?        S    Dec25   0:00 hald-addon-storage: no polling on /dev/fd0 beca
root      1250  0.0  0.0  22180  1116 ?        S    Dec25   0:02 hald-addon-storage: polling /dev/sde (every 2 s
root      1252  0.0  0.0  22180  1112 ?        S    Dec25   0:02 hald-addon-storage: polling /dev/sdi (every 2 s
root      1253  0.0  0.0  22180  1112 ?        S    Dec25   0:01 hald-addon-storage: polling /dev/sdf (every 2 s
root      1254  0.0  0.0  22180  1112 ?        S    Dec25   0:01 hald-addon-storage: polling /dev/sdg (every 2 s
root      1255  0.0  0.0  22180  1108 ?        S    Dec25   0:01 hald-addon-storage: polling /dev/sdh (every 2 s
root      1256  0.0  0.0  22180  1116 ?        S    Dec25   0:06 hald-addon-storage: polling /dev/sr0 (every 2 s
root      1257  0.0  0.0  22180  1116 ?        S    Dec25   0:06 hald-addon-storage: polling /dev/sr1 (every 2 s
root      1274  0.0  0.0  22188  1056 ?        S    Dec25   0:00 /usr/lib/hal/hald-addon-cpufreq
103       1276  0.0  0.0  26080   976 ?        S    Dec25   0:00 hald-addon-acpi: listening on acpid socket /var
root      1313  0.0  0.0   5988   476 tty4     Ss+  Dec25   0:00 /sbin/getty -8 38400 tty4
root      1316  0.0  0.0   5988   476 tty5     Ss+  Dec25   0:00 /sbin/getty -8 38400 tty5
root      1327  0.0  0.0   5988   476 tty2     Ss+  Dec25   0:00 /sbin/getty -8 38400 tty2
root      1328  0.0  0.0   5988   476 tty3     Ss+  Dec25   0:00 /sbin/getty -8 38400 tty3
root      1330  0.0  0.0  65004  1928 tty6     Ss   Dec25   0:00 /bin/login --        
root      1333  0.0  0.0   4352   616 ?        Ss   Dec25   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.soc
root      1335  0.0  0.0  18708   748 ?        Ss   Dec25   0:00 cron
daemon    1336  0.0  0.0  16512   304 ?        Ss   Dec25   0:00 atd
root      1860  0.0  0.0  73904   748 ?        Ss   Dec25   0:00 /usr/sbin/sensord -f daemon
tenshi    1895  0.0  0.3  53320 10604 ?        Ss   Dec25   0:50 /usr/bin/perl /usr/sbin/tenshi -P /var/run/tens
tenshi    1896  0.0  0.0   8192   680 ?        S    Dec25   0:05 /usr/bin/tail -q --follow=name --retry -n 0 /va
root      1968  0.0  0.0  63568  1312 ?        Ss   Dec25   0:00 /usr/sbin/winbindd
114       1981  0.0  0.0  27720   712 ?        Ss   Dec25   0:00 /usr/bin/xfs -daemon -user debian-xfs -droppriv
root      1990  0.0  0.0  63468   664 ?        S    Dec25   0:00 /usr/sbin/winbindd
root      2018  0.0  0.0  75376  2712 ?        Ss   Dec25   0:01 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      2212  0.0  0.0  47024  2160 ?        S    Dec25   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      2301  0.0  0.1  51132  3196 ?        S    Dec25   0:33 /usr/lib/devicekit-disks/devkit-disks-daemon
root      2302  0.0  0.0  42180   584 ?        S    Dec25   1:20 devkit-disks-daemon: polling /dev/sde /dev/sdi 
root      2353  0.0  0.1  59208  3736 ?        S    Dec25   0:00 /usr/lib/policykit-1/polkitd
selmani   2517  0.0  0.0   4004   500 ?        S    Dec25   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchd
selmani   2544  0.0  0.0   4004   220 ?        S    Dec25   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchd
selmani   2545  0.0  0.1  71948  3544 ?        Sl   Dec25   0:04 /usr/lib/erlang/erts-5.7.2/bin/beam -Bd -K true
selmani   2550  0.0  0.0   3772   416 ?        Ss   Dec25   0:00 heart -pid 2545 -ht 11
selmani   2555  0.0  0.0  74448   988 ?        Ss   Dec25   0:00 /usr/lib/couchdb/bin/couchjs /usr/share/couchdb
selmani   2597  0.0  0.1 390352  5048 ?        Sl   Dec25   0:00 /usr/lib/evolution/evolution-data-server-2.28 -
root      2633  6.2  0.0  15224  1052 ?        Ss   Dec25 152:06 /sbin/mount.ntfs /dev/sda1 /media/g15 -o rw,nos
root      2656  0.0  0.0  15228   832 ?        Ss   Dec25   0:01 /sbin/mount.ntfs /dev/sdd1 /media/d300 -o rw,no
root      2672  0.6  0.6  33972 19856 ?        Ss   Dec25  15:00 /sbin/mount.ntfs /dev/sdb1 /media/e500 -o rw,no
root      2706  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kjournald]
timidity  2776  0.0  0.0 104136  1620 ?        S    Dec25   0:00 /usr/bin/timidity -Os -iAD
root      2781  0.0  0.0   5988   476 tty1     Ss+  Dec25   0:00 /sbin/getty -8 38400 tty1
root      2788  0.0  0.0  72112  2588 ?        S    Dec25   0:00 /usr/bin/python /usr/lib/system-service/system-
root      2846  0.0  0.0      0     0 ?        S<   Dec25   0:00 [kjournald]
selmani   2882  0.0  0.1  21996  4764 tty6     S+   13:32   0:00 -bash
selmani   3046  2.5  2.2 590912 68552 ?        Sl   13:40   2:17 /opt/google/chrome/google-chrome
selmani   3049  0.0  0.1 177784  5808 ?        S    13:40   0:02 /opt/google/chrome/google-chrome
selmani   3051  0.0  0.2 188212  8800 ?        S    13:40   0:00 /opt/google/chrome/chrome --type=zygote
selmani   3067  0.0  0.4 782060 14376 ?        Sl   13:40   0:00 /opt/google/chrome/chrome --type=extension --la
selmani   3087  0.0  0.5 782536 16480 ?        Sl   13:40   0:00 /opt/google/chrome/chrome --type=extension --la
selmani   3091  0.0  0.4 781236 13728 ?        Sl   13:40   0:00 /opt/google/chrome/chrome --type=extension --la
selmani   3219  0.0  0.9 348020 28860 ?        Sl   13:47   0:00 /usr/bin/python /usr/bin/fusion-icon --no-start
selmani   3281  1.6  2.8 914624 88500 ?        Sl   13:48   1:20 /opt/google/chrome/chrome --type=renderer --lan
selmani   3298  0.3  0.9 880872 29300 ?        SNl  13:48   0:16 /opt/google/chrome/chrome --type=renderer --lan
selmani   3495  1.4  0.3 142600  9324 ?        S    14:12   0:52 conky
selmani   3579  0.0  0.0   4004   556 ?        Ss   14:21   0:00 /bin/sh -c gnome-terminal
selmani   3580  0.1  0.6 317288 19436 ?        Rl   14:21   0:05 gnome-terminal
selmani   3581  0.0  0.0  14396   780 ?        S    14:21   0:00 gnome-pty-helper
selmani   3582  0.0  0.1  21968  4724 pts/0    Ss   14:21   0:00 bash
root      3747  0.0  0.0  26156   760 ?        S    Dec26   0:00 dbus-launch --autolaunch 2921f07efbb803689be3be
root      3748  0.0  0.0  23328   824 ?        Ss   Dec26   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-a
selmani   4048  0.0  0.0  15164  1144 pts/0    R+   15:11   0:00 ps aux
selmani   4062  0.1  1.3 668680 41732 ?        Sl   Dec26   1:39 nautilus
selmani   5098  0.0  0.1 100104  4728 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.9 /org/gt
selmani   7524  0.0  0.0  28368  2384 ?        S    Dec26   0:00 /usr/bin/wget --header=Content-Type: multipart/
selmani  13164  0.0  0.2 196408  8524 ?        S    Dec26   0:00 /opt/google/chrome/chrome --type=zygote
selmani  13183  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13187  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13194  0.0  0.0      0     0 ?        Z    Dec26   0:07 [chrome] <defunct>
selmani  13200  0.0  0.0      0     0 ?        ZN   Dec26   0:00 [chrome] <defunct>
selmani  13203  0.0  0.0      0     0 ?        ZN   Dec26   0:00 [chrome] <defunct>
selmani  13206  0.0  0.0      0     0 ?        ZN   Dec26   0:00 [chrome] <defunct>
selmani  13209  0.0  0.0      0     0 ?        ZN   Dec26   0:14 [chrome] <defunct>
selmani  13212  0.0  0.0      0     0 ?        Z    Dec26   0:14 [chrome] <defunct>
selmani  13215  0.0  0.0      0     0 ?        ZN   Dec26   0:00 [chrome] <defunct>
selmani  13221  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13224  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13227  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13230  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13234  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13239  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13247  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13488  0.0  0.0      0     0 ?        Z    Dec26   0:04 [chrome] <defunct>
selmani  13498  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13501  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
selmani  13504  0.0  0.0      0     0 ?        Z    Dec26   0:00 [chrome] <defunct>
root     24576  0.0  0.0  76984  2804 ?        S    Dec26   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org
root     24577  3.1  4.3 233704 133864 tty7    Ss+  Dec26  42:28 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/a
gdm      24611  0.0  0.0  26156   468 ?        S    Dec26   0:00 /usr/bin/dbus-launch --exit-with-session
root     24650  0.0  0.0  89288  2888 ?        S    Dec26   0:00 /usr/lib/gdm/gdm-session-worker
selmani  24668  0.0  0.1  96800  3444 ?        Sl   Dec26   0:00 /usr/bin/gnome-keyring-daemon --daemonize --log
selmani  24683  0.0  0.2 168872  7436 ?        Ssl  Dec26   0:00 gnome-session
selmani  24725  0.0  0.0  36060   608 ?        Ss   Dec26   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-
selmani  24728  0.0  0.1  26628  4112 ?        Ss   Dec26   0:11 /bin/dbus-daemon --fork --print-pid 7 --print-a
selmani  24729  0.0  0.0  26156   748 ?        S    Dec26   0:00 /usr/bin/dbus-launch --exit-with-session /usr/b
selmani  24733  0.9  0.1 207244  5484 ?        Ssl  Dec26  12:50 /usr/bin/pulseaudio --start
selmani  24736  0.0  0.1  94308  3260 ?        S    Dec26   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
selmani  24738  0.0  0.2  46848  6692 ?        S    Dec26   0:06 /usr/lib/libgconf2-4/gconfd-2
selmani  24749  0.0  0.4 312380 13144 ?        Ssl  Dec26   1:00 /usr/lib/gnome-settings-daemon/gnome-settings-d
selmani  24750  0.0  0.2 195060  7456 ?        Ss   Dec26   0:00 seahorse-daemon
selmani  24755  0.0  0.1  44000  3112 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd
selmani  24759  0.0  0.5 208140 17196 ?        S    Dec26   0:15 /usr/lib/notify-osd/notify-osd
selmani  24762  0.0  0.0  75492  2768 ?        Ssl  Dec26   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/selmani/.
selmani  24775  1.3  2.6 369792 81012 ?        S    Dec26  18:44 /usr/bin/compiz.real --sm-client-id 10a447c9a7b
selmani  24779  0.2  4.3 591460 134072 ?       Sl   Dec26   3:26 gnome-panel --sm-config-prefix /gnome-panel-60e
selmani  24784  0.0  0.1  87300  4016 ?        Ssl  Dec26   0:00 /usr/lib/bonobo-activation/bonobo-activation-se
selmani  24786  0.0  0.4 195548 15152 ?        S    Dec26   0:02 update-notifier --startup-delay=60
selmani  24787  0.1  0.9 278868 29212 ?        Sl   Dec26   1:59 /usr/bin/python /usr/bin/ubuntuone-client-apple
selmani  24790  0.0  0.4 268036 14048 ?        S    Dec26   0:02 nm-applet --sm-disable
selmani  24791  0.0  0.3 188380 11788 ?        S    Dec26   0:01 gnome-power-manager
selmani  24797  0.0  0.5 353040 16964 ?        Sl   Dec26   0:02 gnome-volume-control-applet
selmani  24799  0.0  0.2 162424  7284 ?        S    Dec26   0:00 /usr/lib/gnome-disk-utility/gdu-notification-da
selmani  24801  0.0  0.3 365824 10200 ?        Sl   Dec26   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
selmani  24806  0.0  0.5 291820 16296 ?        Sl   Dec26   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authent
selmani  24810  0.0  0.5 223976 15988 ?        S    Dec26   0:03 python /usr/share/system-config-printer/applet.
selmani  24816  0.0  0.2 173340  6424 ?        Ss   Dec26   0:05 gnome-screensaver
selmani  24823  0.0  0.3 212764 12352 ?        S    Dec26   0:02 /usr/lib/gnome-applets/cpufreq-applet --oaf-act
selmani  24830  0.0  0.1  58272  3456 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/g
selmani  24857  0.0  0.0   4004   556 ?        Ss   Dec26   0:00 /bin/sh -c /usr/bin/compiz-decorator
selmani  24858  0.0  0.6 309172 19192 ?        Sl   Dec26   0:18 /usr/bin/gtk-window-decorator
selmani  24860  0.0  0.1  87412  3752 ?        Sl   Dec26   0:01 /usr/lib/gvfs/gvfs-gdu-volume-monitor
selmani  24878  0.0  0.2 324800  7644 ?        Sl   Dec26   0:00 /usr/lib/evolution/evolution-data-server-2.28 -
selmani  24887  0.0  0.0  50504  2328 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
selmani  24912  0.0  0.5 252428 15936 ?        S    Dec26   0:00 /usr/lib/indicator-applet/indicator-applet-sess
selmani  24914  0.0  0.5 347668 17252 ?        Sl   Dec26   0:01 /usr/lib/indicator-applet/indicator-applet --oa
selmani  24924  0.2  0.8 134084 25240 ?        Sl   Dec26   2:57 /usr/bin/python /usr/lib/ubuntuone-client/ubunt
selmani  24967  0.0  0.0  43212  2328 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gt
selmani  24983  0.0  0.0  95372  2860 ?        S    Dec26   0:00 /usr/lib/indicator-session/indicator-status-ser
selmani  24985  0.0  0.0  42160  2308 ?        S    Dec26   0:00 /usr/lib/indicator-session/indicator-users-serv
selmani  24987  0.0  0.0  51080  2928 ?        S    Dec26   0:00 /usr/lib/indicator-session/indicator-session-se
selmani  24989  0.0  0.1  64960  4132 ?        S    Dec26   0:00 /usr/lib/indicator-messages/indicator-messages-
selmani  24991  0.0  0.0  34912  2056 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd-metadata
selmani  25690  0.0  0.1  86316  3556 ?        S    Dec26   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
selmani  27474  0.0  0.1  58388  3492 ?        S    Dec26   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.9 /or
root     29869  0.0  0.0  39212  2184 ?        S    12:08   0:00 /usr/bin/ubuntu-tweak-daemon
root     29871  0.0  0.3  73464 10984 ?        S    12:08   0:00 /usr/bin/python /usr/share/ubuntu-tweak/backend
root     31504  0.0  0.0      0     0 ?        S<   12:11   0:00 [xfs_mru_cache]
root     31505  0.0  0.0  17712   468 ?        S<   12:11   0:00 udevd --daemon
root     31506  0.0  0.0  17712   424 ?        S<   12:11   0:00 udevd --daemon
root     31507  0.0  0.0      0     0 ?        S<   12:11   0:00 [xfslogd/0]
root     31508  0.0  0.0      0     0 ?        S<   12:11   0:00 [xfsdatad/0]
root     31509  0.0  0.0      0     0 ?        S<   12:11   0:00 [xfsconvertd/0]
root     31512  0.0  0.0      0     0 ?        S<   12:11   0:00 [jfsIO]
root     31513  0.0  0.0      0     0 ?        S<   12:11   0:00 [jfsCommit]
root     31514  0.0  0.0      0     0 ?        S<   12:11   0:00 [jfsSync]
root     32516  0.0  0.2  61472  8036 ?        S    12:16   0:00 /usr/bin/python /usr/share/ubuntu-tweak/backend
selmani  32592  0.0  0.0  28368  1620 ?        S    Dec26   0:00 /usr/bin/wget --header=Content-Type: multipart/
selmani  32635  0.0  0.1  56632  3600 ?        S    12:22   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.9 /org
selmani  32641  0.0  0.0  51576  2668 ?        S    12:22   0:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.9 /org/g

```

This gives only 221 processes, compared to HTOP: 251 Total Tasks, and CONKY:335 Processes. WTF?

---

### Post by proxess on 2009-12-27
Each google-chrome tab is a process. So, if a tab crashes, the rest remains untouched.

---

### Post by crazyness003 on 2009-12-27
yeah, but I only have 2 tabs open and 5 extensions installed. Also, flash is currently not running. So that should give a total of 8 processes (1 browser + 2 tabs + 5 extensions)

It still doesn't make sense

EDIT: Actually I just observed that each tab adds 2 tasks to HTOP.

---

### Post by lswb on 2009-12-27
htop will list all threads separately even when they belong to a single process. That is why you see 64 instances of cosole-kit-daemon and it likely explains some of the other "duplicates" you see. I have not used chrome or chromium myself but my understanding is that by design it starts a new process for each tab, so that a only a single tab closes rather than crashing the whole browser session when a problem is encountered. 

From a terminal something like "ps aux" will show the separate processes actually running, or "ps aux|wc -l" to get a count of them.

When you say that 1GB of memory is being used, how are you determining that? linux will use memory for caching files and other data so that disk accesses can be avoided. Certain tools report this memory as being used, even though it is available to programs. Are you experiencing low memory related performance problems or just concerned about reported memory usage? Using the "free" command in a terminal, look at the 2nd line that begins "-/+ buffers/cache" The value in that line under the "free" column is what is actually available to running programs.

---

### Post by crazyness003 on 2009-12-27
I was wondering if 64 instances of console-kit-daemon was related to the 64bit OS I was using. Not sure. As for the 1GB of mem used. It's reported in conky, htop and free
```
selmani@main-pc:~$ free
             total       used       free     shared    buffers     cached
Mem:       3092272    1726564    1365708          0      32176     624428
-/+ buffers/cache:    1069960    2022312
Swap:      2096440     101508    1994932

```
Also, ps aux | wc -l reports as follows
```
selmani@main-pc:~$ ps aux | wc -l
221

```

Are these values "normal" (such a subjective questions, I know).

Is there a way to 'weed out' the "unnecessary" processes, or kill them, without affecting the integrity of my current session?

---

### Post by lswb on 2009-12-27
It is subjective to a great degree.

The 64 console-kit-daemon threads is only because a separate thread is created for each possible vt which in a default install is 64. It is "normal" for c-k-d though if you google the subject you will certainly find those who describe it as a questionable programming practice. I see several "defunct" instances of chrome in your ps listing. These are sometimes called "zombie" processes. They do not use any resources other and will normally be closed when the parent chrome instance is terminated. Chrome is after all beta software so I would assume later versions will address this anyway.

At any rate I note from your free listing that you still have about 2GB memory free. Again, are you actually experiencing any low memory related performance problems? I see no indications of any from the info you have posted.

Onmy own system with a single firefox browser and single terminal instance running in a gnome session, "ps aux|wc -l" shows 133 processes running. Your ps listing shows a lot more processes running, many of them to support hardware which my simple laptop does not have. I would not say that process count of 200 or 300 by itself indicates anything is abnormal.

Likely you can reduce the number of running processes but I know of no automated way to do so. Most ubuntu systems have several process started during init that are not really needed. You'll have to make that call yourself after researching what they do. Things in your ps listing like "ubuntu-tweak" are probably unnessary. It can be an interesting excersize if you have some free time to try to pare down what your system runs, but again if you are not experiencing problems, you may not want to bother.

---

### Post by crazyness003 on 2009-12-27
To answer your questions, no I am not, in fact, experiencing any low memory  related performance problems. I was just concerned, since it seems like there should be better resource management (at least thats what I want to think).

As for the zombies; yeah chrome is beta so it is possible those will be fixed in the future. Also, I learned that htop displays 2 processes for each tab/extension in use for chrome, whereas 'ps aux' only displays 1 for each.

Anyway, thanks for the info. I'll free up some time and take a look at each process independently. 

Again thanks.

I'll mark this as Solved.

---

### Post by efflandt on 2009-12-27
Just for comparison this is an example of freshly installed 64-bit Ubuntu 9.10 on USB hard drive (WD Passport) with just Firefox and terminal open on a new Dell 1545:

```
free
             total       used       free     shared    buffers     cached
Mem:       3052180     654572    2397608          0      11124     313716
-/+ buffers/cache:     329732    2722448
Swap:            0          0          0

ps aux | wc -l
154
```

---

### Post by crazyness003 on 2009-12-29
> **efflandt said:**
> Just for comparison this is an example of freshly installed 64-bit Ubuntu 9.10 on USB hard drive (WD Passport) with just Firefox and terminal open on a new Dell 1545:

```
free
             total       used       free     shared    buffers     cached
Mem:       3052180     654572    2397608          0      11124     313716
-/+ buffers/cache:     329732    2722448
Swap:            0          0          0

ps aux | wc -l
154
```
thanks man, I guess I was just getting paranoid.

COMPLETELY UNRELATED EDIT: WHOA! Elgin IL? I was born in Elgin! DUDE! Old house address was 645 N Grove Ave, just up the street from Gail Borden Library. Wow, it really is a small world.

---

