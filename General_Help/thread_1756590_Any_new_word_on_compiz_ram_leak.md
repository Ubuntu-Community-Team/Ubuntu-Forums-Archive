---
title: "Any new word on compiz ram leak?"
date: 2011-05-12
forum: General Help
---

### Post by antaios256 on 2011-05-12
ive been watching the launch-pad but haven't seen any updates lately was wondering if anyone had any information on this issue.

---

### Post by krippa on 2011-05-13
Yeah, what's happening here?! Compiz is using 2.6GB of RAM and my computer is rendered useless from swapping in and out...

---

### Post by mc4man on 2011-05-13
What's this show
```
ps -A u
```

---

### Post by krippa on 2011-05-16
Hi, now I am back in the office and have gotten back up to 1.4GB at least... Here is the output:

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24128  1076 ?        Ss   08:08   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    08:08   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    08:08   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    08:08   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    08:08   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    08:08   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S    08:08   0:00 [migration/2]
root        13  0.0  0.0      0     0 ?        S    08:08   0:00 [ksoftirqd/2]
root        14  0.0  0.0      0     0 ?        S    08:08   0:00 [migration/3]
root        16  0.0  0.0      0     0 ?        S    08:08   0:00 [ksoftirqd/3]
root        17  0.0  0.0      0     0 ?        S<   08:08   0:00 [cpuset]
root        18  0.0  0.0      0     0 ?        S<   08:08   0:00 [khelper]
root        19  0.0  0.0      0     0 ?        S<   08:08   0:00 [netns]
root        21  0.0  0.0      0     0 ?        S    08:08   0:00 [sync_supers]
root        22  0.0  0.0      0     0 ?        S    08:08   0:00 [bdi-default]
root        23  0.0  0.0      0     0 ?        S<   08:08   0:00 [kintegrityd]
root        24  0.0  0.0      0     0 ?        S<   08:08   0:00 [kblockd]
root        25  0.0  0.0      0     0 ?        S<   08:08   0:00 [kacpid]
root        26  0.0  0.0      0     0 ?        S<   08:08   0:00 [kacpi_notify]
root        27  0.0  0.0      0     0 ?        S<   08:08   0:00 [kacpi_hotplug]
root        28  0.0  0.0      0     0 ?        S<   08:08   0:00 [ata_sff]
root        29  0.0  0.0      0     0 ?        S    08:08   0:00 [khubd]
root        30  0.0  0.0      0     0 ?        S<   08:08   0:00 [md]
root        35  0.0  0.0      0     0 ?        S    08:08   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    08:08   0:07 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   08:08   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    08:08   0:00 [fsnotify_mark]
root        39  0.0  0.0      0     0 ?        S<   08:08   0:00 [aio]
root        40  0.0  0.0      0     0 ?        S    08:08   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S<   08:08   0:00 [crypto]
root        45  0.0  0.0      0     0 ?        S<   08:08   0:00 [kthrotld]
root        46  0.0  0.0      0     0 ?        S    08:08   0:00 [scsi_eh_0]
root        47  0.0  0.0      0     0 ?        S    08:08   0:02 [scsi_eh_1]
root        48  0.0  0.0      0     0 ?        S    08:08   0:00 [kworker/u:2]
root        49  0.0  0.0      0     0 ?        S    08:08   0:00 [scsi_eh_2]
root        50  0.0  0.0      0     0 ?        S    08:08   0:00 [scsi_eh_3]
root        51  0.0  0.0      0     0 ?        S    08:08   0:00 [kworker/u:3]
root        53  0.0  0.0      0     0 ?        S<   08:08   0:00 [kmpathd]
root        54  0.0  0.0      0     0 ?        S<   08:08   0:00 [kmpath_handlerd]
root        55  0.0  0.0      0     0 ?        S<   08:08   0:00 [kondemand]
root        56  0.0  0.0      0     0 ?        S<   08:08   0:00 [kconservative]
root       195  0.0  0.0      0     0 ?        S    08:08   0:00 [scsi_eh_4]
root       196  0.0  0.0      0     0 ?        S    08:08   0:00 [scsi_eh_5]
root       226  0.0  0.0      0     0 ?        S    08:08   0:02 [jbd2/sda6-8]
root       227  0.0  0.0      0     0 ?        S<   08:08   0:00 [ext4-dio-unwrit]
root       280  0.0  0.0  17052   472 ?        S    08:09   0:00 upstart-udev-bridge --daemon
root       286  0.0  0.0  21848   376 ?        S<s  08:09   0:00 udevd --daemon
root       452  0.0  0.0  21872   348 ?        S<   08:09   0:00 udevd --daemon
root       468  0.0  0.0  21872   232 ?        S<   08:09   0:00 udevd --daemon
root       586  0.0  0.0      0     0 ?        S<   08:09   0:00 [kpsmoused]
root       640  0.0  0.0  15004    36 ?        S    08:09   0:00 upstart-socket-bridge --daemon
root       650  0.0  0.0      0     0 ?        S<   08:09   0:00 [hd-audio0]
root       817  0.0  0.0      0     0 ?        S    08:09   0:00 [jbd2/sda1-8]
root       818  0.0  0.0      0     0 ?        S<   08:09   0:00 [ext4-dio-unwrit]
root       837  0.0  0.0  91668   620 ?        Ss   08:09   0:00 smbd -F
102        856  0.0  0.0  24952  1796 ?        Ss   08:09   0:01 dbus-daemon --system --fork --activation=upstart
syslog     859  0.0  0.0 119992   568 ?        Sl   08:09   0:00 rsyslogd -c4
root       871  0.0  0.0  79180  1564 ?        Ssl  08:09   0:00 gdm-binary
root       882  0.0  0.0 158228  2312 ?        Ssl  08:09   0:00 NetworkManager
avahi      884  0.0  0.0  32260   992 ?        S    08:09   0:01 avahi-daemon: running [kristofer-desktop.local]
avahi      885  0.0  0.0  32008    68 ?        S    08:09   0:00 avahi-daemon: chroot helper
root       886  0.0  0.0  91552   144 ?        S    08:09   0:00 smbd -F
root       888  0.0  0.0 125276  1544 ?        Sl   08:09   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       890  0.0  0.0  64656  1228 ?        S    08:09   0:00 /usr/sbin/modem-manager
root       955  0.0  0.0 132460  2296 ?        Sl   08:09   0:00 /usr/lib/policykit-1/polkitd
root       973  0.0  0.0  77152  1132 ?        Ss   08:09   0:00 /usr/sbin/cupsd -F
root      1008  0.0  0.0  93808  1332 ?        Sl   08:09   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1017  3.3  4.6 404308 189036 tty7    Ss+  08:09  20:24 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-yW8zbp/database -nolisten tcp vt7
root      1021  0.0  0.0  28812   308 ?        S    08:09   0:00 /sbin/wpa_supplicant -u -s
root      1054  0.0  0.0   6196   260 tty4     Ss+  08:09   0:00 /sbin/getty -8 38400 tty4
root      1057  0.0  0.0   6196   260 tty5     Ss+  08:09   0:00 /sbin/getty -8 38400 tty5
root      1064  0.0  0.0   6196   260 tty2     Ss+  08:09   0:00 /sbin/getty -8 38400 tty2
root      1065  0.0  0.0   6196   260 tty3     Ss+  08:09   0:00 /sbin/getty -8 38400 tty3
root      1068  0.0  0.0   6196   260 tty6     Ss+  08:09   0:00 /sbin/getty -8 38400 tty6
root      1073  0.0  0.0   4284   268 ?        Ss   08:09   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1088  0.0  0.0  16728    48 ?        Ss   08:09   0:00 atd
root      1089  0.0  0.0  18928   416 ?        Ss   08:09   0:00 cron
root      1194  0.0  0.0  37364   528 ?        Ss   08:09   0:00 /usr/lib/postfix/master
root      1251  0.0  0.0  65852   628 ?        Ss   08:09   0:00 /usr/sbin/winbindd
root      1294  0.0  0.0  65956   480 ?        S    08:09   0:00 /usr/sbin/winbindd
root      1357  0.0  0.0 120260   520 ?        Ss   08:09   0:01 /usr/sbin/apache2 -k start
root      1415  0.0  0.0      0     0 ?        S    08:09   0:01 [flush-8:0]
root      1439  0.0  0.0   7084   716 ?        S    08:09   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-071ebf18-6872-46e8-84b2-df5dbf9f6fc1-eth0.l
rtkit     1470  0.0  0.0  37628   760 ?        SNl  08:09   0:00 /usr/lib/rtkit/rtkit-daemon
root      1474  0.0  0.0 143152  1620 ?        Sl   08:09   0:00 /usr/lib/upower/upowerd
root      1552  0.0  0.0   6196   260 tty1     Ss+  08:09   0:00 /sbin/getty -8 38400 tty1
postfix   1613  0.0  0.0  39588   548 ?        S    08:09   0:00 qmgr -l -t fifo -u
root      1624  0.0  0.0  61688   900 ?        Ss   08:09   0:00 nmbd -D
root      1647  0.0  0.0      0     0 ?        S    08:09   0:29 [cifsd]
root      1659  0.0  0.0 171940  1240 ?        Sl   08:10   0:00 /usr/lib/gdm/gdm-session-worker
root      1662  0.0  0.0  65928   580 ?        S    08:11   0:00 /usr/sbin/winbindd
1000      1665  0.0  0.0 235796  3712 ?        Sl   08:11   0:01 /usr/bin/gnome-keyring-daemon --daemonize --login
1000      1684  0.0  0.0 239336  2792 ?        Ssl  08:11   0:00 gnome-session --session=ubuntu
1000      1721  0.0  0.0  12092    12 ?        Ss   08:11   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
1000      1724  0.0  0.0  26400   148 ?        S    08:11   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
1000      1725  0.3  0.0  28500  3860 ?        Ss   08:11   2:19 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
1000      1730  0.0  0.0  57428  2776 ?        S    08:11   0:09 /usr/lib/libgconf2-4/gconfd-2
1000      1739  0.0  0.1 390596  4620 ?        Ssl  08:11   0:16 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
1000      1744  0.0  0.0  51968  1000 ?        S    08:11   0:00 /usr/lib/gvfs/gvfsd
1000      1749  0.0  0.0  89340   784 ?        Ssl  08:11   0:05 /usr/lib/gvfs//gvfs-fuse-daemon /home/kristofer/.gvfs
1000      1753  3.5 34.9 3240836 1416184 ?     Sl   08:11  21:49 compiz
1000      1758  0.1  1.0 824904 44104 ?        Sl   08:11   0:42 nautilus
1000      1760  0.0  0.1 399544  4204 ?        Sl   08:11   0:00 nm-applet --sm-disable
1000      1762  0.0  0.1 407976  5692 ?        SLl  08:11   0:00 /usr/lib/evolution/2.32/evolution-alarm-notify
1000      1764  0.0  0.0 222952  2704 ?        Sl   08:11   0:00 zeitgeist-datahub
1000      1765  0.0  0.0 267520  2816 ?        Sl   08:11   0:00 bluetooth-applet
1000      1770  0.0  0.1 340664  6932 ?        Sl   08:11   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
1000      1771  0.0  0.3 485872 12184 ?        Sl   08:11   0:02 /usr/bin/python /usr/bin/indicator-weather
1000      1773  0.0  0.3 186232 12688 ?        Sl   08:11   0:01 /usr/bin/python /usr/bin/zeitgeist-daemon
1000      1775  0.5  0.1 320792  4928 ?        Sl   08:11   3:10 indicator-multiload
1000      1778  0.0  0.1 307452  4964 ?        Sl   08:11   0:00 gnome-power-manager
1000      1799  0.0  0.0   6860   188 ?        S    08:11   0:00 /bin/cat
1000      1801  0.0  0.0      0     0 ?        Z    08:11   0:00 [zeitgeist-datah] <defunct>
1000      1811  0.0  0.0 106340  3420 ?        S    08:11   0:29 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
1000      1819  0.0  0.1 304260  7408 ?        Sl   08:11   0:02 /usr/lib/notify-osd/notify-osd
1000      1826  0.0  0.3 456472 13164 ?        Sl   08:11   0:08 /usr/lib/evolution/e-calendar-factory
1000      1837  0.0  0.0 158024  1896 ?        S    08:11   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1839  0.0  0.0 127624  2280 ?        Sl   08:11   0:00 /usr/lib/udisks/udisks-daemon
root      1840  0.0  0.0  45168   592 ?        S    08:11   0:03 udisks-daemon: polling /dev/sr0
1000      1864  0.0  0.0  73364   936 ?        Sl   08:11   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
1000      1867  0.0  0.0  59568  1188 ?        S    08:11   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1000      1870  0.0  0.0  58096  1812 ?        S    08:11   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.10 /org/gtk/gvfs/exec_spaw/0
1000      1878  0.0  0.0 337280  1468 ?        Sl   08:11   0:00 /usr/lib/evolution/e-addressbook-factory
1000      1888  0.0  0.1 241600  4384 ?        Sl   08:11   0:01 /usr/bin/gnome-screensaver --no-daemon
1000      1904  0.0  0.0   4220   200 ?        S    08:11   0:00 /bin/sh -e /usr/bin/couchdb -n -a /etc/couchdb/default.ini -a /etc/xdg/desktop-couch/compulsory-auth.ini -a /home/kristofer/.config/desktop-couch/desktop-couchdb.ini -b -r
1000      1911  0.0  0.0   4220    52 ?        S    08:11   0:00 /bin/sh -e /usr/bin/couchdb -n -a /etc/couchdb/default.ini -a /etc/xdg/desktop-couch/compulsory-auth.ini -a /home/kristofer/.config/desktop-couch/desktop-couchdb.ini -b -r
1000      1912  1.0  0.4 208768 19344 ?        Sl   08:11   6:14 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -A 4 -- -root /usr/lib/erlang -progname erl -- -home /home/kristofer -- -noshell -noinput -sasl errlog_type error -couch
1000      1928  0.0  0.0   3984     4 ?        Ss   08:11   0:00 heart -pid 1912 -ht 11
1000      1941  0.0  0.1 108852  6824 ?        SN   08:11   0:30 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
1000      1942  0.0  0.0      0     0 ?        Z    08:11   0:00 [desktopcouch-se] <defunct>
1000      1947  0.0  0.0 157740  1496 ?        Ssl  08:11   0:00 /usr/lib/couchdb/bin/couchjs /usr/share/couchdb/server/main.js
1000      1964  0.0  0.0 122464  1464 ?        Sl   08:11   0:00 /usr/lib/d-conf/dconf-service
1000      1973  0.0  0.0   4220   164 ?        Ss   08:11   0:00 /bin/sh -c /usr/bin/compiz-decorator
1000      1974  0.0  0.2 252016  9188 ?        Sl   08:11   0:11 /usr/bin/unity-window-decorator
1000      1976  0.0  0.1 226856  6516 ?        S    08:11   0:04 /usr/lib/bamf/bamfdaemon
1000      1979  0.0  0.0 176224  2472 ?        S    08:11   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
1000      1984  0.0  0.0  52232  1032 ?        S    08:11   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.10 /org/gtk/gvfs/exec_spaw/1
1000      1989  1.3  0.7 448640 30740 ?        Sl   08:11   8:08 /usr/lib/unity/unity-panel-service
1000      1993  0.0  0.1 266628  5660 ?        Sl   08:11   0:01 /usr/lib/unity-place-applications/unity-applications-daemon
1000      1995  0.0  0.0 242292  3024 ?        Sl   08:11   0:00 /usr/lib/unity-place-files/unity-files-daemon
1000      2031  0.0  0.0  46792  2036 ?        S    08:11   0:00 /usr/lib/gvfs/gvfsd-metadata
1000      2034  0.2  0.2 282488  9832 ?        Sl   08:11   1:29 /usr/lib/indicator-application/indicator-application-service
1000      2036  0.0  0.0 307000  2176 ?        Sl   08:11   0:00 /usr/lib/indicator-me/indicator-me-service
1000      2038  0.0  0.0 335936  2528 ?        Sl   08:11   0:00 /usr/lib/indicator-sound/indicator-sound-service
1000      2040  0.0  0.0 222920  1584 ?        Sl   08:11   0:00 /usr/lib/indicator-messages/indicator-messages-service
1000      2042  0.0  0.0 236056  2496 ?        Sl   08:11   0:00 /usr/lib/indicator-session/indicator-session-service
1000      2044  0.0  0.8 411392 32872 ?        SLl  08:11   0:09 /usr/lib/indicator-datetime/indicator-datetime-service
1000      2064  0.0  0.0 159216  1740 ?        Sl   08:11   0:00 /usr/lib/geoclue/geoclue-master
1000      2091  0.0  0.0 233232  3740 ?        S    08:11   0:30 /usr/bin/python /usr/share/system-config-printer/applet.py
1000      2202  0.0  0.1 323848  4672 ?        Sl   08:12   0:00 update-notifier
root      2221  0.0  0.0  84052  1340 ?        S    08:12   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
1000      2615  7.5 15.1 1637844 611200 ?      Sl   08:13  46:02 /usr/lib/firefox-4.0.1/firefox-bin
1000      2945  0.1  0.0 237752  3212 ?        Sl   08:19   0:41 /usr/lib/firefox-4.0.1/plugin-container /var/lib/flashplugin-installer/npwrapper.libflashplayer.so -omnijar /usr/lib/firefox-4.0.1/omni.jar 2615 true plugin
1000      2958  0.4  0.1  90096  4180 ?        S    08:19   2:49 /usr/lib/nspluginwrapper/i386/linux/npviewer.bin --plugin /usr/lib/flashplugin-installer/libflashplayer.so --connection /org/wrapper/NSPlugins/libflashplayer.so/2945-1
www-data  3471  0.0  0.0 120392   280 ?        S    08:24   0:00 /usr/sbin/apache2 -k start
www-data  3472  0.0  0.0 120392   280 ?        S    08:24   0:00 /usr/sbin/apache2 -k start
www-data  3473  0.0  0.0 120260   292 ?        S    08:24   0:00 /usr/sbin/apache2 -k start
www-data  3474  0.0  0.0 120260    64 ?        S    08:24   0:00 /usr/sbin/apache2 -k start
www-data  3475  0.0  0.0 120260    64 ?        S    08:24   0:00 /usr/sbin/apache2 -k start
1000      4066  0.0  0.0 278708  1760 ?        S    08:38   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.10 /org/gtk/gvfs/exec_spaw/2
1000      5356  0.0  0.2 335704 11312 ?        Sl   09:15   0:05 gnome-terminal
1000      5361  0.0  0.0  14612   280 ?        S    09:15   0:00 gnome-pty-helper
1000      5362  0.0  0.0  24568   384 pts/0    Ss   09:15   0:00 bash
1000      5474  0.0  0.0  33336  1552 pts/1    Ss   09:17   0:00 bash
1000      5831  0.0  0.0 278408  3400 ?        Sl   09:24   0:00 /usr/lib/firefox-4.0.1/plugin-container /usr/lib/mozilla/plugins/libtotem-cone-plugin.so -omnijar /usr/lib/firefox-4.0.1/omni.jar 2615 true plugin
1000      5932  0.0  0.0  12508   348 ?        S    09:26   0:00 /bin/bash /usr/local/netbeans-6.9.1/bin/../platform/lib/nbexec --userdir /home/kristofer/.netbeans/6.9 --jdkhome /usr/lib/jvm/java-6-sun --branding nb --clusters /usr/local
1000      6187  128 19.1 1294160 774724 ?      SLl  09:26 684:30 /usr/lib/jvm/java-6-sun/bin/java -Djdk.home=/usr/lib/jvm/java-6-sun -classpath /home/kristofer/.netbeans/6.9/lib/boot.jar:/home/kristofer/.netbeans/6.9/lib/org-openide-modu
1000      8019  0.1  0.2 439124  8432 ?        Sl   09:58   0:56 rapidsvn
1000      8664  1.8  0.0 323544   688 ?        Sl   10:15   8:48 skype
root      9462  0.0  0.0      0     0 ?        S    11:37   0:09 [kworker/3:1]
1000      9489  0.2  0.6 455312 25728 ?        Sl   11:42   0:53 /usr/bin/python /usr/bin/meld
1000      9509  0.0  0.0      0     0 ?        Z    11:46   0:00 [xdg-open] <defunct>
1000      9893  0.1  0.9 756220 37048 ?        Sl   13:15   0:24 /usr/lib/libreoffice/program/soffice.bin -impress /tmp/CMS HOTDEAL PROMO TEMPLATE - europcar-1.ppt -splash-pipe=5
108      10238  0.0  0.0  45792  2188 ?        Ssl  13:54   0:00 /usr/sbin/hald
root     10239  0.0  0.0  22640   772 ?        S    13:54   0:00 hald-runner
root     10274  0.0  0.0  24760   568 ?        S    13:54   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event3 /dev/input/event0 /dev/input/event1
root     10320  0.0  0.0  24756   768 ?        S    13:54   0:02 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root     10321  0.0  0.0  24768   608 ?        S    13:54   0:00 /usr/lib/hal/hald-addon-cpufreq
108      10322  0.0  0.0  26544   532 ?        S    13:54   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
1000     12701  0.0  0.0  13156  1168 ?        S    15:19   0:00 /bin/bash /usr/share/playonlinux/playonlinux --run Internet Explorer 6
1000     12724  0.0  0.0  12304   324 ?        S    15:19   0:00 bash Internet Explorer 6 
1000     12725  0.0  1.0 2705208 42988 ?       Sl   15:19   0:05 iexplore.exe                                      
1000     12728  0.0  0.1   8148  5172 ?        Ss   15:19   0:05 /usr/bin/wineserver
1000     12736  0.0  0.0 2656160 3516 ?        Ss   15:19   0:00 C:\windows\system32\explorer.exe /desktop                                      
1000     12761  0.0  0.0  13156  1380 ?        S    15:19   0:00 /bin/bash /usr/share/playonlinux/playonlinux --run Internet Explorer 7
1000     12784  0.0  0.0  12304   764 ?        S    15:20   0:00 bash Internet Explorer 7 
1000     12785  0.1  0.8 2675808 32896 ?       Sl   15:20   0:12 iexplore.exe                                                                                                                                    
1000     12788  0.0  0.1   8140  4440 ?        Ss   15:20   0:06 /home/kristofer/.PlayOnLinux/WineVersions/1.3.6/usr/bin/wineserver
1000     12792  0.0  0.0 2643436  564 ?        Sl   15:20   0:00 C:\windows\system32\services.exe                                                                                                                                    
1000     12794  0.0  0.0 2644112  452 ?        Sl   15:20   0:00 C:\windows\system32\winedevice.exe MountMgr                                                                                                                                
1000     12804  0.0  0.0 2655324 2296 ?        Ss   15:20   0:00 C:\windows\system32\explorer.exe /desktop                                                                                                                                  
1000     12961  0.1  0.5 398028 23100 ?        Sl   15:30   0:10 gedit /home/kristofer/Desktop/test hotdeal css.html
root     13259  0.0  0.0      0     0 ?        S    15:54   0:06 [kworker/1:1]
1000     13899  0.0  0.5 350080 20576 ?        Sl   18:00   0:00 ruby /usr/bin/screenruler
root     13906  0.0  0.0      0     0 ?        S    18:00   0:00 [kworker/2:0]
1000     13909  0.0  0.0  13156  1768 ?        S    18:00   0:00 /bin/bash /usr/share/playonlinux/playonlinux --run Internet Explorer 6
1000     13932  0.0  0.0  12304   900 ?        S    18:00   0:00 bash Internet Explorer 6 
1000     13933  0.4  1.3 2701380 55848 ?       Sl   18:00   0:05 iexplore.exe                                      
root     14049  0.0  0.0      0     0 ?        S    18:06   0:00 [kworker/0:1]
postfix  14069  0.0  0.0  39428  1336 ?        S    18:08   0:00 pickup -l -t fifo -u -c
1000     14089  0.1  0.0   5904  3000 ?        Rs   18:09   0:00 /usr/bin/wineserver
1000     14093  0.0  0.0 2643588 1736 ?        Sl   18:09   0:00 C:\windows\system32\services.exe                                      
1000     14095  0.0  0.0 2644216 1708 ?        Sl   18:09   0:00 C:\windows\system32\winedevice.exe MountMgr                                      
1000     14104  0.0  0.0 2643412 1480 ?        Sl   18:09   0:00 C:\windows\system32\plugplay.exe                                      
1000     14109  0.0  0.1 2655420 4472 ?        Ss   18:09   0:00 C:\windows\system32\explorer.exe /desktop                                      
1000     14112  0.3  0.5 2679768 21920 ?       Sl   18:09   0:02 C:\Program Files\Spotify\spotify.exe                                      
1000     14153  0.0  0.0 209468  3516 ?        S<sl 18:10   0:00 /usr/bin/pulseaudio --start --log-target=syslog
1000     14163  0.0  0.0 181372  2972 ?        Sl   18:10   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root     14169  0.0  0.0      0     0 ?        S    18:10   0:00 [kworker/2:2]
root     14172  0.0  0.0      0     0 ?        R    18:11   0:00 [kworker/0:2]
root     14188  0.0  0.0      0     0 ?        S    18:13   0:00 [kworker/1:0]
root     14199  0.0  0.0      0     0 ?        S    18:14   0:00 [kworker/3:0]
root     14216  0.0  0.0      0     0 ?        S    18:15   0:00 [kworker/2:1]
root     14220  0.0  0.0      0     0 ?        S    18:16   0:00 [kworker/0:0]
root     14227  0.0  0.0      0     0 ?        S    18:17   0:00 [flush-cifs-1]
root     14239  0.0  0.0      0     0 ?        S    18:18   0:00 [kworker/1:2]
root     14247  0.0  0.0      0     0 ?        S    18:19   0:00 [kworker/3:2]
1000     14248  0.0  0.0  17944  1404 pts/1    R+   18:19   0:00 ps -A u

```

---

