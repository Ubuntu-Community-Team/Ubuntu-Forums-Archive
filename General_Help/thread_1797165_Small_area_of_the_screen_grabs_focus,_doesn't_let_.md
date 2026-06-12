---
title: "Small area of the screen grabs focus, doesn't let any window receive mouse actions"
date: 2011-07-04
forum: General Help
---

### Post by intheflesh on 2011-07-04
One of those things that make yo go "WTF?"

After browsing the internet with Firefox, there appears a peculiar problem: if I move the pointer to a certain area of the screen, I can't click (left, right, middle) nor use mouse wheel. The area can be of variable size, but usually it's small, in the lower part of the screen, it's x dimension greater than y one (a horizontally placed rectangle). The problem doesn't go away when I restart Firefox (obviously it does when I reboot). It obstructs any window under it (I can't even click on the desktop where 'it' is). It's as if there is an invisible window that 'steals' focus when I move the mouse over it.

Does anyone know why it occurs and how do I fix it?

I'm on 11.04, Classic Ubuntu (Gnome 2.3x).

A quick UPDATE: dragging an icon and dropping it on the said area behaves as if I dragged an item and dropped it where it doesn't belong (i.e. it just slowly returns to it's original position).
Also, I tried killing it with Force Quit applet, but only my desktop reloaded.

---

### Post by intheflesh on 2011-07-04
Well, super key + middle mouse click doesn't resize it, nor does  super key + left click move it.

---

### Post by JC Cheloven on 2011-07-04
Strange enough. 
Have you tried to display a list of processes when that happens to see if there is a process that could be causing that? 

To see runing processes you can type "top" (or "htop" if you have it installed), or simply from the menu: 
System -> System monitor -> Processes tab.

If you identify the insidious process you can eventually kill it from terminal (kill command) or from the aforementioned tool from the menu.

---

### Post by intheflesh on 2011-07-04
Here's the listing of ps ax command:

```
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:00 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    6 ?        S      0:00 [migration/0]
    7 ?        S      0:00 [migration/1]
    9 ?        S      0:00 [ksoftirqd/1]
   11 ?        S      0:00 [migration/2]
   13 ?        S      0:00 [ksoftirqd/2]
   14 ?        S      0:00 [migration/3]
   16 ?        S      0:00 [ksoftirqd/3]
   17 ?        S<     0:00 [cpuset]
   18 ?        S<     0:00 [khelper]
   19 ?        S<     0:00 [netns]
   21 ?        S      0:00 [sync_supers]
   22 ?        S      0:00 [bdi-default]
   23 ?        S<     0:00 [kintegrityd]
   24 ?        S<     0:00 [kblockd]
   25 ?        S<     0:00 [kacpid]
   26 ?        S<     0:00 [kacpi_notify]
   27 ?        S<     0:00 [kacpi_hotplug]
   28 ?        S<     0:00 [ata_sff]
   29 ?        S      0:00 [khubd]
   30 ?        S<     0:00 [md]
   31 ?        S      0:00 [kworker/2:1]
   32 ?        S      0:00 [khungtaskd]
   33 ?        S      0:00 [kswapd0]
   34 ?        SN     0:00 [ksmd]
   35 ?        S      0:00 [fsnotify_mark]
   36 ?        S<     0:00 [aio]
   37 ?        S      0:00 [ecryptfs-kthrea]
   38 ?        S<     0:00 [crypto]
   42 ?        S<     0:00 [kthrotld]
   43 ?        S      0:00 [kworker/u:2]
   45 ?        S<     0:00 [kmpathd]
   46 ?        S<     0:00 [kmpath_handlerd]
   47 ?        S<     0:00 [kondemand]
   48 ?        S<     0:00 [kconservative]
   69 ?        S      0:01 [kworker/1:1]
  168 ?        S      0:00 [scsi_eh_0]
  218 ?        S      0:00 [scsi_eh_1]
  255 ?        S      0:00 [scsi_eh_2]
  256 ?        S      0:00 [scsi_eh_3]
  258 ?        S      0:00 [scsi_eh_4]
  260 ?        S      0:00 [scsi_eh_5]
  261 ?        S      0:00 [kworker/u:5]
  293 ?        S      0:03 [kjournald]
  347 ?        S      0:00 upstart-udev-bridge --daemon
  353 ?        S<s    0:00 udevd --daemon
  560 ?        S<     0:00 [kpsmoused]
  623 ?        S<     0:00 [ttm_swap]
  686 ?        S      0:00 upstart-socket-bridge --daemon
  699 ?        S<     0:00 [hd-audio0]
  752 ?        S<     0:00 [hd-audio1]
  762 ?        Ss     0:02 /sbin/mount.ntfs /dev/sda5 /data1 -o rw,nls=utf8,umask=007,gid=46
  769 ?        Ss     0:01 /sbin/mount.ntfs /dev/sda8 /data2 -o rw,nls=utf8,umask=007,gid=46
  774 ?        Ss     0:01 /sbin/mount.ntfs /dev/sda1 /windows -o rw,nls=utf8,umask=007,gid=46
  794 ?        Ss     0:00 /usr/sbin/sshd -D
  804 ?        Sl     0:00 rsyslogd -c4
  810 ?        Ss     0:01 dbus-daemon --system --fork --activation=upstart
  823 ?        Ssl    0:00 gdm-binary
  827 ?        S      0:00 avahi-daemon: running [emptiespace.local]
  828 ?        S      0:00 avahi-daemon: chroot helper
  829 ?        Ssl    0:00 NetworkManager
  831 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
  833 ?        S      0:00 /usr/sbin/modem-manager
  841 ?        Sl     0:00 /usr/lib/policykit-1/polkitd
  911 ?        Sl     0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
  914 ?        S      0:00 /sbin/wpa_supplicant -u -s
  915 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-5eac957d-ef5b-49e0-aa6c-ccd1e5a004b7-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
  985 tty7     Ss+    9:02 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-CUXjIo/database -nolisten tcp vt7
  998 tty4     Ss+    0:00 /sbin/getty -8 38400 tty4
 1003 tty5     Ss+    0:00 /sbin/getty -8 38400 tty5
 1015 tty2     Ss+    0:00 /sbin/getty -8 38400 tty2
 1016 tty3     Ss+    0:00 /sbin/getty -8 38400 tty3
 1019 tty6     Ss+    0:00 /sbin/getty -8 38400 tty6
 1032 ?        Ss     0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
 1049 ?        Ssl    0:01 /usr/sbin/mysqld
 1056 ?        Ss     0:00 cron
 1057 ?        S<     0:00 [kvm-irqfd-clean]
 1060 ?        Ss     0:00 atd
 1087 ?        S<L    0:00 /usr/bin/atop -a -w /var/log/atop.log 600
 1162 ?        S      0:00 logkeys -o /tmp/tmpoutput -u -s
 1251 ?        Ss     0:00 /usr/lib/postfix/master
 1305 ?        Ss     0:00 /usr/sbin/winbindd
 1307 ?        S      0:00 /usr/sbin/winbindd
 1455 ?        S      0:00 [flush-8:0]
 1456 ?        Sl     0:00 /usr/lib/gdm/gdm-session-worker
 1461 ?        Sl     0:00 /usr/lib/upower/upowerd
 1611 ?        S      0:00 /usr/bin/timidity -Os -iAD
 1616 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
 1676 ?        S      0:00 qmgr -l -t fifo -u
 1703 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 1722 ?        Ssl    0:00 gnome-session --session=classic-gnome
 1769 ?        Ssl    0:00 /usr/bin/seahorse-agent --execute gnome-session -- --session=classic-gnome
 1772 ?        S      0:00 dbus-launch --exit-with-session gnome-session --session=classic-gnome
 1773 ?        Ss     0:01 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 1778 ?        S      0:01 /usr/lib/libgconf2-4/gconfd-2
 1784 ?        Sl     0:35 /usr/lib/at-spi/at-spi-registryd
 1789 ?        Ssl    0:04 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 1792 ?        Ssl    0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 1799 ?        S      0:00 /usr/lib/gvfs/gvfsd
 1804 ?        Ssl    0:01 /usr/lib/gvfs//gvfs-fuse-daemon /home/vladimir/.gvfs
 1808 ?        Sl     2:17 compiz
 1813 ?        S<sl   1:22 /usr/bin/pulseaudio --start --log-target=syslog
 1815 ?        SNl    0:00 /usr/lib/rtkit/rtkit-daemon
 1825 ?        Sl     0:00 zeitgeist-datahub
 1828 ?        Sl     0:00 /usr/lib/evolution/2.32/evolution-alarm-notify
 1832 ?        Sl     0:11 gnome-panel
 1833 ?        Sl     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 1834 ?        Sl     0:00 nm-applet --sm-disable
 1839 ?        Sl     0:00 /usr/bin/python /usr/bin/zeitgeist-daemon
 1847 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.14 /org/gtk/gvfs/exec_spaw/0
 1851 ?        Sl     0:00 /usr/lib/evolution/e-calendar-factory
 1853 ?        S      0:00 /usr/bin/gnome-keyring-daemon --start --foreground --components=secrets
 1857 ?        Sl     0:00 /usr/lib/notify-osd/notify-osd
 1858 ?        S      0:00 /bin/cat
 1866 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
 1867 ?        Sl     0:05 /usr/bin/unity-window-decorator
 1871 ?        Sl     0:00 /usr/lib/evolution/e-addressbook-factory
 1879 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 1881 ?        Sl     0:00 /usr/lib/udisks/udisks-daemon
 1882 ?        S      0:00 udisks-daemon: polling /dev/sr0
 1885 ?        Sl     0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
 1888 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 1896 ?        Sl     0:18 /usr/bin/python /usr/bin/dockbarx_factory.py --oaf-activate-iid=OAFIID:GNOME_DockBarXApplet_Factory --oaf-ior-fd=24
 1897 ?        Sl     0:02 /usr/lib/gnome-panel/wnck-applet
 1901 ?        Z      0:00 [zeitgeist-datah] <defunct>
 1909 ?        S      0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.14 /org/gtk/gvfs/exec_spaw/1
 1911 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet
 1913 ?        Sl     0:13 /usr/lib/gnome-applets/multiload-applet-2
 1915 ?        Sl     0:01 /usr/lib/gnome-panel/clock-applet
 1917 ?        Sl     0:00 /usr/lib/indicator-applet/indicator-applet-session
 1919 ?        Sl     0:01 /usr/lib/indicator-applet/indicator-applet
 1934 ?        Sl     0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 1937 ?        S      0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.14 /org/gtk/gvfs/exec_spaw/2
 1969 ?        S      0:00 /usr/lib/gvfs/gvfsd-metadata
 1976 ?        Sl     0:00 /usr/lib/indicator-session/indicator-session-service
 1978 ?        Sl     0:00 /usr/lib/indicator-me/indicator-me-service
 1986 ?        Sl     0:00 /usr/lib/indicator-messages/indicator-messages-service
 1987 ?        Sl     0:00 /usr/lib/indicator-application/indicator-application-service
 1988 ?        Sl     0:00 /usr/lib/indicator-sound/indicator-sound-service
 2012 ?        Ss     0:00 gnome-screensaver
 2029 ?        S      0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 2059 ?        S      0:01 /usr/lib/bamf/bamfdaemon
 2079 ?        S      0:08 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
 2104 ?        S      0:00 /bin/sh -e /usr/bin/couchdb -n -a /etc/couchdb/default.ini -a /etc/xdg/desktop-couch/compulsory-auth.ini -a /home/vladimir/.config/desktop-couch/desktop-couchdb.ini -b -r 0 -p /home/vladimir/.cache/desktop-couch/desktop-couchdb.pid -o /home/vladimir/.cache/desktop-couch/desktop-couchdb.stdout -e /home/vladimir/.cache/desktop-couch/desktop-couchdb.stderr -R
 2111 ?        S      0:00 /bin/sh -e /usr/bin/couchdb -n -a /etc/couchdb/default.ini -a /etc/xdg/desktop-couch/compulsory-auth.ini -a /home/vladimir/.config/desktop-couch/desktop-couchdb.ini -b -r 0 -p /home/vladimir/.cache/desktop-couch/desktop-couchdb.pid -o /home/vladimir/.cache/desktop-couch/desktop-couchdb.stdout -e /home/vladimir/.cache/desktop-couch/desktop-couchdb.stderr -R
 2112 ?        Sl     2:23 /usr/lib/erlang/erts-5.7.4/bin/beam.smp -Bd -K true -A 4 -- -root /usr/lib/erlang -progname erl -- -home /home/vladimir -- -noshell -noinput -sasl errlog_type error -couch_ini /etc/couchdb/default.ini /etc/xdg/desktop-couch/compulsory-auth.ini /home/vladimir/.config/desktop-couch/desktop-couchdb.ini -s couch -pidfile /home/vladimir/.cache/desktop-couch/desktop-couchdb.pid -heart
 2128 ?        Ss     0:00 heart -pid 2112 -ht 11
 2135 ?        SN     0:13 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service
 2136 ?        Z      0:00 [desktopcouch-se] <defunct>
 2140 ?        Ssl    0:00 /usr/lib/couchdb/bin/couchjs /usr/share/couchdb/server/main.js
 2149 ?        Ss     0:00 inet_gethost 4
 2150 ?        S      0:00 inet_gethost 4
 2161 ?        Sl     0:10 update-notifier
 2175 ?        S      0:00 /usr/bin/python /usr/lib/system-service/system-service-d
 2543 ?        Sl     0:00 /usr/bin/gnome-power-manager
 2963 ?        S      0:00 /bin/sh -c gnome-terminal
 2964 ?        Sl     0:17 gnome-terminal
 2967 ?        S      0:00 gnome-pty-helper
 3094 ?        S      0:00 dbus-launch --autolaunch=f484ae9a42559ce2454cb23d4cfd014d --binary-syntax --close-stderr
 3095 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 3101 pts/1    Ss+    0:00 bash
 3752 ?        S      0:00 pickup -l -t fifo -u -c
 3771 ?        Sl     0:07 nautilus
 4099 pts/0    Ss     0:00 bash
 6336 ?        S      0:00 [kworker/3:2]
 8841 ?        Ss     0:00 /usr/sbin/cupsd -F
17295 ?        S      0:00 /bin/sh -c firefox 
17296 ?        Sl     3:48 /usr/lib/firefox-5.0/firefox-bin
17336 ?        Sl     1:26 /usr/lib/firefox-5.0/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -omnijar /usr/lib/firefox-5.0/omni.jar 17296 true plugin
17410 ?        S      0:00 [kworker/0:0]
17483 ?        Sl     0:00 /usr/bin/python /usr/bin/gwibber-service
17494 ?        S      0:00 /usr/bin/python /usr/bin/gwibber-service
17495 ?        S      0:00 /usr/bin/python /usr/bin/gwibber-service
17496 ?        S      0:00 /usr/bin/python /usr/bin/gwibber-service
17497 ?        S      0:00 /usr/bin/python /usr/bin/gwibber-service
17553 ?        S      0:00 [kworker/3:0]
17554 ?        S      0:00 [kworker/2:0]
17555 ?        S      0:00 [kworker/1:2]
17560 ?        S      0:00 [kworker/0:1]
17563 ?        Z      0:03 [dbx_preference.] <defunct>
17566 ?        S      0:00 [kworker/3:1]
17572 ?        S      0:00 [kworker/1:0]
17574 ?        S      0:00 [kworker/0:2]
17575 ?        S      0:00 [kworker/2:2]
17579 pts/0    R+     0:00 ps ax
```

---

### Post by intheflesh on 2011-07-31
UPDATE: this doesn't happen anymore, I'm happy to report, but I have another problem. It is equally strange and a little less annoying. I installed the binary ATi drivers from AMD's website. It is much faster and I can use shaders in Sauerbraten (with opensource drivers turning them on would result in garbled geometry instead of gun models).
But if I move the mouse to the bottom right part of the screen and I move the cursor around a bit, it stops moving for a second or two, like something grabs it, and then releases it for another second or two. And then it alternates between holding it and moving normally. WTF?
EDIT: not only does the mouse stop moving, the whole display freezes.
EDIT2: this seems to be a Catalyst driver problem. It affects versions 11.5+ [https://bbs.archlinux.org/viewtopic.php?pid=940522#p940522](https://bbs.archlinux.org/viewtopic.php?pid=940522#p940522)
EDIT3: if you have a similar issue, go here and tell ATI/AMD about it: [http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36](http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36)

---

### Post by bogdanbiv on 2011-10-14
My advice is post here what solved your initial problem. It may be useful even for you as some problems come back long after you forgot what the solution was.

Also, don't re-use your threads for new problems. Start a new thread every time you encounter a different problem.

---

