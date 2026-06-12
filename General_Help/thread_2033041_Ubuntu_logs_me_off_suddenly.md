---
title: "Ubuntu logs me off suddenly"
date: 2012-07-25
forum: General Help
---

### Post by wanichan on 2012-07-25
Ubuntu all of a sudden logs me off, it resembles what could happen if, e.g., X gets restarted. It's on 12.04 LTS and this has been happening a lot. 

It flashes a message that it recovered from an internal error, and I have no idea what's prompting it or what could be going on.

 Here is the output of ps -ef right after I had to re-log in.
```
root      5954     2  0 06:34 ?        00:00:00 [migration/1]
root      5956     2  0 06:34 ?        00:00:00 [ksoftirqd/1]
root      5957     2  0 06:34 ?        00:00:00 [watchdog/1]
root      5958     2  0 06:34 ?        00:00:01 [kworker/1:0]
root      5963     2  0 06:34 ?        00:00:00 [kworker/u:23]
root      5972   301  0 06:34 ?        00:00:00 /sbin/udevd --daemon
root      5973   301  0 06:34 ?        00:00:00 /sbin/udevd --daemon
root      6387   681  0 06:36 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/li
nobody    6390   681  0 06:36 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --
root      6482   887 10 06:38 tty7     00:01:06 /usr/bin/X :0 -auth /var/run/lig
root      6573   887  0 06:38 ?        00:00:00 lightdm --session-child 12 25
user1  6663     1  0 06:38 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
user1  6674  6573  0 06:38 ?        00:00:00 gnome-session --session=ubuntu
user1  6703  6674  0 06:38 ?        00:00:05 /usr/bin/ibus-daemon --xim
user1  6706  6703  0 06:38 ?        00:00:01 /usr/lib/i386-linux-gnu/ibus/ibu
user1  6708  6703  0 06:38 ?        00:00:03 /usr/bin/python /usr/share/ibus/
user1  6711     1  0 06:38 ?        00:00:00 /usr/lib/i386-linux-gnu/ibus/ibu
user1  6725     1  0 06:38 ?        00:00:00 dbus-launch --autolaunch 09d9704
user1  6728     1  0 06:38 ?        00:00:00 //bin/dbus-daemon --fork --print
user1  6729  6674  0 06:38 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
user1  6732     1  0 06:38 ?        00:00:00 /usr/bin/dbus-launch --exit-with
user1  6734     1  0 06:38 ?        00:00:00 /usr/lib/i386-linux-gnu/gconf/gc
user1  6735     1  0 06:38 ?        00:00:03 //bin/dbus-daemon --fork --print
user1  6740  6703  0 06:38 ?        00:00:01 /usr/bin/python /usr/share/ibus-
user1  6745  6674  0 06:38 ?        00:00:02 /usr/lib/gnome-settings-daemon/g
user1  6755     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfsd
user1  6757     1  0 06:38 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
user1  6770  6674  6 06:38 ?        00:00:38 compiz
user1  6775     1  0 06:38 ?        00:00:00 /usr/lib/i386-linux-gnu/gconf/gc
user1  6782     1  0 06:38 ?        00:00:00 /usr/lib/notify-osd/notify-osd
user1  6783  6745  0 06:38 ?        00:00:00 syndaemon -i 2.0 -K -R -t
user1  6790     1  0 06:38 ?        00:00:00 /usr/bin/pulseaudio --start --lo
user1  6792     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfsd
user1  6797  6674  0 06:38 ?        00:00:00 bluetooth-applet
user1  6798  6674  1 06:38 ?        00:00:11 nautilus -n
user1  6799  6674  0 06:38 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
user1  6800  6674  0 06:38 ?        00:00:00 nm-applet
user1  6802  6674  0 06:38 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
user1  6809  6790  0 06:38 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
user1  6819     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
user1  6824     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
user1  6826     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
user1  6830     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
user1  6834     1  0 06:38 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
user1  6839     1  0 06:38 ?        00:00:02 /usr/lib/bamf/bamfdaemon
user1  6849  6674  0 06:38 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-
user1  6857     1  1 06:38 ?        00:00:07 /usr/lib/unity/unity-panel-servi
user1  6859     1  0 06:38 ?        00:00:02 /usr/lib/indicator-appmenu/hud-s
user1  6873     1  0 06:38 ?        00:00:00 /usr/lib/indicator-messages/indi
user1  6877     1  0 06:38 ?        00:00:00 /usr/lib/indicator-application/i
user1  6881     1  0 06:38 ?        00:00:00 /usr/lib/indicator-printers/indi
user1  6885     1  0 06:38 ?        00:00:00 /usr/lib/indicator-session/indic
user1  6921     1  0 06:38 ?        00:00:00 /usr/lib/geoclue/geoclue-master
user1  6923     1  0 06:38 ?        00:00:00 /usr/lib/ubuntu-geoip/ubuntu-geo
user1  6929  6770  0 06:38 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
user1  6930  6929  0 06:38 ?        00:00:01 /usr/bin/gtk-window-decorator
user1  6941     1  0 06:38 ?        00:00:00 /usr/lib/indicator-datetime/indi
user1  6942     1  0 06:38 ?        00:00:00 /usr/lib/indicator-sound/indicat
user1  6952  6674  0 06:38 ?        00:00:00 telepathy-indicator
user1  6959     1  0 06:38 ?        00:00:00 /usr/lib/telepathy/mission-contr
user1  6964     1  0 06:38 ?        00:00:00 /usr/lib/gnome-online-accounts/g
user1  6968  6674  0 06:39 ?        00:00:00 gnome-screensaver
user1  6969  6674  0 06:39 ?        00:00:00 zeitgeist-datahub
user1  6976     1  0 06:39 ?        00:00:00 /usr/bin/zeitgeist-daemon
user1  6983     1  0 06:39 ?        00:00:00 /usr/lib/zeitgeist/zeitgeist-fts
user1  6991  6983  0 06:39 ?        00:00:00 /bin/cat
user1  7001     1 42 06:39 ?        00:04:03 /usr/lib/firefox/firefox
user1  7005     1  0 06:39 ?        00:00:02 /usr/lib/unity-lens-applications
user1  7007     1  0 06:39 ?        00:00:00 /usr/lib/unity-lens-files/unity-
user1  7010     1  0 06:39 ?        00:00:00 /usr/bin/python /usr/lib/unity-l
user1  7011     1  0 06:39 ?        00:00:00 /usr/lib/unity-lens-music/unity-
user1  7063     1  0 06:39 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus
user1  7069     1  0 06:39 ?        00:00:00 /usr/lib/unity-lens-music/unity-
user1  7088     1  0 06:39 ?        00:00:00 /usr/bin/python /usr/lib/unity-s
user1  7115  6674  0 06:39 ?        00:00:00 update-notifier
user1  7124  7001  7 06:39 ?        00:00:42 /usr/lib/firefox/plugin-containe
root      7159     2  0 06:39 ?        00:00:01 [kworker/0:0]
root      7176     2  0 06:40 ?        00:00:01 [kworker/1:1]
user1  7257  6674  0 06:40 ?        00:00:00 /usr/lib/deja-dup/deja-dup/deja-
root      7660     2  0 06:41 ?        00:00:00 [kworker/u:0]
user1  7677     1  0 06:43 ?        00:00:00 /usr/lib/dconf/dconf-service
user1  7688     1  0 06:43 ?        00:00:00 /usr/lib/libreoffice/program/oos
user1  7709  7688  3 06:43 ?        00:00:09 /usr/lib/libreoffice/program/sof
user1  7735     1  0 06:44 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawn
user1  7740     1  1 06:45 ?        00:00:02 gnome-terminal
user1  7749  7740  0 06:45 ?        00:00:00 gnome-pty-helper
user1  7750  7740  0 06:45 pts/0    00:00:01 bash
root      7809     2  0 06:46 ?        00:00:00 [kworker/1:2]
root      7810     2  0 06:47 ?        00:00:00 [kworker/u:1]
user1  7824  7750  0 06:48 pts/0    00:00:00 ps -ef

```

Linux version 3.2.0-27-generic-pae (buildd@akateko) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012

and this is on a Toshiba NB 505 netbook. Any ideas :confused:

Thanks!

---

### Post by Wim Sturkenboom on 2012-07-25
Plenty of threads here about that issue from what I have seen; seems to be an issue with the computers that have nvidia cards. I suggest you do a search; you will find, amongst others, [http://ubuntuforums.org/showthread.php?t=2028502](http://ubuntuforums.org/showthread.php?t=2028502)

---

