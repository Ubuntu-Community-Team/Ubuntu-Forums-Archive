---
title: "why is my computer idling at 50% CPU load?"
date: 2010-12-06
forum: General Help
---

### Post by mdgtptrl on 2010-12-06
I'm sitting here watching the resources screen in system monitor :popcorn: (exciting night) and the CPU load is oscillating about 50%... but if i flip over to processes, there's less than 20% load... what's happening?

in addition, the full screen screenshot works just fine. But if i try to do the window screenshot, the top half comes out black. What's with that?

pictures attached

---

### Post by loell on 2010-12-06
my hunch,
it's video related issue, it probably uses 50% of the CPU when displaying those graphs (it's Gtk Cairo that depends on video hardware acceleration when needed.)

what's your video card if any?

---

### Post by wilee-nilee on 2010-12-06
open a terminal and type in ```
top
``` the hit enter it will tell you whats running.

---

### Post by mdgtptrl on 2010-12-06
> **loell said:**
> my hunch,
it's video related issue, it probably uses 50% of the CPU when displaying those graphs (it's Gtk Cairo that depends on video hardware acceleration when needed.)

what's your video card if any?Radeon X850XT which uses an R480 I believe... what can i say, it IS a 6 or 7 year old system :P

> **wilee-nilee said:**
> open a terminal and type in ```
top
``` the hit enter it will tell you whats running.huh, I was expecting top and system monitor to show the same stuff. They're very similar, but top shows a few more things. Top also has palimpsest and gnome-system-monitor as the top two, then Xorg, then md0_resync and md0_raid1 ([i'm running a software raid and having some issues]("http://ubuntuforums.org/showthread.php?t=1638631"))

How can i get top to spit out a full list of processes, instead of a limited, updating list? 
EDIT: oh, "ps aux". As soon as firefox on my ubuntu machine stops being dumb, i'll put up the whole output
EDIT2:
```
root      1110  0.0  0.0   2116   880 ?        Ss   22:40   0:00 acpid -c /etc/a
cpi/events -s /var/run/acpid.socket
root      1112  0.0  0.0   2460   864 ?        Ss   22:40   0:00 cron
daemon    1113  0.0  0.0   2320   356 ?        Ss   22:40   0:00 atd
root      1122 21.4  1.0  31844 21904 tty7     Rs+  22:40  13:43 /usr/bin/X :0 -
nr -verbose -auth /var/run/gdm/auth-for-gdm-apX0XW/database -nolisten tcp vt7
root      1151  0.0  0.0   2300   632 ?        Ss   22:40   0:00 /sbin/mdadm --m
onitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
root      1164  0.0  0.0   1960   544 ?        S    22:40   0:00 /usr/sbin/cnid_
metad
root      1166  0.0  0.0   3436  1148 ?        S    22:40   0:00 /usr/sbin/afpd 
-U uams_dhx2.so,uams_clrtxt.so -g nobody -c 20 -n kermit
root      1225  0.0  0.1  19868  3008 ?        Sl   22:40   0:00 /usr/lib/gdm/gd
m-session-worker
danny     1267  0.0  0.3  34804  7092 ?        Ssl  22:40   0:00 gnome-session
danny     1301  0.0  0.0   3352   200 ?        Ss   22:40   0:00 /usr/bin/ssh-ag
ent /usr/bin/dbus-launch --exit-with-session gnome-session
danny     1304  0.0  0.0   3460   560 ?        S    22:40   0:00 /usr/bin/dbus-l
aunch --exit-with-session gnome-session
danny     1307  0.0  0.0   4408  1724 ?        Ss   22:40   0:00 /bin/dbus-daemo
n --fork --print-pid 5 --print-address 7 --session
root      1375  0.0  0.0   1860   560 tty1     Ss+  22:40   0:00 /sbin/getty -8 
38400 tty1
danny     1378  0.0  0.2   9260  4192 ?        S    22:40   0:00 /usr/lib/libgco
nf2-4/gconfd-2
danny     1390  0.0  0.3  28524  7728 ?        Sl   22:40   0:00 gnome-power-man
ager
danny     1395  0.1  0.7 142692 15088 ?        Ssl  22:40   0:03 /usr/lib/gnome-
settings-daemon/gnome-settings-daemon
danny     1397  0.0  0.1  24828  2140 ?        Sl   22:40   0:00 /usr/bin/gnome-
keyring-daemon --start --components=pkcs11
root      1401  0.0  0.1   8432  3168 ?        S    22:40   0:00 /usr/lib/upower
/upowerd
root      1424  0.0  0.2   9152  4368 ?        S    22:40   0:01 /usr/lib/policy
kit-1/polkitd
danny     1509  0.0  0.1   7536  2300 ?        S    22:40   0:00 /usr/lib/gvfs/g
vfsd
danny     1514  0.0  0.1  30748  2248 ?        Ssl  22:40   0:00 /usr/lib/gvfs//
gvfs-fuse-daemon /home/danny/.gvfs
danny     1535  0.0  0.5 114692 11524 ?        Sl   22:40   0:00 nm-applet --sm-
disable
danny     1539  0.0  0.7  77176 15872 ?        Sl   22:40   0:02 gnome-panel
danny     1540  0.0  0.4  38456  9156 ?        Sl   22:40   0:00 /usr/lib/evolut
ion/2.30/evolution-alarm-notify
danny     1541  0.2  0.6 149240 13808 ?        Sl   22:40   0:08 metacity --repl
ace
danny     1543  0.2  1.3 126368 27004 ?        Sl   22:40   0:09 nautilus
danny     1545  0.0  0.3  27776  7440 ?        Sl   22:40   0:00 bluetooth-apple
t
danny     1548  0.0  0.5  72892 12328 ?        Sl   22:40   0:00 /usr/lib/policy
kit-1-gnome/polkit-gnome-authentication-agent-1
danny     1551  0.0  0.2  95676  5056 ?        S<sl 22:40   0:00 /usr/bin/pulsea
udio --start --log-target=syslog
rtkit     1553  0.0  0.0  22996  1188 ?        SNl  22:40   0:00 /usr/lib/rtkit/
rtkit-daemon
danny     1598  0.0  0.1  20684  3272 ?        Sl   22:40   0:00 /usr/lib/pulsea
udio/pulse/gconf-helper
danny     1601  0.0  0.1   8012  3100 ?        S    22:40   0:00 /usr/lib/gvfs/g
vfsd-trash --spawner :1.13 /org/gtk/gvfs/exec_spaw/0
danny     1605  0.0  0.1  26816  3648 ?        Ss   22:40   0:00 gnome-screensav
er
danny     1607  0.0  0.1  50540  3476 ?        Ssl  22:40   0:00 /usr/lib/bonobo
-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
danny     1623  0.1  0.7  76912 15572 ?        Sl   22:40   0:06 /usr/lib/gnome-
panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=2
2
danny     1624  0.0  0.5  74100 11244 ?        Sl   22:40   0:00 /usr/lib/gnome-
applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --
oaf-ior-fd=28
danny     1626  0.3  0.1  33520  3664 ?        S    22:40   0:14 /usr/lib/gvfs/g
vfs-gdu-volume-monitor
root      1628  0.5  0.1  16324  3468 ?        Sl   22:40   0:22 /usr/lib/udisks
/udisks-daemon
root      1629  0.0  0.0   5616   728 ?        S    22:40   0:00 udisks-daemon: 
polling /dev/sr0 /dev/sr1
danny     1633  0.0  0.1  17992  2212 ?        Sl   22:40   0:00 /usr/lib/gvfs/g
vfs-afc-volume-monitor
danny     1636  0.0  0.1   8176  2108 ?        S    22:40   0:00 /usr/lib/gvfs/g
vfs-gphoto2-volume-monitor
danny     1639  0.0  0.0   1900   496 ?        Ss   22:40   0:00 /bin/sh -c /usr
/bin/compiz-decorator
danny     1640  0.0  0.4  28388  9700 ?        Sl   22:40   0:01 /usr/bin/gtk-wi
ndow-decorator
danny     1654  0.0  0.6  83292 13492 ?        Sl   22:40   0:00 /usr/lib/indica
tor-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwit
chApplet_Factory --oaf-ior-fd=23
danny     1655  0.0  0.6  39816 14296 ?        Sl   22:40   0:01 /usr/lib/gnome-
panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior
-fd=32
danny     1656  0.0  0.6  83108 13516 ?        Sl   22:40   0:00 /usr/lib/indica
tor-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Fact
ory --oaf-ior-fd=38
danny     1657  0.0  0.4  31112  9076 ?        Sl   22:40   0:00 /usr/lib/gnome-
panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaA
pplet_Factory --oaf-ior-fd=44
danny     1670  0.0  0.0   7280  1960 ?        S    22:40   0:00 /usr/lib/gvfs/g
vfsd-metadata
danny     1671  0.0  0.1  15732  3612 ?        S    22:40   0:00 /usr/lib/indica
tor-application/indicator-application-service
danny     1673  0.0  0.2  86836  4712 ?        S    22:40   0:00 /usr/lib/indica
tor-sound/indicator-sound-service
danny     1675  0.0  0.2  18200  4284 ?        S    22:40   0:00 /usr/lib/indica
tor-messages/indicator-messages-service
danny     1680  0.0  0.2  27056  4976 ?        Sl   22:40   0:00 /usr/lib/indica
tor-session/indicator-session-service
danny     1682  0.0  0.1   7436  2368 ?        S    22:40   0:00 /usr/lib/gvfs/g
vfsd-burn --spawner :1.13 /org/gtk/gvfs/exec_spaw/1
danny     1684  0.0  0.2  28008  4852 ?        Sl   22:40   0:00 /usr/lib/indica
tor-me/indicator-me-service
danny     1687  0.3  0.3  19356  7048 ?        S    22:40   0:12 /usr/lib/gnome-
disk-utility/gdu-notification-daemon
danny     1692  0.0  0.7  32424 15512 ?        S    22:40   0:00 /usr/bin/python
 /usr/share/system-config-printer/applet.py
danny     1700  0.3  0.5  71976 11924 ?        Sl   22:41   0:12 update-notifier
danny     1705 14.1  1.0  81480 21464 ?        Sl   22:45   8:22 gnome-system-mo
nitor
root      1710  0.0  0.3  13936  8072 ?        S    22:47   0:00 /usr/bin/python
 /usr/lib/system-service/system-service-d
root      1721  0.0  0.0   2844  1272 ?        S<   22:50   0:00 udevd --daemon
danny     1906  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/li
b/firefox-3.6.10/firefox
danny     1910  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/li
b/firefox-3.6.10/run-mozilla.sh /usr/lib/firefox-3.6.10/firefox-bin
danny     1914  3.4  3.1 332624 64592 ?        Sl   23:13   1:03 /usr/lib/firefo
x-3.6.10/firefox-bin
danny     1997 11.9  0.7  68088 15896 ?        S    23:22   2:39 palimpsest
root      2043  2.1  0.0      0     0 ?        S    23:30   0:18 [md0_raid1]
root      2045  0.0  0.0   2844  1200 ?        S<   23:30   0:00 udevd --daemon
root      2046  2.2  0.0      0     0 ?        D    23:30   0:19 [md0_resync]
danny     2099  0.0  0.1  16084  2900 ?        S    23:31   0:00 /usr/lib/gvfs/g
vfsd-computer --spawner :1.13 /org/gtk/gvfs/exec_spaw/2
root      2122  0.0  0.0      0     0 ?        S    23:33   0:00 [jbd2/md0p1-8]
root      2123  0.0  0.0      0     0 ?        S    23:33   0:00 [ext4-dio-unwri
t]
danny     2152  0.3  0.6  90132 13408 ?        Sl   23:35   0:01 gnome-terminal
danny     2155  0.0  0.0   2056   696 ?        S    23:35   0:00 gnome-pty-helpe
r
danny     2156  0.0  0.1   6876  3516 pts/0    Ss   23:35   0:00 bash
danny     2206  0.0  0.0   4592  1072 pts/0    R+   23:44   0:00 ps aux
danny@kermit:~$ more output.txt
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2872  1660 ?        Ss   22:40   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    22:40   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    22:40   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    22:40   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    22:40   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    22:40   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    22:40   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    22:40   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    22:40   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    22:40   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    22:40   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    22:40   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    22:40   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    22:40   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    22:40   0:03 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    22:40   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    22:40   0:00 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    22:40   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    22:40   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    22:40   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    22:40   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    22:40   0:02 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   22:40   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    22:40   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    22:40   0:00 [ecryptfs-kthrea]
root        30  0.0  0.0      0     0 ?        S    22:40   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    22:40   0:00 [kstriped]
root        37  0.0  0.0      0     0 ?        S    22:40   0:00 [kmpathd/0]
root        38  0.0  0.0      0     0 ?        S    22:40   0:00 [kmpath_handlerd]
root        39  0.0  0.0      0     0 ?        S    22:40   0:00 [ksnapd]
root        40  0.1  0.0      0     0 ?        S    22:40   0:06 [kondemand/0]
root        41  0.0  0.0      0     0 ?        S    22:40   0:00 [kconservative/0]
root       280  0.0  0.0      0     0 ?        S    22:40   0:00 [usbhid_resumer]
root       288  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_0]
root       291  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_1]
root       294  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_2]
root       295  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_3]
root       297  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_4]
root       300  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_5]
root       349  0.0  0.0      0     0 ?        S    22:40   0:00 [jbd2/sda1-8]
root       350  0.0  0.0      0     0 ?        S    22:40   0:00 [ext4-dio-unwrit]
root       385  0.0  0.0      0     0 ?        S    22:40   0:00 [flush-8:0]
root       411  0.0  0.0   2396   608 ?        S    22:40   0:00 upstart-udev-bridge --daemon
root       423  0.0  0.0   2848  1220 ?        S<s  22:40   0:00 udevd --daemon
root       804  0.0  0.0      0     0 ?        S    22:40   0:00 [radeon/0]
root       805  0.0  0.0      0     0 ?        S    22:40   0:00 [ttm_swap]
root       846  0.2  0.0      0     0 ?        S<   22:40   0:10 [kslowd000]
root       847  0.2  0.0      0     0 ?        S<   22:40   0:10 [kslowd001]
root       897  0.0  0.0      0     0 ?        S    22:40   0:00 [jbd2/sda5-8]
root       898  0.0  0.0      0     0 ?        S    22:40   0:00 [ext4-dio-unwrit]
syslog     934  0.0  0.0  33572  1144 ?        Sl   22:40   0:00 rsyslogd -c4
102        952  0.2  0.0   3580  1848 ?        Ss   22:40   0:09 dbus-daemon --system --fork
root       961  0.0  0.1  19852  3380 ?        Ssl  22:40   0:00 gdm-binary
root       990  0.0  0.2  19480  4144 ?        Ssl  22:40   0:00 NetworkManager
avahi      991  0.0  0.0   3016  1328 ?        S    22:40   0:00 avahi-daemon: running [kermit.local]
avahi      993  0.0  0.0   3016   440 ?        S    22:40   0:00 avahi-daemon: chroot helper
root       994  0.0  0.1   4432  2392 ?        S    22:40   0:00 /usr/sbin/modem-manager
root       997  0.0  0.1  19984  2964 ?        Sl   22:40   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1065  0.0  0.0   4904  1508 ?        S    22:40   0:00 /sbin/wpa_supplicant -u -s
root      1069  0.0  0.1   6780  2416 ?        Ss   22:40   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1074  0.0  0.0   2300   988 ?        S    22:40   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-clie
nt.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp3/dhclient-5e172676-24d4-4221-a244-8ed73b9ffab2-eth1.lease -cf /v
ar/run/nm-dhclient-eth1.conf eth1
root      1076  0.0  0.1  21552  3616 ?        Sl   22:40   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/Disp
layManager/Display1
root      1092  0.0  0.0   1860   556 tty4     Ss+  22:40   0:00 /sbin/getty -8 38400 tty4
root      1098  0.0  0.0   1860   556 tty5     Ss+  22:40   0:00 /sbin/getty -8 38400 tty5
root      1105  0.0  0.0   1860   560 tty2     Ss+  22:40   0:00 /sbin/getty -8 38400 tty2
root      1106  0.0  0.0   1860   560 tty3     Ss+  22:40   0:00 /sbin/getty -8 38400 tty3
root      1108  0.0  0.0   1860   556 tty6     Ss+  22:40   0:00 /sbin/getty -8 38400 tty6
root      1110  0.0  0.0   2116   880 ?        Ss   22:40   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1112  0.0  0.0   2460   864 ?        Ss   22:40   0:00 cron
daemon    1113  0.0  0.0   2320   356 ?        Ss   22:40   0:00 atd
root      1122 21.4  1.0  31844 21904 tty7     Rs+  22:40  13:43 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm
-apX0XW/database -nolisten tcp vt7
root      1151  0.0  0.0   2300   632 ?        Ss   22:40   0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pi
d --daemonise --scan --syslog
root      1164  0.0  0.0   1960   544 ?        S    22:40   0:00 /usr/sbin/cnid_metad
root      1166  0.0  0.0   3436  1148 ?        S    22:40   0:00 /usr/sbin/afpd -U uams_dhx2.so,uams_clrtxt.so -g nobody -c
 20 -n kermit
root      1225  0.0  0.1  19868  3008 ?        Sl   22:40   0:00 /usr/lib/gdm/gdm-session-worker
danny     1267  0.0  0.3  34804  7092 ?        Ssl  22:40   0:00 gnome-session
danny     1301  0.0  0.0   3352   200 ?        Ss   22:40   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-sessio
n gnome-session
danny     1304  0.0  0.0   3460   560 ?        S    22:40   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
danny     1307  0.0  0.0   4408  1724 ?        Ss   22:40   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --
session
root      1375  0.0  0.0   1860   560 tty1     Ss+  22:40   0:00 /sbin/getty -8 38400 tty1
danny     1378  0.0  0.2   9260  4192 ?        S    22:40   0:00 /usr/lib/libgconf2-4/gconfd-2
danny     1390  0.0  0.3  28524  7728 ?        Sl   22:40   0:00 gnome-power-manager
danny     1395  0.1  0.7 142692 15088 ?        Ssl  22:40   0:03 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
danny     1397  0.0  0.1  24828  2140 ?        Sl   22:40   0:00 /usr/bin/gnome-keyring-daemon --start --components=pkcs11
root      1401  0.0  0.1   8432  3168 ?        S    22:40   0:00 /usr/lib/upower/upowerd
root      1424  0.0  0.2   9152  4368 ?        S    22:40   0:01 /usr/lib/policykit-1/polkitd
danny     1509  0.0  0.1   7536  2300 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd
danny     1514  0.0  0.1  30748  2248 ?        Ssl  22:40   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/danny/.gvfs
danny     1535  0.0  0.5 114692 11524 ?        Sl   22:40   0:00 nm-applet --sm-disable
danny     1539  0.0  0.7  77176 15872 ?        Sl   22:40   0:02 gnome-panel
danny     1540  0.0  0.4  38456  9156 ?        Sl   22:40   0:00 /usr/lib/evolution/2.30/evolution-alarm-notify
danny     1541  0.2  0.6 149240 13808 ?        Sl   22:40   0:08 metacity --replace
danny     1543  0.2  1.3 126368 27004 ?        Sl   22:40   0:09 nautilus
danny     1545  0.0  0.3  27776  7440 ?        Sl   22:40   0:00 bluetooth-applet
danny     1548  0.0  0.5  72892 12328 ?        Sl   22:40   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-age
nt-1
danny     1551  0.0  0.2  95676  5056 ?        S<sl 22:40   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1553  0.0  0.0  22996  1188 ?        SNl  22:40   0:00 /usr/lib/rtkit/rtkit-daemon
danny     1598  0.0  0.1  20684  3272 ?        Sl   22:40   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
danny     1601  0.0  0.1   8012  3100 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.13 /org/gtk/gvfs/ex
ec_spaw/0
danny     1605  0.0  0.1  26816  3648 ?        Ss   22:40   0:00 gnome-screensaver
danny     1607  0.0  0.1  50540  3476 ?        Ssl  22:40   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-a
ctivate --ior-output-fd=20
danny     1623  0.1  0.7  76912 15572 ?        Sl   22:40   0:06 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID
:GNOME_Wncklet_Factory --oaf-ior-fd=22
danny     1624  0.0  0.5  74100 11244 ?        Sl   22:40   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFI
ID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=28
danny     1626  0.3  0.1  33520  3664 ?        S    22:40   0:14 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1628  0.5  0.1  16324  3468 ?        Sl   22:40   0:22 /usr/lib/udisks/udisks-daemon
root      1629  0.0  0.0   5616   728 ?        S    22:40   0:00 udisks-daemon: polling /dev/sr0 /dev/sr1
danny     1633  0.0  0.1  17992  2212 ?        Sl   22:40   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
danny     1636  0.0  0.1   8176  2108 ?        S    22:40   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
danny     1639  0.0  0.0   1900   496 ?        Ss   22:40   0:00 /bin/sh -c /usr/bin/compiz-decorator
danny     1640  0.0  0.4  28388  9700 ?        Sl   22:40   0:01 /usr/bin/gtk-window-decorator
danny     1654  0.0  0.6  83292 13492 ?        Sl   22:40   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-a
ctivate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=23
danny     1655  0.0  0.6  39816 14296 ?        Sl   22:40   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFII
D:GNOME_ClockApplet_Factory --oaf-ior-fd=32
danny     1656  0.0  0.6  83108 13516 ?        Sl   22:40   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-
iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=38
danny     1657  0.0  0.4  31112  9076 ?        Sl   22:40   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activa
te-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=44
danny     1670  0.0  0.0   7280  1960 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-metadata
danny     1671  0.0  0.1  15732  3612 ?        S    22:40   0:00 /usr/lib/indicator-application/indicator-application-servi
ce
danny     1673  0.0  0.2  86836  4712 ?        S    22:40   0:00 /usr/lib/indicator-sound/indicator-sound-service
danny     1675  0.0  0.2  18200  4284 ?        S    22:40   0:00 /usr/lib/indicator-messages/indicator-messages-service
danny     1680  0.0  0.2  27056  4976 ?        Sl   22:40   0:00 /usr/lib/indicator-session/indicator-session-service
danny     1682  0.0  0.1   7436  2368 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.13 /org/gtk/gvfs/exe
c_spaw/1
danny     1684  0.0  0.2  28008  4852 ?        Sl   22:40   0:00 /usr/lib/indicator-me/indicator-me-service
danny     1687  0.3  0.3  19356  7048 ?        S    22:40   0:12 /usr/lib/gnome-disk-utility/gdu-notification-daemon
danny     1692  0.0  0.7  32424 15512 ?        S    22:40   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
danny     1700  0.3  0.5  71976 11924 ?        Sl   22:41   0:12 update-notifier
danny     1705 14.1  1.0  81480 21464 ?        Sl   22:45   8:22 gnome-system-monitor
root      1710  0.0  0.3  13936  8072 ?        S    22:47   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      1721  0.0  0.0   2844  1272 ?        S<   22:50   0:00 udevd --daemon
danny     1906  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/lib/firefox-3.6.10/firefox
danny     1910  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/lib/firefox-3.6.10/run-mozilla.sh /usr/lib/fi
refox-3.6.10/firefox-bin
danny     1914  3.4  3.1 332624 64592 ?        Sl   23:13   1:03 /usr/lib/firefox-3.6.10/firefox-bin
danny     1997 11.9  0.7  68088 15896 ?        S    23:22   2:39 palimpsest
root      2043  2.1  0.0      0     0 ?        S    23:30   0:18 [md0_raid1]
root      2045  0.0  0.0   2844  1200 ?        S<   23:30   0:00 udevd --daemon
root      2046  2.2  0.0      0     0 ?        D    23:30   0:19 [md0_resync]
danny     2099  0.0  0.1  16084  2900 ?        S    23:31   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.13 /org/gtk/gvfs
/exec_spaw/2
root      2122  0.0  0.0      0     0 ?        S    23:33   0:00 [jbd2/md0p1-8]
root      2123  0.0  0.0      0     0 ?        S    23:33   0:00 [ext4-dio-unwrit]
danny     2152  0.3  0.6  90132 13408 ?        Sl   23:35   0:01 gnome-terminal
danny     2155  0.0  0.0   2056   696 ?        S    23:35   0:00 gnome-pty-helper
danny     2156  0.0  0.1   6876  3516 pts/0    Ss   23:35   0:00 bash
danny     2206  0.0  0.0   4592  1072 pts/0    R+   23:44   0:00 ps aux
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ less output.txt
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ 
danny@kermit:~$ clear

danny@kermit:~$ more output.txt
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2872  1660 ?        Ss   22:40   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    22:40   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    22:40   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    22:40   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    22:40   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    22:40   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    22:40   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    22:40   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    22:40   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    22:40   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    22:40   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    22:40   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    22:40   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    22:40   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    22:40   0:03 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    22:40   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    22:40   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    22:40   0:00 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    22:40   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    22:40   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    22:40   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    22:40   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    22:40   0:02 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   22:40   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    22:40   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    22:40   0:00 [ecryptfs-kthrea]
root        30  0.0  0.0      0     0 ?        S    22:40   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    22:40   0:00 [kstriped]
root        37  0.0  0.0      0     0 ?        S    22:40   0:00 [kmpathd/0]
root        38  0.0  0.0      0     0 ?        S    22:40   0:00 [kmpath_handlerd]
root        39  0.0  0.0      0     0 ?        S    22:40   0:00 [ksnapd]
root        40  0.1  0.0      0     0 ?        S    22:40   0:06 [kondemand/0]
root        41  0.0  0.0      0     0 ?        S    22:40   0:00 [kconservative/0]
root       280  0.0  0.0      0     0 ?        S    22:40   0:00 [usbhid_resumer]
root       288  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_0]
root       291  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_1]
root       294  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_2]
root       295  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_3]
root       297  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_4]
root       300  0.0  0.0      0     0 ?        S    22:40   0:00 [scsi_eh_5]
root       349  0.0  0.0      0     0 ?        S    22:40   0:00 [jbd2/sda1-8]
root       350  0.0  0.0      0     0 ?        S    22:40   0:00 [ext4-dio-unwrit]
root       385  0.0  0.0      0     0 ?        S    22:40   0:00 [flush-8:0]
root       411  0.0  0.0   2396   608 ?        S    22:40   0:00 upstart-udev-bridge --daemon
root       423  0.0  0.0   2848  1220 ?        S<s  22:40   0:00 udevd --daemon
root       804  0.0  0.0      0     0 ?        S    22:40   0:00 [radeon/0]
root       805  0.0  0.0      0     0 ?        S    22:40   0:00 [ttm_swap]
root       846  0.2  0.0      0     0 ?        S<   22:40   0:10 [kslowd000]
root       847  0.2  0.0      0     0 ?        S<   22:40   0:10 [kslowd001]
root       897  0.0  0.0      0     0 ?        S    22:40   0:00 [jbd2/sda5-8]
root       898  0.0  0.0      0     0 ?        S    22:40   0:00 [ext4-dio-unwrit]
syslog     934  0.0  0.0  33572  1144 ?        Sl   22:40   0:00 rsyslogd -c4
102        952  0.2  0.0   3580  1848 ?        Ss   22:40   0:09 dbus-daemon --system --fork
root       961  0.0  0.1  19852  3380 ?        Ssl  22:40   0:00 gdm-binary
root       990  0.0  0.2  19480  4144 ?        Ssl  22:40   0:00 NetworkManager
avahi      991  0.0  0.0   3016  1328 ?        S    22:40   0:00 avahi-daemon: running [kermit.local]
avahi      993  0.0  0.0   3016   440 ?        S    22:40   0:00 avahi-daemon: chroot helper
root       994  0.0  0.1   4432  2392 ?        S    22:40   0:00 /usr/sbin/modem-manager
root       997  0.0  0.1  19984  2964 ?        Sl   22:40   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1065  0.0  0.0   4904  1508 ?        S    22:40   0:00 /sbin/wpa_supplicant -u -s
root      1069  0.0  0.1   6780  2416 ?        Ss   22:40   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1074  0.0  0.0   2300   988 ?        S    22:40   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-clie
nt.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp3/dhclient-5e172676-24d4-4221-a244-8ed73b9ffab2-eth1.lease -cf /v
ar/run/nm-dhclient-eth1.conf eth1
root      1076  0.0  0.1  21552  3616 ?        Sl   22:40   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/Disp
layManager/Display1
root      1092  0.0  0.0   1860   556 tty4     Ss+  22:40   0:00 /sbin/getty -8 38400 tty4
root      1098  0.0  0.0   1860   556 tty5     Ss+  22:40   0:00 /sbin/getty -8 38400 tty5
root      1105  0.0  0.0   1860   560 tty2     Ss+  22:40   0:00 /sbin/getty -8 38400 tty2
root      1106  0.0  0.0   1860   560 tty3     Ss+  22:40   0:00 /sbin/getty -8 38400 tty3
root      1108  0.0  0.0   1860   556 tty6     Ss+  22:40   0:00 /sbin/getty -8 38400 tty6
root      1110  0.0  0.0   2116   880 ?        Ss   22:40   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1112  0.0  0.0   2460   864 ?        Ss   22:40   0:00 cron
daemon    1113  0.0  0.0   2320   356 ?        Ss   22:40   0:00 atd
root      1122 21.4  1.0  31844 21904 tty7     Rs+  22:40  13:43 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm
-apX0XW/database -nolisten tcp vt7
root      1151  0.0  0.0   2300   632 ?        Ss   22:40   0:00 /sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pi
d --daemonise --scan --syslog
root      1164  0.0  0.0   1960   544 ?        S    22:40   0:00 /usr/sbin/cnid_metad
root      1166  0.0  0.0   3436  1148 ?        S    22:40   0:00 /usr/sbin/afpd -U uams_dhx2.so,uams_clrtxt.so -g nobody -c
 20 -n kermit
root      1225  0.0  0.1  19868  3008 ?        Sl   22:40   0:00 /usr/lib/gdm/gdm-session-worker
danny     1267  0.0  0.3  34804  7092 ?        Ssl  22:40   0:00 gnome-session
danny     1301  0.0  0.0   3352   200 ?        Ss   22:40   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-sessio
n gnome-session
danny     1304  0.0  0.0   3460   560 ?        S    22:40   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
danny     1307  0.0  0.0   4408  1724 ?        Ss   22:40   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --
session
root      1375  0.0  0.0   1860   560 tty1     Ss+  22:40   0:00 /sbin/getty -8 38400 tty1
danny     1378  0.0  0.2   9260  4192 ?        S    22:40   0:00 /usr/lib/libgconf2-4/gconfd-2
danny     1390  0.0  0.3  28524  7728 ?        Sl   22:40   0:00 gnome-power-manager
danny     1395  0.1  0.7 142692 15088 ?        Ssl  22:40   0:03 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
danny     1397  0.0  0.1  24828  2140 ?        Sl   22:40   0:00 /usr/bin/gnome-keyring-daemon --start --components=pkcs11
root      1401  0.0  0.1   8432  3168 ?        S    22:40   0:00 /usr/lib/upower/upowerd
root      1424  0.0  0.2   9152  4368 ?        S    22:40   0:01 /usr/lib/policykit-1/polkitd
danny     1509  0.0  0.1   7536  2300 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd
danny     1514  0.0  0.1  30748  2248 ?        Ssl  22:40   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/danny/.gvfs
danny     1535  0.0  0.5 114692 11524 ?        Sl   22:40   0:00 nm-applet --sm-disable
danny     1539  0.0  0.7  77176 15872 ?        Sl   22:40   0:02 gnome-panel
danny     1540  0.0  0.4  38456  9156 ?        Sl   22:40   0:00 /usr/lib/evolution/2.30/evolution-alarm-notify
danny     1541  0.2  0.6 149240 13808 ?        Sl   22:40   0:08 metacity --replace
danny     1543  0.2  1.3 126368 27004 ?        Sl   22:40   0:09 nautilus
danny     1545  0.0  0.3  27776  7440 ?        Sl   22:40   0:00 bluetooth-applet
danny     1548  0.0  0.5  72892 12328 ?        Sl   22:40   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-age
nt-1
danny     1551  0.0  0.2  95676  5056 ?        S<sl 22:40   0:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1553  0.0  0.0  22996  1188 ?        SNl  22:40   0:00 /usr/lib/rtkit/rtkit-daemon
danny     1598  0.0  0.1  20684  3272 ?        Sl   22:40   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
danny     1601  0.0  0.1   8012  3100 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.13 /org/gtk/gvfs/ex
ec_spaw/0
danny     1605  0.0  0.1  26816  3648 ?        Ss   22:40   0:00 gnome-screensaver
danny     1607  0.0  0.1  50540  3476 ?        Ssl  22:40   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-a
ctivate --ior-output-fd=20
danny     1623  0.1  0.7  76912 15572 ?        Sl   22:40   0:06 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID
:GNOME_Wncklet_Factory --oaf-ior-fd=22
danny     1624  0.0  0.5  74100 11244 ?        Sl   22:40   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFI
ID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=28
danny     1626  0.3  0.1  33520  3664 ?        S    22:40   0:14 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1628  0.5  0.1  16324  3468 ?        Sl   22:40   0:22 /usr/lib/udisks/udisks-daemon
root      1629  0.0  0.0   5616   728 ?        S    22:40   0:00 udisks-daemon: polling /dev/sr0 /dev/sr1
danny     1633  0.0  0.1  17992  2212 ?        Sl   22:40   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
danny     1636  0.0  0.1   8176  2108 ?        S    22:40   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
danny     1639  0.0  0.0   1900   496 ?        Ss   22:40   0:00 /bin/sh -c /usr/bin/compiz-decorator
danny     1640  0.0  0.4  28388  9700 ?        Sl   22:40   0:01 /usr/bin/gtk-window-decorator
danny     1654  0.0  0.6  83292 13492 ?        Sl   22:40   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-a
ctivate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=23
danny     1655  0.0  0.6  39816 14296 ?        Sl   22:40   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFII
D:GNOME_ClockApplet_Factory --oaf-ior-fd=32
danny     1656  0.0  0.6  83108 13516 ?        Sl   22:40   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-
iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=38
danny     1657  0.0  0.4  31112  9076 ?        Sl   22:40   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activa
te-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=44
danny     1670  0.0  0.0   7280  1960 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-metadata
danny     1671  0.0  0.1  15732  3612 ?        S    22:40   0:00 /usr/lib/indicator-application/indicator-application-servi
ce
danny     1673  0.0  0.2  86836  4712 ?        S    22:40   0:00 /usr/lib/indicator-sound/indicator-sound-service
danny     1675  0.0  0.2  18200  4284 ?        S    22:40   0:00 /usr/lib/indicator-messages/indicator-messages-service
danny     1680  0.0  0.2  27056  4976 ?        Sl   22:40   0:00 /usr/lib/indicator-session/indicator-session-service
danny     1682  0.0  0.1   7436  2368 ?        S    22:40   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.13 /org/gtk/gvfs/exe
c_spaw/1
danny     1684  0.0  0.2  28008  4852 ?        Sl   22:40   0:00 /usr/lib/indicator-me/indicator-me-service
danny     1687  0.3  0.3  19356  7048 ?        S    22:40   0:12 /usr/lib/gnome-disk-utility/gdu-notification-daemon
danny     1692  0.0  0.7  32424 15512 ?        S    22:40   0:00 /usr/bin/python /usr/share/system-config-printer/applet.py
danny     1700  0.3  0.5  71976 11924 ?        Sl   22:41   0:12 update-notifier
danny     1705 14.1  1.0  81480 21464 ?        Sl   22:45   8:22 gnome-system-monitor
root      1710  0.0  0.3  13936  8072 ?        S    22:47   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      1721  0.0  0.0   2844  1272 ?        S<   22:50   0:00 udevd --daemon
danny     1906  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/lib/firefox-3.6.10/firefox
danny     1910  0.0  0.0   1900   512 ?        S    23:13   0:00 /bin/sh /usr/lib/firefox-3.6.10/run-mozilla.sh /usr/lib/fi
refox-3.6.10/firefox-bin
danny     1914  3.4  3.1 332624 64592 ?        Sl   23:13   1:03 /usr/lib/firefox-3.6.10/firefox-bin
danny     1997 11.9  0.7  68088 15896 ?        S    23:22   2:39 palimpsest
root      2043  2.1  0.0      0     0 ?        S    23:30   0:18 [md0_raid1]
root      2045  0.0  0.0   2844  1200 ?        S<   23:30   0:00 udevd --daemon
root      2046  2.2  0.0      0     0 ?        D    23:30   0:19 [md0_resync]
danny     2099  0.0  0.1  16084  2900 ?        S    23:31   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.13 /org/gtk/gvfs
/exec_spaw/2
root      2122  0.0  0.0      0     0 ?        S    23:33   0:00 [jbd2/md0p1-8]
root      2123  0.0  0.0      0     0 ?        S    23:33   0:00 [ext4-dio-unwrit]
danny     2152  0.3  0.6  90132 13408 ?        Sl   23:35   0:01 gnome-terminal
danny     2155  0.0  0.0   2056   696 ?        S    23:35   0:00 gnome-pty-helper
danny     2156  0.0  0.1   6876  3516 pts/0    Ss   23:35   0:00 bash
danny     2206  0.0  0.0   4592  1072 pts/0    R+   23:44   0:00 ps aux

```

---

