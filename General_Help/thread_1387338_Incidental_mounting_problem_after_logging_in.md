---
title: "Incidental mounting problem after logging in"
date: 2010-01-21
forum: General Help
---

### Post by chainzz on 2010-01-21
Hello,

I am running Ubuntu 9.10 64 bit with all the latest updates. I am really happy with Ubuntu, but there's one problem that is really annoying me.

I have a separate disk mounted at /media/opslag ('opslag' is Dutch for 'storage' :)) which is automatically mounted at startup. Sometimes, say one in ten times, Ubuntu takes a really long time to mount the disk. When this happens the HDD LED is constantly on (like it is checking the whole disk or something) until 5-10 minutes after I have logged in. When the HDD LED finally goes off, I see my wallpaper (as it is located at /media/opslag) and a icon called 'opslag' appearing on the desktop. Dropbox isn't very happy with this either: everytime it happens it complains about the Dropbox folder gone missing, which is logical because the Dropbox folder is also located at /media/opslag. 

I have already checked if there is a fsck process (or something likewise) running when this happens, but this doesn't seem to be the case. I have also manually checked the disk multiple times with fsck to see if it is corrupted or something, but it seems to be healthy.

Does anybody have a suggestion? Thanks!

---

### Post by quixote on 2010-01-23
Is "opslag" a partition on the same HD?  A networked drive?  A USB drive?  If it's on the same HD, this shouldn't be happening :( .  Is it ext3 format, or something else?

---

### Post by chainzz on 2010-01-23
> **quixote said:**
> Is "opslag" a partition on the same HD?  A networked drive?  A USB drive?  If it's on the same HD, this shouldn't be happening :( .  Is it ext3 format, or something else?
No, it's a separate interal 500GB drive formatted in ext3. The whole disk has only one partition, which uses the full 500GB of the disk.

---

### Post by quixote on 2010-01-23
Well, given that everything works except that it takes forever to get going, I wonder if you're exactly right: it's doing some kind of disk check?  But what?  The usual kind which it does during boot up, it tells you that's what it's doing.  Maybe some kind of updatedb?? But that should affect your whole system.  

While the drive is in limbo, you could quick open a terminal and type ps -A or ps -ef to see which processes are running.  Maybe that'll give some useful info?  Sorry, but I'm out of ideas and no help here!

---

### Post by chainzz on 2010-01-24
I checked the list of processes once when it happened but I could not find anything unusual, the next time it happens I will post a list of running processes here!

---

### Post by chainzz on 2010-02-04
Today the problem occurred again, and it seems that I was wrong, there was a fsck process running. This is the output from 'ps aux':
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  1.2  0.0  19452  1840 ?        Ss   19:20   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:20   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/2]
root        10  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/2]
root        11  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/2]
root        12  0.0  0.0      0     0 ?        S<   19:20   0:00 [migration/3]
root        13  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksoftirqd/3]
root        14  0.0  0.0      0     0 ?        S<   19:20   0:00 [watchdog/3]
root        15  0.0  0.0      0     0 ?        S<   19:20   0:00 [events/0]
root        16  0.0  0.0      0     0 ?        S<   19:20   0:00 [events/1]
root        17  0.0  0.0      0     0 ?        S<   19:20   0:00 [events/2]
root        18  0.0  0.0      0     0 ?        S<   19:20   0:00 [events/3]
root        19  0.0  0.0      0     0 ?        S<   19:20   0:00 [cpuset]
root        20  0.0  0.0      0     0 ?        S<   19:20   0:00 [khelper]
root        21  0.0  0.0      0     0 ?        S<   19:20   0:00 [netns]
root        22  0.0  0.0      0     0 ?        S<   19:20   0:00 [async/mgr]
root        23  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/0]
root        24  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/1]
root        25  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/2]
root        26  0.0  0.0      0     0 ?        S<   19:20   0:00 [kintegrityd/3]
root        27  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/0]
root        28  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/1]
root        29  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/2]
root        30  0.0  0.0      0     0 ?        S<   19:20   0:00 [kblockd/3]
root        31  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpi_notify]
root        33  0.0  0.0      0     0 ?        S<   19:20   0:00 [kacpi_hotplug]
root        34  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/0]
root        35  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/1]
root        36  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/2]
root        37  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata/3]
root        38  0.0  0.0      0     0 ?        S<   19:20   0:00 [ata_aux]
root        39  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksuspend_usbd]
root        40  0.0  0.0      0     0 ?        S<   19:20   0:00 [khubd]
root        41  0.0  0.0      0     0 ?        S<   19:20   0:00 [kseriod]
root        42  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmmcd]
root        43  0.0  0.0      0     0 ?        S<   19:20   0:00 [bluetooth]
root        44  0.0  0.0      0     0 ?        S    19:20   0:00 [khungtaskd]
root        45  0.0  0.0      0     0 ?        S    19:20   0:00 [pdflush]
root        46  0.0  0.0      0     0 ?        S    19:20   0:00 [pdflush]
root        47  0.0  0.0      0     0 ?        S<   19:20   0:00 [kswapd0]
root        48  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/0]
root        49  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/1]
root        50  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/2]
root        51  0.0  0.0      0     0 ?        S<   19:20   0:00 [aio/3]
root        52  0.0  0.0      0     0 ?        S<   19:20   0:00 [ecryptfs-kthrea]
root        53  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/0]
root        54  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/1]
root        55  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/2]
root        56  0.0  0.0      0     0 ?        S<   19:20   0:00 [crypto/3]
root        65  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_0]
root        66  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_1]
root        69  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_2]
root        70  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_3]
root        74  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_4]
root        75  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_5]
root        86  0.0  0.0      0     0 ?        S<   19:20   0:00 [kstriped]
root        87  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/0]
root        88  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/1]
root        89  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/2]
root        90  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpathd/3]
root        91  0.0  0.0      0     0 ?        S<   19:20   0:00 [kmpath_handlerd]
root        92  0.0  0.0      0     0 ?        S<   19:20   0:00 [ksnapd]
root        93  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/0]
root        94  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/1]
root        95  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/2]
root        96  0.0  0.0      0     0 ?        S<   19:20   0:00 [kondemand/3]
root        97  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative/0]
root        98  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative/1]
root        99  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative/2]
root       100  0.0  0.0      0     0 ?        S<   19:20   0:00 [kconservative/3]
root       101  0.0  0.0      0     0 ?        S<   19:20   0:00 [krfcommd]
root       243  0.0  0.0      0     0 ?        S<   19:20   0:00 [khpsbpkt]
root       343  0.0  0.0      0     0 ?        S<   19:20   0:00 [scsi_eh_6]
root       344  0.0  0.0      0     0 ?        S<   19:20   0:00 [usb-storage]
root       351  0.0  0.0      0     0 ?        S<   19:20   0:00 [knodemgrd_0]
root       393  0.0  0.0      0     0 ?        S<   19:20   0:00 [usbhid_resumer]
root       433  0.0  0.0      0     0 ?        D<   19:20   0:00 [kjournald2]
root       482  0.0  0.0  21320  1324 ?        S    19:20   0:00 mountall --daemon --tmptime=0
root       497  0.0  0.0  12768   920 ?        S    19:20   0:00 upstart-udev-bridge --daemon
root       499  0.0  0.0  17452  1264 ?        S<s  19:20   0:00 udevd --daemon
root       549  0.0  0.0   8120   796 ?        S    19:20   0:00 fsck -a -C10 -t ext3 /dev/disk/by-uuid/51839a1b-1f14-4e5d-8280-d684f523e2ff
root       673  0.0  0.0  17448  1252 ?        S<   19:20   0:00 udevd --daemon
root       675  0.0  0.0  17448  1188 ?        S<   19:20   0:00 udevd --daemon
root       737  3.8  1.7  51712 35980 ?        D    19:20   0:02 fsck.ext3 -a -C10 /dev/sdb2
root       861  0.0  0.0      0     0 ?        S<   19:20   0:00 [hd-audio0]
root       900  0.0  0.0   8192   612 ?        Ss   19:20   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog     902  0.0  0.1 124380  2076 ?        Sl   19:20   0:00 rsyslogd -c4
102        903  0.3  0.0  24288  1900 ?        Ss   19:20   0:00 dbus-daemon --system --fork
avahi      916  0.0  0.0  31896  1624 ?        Ss   19:20   0:00 avahi-daemon: running [computerbas.local]
107        917  0.1  0.2  34252  4908 ?        Ss   19:20   0:00 hald --daemon=yes
avahi      918  0.0  0.0  31760   544 ?        Ss   19:20   0:00 avahi-daemon: chroot helper
root       926  0.0  0.1 120284  3216 ?        Ssl  19:20   0:00 /usr/sbin/console-kit-daemon
root       991  0.0  0.1  89388  4036 ?        Ssl  19:20   0:00 NetworkManager
root       995  0.0  0.0  20180  1336 ?        S    19:20   0:00 hald-runner
root       999  0.0  0.1  51476  2344 ?        S    19:20   0:00 /usr/sbin/modem-manager
root      1015  0.0  0.0  28216  2032 ?        S    19:20   0:00 /sbin/wpa_supplicant -u -s
root      1016  0.0  0.0   6464  1072 ?        S    19:20   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-7e986264-ac84-45a4-bef4-858b257a0889-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      1120  0.0  0.0   5988   608 tty4     Ss+  19:20   0:00 /sbin/getty -8 38400 tty4
root      1123  0.0  0.0   5988   608 tty5     Ss+  19:20   0:00 /sbin/getty -8 38400 tty5
root      1129  0.0  0.0   5988   604 tty2     Ss+  19:20   0:00 /sbin/getty -8 38400 tty2
root      1130  0.0  0.0   5988   604 tty3     Ss+  19:20   0:00 /sbin/getty -8 38400 tty3
root      1132  0.0  0.0   5988   604 tty6     Ss+  19:20   0:00 /sbin/getty -8 38400 tty6
root      1140  0.0  0.0   4352  1128 ?        Ss   19:20   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1201  0.0  0.0   4004   624 ?        S    19:20   0:00 /bin/sh /usr/bin/mysqld_safe
root      1210  0.0  0.0  22180  1236 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      1215  0.0  0.0  22180  1236 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root      1224  0.0  0.0  22180  1236 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root      1260  0.0  0.0  18708   992 ?        Ss   19:20   0:00 cron
daemon    1261  0.0  0.0  16512   472 ?        Ss   19:20   0:00 atd
mysql     1322  0.1  1.1 178112 24564 ?        Sl   19:20   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1323  0.0  0.0   3908   624 ?        S    19:20   0:00 logger -t mysqld -p daemon.error
root      1325  0.0  0.0  22180  1240 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
107       1335  0.0  0.0  26080  1216 ?        S    19:20   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1340  0.0  0.0  22180  1244 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sr1 (every 2 sec)
root      1342  0.0  0.0  22180  1244 ?        S    19:20   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1344  0.0  0.0  22180  1236 ?        S    19:20   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event1 /dev/input/event0 /dev/input/event5
root      1576  0.0  0.1  75148  2840 ?        Ss   19:20   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1744  0.0  0.4 171728  8540 ?        Ss   19:20   0:00 /usr/sbin/apache2 -k start
www-data  1749  0.0  0.2 171728  4944 ?        S    19:20   0:00 /usr/sbin/apache2 -k start
www-data  1750  0.0  0.2 171728  4944 ?        S    19:20   0:00 /usr/sbin/apache2 -k start
www-data  1751  0.0  0.2 171728  4944 ?        S    19:20   0:00 /usr/sbin/apache2 -k start
www-data  1753  0.0  0.2 171728  4944 ?        S    19:20   0:00 /usr/sbin/apache2 -k start
www-data  1755  0.0  0.2 171728  4944 ?        S    19:20   0:00 /usr/sbin/apache2 -k start
root      1886  0.0  0.0   4004   648 ?        S    19:20   0:00 /bin/sh /etc/init.d/ondemand background
root      1894  0.0  0.0   8168   592 ?        S    19:20   0:00 sleep 60
root      1907  0.0  0.0   5988   604 tty1     Ss+  19:20   0:00 /sbin/getty -8 38400 tty1
root      2007  0.0  0.1  74812  3732 ?        Ss   19:20   0:00 gdm-binary
root      2014  0.0  0.1  76852  3916 ?        S    19:20   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      2015  4.9  1.3 899412 27496 tty7     Ss+  19:20   0:02 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-sgdpZl/database -nolisten tcp vt7
gdm       2052  0.0  0.0  26156   780 ?        S    19:20   0:00 /usr/bin/dbus-launch --exit-with-session
root      2057  0.0  0.1  47032  2792 ?        S    19:20   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      2098  0.0  0.0   3924   700 ?        Ss   19:20   0:00 anacron -s
root      2119  0.0  0.1  89288  3396 ?        S    19:20   0:00 /usr/lib/gdm/gdm-session-worker
ntp       2151  0.0  0.0  25620  1432 ?        Ss   19:20   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:121 -g
bas       2179  0.0  0.1 162332  3820 ?        Sl   19:21   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
bas       2194  0.1  0.3 170984  7604 ?        Ssl  19:21   0:00 gnome-session
bas       2234  0.0  0.0  36060   704 ?        Ss   19:21   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
bas       2237  0.2  0.0  23984  1492 ?        Ss   19:21   0:00 /bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
bas       2238  0.0  0.0  26156   772 ?        S    19:21   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
bas       2242  0.1  0.2 206560  5004 ?        Ssl  19:21   0:00 /usr/bin/pulseaudio --start
bas       2247  0.0  0.1  94308  3420 ?        S    19:21   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
bas       2249  0.3  0.3  46340  6208 ?        S    19:21   0:00 /usr/lib/libgconf2-4/gconfd-2
bas       2259  0.0  0.4 197068  8412 ?        Ss   19:21   0:00 seahorse-daemon
bas       2261  0.1  0.4 310948 10172 ?        Ssl  19:21   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
bas       2266  0.0  0.1  43208  2344 ?        S    19:21   0:00 /usr/lib/gvfs/gvfsd
bas       2272  0.0  0.3 169028  7368 ?        S    19:21   0:00 /usr/lib/notify-osd/notify-osd
bas       2273  0.0  0.1  75492  2768 ?        Ssl  19:21   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/bas/.gvfs
bas       2286  0.0  0.0   4004   640 ?        S    19:21   0:00 /bin/sh /usr/bin/compiz
bas       2354  1.5  2.6 305944 55268 ?        S    19:21   0:00 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 10a4e97a9b3d46e0a5126530766730966300000021940025 --loose-binding move resize place decoration animation ccp
bas       2355  1.2  1.1 342820 23852 ?        S    19:21   0:00 gnome-panel
bas       2356  0.0  0.0   4004   556 ?        Ss   19:21   0:00 /bin/sh -c /usr/bin/compiz-decorator
bas       2357  0.3  0.5 180116 10972 ?        S    19:21   0:00 /usr/bin/gtk-window-decorator
bas       2359  2.1  2.2 698052 45652 ?        Sl   19:21   0:00 nautilus
bas       2361  0.0  0.1 152380  3980 ?        Ssl  19:21   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
bas       2363  0.0  0.0   4004   580 ?        S    19:21   0:00 /bin/sh /usr/bin/gnome-do
bas       2372  0.3  0.6 228208 13312 ?        S    19:21   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
bas       2381  0.0  0.3 166976  7768 ?        S    19:21   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
bas       2382  2.2  1.7 346772 35736 ?        Sl   19:21   0:00 /usr/bin/cli /usr/lib/gnome-do/Do.exe
bas       2386  0.4  0.6 261248 13400 ?        S    19:21   0:00 gnome-volume-control-applet
bas       2390  0.0  0.1  54260  3272 ?        S    19:21   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      2395  0.4  0.1  42560  3172 ?        S    19:21   0:00 /usr/lib/devicekit-disks/devkit-disks-daemon
bas       2396  0.0  0.3 158852  8132 ?        S    19:21   0:00 bluetooth-applet
root      2398  0.0  0.0  42180   832 ?        S    19:21   0:00 devkit-disks-daemon: polling /dev/sr0 /dev/sr1 /dev/sde /dev/sdc /dev/sdd /dev/sdf
bas       2400  0.0  0.1  49692  3032 ?        S    19:21   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
bas       2401  0.0  0.3 165172  7916 ?        S    19:21   0:00 update-notifier --startup-delay=60
bas       2402  0.0  0.4 161060  8276 ?        S    19:21   0:00 gnome-power-manager
bas       2404  0.1  0.6 400568 13340 ?        Sl   19:21   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
bas       2407  0.2  0.9 226092 19540 ?        S    19:21   0:00 python /usr/share/system-config-printer/applet.py
bas       2412  0.6  0.8 213644 16712 ?        S    19:21   0:00 nm-applet --sm-disable
bas       2413  0.0  0.3 151624  6500 ?        S    19:21   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
root      2418  0.0  0.1  53704  3916 ?        S    19:21   0:00 /usr/lib/policykit-1/polkitd
bas       2420  0.0  0.1  50504  2500 ?        S    19:21   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
bas       2434  0.4  0.7 241504 14512 ?        S    19:21   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=19
bas       2436  0.4  0.7 242712 16040 ?        S    19:21   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=26
bas       2444  0.0  0.1 175176  3072 ?        Ss   19:21   0:00 gnome-screensaver
bas       2459  0.1  0.1  64724  3968 ?        S    19:21   0:00 /usr/lib/indicator-messages/indicator-messages-service
bas       2460  0.2  0.7 235860 14712 ?        Sl   19:21   0:00 /usr/bin/python /usr/lib/pymodules/python2.6/rabbitvcs/dbus/service.pyc
bas       2463  0.0  0.1  95376  3728 ?        S    19:21   0:00 /usr/lib/indicator-session/indicator-status-service
bas       2465  0.0  0.1  42160  2360 ?        S    19:21   0:00 /usr/lib/indicator-session/indicator-users-service
bas       2467  0.0  0.1  51080  3040 ?        S    19:21   0:00 /usr/lib/indicator-session/indicator-session-service
bas       2493  0.0  0.0  34636  1840 ?        S    19:21   0:00 /usr/lib/gvfs/gvfsd-metadata
bas       2496  0.0  0.1  43212  2464 ?        S    19:21   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
bas       2502  1.7  0.7 208680 16428 ?        Sl   19:21   0:00 gnome-terminal
bas       2503  0.0  0.0  14396   784 ?        S    19:21   0:00 gnome-pty-helper
bas       2504  0.3  0.2  21624  4396 pts/0    Ss   19:21   0:00 bash
bas       2527  0.0  0.0  15164  1136 pts/0    R+   19:21   0:00 ps aux
```
As you can see fsck is running. At the bootscreen Ubuntu indicated that it was checking my disk, but after a few seconds it disappeared and the GDM login screen appeared. I logged in and fired up a terminal to retrieve this process list with 'ps aux'. Previous versions of Ubuntu always paused at the login screen until the checking was done.

---

### Post by quixote on 2010-02-07
Very unsettling that fsck should be running somehow in background.  I'd always understood that if it ran on a mounted drive, it could corrupt it.  

Maybe this is some sort of bug?  I just saw another thread with people reporting background fsck.  Of course, now I can't find the link.  I'll add it later if and when I find it.

---

### Post by petehall on 2010-04-27
This is by design in 9.10

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604)

I know, I don't like it either.

Basically, the old way of doing things was that the entire boot process would be paused while fsck ran. The new way of doing things is to only pause the boot process for fscking the root partition. For any additional drives, the process runs in parallel, and the drive won't be mounted until fsck has finished.

So there's no risk of data corruption, but it does mean that if you aren't aware of what's going on, you can get into a right panic thinking that one of your drives is missing.

Pete

---

### Post by rnerwein on 2010-04-27
hi 
have a look at the man pages for --> tune2fs
there is an option called: max-mount-counts - this number tells the system, when it is reached, to force a fsck even 
the --> Filesystem state is set to clean.
you can alter this value by using the -c option whith the command.
see man pages for further information.
hint: if you use this command even set down the  Reserved block count  by using the -m option.
      the default is 5% of partiton size. set it down to 1 ( 1% ) that will give you 20GB more disk space for free :-)
ciao

---

### Post by quixote on 2010-04-27
By design, hm?  Interesting.  Then they should have also designed a quiet little text messsage at the bottom saying "(Currently checking /dev/sda-whatnot in background)".  Honestly.  Some devs seem to have as much concept of user issues as an alien who communicates using microwaves.

Thanks for the info!

---

