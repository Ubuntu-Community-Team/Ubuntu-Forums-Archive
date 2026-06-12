---
title: "Ubuntu screen margins off | HELP"
date: 2012-02-22
forum: General Help
---

### Post by zDrUrYz on 2012-02-22
Hello, I just installed Ubuntu on my custom built PC. Everything was going fine until I updated my Graphics Drivers. When I rebooted, about an inch of screen was off of the TV I'm using. I can't see the entire screen. I tried changing resolution, everything. Nothing happened. I have experienced this before on Windows with this same computer. But then, I just opened Nvidia control panel and changed the screen size manually. I also looked through the settings on my TV. Any idea what to do?

GPU: EVGA GTX 560ti

TV: 32" 1080p Element

I am doing this through HDMI.

:confused:

---

### Post by roelforg on 2012-02-22
Does the screen have an auto-ajust option?
If so, try it.

---

### Post by zDrUrYz on 2012-02-22
Nothing happened. It has to be some setting that you can change on the PC.. It was fine until I updated my Drivers.

---

### Post by roelforg on 2012-02-22
> **zDrUrYz said:**
> Nothing happened. It has to be some setting that you can change on the PC.. It was fine until I updated my Drivers.
IIRC: there should be an option in either the lightdm or the monitor config prog.
You've gotta go menu-diving to find it; i use a different DE so i wouldn't know where to look.

---

### Post by zDrUrYz on 2012-02-22
Didn't find anything...

---

### Post by roelforg on 2012-02-22
My ubuntu runs lxde and i have that setting in the openbox config.

Would you post the output of
```

sudo ps ax

```
?

It would allow me to find out what control's your screen.

---

### Post by zDrUrYz on 2012-02-22
> **roelforg said:**
> My ubuntu runs lxde and i have that setting in the openbox config.

Would you post the output of
```

sudo ps ax

```
?

It would allow me to find out what control's your screen.



I got:


 TTY      STAT   TIME COMMAND
    1 ?        Ss     0:00 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    4 ?        S      0:00 [kworker/0:0]
    5 ?        S      0:00 [kworker/u:0]
    6 ?        S      0:00 [migration/0]
    7 ?        S      0:00 [migration/1]
    8 ?        S      0:00 [kworker/1:0]
    9 ?        S      0:00 [ksoftirqd/1]
   10 ?        S      0:00 [kworker/0:1]
   11 ?        S      0:00 [migration/2]
   12 ?        S      0:00 [kworker/2:0]
   13 ?        S      0:00 [ksoftirqd/2]
   14 ?        S      0:00 [migration/3]
   15 ?        S      0:00 [kworker/3:0]
   16 ?        S      0:00 [ksoftirqd/3]
   17 ?        S<     0:00 [cpuset]
   18 ?        S<     0:00 [khelper]
   19 ?        S<     0:00 [netns]
   20 ?        S      0:00 [kworker/u:1]
   21 ?        S      0:00 [sync_supers]
   22 ?        S      0:00 [bdi-default]
   23 ?        S<     0:00 [kintegrityd]
   24 ?        S<     0:00 [kblockd]
   25 ?        S<     0:00 [ata_sff]
   26 ?        S      0:00 [khubd]
   27 ?        S<     0:00 [md]
   54 ?        S      0:00 [kworker/1:1]
   55 ?        S      0:00 [khungtaskd]
   56 ?        S      0:00 [kswapd0]
   57 ?        SN     0:00 [ksmd]
   58 ?        SN     0:00 [khugepaged]
   59 ?        S      0:00 [fsnotify_mark]
   60 ?        S      0:00 [ecryptfs-kthrea]
   61 ?        S<     0:00 [crypto]
   69 ?        S<     0:00 [kthrotld]
   81 ?        S      0:00 [kworker/3:1]
  101 ?        S      0:00 [kworker/3:2]
  224 ?        S      0:00 [scsi_eh_0]
  245 ?        S      0:00 [scsi_eh_1]
  273 ?        S      0:00 [scsi_eh_2]
  283 ?        S      0:00 [scsi_eh_3]
  286 ?        S      0:00 [kworker/u:2]
  290 ?        S      0:00 [kworker/u:3]
  292 ?        S      0:00 [kworker/u:4]
  293 ?        S      0:00 [scsi_eh_4]
  295 ?        S      0:00 [scsi_eh_5]
  296 ?        S      0:00 [kworker/u:5]
  297 ?        S      0:00 [kworker/u:6]
  304 ?        S      0:00 [kworker/2:1]
  306 ?        S      0:00 [kworker/u:7]
  314 ?        S      0:00 [kworker/2:2]
  329 ?        Ss     0:01 mount.ntfs /dev/disk/by-uuid/5E6C97FA6C97CAE3 /root
  336 ?        S<     0:00 [loop0]
  360 ?        S      0:00 [kjournald]
  384 ?        S      0:00 [flush-7:0]
  385 ?        S      0:00 [flush-8:0]
  434 ?        S      0:00 upstart-udev-bridge --daemon
  442 ?        Ss     0:00 udevd --daemon
  554 ?        S      0:00 [kworker/1:2]
  621 ?        S      0:00 udevd --daemon
  679 ?        S      0:00 [kworker/0:2]
  691 ?        S      0:00 upstart-socket-bridge --daemon
  705 ?        S<     0:00 [edac-poller]
  706 ?        S<     0:00 [kpsmoused]
  729 ?        S      0:00 udevd --daemon
  772 ?        S<     0:00 [hd-audio0]
  778 ?        S<     0:00 [hd-audio1]
  994 ?        Sl     0:00 rsyslogd -c5
 1017 ?        Ss     0:00 dbus-daemon --system --fork --activation=upstart
 1025 ?        S      0:00 /usr/sbin/modem-manager
 1028 ?        S      0:00 avahi-daemon: running [ubuntu.local]
 1029 ?        S      0:00 avahi-daemon: chroot helper
 1030 ?        Ssl    0:00 NetworkManager
 1059 ?        Sl     0:00 /usr/lib/policykit-1/polkitd
 1092 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
 1098 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
 1116 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
 1117 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
 1120 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
 1124 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
 1130 ?        Ss     0:00 /usr/sbin/irqbalance
 1134 ?        Ss     0:00 cron
 1135 ?        Ss     0:00 atd
 1172 ?        Ss     0:00 /usr/sbin/cupsd -F
 1179 ?        Ssl    0:00 lightdm
 1188 tty7     Ss+    0:04 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -noliste
 1198 ?        Ss     0:00 /usr/sbin/bluetoothd
 1204 ?        S<     0:00 [l2cap]
 1209 ?        S<     0:00 [krfcommd]
 1329 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 1331 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-d
 1338 ?        Sl     0:00 /usr/lib/accountsservice/accounts-daemon
 1345 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
 1450 ?        Sl     0:00 /usr/lib/upower/upowerd
 1503 ?        Sl     0:00 /usr/lib/x86_64-linux-gnu/colord/colord
 1562 ?        SNl    0:00 /usr/lib/rtkit/rtkit-daemon
 1632 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 1642 ?        Ssl    0:00 /usr/bin/gnome-session --session=gnome
 1675 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-s
 1678 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gno
 1680 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 8 --print-addres
 1682 ?        S      0:00 /usr/lib/gvfs/gvfsd
 1687 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/daniel/.gvfs
 1699 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 1710 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 1712 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gsd-printer
 1714 ?        Sl     0:00 /usr/bin/gnome-screensaver --no-daemon
 1715 ?        Sl     0:10 /usr/bin/gnome-shell
 1724 ?        S<l    0:00 /usr/bin/pulseaudio --start --log-target=syslog
 1735 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 1739 ?        Sl     0:00 /usr/lib/d-conf/dconf-service
 1745 ?        Sl     0:00 /usr/lib/vino/vino-server --sm-disable
 1748 ?        Sl     0:00 nautilus -n
 1749 ?        Sl     0:00 nm-applet
 1757 ?        S      0:00 /usr/lib/telepathy/mission-control-5
 1767 ?        Sl     0:00 /usr/lib/gnome-shell/gnome-shell-calendar-server
 1769 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 1773 ?        Sl     0:00 /usr/lib/udisks/udisks-daemon
 1774 ?        S      0:00 udisks-daemon: polling /dev/sr0
 1777 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 1779 ?        Sl     0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
 1787 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.1 /org/gtk/gvf
 1789 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.1 /org/gtk/gvfs
 1804 ?        Sl     0:00 telepathy-indicator
 1837 ?        S      0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 1885 ?        Sl     0:00 zeitgeist-datahub
 1891 ?        Sl     0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
 1892 ?        S      0:00 /bin/cat
 1910 ?        S      0:00 /usr/bin/python /usr/share/system-config-printer/appl
 1914 ?        SLl    0:01 /usr/lib/chromium-browser/chromium-browser
 1916 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser
 1918 ?        S      0:00 /usr/lib/chromium-browser/chromium-browser --type=zyg
 1945 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1952 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1958 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1964 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1970 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1976 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1982 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 1988 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=ren
 2082 ?        Sl     0:01 /usr/lib/chromium-browser/chromium-browser --type=ren
 2127 ?        Sl     0:00 update-notifier
 2150 ?        Sl     0:00 gnome-terminal
 2154 ?        S      0:00 gnome-pty-helper
 2155 pts/0    Ss     0:00 bash
 2208 pts/0    S+     0:00 sudo ps ax
 2209 pts/0    R+     0:00 ps ax

---

### Post by roelforg on 2012-02-22
You're using gnome.

Next time, put large outputs between code tags.

Have a look at the manpage of xrandr, it might be what you're looking for.
[http://www.manpagez.com/man/1/xrandr/](http://www.manpagez.com/man/1/xrandr/)

---

### Post by roelforg on 2012-02-22
Try:
```

sudo xrandr --output VGA --pos xoffsetxyoffset

```e.g
```

sudo xrandr --output VGA --pos 4x3

```
Experiment a bit until you find the right offset.

---

### Post by zDrUrYz on 2012-02-22
I'm not using VGA. I'm using HDMI.

---

