---
title: "[precise] stability problems with latest 3.2.0-x kernels"
date: 2012-09-12
forum: General Help
---

### Post by buckminster on 2012-09-12
I have been having random problems (numerous Error messages, kicked back to the login screen after typing on the keyboard, not able to resume properly from suspend to RAM) happening multiple times a day when using 3.2.0-29-generic-pae and 3.2.0-30-generic-pae. I've been using 3.2.0-27-generic-pae and things seem to have settled down.

It's a fresh install (less than a week) and fairly vanilla. Here's my system and process info. Any help or insight would be appreciated.

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 03:52 ?        00:00:01 /sbin/init
root         2     0  0 03:52 ?        00:00:00 [kthreadd]
root         3     2  0 03:52 ?        00:00:00 [ksoftirqd/0]
root         6     2  0 03:52 ?        00:00:00 [migration/0]
root         7     2  0 03:52 ?        00:00:00 [watchdog/0]
root        13     2  0 03:52 ?        00:00:00 [cpuset]
root        14     2  0 03:52 ?        00:00:00 [khelper]
root        15     2  0 03:52 ?        00:00:00 [kdevtmpfs]
root        16     2  0 03:52 ?        00:00:00 [netns]
root        18     2  0 03:52 ?        00:00:00 [sync_supers]
root        19     2  0 03:52 ?        00:00:00 [bdi-default]
root        20     2  0 03:52 ?        00:00:00 [kintegrityd]
root        21     2  0 03:52 ?        00:00:00 [kblockd]
root        22     2  0 03:52 ?        00:00:00 [ata_sff]
root        23     2  0 03:52 ?        00:00:00 [khubd]
root        24     2  0 03:52 ?        00:00:00 [md]
root        26     2  0 03:52 ?        00:00:00 [khungtaskd]
root        27     2  0 03:52 ?        00:00:04 [kswapd0]
root        28     2  0 03:52 ?        00:00:00 [ksmd]
root        29     2  0 03:52 ?        00:00:00 [khugepaged]
root        30     2  0 03:52 ?        00:00:00 [fsnotify_mark]
root        31     2  0 03:52 ?        00:00:00 [ecryptfs-kthrea]
root        32     2  0 03:52 ?        00:00:00 [crypto]
root        40     2  0 03:52 ?        00:00:00 [kthrotld]
root        42     2  0 03:52 ?        00:00:00 [scsi_eh_0]
root        43     2  0 03:52 ?        00:00:00 [scsi_eh_1]
root        44     2  0 03:52 ?        00:00:00 [scsi_eh_2]
root        45     2  0 03:52 ?        00:00:00 [scsi_eh_3]
root        67     2  0 03:52 ?        00:00:00 [devfreq_wq]
root       258     2  0 03:52 ?        00:00:01 [jbd2/sda6-8]
root       259     2  0 03:52 ?        00:00:00 [ext4-dio-unwrit]
root       345     1  0 03:52 ?        00:00:00 upstart-udev-bridge --daemon
root       366     1  0 03:52 ?        00:00:00 /sbin/udevd --daemon
root       558     2  0 03:52 ?        00:00:00 [cfg80211]
102        614     1  0 03:52 ?        00:00:20 dbus-daemon --system --fork --activation=upstart
root       616     2  0 03:52 ?        00:00:00 [kpsmoused]
root       663     1  0 03:52 ?        00:00:00 /usr/sbin/bluetoothd
syslog     668     1  0 03:52 ?        00:00:02 rsyslogd -c5
avahi      678     1  0 03:52 ?        00:00:02 avahi-daemon: running [Quixote-Ubuntu.local]
avahi      685   678  0 03:52 ?        00:00:00 avahi-daemon: chroot helper
root       695     2  0 03:52 ?        00:00:00 [krfcommd]
root       699     1  0 03:52 ?        00:00:00 /usr/sbin/cupsd -F
colord     741     1  0 03:52 ?        00:00:00 /usr/lib/i386-linux-gnu/colord/colord
root       768     1  0 03:52 ?        00:00:00 /usr/sbin/modem-manager
root       784     1  0 03:52 ?        00:00:08 NetworkManager
root       789     1  0 03:52 ?        00:00:22 /usr/lib/policykit-1/polkitd --no-debug
root       806     1  0 03:52 ?        00:00:00 upstart-socket-bridge --daemon
root       891     2  0 03:52 ?        00:00:00 [hd-audio0]
root       904     1  0 03:52 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       908     1  0 03:52 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       925     1  0 03:52 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       927     1  0 03:52 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       931     1  0 03:52 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       951     1  0 03:52 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       954     1  0 03:52 ?        00:00:03 /usr/sbin/irqbalance
root       957     1  0 03:52 ?        00:00:00 cron
daemon     959     1  0 03:52 ?        00:00:00 atd
whoopsie   962     1  0 03:52 ?        00:00:02 whoopsie
root       965     1  0 03:52 ?        00:00:00 /usr/sbin/winbindd
root       995     1  0 03:52 ?        00:00:00 lightdm
root      1038   995  1 03:52 tty7     00:14:30 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
root      1042     1  0 03:52 ?        00:00:01 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      1078   965  0 03:52 ?        00:00:00 /usr/sbin/winbindd
root      1086     1  0 03:52 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
root      1215     2  0 03:52 ?        00:00:00 [kdmflush]
root      1223     2  0 03:52 ?        00:00:00 [kcryptd_io]
root      1224     2  0 03:52 ?        00:00:00 [kcryptd]
root      1234     1  0 03:52 ?        00:00:05 /usr/sbin/console-kit-daemon --no-daemon
root      1278     1  0 03:52 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1357     2  0 03:52 ?        00:00:01 [flush-8:0]
root      1379     1  0 03:52 ?        00:00:03 /usr/lib/upower/upowerd
root      1536   995  0 03:52 ?        00:00:00 lightdm --session-child 12 19
rtkit     1570     1  0 03:52 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
pablo     1698     1  0 03:53 ?        00:00:02 /usr/bin/gnome-keyring-daemon --daemonize --login
pablo     1709  1536  0 03:53 ?        00:00:01 gnome-session --session=ubuntu
pablo     1744  1709  0 03:53 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
pablo     1747     1  0 03:53 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
pablo     1748     1  0 03:53 ?        00:00:19 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
pablo     1757  1709  0 03:53 ?        00:00:15 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
pablo     1766     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfsd
pablo     1768     1  0 03:53 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /home/pablo/.gvfs
pablo     1775  1709  0 03:53 ?        00:05:46 compiz
pablo     1778     1  0 03:53 ?        00:00:00 /usr/lib/i386-linux-gnu/gconf/gconfd-2
pablo     1784  1757  0 03:53 ?        00:00:07 syndaemon -i 2.0 -K -R -t
pablo     1789     1  0 03:53 ?        00:00:17 /usr/bin/pulseaudio --start --log-target=syslog
pablo     1791     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
pablo     1794  1709  0 03:53 ?        00:00:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
pablo     1795  1709  0 03:53 ?        00:00:08 nm-applet
pablo     1796  1709  0 03:53 ?        00:00:04 nautilus -n
pablo     1797  1789  0 03:53 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
pablo     1799  1709  0 03:53 ?        00:00:00 bluetooth-applet
pablo     1801  1709  0 03:53 ?        00:00:05 /usr/bin/python /usr/bin/indicator-weather
pablo     1802  1709  0 03:53 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
pablo     1815     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1817     1  0 03:53 ?        00:00:01 /usr/lib/udisks/udisks-daemon
root      1818  1817  0 03:53 ?        00:00:00 udisks-daemon: not polling any devices
pablo     1821     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
pablo     1825     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
pablo     1832     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
pablo     1841     1  0 03:53 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
pablo     1844     1  0 03:53 ?        00:00:00 /usr/lib/dconf/dconf-service
pablo     1850     1  0 03:53 ?        00:00:08 /usr/lib/bamf/bamfdaemon
pablo     1856     1  0 03:53 ?        00:00:26 /usr/lib/unity/unity-panel-service
pablo     1858     1  0 03:53 ?        00:00:16 /usr/lib/indicator-appmenu/hud-service
pablo     1880     1  0 03:53 ?        00:00:03 /usr/lib/indicator-application/indicator-application-service
pablo     1884     1  0 03:53 ?        00:00:00 /usr/lib/indicator-session/indicator-session-service
pablo     1886     1  0 03:53 ?        00:00:00 /usr/lib/indicator-messages/indicator-messages-service
pablo     1918     1  0 03:53 ?        00:00:00 /usr/lib/geoclue/geoclue-master
pablo     1926  1775  0 03:53 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
pablo     1927  1926  0 03:53 ?        00:00:08 /usr/bin/gtk-window-decorator
pablo     1934     1  0 03:53 ?        00:00:01 /usr/lib/ubuntu-geoip/ubuntu-geoip-provider
pablo     1941  1709  0 03:53 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
pablo     1946     1  0 03:53 ?        00:00:00 /usr/lib/indicator-datetime/indicator-datetime-service
pablo     1948     1  0 03:53 ?        00:00:00 /usr/lib/indicator-sound/indicator-sound-service
pablo     1950     1  0 03:53 ?        00:00:00 /usr/lib/indicator-printers/indicator-printers-service
pablo     1966  1709  0 03:53 ?        00:00:01 telepathy-indicator
pablo     1972     1  0 03:53 ?        00:00:05 /usr/lib/telepathy/mission-control-5
pablo     1977     1  0 03:53 ?        00:00:00 /usr/lib/gnome-online-accounts/goa-daemon
pablo     1982  1709  0 03:53 ?        00:00:04 gnome-screensaver
pablo     1983  1709  0 03:53 ?        00:00:00 zeitgeist-datahub
pablo     1990     1  0 03:53 ?        00:00:01 /usr/bin/zeitgeist-daemon
pablo     1997     1  0 03:53 ?        00:00:01 /usr/lib/zeitgeist/zeitgeist-fts
pablo     2005  1997  0 03:53 ?        00:00:00 /bin/cat
pablo     2022     1  0 03:53 ?        00:00:15 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
pablo     2062     1  0 03:53 ?        00:00:03 /usr/lib/unity-lens-applications/unity-applications-daemon
pablo     2064     1  0 03:53 ?        00:00:00 /usr/lib/unity-lens-files/unity-files-daemon
pablo     2066     1  0 03:53 ?        00:00:10 /usr/lib/unity-lens-music/unity-music-daemon
pablo     2068     1  0 03:53 ?        00:00:01 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
pablo     2110     1  0 03:53 ?        00:00:01 /usr/bin/python /usr/lib/unity-scope-video-remote/unity-scope-video-remote
pablo     2111     1  0 03:53 ?        00:00:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
pablo     2188     1  5 03:54 ?        00:45:54 /usr/lib/firefox/firefox
pablo     2202  1709  0 03:54 ?        00:00:01 update-notifier
pablo     2214     1  0 03:54 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
pablo     2261     1  0 03:54 ?        00:02:21 empathy
pablo     2272     1  0 03:54 ?        00:01:04 /usr/lib/notify-osd/notify-osd
pablo     2281     1  0 03:54 ?        00:00:00 /usr/lib/telepathy/telepathy-salut
pablo     2283     1  0 03:54 ?        00:00:00 /usr/lib/evolution/e-addressbook-factory
pablo     2289     1  0 03:54 ?        00:00:00 /usr/lib/telepathy/telepathy-logger
pablo     2309  1775  0 03:54 ?        00:00:00 /bin/sh -c gnome-terminal
pablo     2310  2309  0 03:54 ?        00:00:05 gnome-terminal
pablo     2317  2310  0 03:54 ?        00:00:00 gnome-pty-helper
pablo     2319  2310  0 03:54 pts/0    00:00:01 bash
pablo     2375  1709  0 03:55 ?        00:00:01 /usr/lib/deja-dup/deja-dup/deja-dup-monitor
root      2822     2  0 03:55 ?        00:00:06 [flush-ecryptfs-]
root      7094     2  0 16:04 ?        00:00:00 [migration/1]
root      7096     2  0 16:04 ?        00:00:00 [ksoftirqd/1]
root      7097     2  0 16:04 ?        00:00:00 [watchdog/1]
root      7103   366  0 16:04 ?        00:00:00 /sbin/udevd --daemon
root      7108   366  0 16:04 ?        00:00:00 /sbin/udevd --daemon
root      7542   784  0 16:04 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-wlan0.pid -lf /var/lib/dhcp/dhclient-8fb66a0a-9abe-43c1-aeca-b554e3538d6d-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
nobody    7545   784  0 16:04 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec
pablo     7582     1  0 16:04 ?        00:00:03 /usr/lib/telepathy/telepathy-gabble
root      8127     2  0 17:07 ?        00:00:00 [kworker/1:0]
root      8128     2  0 17:07 ?        00:00:02 [kworker/0:0]
root      8275     2  0 17:18 ?        00:00:02 [kworker/1:1]
root      8327     2  0 17:25 ?        00:00:00 [kworker/u:2]
root      8359     2  0 17:30 ?        00:00:00 [kworker/0:2]
root      8364     2  0 17:31 ?        00:00:00 [kworker/u:0]
root      8394     2  0 17:37 ?        00:00:00 [kworker/u:1]
root      8395     2  0 17:38 ?        00:00:00 [kworker/1:2]
pablo     8399  2319  0 17:39 pts/0    00:00:00 ps -fA

```

---

### Post by Alcidious on 2012-09-15
As I'm not exactly a power user (more like working on intermediate), I'm not qualified to dig through the details of your system, but I can say that the 3.2.27 kernel has given me quite the headache.

On my Samsung laptop the screen will flash and freeze... so I reported the bug and have been subscribed to troubleshooting updates since June or so.  For my particular issue, and perhaps for all users, there will be a kernel update to 3.2.30 early next week. 

At the moment I'm trying to test the proposed, but perhaps when the update is officially released it will address the bugs you've been experiencing?

---

