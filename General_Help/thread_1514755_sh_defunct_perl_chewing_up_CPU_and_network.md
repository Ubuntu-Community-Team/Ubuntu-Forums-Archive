---
title: "sh defunct perl chewing up CPU and network"
date: 2010-06-21
forum: General Help
---

### Post by coyoteboy on 2010-06-21
I've been having recurring problems with something on 9.10, I can't identify what, chewing up 100% cpu usage and leaving loads of defunct perl and sh processes. I've been unable to identify what might be the cause of it, it started after installation of squid (but not having it active yet). Whatever it is is obviously jamming the CPU up but also appears to be eating up network bandwidth, strangely disabling all the other (windows) computers on the network by grinding their connections to a halt, but according to the network activity monitor it's not actually DL/ULing anything significant on the server? All the other machines still get IP addresses (handed out by router, except the server who's fixed in its own pool). If I kill all the defunct processes and their parents (one of note was kthreadd) everything returns to normal, but half an hour later the whole process starts again. It doesn't seem to be linked with any cron jobs and once it occurs I have no remote access to the server.

At the same time as the addition of squid I also updated the kernel with the latest update, which I had been putting off for fear of stability problems! :)

Any help in finding the right direction to narrow this down rapidly without having to get a man on the ground to hard reboot the system every 30 minutes? I have SSH on a non-standard port and a range of 10 other open ports with various services behind them but none of those seem to be causing the clogging. I wonder if I'm being bombarded? Denyhosts isn't reporting any notable increase in bannings (usually about 1 or 2 a week).

---

### Post by coyoteboy on 2010-06-21
All the perl processes are started by www-data and despite killing apache it still spawns more. A killall -s9 -u www-data gets rid of them and without apache running it seems to not return - is this a bug in apache?

---

### Post by coyoteboy on 2010-06-22
```
A ps -ef returns:
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun15 ?        00:00:03 /sbin/init
root         2     0  0 Jun15 ?        00:00:00 [kthreadd]
root         3     2  0 Jun15 ?        00:00:00 [migration/0]
root         4     2  0 Jun15 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 Jun15 ?        00:00:00 [watchdog/0]
root         6     2  0 Jun15 ?        00:00:01 [events/0]
root         7     2  0 Jun15 ?        00:00:00 [cpuset]
root         8     2  0 Jun15 ?        00:00:00 [khelper]
root         9     2  0 Jun15 ?        00:00:00 [netns]
root        10     2  0 Jun15 ?        00:00:00 [async/mgr]
root        11     2  0 Jun15 ?        00:00:00 [kintegrityd/0]
root        12     2  0 Jun15 ?        00:00:00 [kblockd/0]
root        13     2  0 Jun15 ?        00:00:00 [kacpid]
root        14     2  0 Jun15 ?        00:00:00 [kacpi_notify]
root        15     2  0 Jun15 ?        00:00:00 [kacpi_hotplug]
root        16     2  0 Jun15 ?        00:00:27 [ata/0]
root        17     2  0 Jun15 ?        00:00:00 [ata_aux]
root        18     2  0 Jun15 ?        00:00:00 [ksuspend_usbd]
root        19     2  0 Jun15 ?        00:00:00 [khubd]
root        20     2  0 Jun15 ?        00:00:00 [kseriod]
root        21     2  0 Jun15 ?        00:00:00 [kmmcd]
root        22     2  0 Jun15 ?        00:00:00 [bluetooth]
root        23     2  0 Jun15 ?        00:00:00 [khungtaskd]
root        25     2  0 Jun15 ?        00:00:01 [pdflush]
root        26     2  0 Jun15 ?        00:00:14 [kswapd0]
root        27     2  0 Jun15 ?        00:00:00 [aio/0]
root        28     2  0 Jun15 ?        00:00:00 [ecryptfs-kthrea]
root        29     2  0 Jun15 ?        00:00:00 [crypto/0]
root        33     2  0 Jun15 ?        00:00:00 [scsi_eh_0]
root        34     2  0 Jun15 ?        00:00:40 [scsi_eh_1]
root        36     2  0 Jun15 ?        00:00:00 [kstriped]
root        37     2  0 Jun15 ?        00:00:00 [kmpathd/0]
root        38     2  0 Jun15 ?        00:00:00 [kmpath_handlerd]
root        39     2  0 Jun15 ?        00:00:00 [ksnapd]
root        40     2  0 Jun15 ?        00:00:00 [kondemand/0]
root        41     2  0 Jun15 ?        00:00:00 [kconservative/0]
root        42     2  0 Jun15 ?        00:00:00 [krfcommd]
root       243     2  0 Jun15 ?        00:00:00 [scsi_eh_2]
root       272     2  0 Jun15 ?        00:00:00 [scsi_eh_3]
root       358     2  0 Jun15 ?        00:00:02 [kjournald2]
root       417     1  0 Jun15 ?        00:00:00 upstart-udev-bridge --daemon
root       419     1  0 Jun15 ?        00:00:00 udevd --daemon
root       644     2  0 Jun15 ?        00:00:00 [kpsmoused]
root       715     1  0 Jun15 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
102        723     1  0 Jun15 ?        00:00:01 dbus-daemon --system --fork
107        736     1  0 Jun15 ?        00:00:02 hald --daemon=yes
avahi      741     1  0 Jun15 ?        00:00:00 avahi-daemon: running [server.local]
avahi      742   741  0 Jun15 ?        00:00:00 avahi-daemon: chroot helper
root       743     1  0 Jun15 ?        00:00:00 NetworkManager
root       752     1  0 Jun15 ?        00:00:00 /usr/sbin/modem-manager
root       755     1  0 Jun15 ?        00:00:00 /usr/sbin/console-kit-daemon
root       818     2  0 Jun15 ?        00:00:00 [kgameportd]
root       839   736  0 Jun15 ?        00:00:00 hald-runner
root       873     1  0 Jun15 ?        00:00:00 /sbin/wpa_supplicant -u -s
root       921     2  0 Jun15 ?        00:00:00 [kjournald]
107       1173   839  0 Jun15 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1203   839  0 Jun15 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event4 /dev/input/event2 /dev/input/event0
root      1217   839  0 Jun15 ?        00:00:21 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1241     1  0 Jun15 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1246     1  0 Jun15 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1252     1  0 Jun15 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1262     1  0 Jun15 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1266     1  0 Jun15 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1274     1  0 Jun15 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1290     1  0 Jun15 ?        00:00:00 atd
root      1291     1  0 Jun15 ?        00:00:00 cron
root      1307     1  0 Jun15 ?        00:00:00 /usr/sbin/sshd
root      1536     1  0 Jun15 ?        00:00:24 ddclient - sleeping for 240 seconds
116       2223     1  0 Jun15 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
root      2327     1  0 Jun15 ?        00:00:00 /usr/sbin/hddtemp -d -l 192.168.1.67 -p 7634 -s | /dev/sg0 /dev/sg1 /dev/sg2 /dev/sda /dev/sdb /dev/sdc
root      2376     1  0 Jun15 ?        00:00:01 /usr/sbin/nmbd -D
root      2380     1  0 Jun15 ?        00:00:00 /usr/sbin/smbd -D
root      2391  2380  0 Jun15 ?        00:00:00 /usr/sbin/smbd -D
root      2398     1  0 Jun15 ?        00:00:17 /usr/sbin/sensord -f daemon
ntp       2461     1  0 Jun15 ?        00:00:07 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 117:124 -g
root      2565     1  0 Jun15 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      2713     2  0 Jun15 ?        00:00:00 [kdmflush]
root      2717     2  0 Jun15 ?        00:00:00 [kdmflush]
root      2826     1  0 Jun15 ?        00:00:01 /usr/bin/perl /usr/local/src/webmin-1.510/miniserv.pl /etc/webmin/miniserv.conf
root      2833     1  0 Jun15 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      2841     2  0 Jun15 ?        00:00:00 [kjournald]
root      2882     1  0 Jun15 ?        00:00:00 gdm-binary
root      2889  2882  0 Jun15 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      2890  2889  1 Jun15 tty7     01:39:36 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-ef5a7g/database -nolisten tcp vt7
gdm       2927     1  0 Jun15 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session
root      2932     1  0 Jun15 ?        00:00:00 /usr/lib/devicekit-power/devkit-power-daemon
root      2984  2889  0 Jun15 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
james     3015     1  0 Jun15 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
james     3030  2984  0 Jun15 ?        00:00:00 gnome-session
james     3071  3030  0 Jun15 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
james     3074     1  0 Jun15 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
james     3075     1  0 Jun15 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
james     3079     1  0 Jun15 ?        00:00:00 /usr/bin/pulseaudio --start
james     3082  3079  0 Jun15 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
james     3084     1  0 Jun15 ?        00:00:02 /usr/lib/libgconf2-4/gconfd-2
james     3095     1  0 Jun15 ?        00:00:23 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
james     3096     1  0 Jun15 ?        00:00:00 seahorse-daemon
james     3101     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs/gvfsd
james     3106     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/james/.gvfs
james     3110     1  0 Jun15 ?        00:00:00 /usr/lib/notify-osd/notify-osd
james     3119  3030  0 Jun15 ?        00:00:00 /bin/sh /usr/bin/compiz
james     3188  3119  0 Jun15 ?        00:59:19 /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-client-id 108a24079b5d4cb85f12766146037939300000030300022 --loose-binding move resize place decoration animation ccp
james     3189  3030  0 Jun15 ?        00:00:23 gnome-panel
james     3190  3030  0 Jun15 ?        00:00:02 nautilus
james     3192     1  0 Jun15 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
james     3195  3030  0 Jun15 ?        00:00:00 nm-applet --sm-disable
james     3196  3030  0 Jun15 ?        00:00:00 /usr/lib/evolution/2.28/evolution-alarm-notify
james     3201  3030  0 Jun15 ?        00:00:00 python /usr/share/system-config-printer/applet.py
james     3204  3030  0 Jun15 ?        00:00:00 bluetooth-applet
james     3205  3030  0 Jun15 ?        00:00:02 gnome-power-manager
james     3206  3030  0 Jun15 ?        00:00:00 gnome-volume-control-applet
james     3209  3030  0 Jun15 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
james     3211  3030  0 Jun15 ?        00:00:10 update-notifier --startup-delay=60
james     3214  3030  0 Jun15 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
root      3217     1  0 Jun15 ?        00:00:00 /usr/lib/policykit-1/polkitd
james     3218     1  0 Jun15 ?        00:00:07 gnome-screensaver
root      3220     1  0 Jun15 ?        00:00:00 /usr/lib/devicekit-disks/devkit-disks-daemon
root      3221  3220  0 Jun15 ?        00:02:27 devkit-disks-daemon: polling /dev/sr0       
james     3228     1  0 Jun15 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
james     3230     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
james     3232     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
james     3234     1  0 Jun15 ?        00:00:01 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
james     3235  3188  0 Jun15 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
james     3236  3235  0 Jun15 ?        00:00:04 /usr/bin/gtk-window-decorator
james     3244     1  0 Jun15 ?        00:14:41 /usr/lib/cpufire-applet/cpufire_applet --oaf-activate-iid=OAFIID:CPUFire_Applet_Factory --oaf-ior-fd=19
james     3246     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=26
james     3248     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=32
james     3250     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-session/indicator-status-service
james     3252     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-session/indicator-users-service
james     3254     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-session/indicator-session-service
james     3256     1  0 Jun15 ?        00:00:00 /usr/lib/indicator-messages/indicator-messages-service
james     3268     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
james     3270     1  0 Jun15 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
root      3277     1  0 Jun15 ?        00:00:00 /usr/bin/python /usr/lib/system-service/system-service-d
root     12198   419  0 Jun20 ?        00:00:00 udevd --daemon
root     12199   419  0 Jun20 ?        00:00:00 udevd --daemon
root     12629     1  0 Jun20 ?        00:00:56 python /usr/sbin/denyhosts --daemon --purge --config=/etc/denyhosts.conf --config=/etc/denyhosts.conf
james    14259     1  0 Jun21 ?        00:00:08 /usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map
root     15358     2  0 Jun21 ?        00:00:00 [pdflush]
clamav   16718     1  0 Jun21 ?        00:00:17 /usr/bin/freshclam -d --quiet
root     17207     1  0 Jun21 ?        00:02:36 Xvnc :1 -desktop server:1 (root) -auth /home/james/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /home/james/.vnc/passwd -rfbport 5901 -pn -extension XFIXES
root     17209     1  0 Jun21 ?        00:00:00 /bin/sh /home/james/.vnc/xstartup
root     17210 17209  0 Jun21 ?        00:00:00 /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session x-session-manager
root     17240 17210  0 Jun21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session x-session-manager
root     17249 17210  0 Jun21 ?        00:00:00 x-session-manager
root     17252     1  0 Jun21 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session x-session-manager
root     17253     1  0 Jun21 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root     17259     1  0 Jun21 ?        00:00:38 /usr/lib/libgconf2-4/gconfd-2
root     17264     1  0 Jun21 ?        00:00:00 gnome-keyring-daemon --start
root     17268     1  0 Jun21 ?        00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root     17269     1  0 Jun21 ?        00:00:00 seahorse-daemon
root     17274     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfsd
root     17278     1  0 Jun21 ?        00:00:02 /usr/lib/gvfs//gvfs-fuse-daemon /root/.gvfs
root     17285     1  0 Jun21 ?        00:00:00 /usr/lib/notify-osd/notify-osd
root     17295 17249  0 Jun21 ?        00:00:02 /usr/bin/metacity --replace
root     17332 17249  0 Jun21 ?        00:00:16 gnome-panel
root     17333 17249  0 Jun21 ?        00:00:01 nautilus
root     17335     1  0 Jun21 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
root     17339 17249  0 Jun21 ?        00:00:00 /usr/lib/evolution/2.28/evolution-alarm-notify
root     17344 17249  0 Jun21 ?        00:00:00 python /usr/share/system-config-printer/applet.py
root     17347 17249  0 Jun21 ?        00:00:00 bluetooth-applet
root     17348 17249  0 Jun21 ?        00:00:00 gnome-power-manager
root     17349 17249  0 Jun21 ?        00:00:00 gnome-volume-control-applet
root     17353 17249  0 Jun21 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
root     17355 17249  0 Jun21 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
root     17357     1  0 Jun21 ?        00:00:00 gnome-screensaver
root     17364     1  0 Jun21 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
root     17367     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.7 /org/gtk/gvfs/exec_spaw/0
root     17369     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root     17375     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
root     17388     1  0 Jun21 ?        00:01:13 /usr/lib/gnome-panel/sensors-applet --oaf-activate-iid=OAFIID:SensorsApplet_Factory --oaf-ior-fd=26
root     17390     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=32
root     17392     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=35
root     17410     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.7 /org/gtk/gvfs/exec_spaw/1
root     17418     1  0 Jun21 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
root     17420     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-session/indicator-status-service
root     17422     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-session/indicator-users-service
root     17424     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-session/indicator-session-service
root     17426     1  0 Jun21 ?        00:00:00 /usr/lib/indicator-messages/indicator-messages-service
root     17435     1  0 Jun21 ?        00:00:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=22
root     17439     1  0 Jun21 ?        00:00:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=23
root     18790     1  0 Jun21 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql    18905 18790  0 Jun21 ?        00:01:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --log-error=/var/log/mqsylerrorlog.err --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root     20650     1  0 00:03 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 20655 20650  0 00:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20656 20650  0 00:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20657 20650  0 00:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20658 20650  0 00:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20659 20650  0 00:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20661 20650  0 00:04 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20662 20650  0 00:04 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20666 20650  0 00:04 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20667 20650  0 00:04 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20668 20650  0 00:04 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20722 20668  0 00:09 ?        00:00:00 [sh] <defunct>
www-data 20726     1  0 00:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20730     1  0 00:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20735     1  0 00:09 ?        00:00:02 /usr/local/apache/bin/httpd -DSSL
www-data 20740     1  0 00:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20742 20659  0 00:16 ?        00:00:00 [sh] <defunct>
www-data 20746     1  0 00:16 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20750     1  0 00:16 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20759     1  0 00:16 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20917 20655  0 00:22 ?        00:00:00 [sh] <defunct>
www-data 20921     1  0 00:22 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20925     1  0 00:22 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20934     1  0 00:22 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20939 20658  0 00:29 ?        00:00:00 [sh] <defunct>
www-data 20943     1  0 00:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20947     1  0 00:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20956     1  0 00:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20959 20662  0 00:35 ?        00:00:00 [sh] <defunct>
www-data 20963     1  0 00:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20967     1  0 00:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20976     1  0 00:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20979 20650  0 00:35 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 20988 20657  0 00:42 ?        00:00:00 [sh] <defunct>
www-data 20992     1  0 00:42 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 20996     1  0 00:42 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21005     1  0 00:42 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21008 20666  0 00:48 ?        00:00:00 [sh] <defunct>
www-data 21010 20650  0 00:48 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21013     1  0 00:48 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21017     1  0 00:48 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21026     1  0 00:48 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21029 20650  0 00:48 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21030 20979  0 00:55 ?        00:00:00 [sh] <defunct>
www-data 21034     1  0 00:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21038     1  0 00:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21047     1  0 00:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21050 20650  0 00:55 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21075 20661  0 01:02 ?        00:00:00 [sh] <defunct>
www-data 21079     1  0 01:02 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21083     1  0 01:02 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21092     1  0 01:02 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21095 20650  0 01:02 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21104 21029  0 01:09 ?        00:00:00 [sh] <defunct>
www-data 21108     1  0 01:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21112     1  0 01:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21121     1  0 01:09 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21124 20650  0 01:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21125 20650  0 01:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21137 21124  0 01:55 ?        00:00:00 [sh] <defunct>
www-data 21141     1  0 01:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21145     1  0 01:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21154     1  0 01:55 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21177 20656  0 02:01 ?        00:00:00 [sh] <defunct>
www-data 21181     1  0 02:01 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21185     1  0 02:01 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21194     1  0 02:01 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21197 20650  0 02:01 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21198 21010  0 02:07 ?        00:00:00 [sh] <defunct>
www-data 21202     1  0 02:07 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21206     1  0 02:07 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21215     1  0 02:07 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21226 20650  0 02:12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21227 21125  0 02:12 ?        00:00:00 [sh] <defunct>
www-data 21231     1  0 02:12 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21235     1  0 02:12 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21244     1  0 02:12 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21247 20650  0 02:12 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21251 21197  0 02:17 ?        00:00:00 [sh] <defunct>
www-data 21255     1  0 02:17 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21259     1  0 02:17 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21268     1  0 02:17 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21270 20650  0 02:17 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21272 21226  0 02:23 ?        00:00:00 [sh] <defunct>
www-data 21276     1  0 02:23 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21280     1  0 02:23 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21289     1  0 02:23 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21292 20650  0 02:23 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 21293 21050  0 02:29 ?        00:00:00 [sh] <defunct>
www-data 21297     1  0 02:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21301     1  0 02:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21310     1  0 02:29 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21313 20650  0 02:29 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21314 20667  0 02:32 ?        00:00:00 [sh] <defunct>
www-data 21318     1  0 02:32 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21322     1  0 02:32 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21331     1  0 02:32 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21333 20650  0 02:32 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21335 21313  0 02:35 ?        00:00:00 [sh] <defunct>
www-data 21339     1  0 02:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21343     1  0 02:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21352     1  0 02:35 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21355 20650  0 02:36 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21364 21095  0 02:40 ?        00:00:00 [sh] <defunct>
www-data 21368     1  0 02:40 ?        00:00:01 xXx
www-data 21373 20650  0 02:41 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21395 20650  0 02:57 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21517 21247  0 04:46 ?        00:00:00 [sh] <defunct>
www-data 21521     1  0 04:46 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21525     1  0 04:46 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21534     1  0 04:46 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21537 21333  0 04:54 ?        00:00:00 [sh] <defunct>
www-data 21541     1  0 04:54 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21545     1  0 04:54 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21554     1  0 04:54 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21577 20650  0 05:03 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21578 21355  0 05:03 ?        00:00:00 [sh] <defunct>
www-data 21582     1  0 05:03 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21586     1  0 05:03 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21595     1  0 05:03 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21606 21373  0 05:11 ?        00:00:00 [sh] <defunct>
www-data 21608 20650  0 05:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21611     1  0 05:11 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21615     1  0 05:11 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21624     1  0 05:11 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21627 20650  0 05:11 ?        00:00:01 /usr/sbin/apache2 -k start
www-data 21631 21270  0 05:19 ?        00:00:00 [sh] <defunct>
www-data 21635     1  0 05:19 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21639     1  0 05:19 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21648     1  0 05:19 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21651 20650  0 05:19 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21652 21292  0 05:27 ?        00:00:00 [sh] <defunct>
www-data 21656     1  0 05:27 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21660     1  0 05:27 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21669     1  0 05:27 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21672 20650  0 05:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21673 21395  0 05:33 ?        00:00:00 [sh] <defunct>
www-data 21677     1  0 05:33 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21681     1  0 05:33 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21690     1  0 05:33 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21692 20650  0 05:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21702 21577  0 05:41 ?        00:00:00 [sh] <defunct>
www-data 21706     1  0 05:41 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21710     1  0 05:41 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21719     1  0 05:41 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21722 21608  0 05:45 ?        00:00:00 [sh] <defunct>
www-data 21726     1  0 05:45 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21728 20650  0 05:45 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21731     1  0 05:45 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21740     1  0 05:45 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21743 20650  0 05:45 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21744 21728  0 05:53 ?        00:00:00 [sh] <defunct>
www-data 21748     1  0 05:53 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21752     1  0 05:53 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21761     1  0 05:53 ?        00:00:00 /usr/local/apache/bin/httpd -DSSL
www-data 21764 20650  0 05:53 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21826 20650  0 07:02 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21827 20650  0 07:02 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 21828 20650  0 07:02 ?        00:00:00 /usr/sbin/apache2 -k start
syslog   21907     1  0 09:00 ?        00:00:00 rsyslogd -c4
root     21938     1  3 09:01 ?        00:00:06 gnome-terminal
root     21939 21938  0 09:01 ?        00:00:00 gnome-pty-helper
root     21940 21938  0 09:01 pts/0    00:00:00 bash
root     22027 21940  0 09:04 pts/0    00:00:00 ps -ef
```

---

### Post by coyoteboy on 2010-06-22
One site seems to suggest it may be a vulnerability in either ssh or something else. Grrrr

---

### Post by coyoteboy on 2010-06-22
Looks as thought it could have been a worm of some sort, something was dropping a payload called al.txt perl script into the /tmp folder. Possibly through injection via log.php from e107 on one of the hosted sites. Still trying to clean it up.

---

