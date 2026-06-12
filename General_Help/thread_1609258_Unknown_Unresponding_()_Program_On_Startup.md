---
title: "Unknown Unresponding (?) Program On Startup"
date: 2010-10-30
forum: General Help
---

### Post by lanetherif on 2010-10-30
Hi,

on every start up, I get a frame which can not be closed because I don't know to which program it belongs to. 
Since I am not that familiar with running programs and their respective tasks on system monitor, I can't figure out which one to close. By the way the second one showed up around the time I was taking the screen shot and I don't remember what it was about.

Any idea will be appreciated. 
Here is a screen shot and  list of running tasks:

[http://dl.dropbox.com/u/8054767/Screenshot.jpg](http://dl.dropbox.com/u/8054767/Screenshot.jpg)
```
 UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 11:59 ?        00:00:00 /sbin/init
root         2     0  0 11:59 ?        00:00:00 [kthreadd]
root         3     2  0 11:59 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 11:59 ?        00:00:00 [migration/0]
root         5     2  0 11:59 ?        00:00:00 [watchdog/0]
root         6     2  0 11:59 ?        00:00:00 [migration/1]
root         7     2  0 11:59 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 11:59 ?        00:00:00 [watchdog/1]
root         9     2  0 11:59 ?        00:00:00 [migration/2]
root        10     2  0 11:59 ?        00:00:00 [ksoftirqd/2]
root        11     2  0 11:59 ?        00:00:00 [watchdog/2]
root        12     2  0 11:59 ?        00:00:00 [migration/3]
root        13     2  0 11:59 ?        00:00:00 [ksoftirqd/3]
root        14     2  0 11:59 ?        00:00:00 [watchdog/3]
root        15     2  0 11:59 ?        00:00:00 [events/0]
root        16     2  0 11:59 ?        00:00:00 [events/1]
root        17     2  0 11:59 ?        00:00:00 [events/2]
root        18     2  0 11:59 ?        00:00:00 [events/3]
root        19     2  0 11:59 ?        00:00:00 [cpuset]
root        20     2  0 11:59 ?        00:00:00 [khelper]
root        21     2  0 11:59 ?        00:00:00 [netns]
root        22     2  0 11:59 ?        00:00:00 [async/mgr]
root        23     2  0 11:59 ?        00:00:00 [pm]
root        25     2  0 11:59 ?        00:00:00 [sync_supers]
root        26     2  0 11:59 ?        00:00:00 [bdi-default]
root        27     2  0 11:59 ?        00:00:00 [kintegrityd/0]
root        28     2  0 11:59 ?        00:00:00 [kintegrityd/1]
root        29     2  0 11:59 ?        00:00:00 [kintegrityd/2]
root        30     2  0 11:59 ?        00:00:00 [kintegrityd/3]
root        31     2  0 11:59 ?        00:00:00 [kblockd/0]
root        32     2  0 11:59 ?        00:00:00 [kblockd/1]
root        33     2  0 11:59 ?        00:00:00 [kblockd/2]
root        34     2  0 11:59 ?        00:00:00 [kblockd/3]
root        35     2  0 11:59 ?        00:00:00 [kacpid]
root        36     2  0 11:59 ?        00:00:00 [kacpi_notify]
root        37     2  0 11:59 ?        00:00:00 [kacpi_hotplug]
root        38     2  0 11:59 ?        00:00:00 [ata_aux]
root        39     2  0 11:59 ?        00:00:00 [ata_sff/0]
root        40     2  0 11:59 ?        00:00:00 [ata_sff/1]
root        41     2  0 11:59 ?        00:00:00 [ata_sff/2]
root        42     2  0 11:59 ?        00:00:00 [ata_sff/3]
root        43     2  0 11:59 ?        00:00:00 [khubd]
root        44     2  0 11:59 ?        00:00:00 [kseriod]
root        45     2  0 11:59 ?        00:00:00 [kmmcd]
root        70     2  0 11:59 ?        00:00:00 [khungtaskd]
root        71     2  0 11:59 ?        00:00:00 [kswapd0]
root        72     2  0 11:59 ?        00:00:00 [ksmd]
root        73     2  0 11:59 ?        00:00:00 [aio/0]
root        74     2  0 11:59 ?        00:00:00 [aio/1]
root        75     2  0 11:59 ?        00:00:00 [aio/2]
root        76     2  0 11:59 ?        00:00:00 [aio/3]
root        77     2  0 11:59 ?        00:00:00 [ecryptfs-kthrea]
root        78     2  0 11:59 ?        00:00:00 [crypto/0]
root        79     2  0 11:59 ?        00:00:00 [crypto/1]
root        80     2  0 11:59 ?        00:00:00 [crypto/2]
root        81     2  0 11:59 ?        00:00:00 [crypto/3]
root        97     2  0 11:59 ?        00:00:00 [kstriped]
root        98     2  0 11:59 ?        00:00:00 [kmpathd/0]
root        99     2  0 11:59 ?        00:00:00 [kmpathd/1]
root       100     2  0 11:59 ?        00:00:00 [kmpathd/2]
root       101     2  0 11:59 ?        00:00:00 [kmpathd/3]
root       102     2  0 11:59 ?        00:00:00 [kmpath_handlerd]
root       103     2  0 11:59 ?        00:00:00 [ksnapd]
root       104     2  0 11:59 ?        00:00:00 [kondemand/0]
root       105     2  0 11:59 ?        00:00:00 [kondemand/1]
root       106     2  0 11:59 ?        00:00:00 [kondemand/2]
root       107     2  0 11:59 ?        00:00:01 [kondemand/3]
root       108     2  0 11:59 ?        00:00:00 [kconservative/0]
root       109     2  0 11:59 ?        00:00:00 [kconservative/1]
root       110     2  0 11:59 ?        00:00:00 [kconservative/2]
root       111     2  0 11:59 ?        00:00:00 [kconservative/3]
root       276     2  0 11:59 ?        00:00:00 [scsi_eh_0]
root       303     2  0 11:59 ?        00:00:00 [scsi_eh_1]
root       304     2  0 11:59 ?        00:00:00 [scsi_eh_2]
root       305     2  0 11:59 ?        00:00:00 [scsi_eh_3]
root       310     2  0 11:59 ?        00:00:00 [scsi_eh_4]
root       311     2  0 11:59 ?        00:00:00 [scsi_eh_5]
root       316     2  0 11:59 ?        00:00:00 [scsi_eh_6]
root       317     2  0 11:59 ?        00:00:00 [usb-storage]
root       337     2  0 11:59 ?        00:00:00 [jbd2/sda1-8]
root       338     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       339     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       340     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       341     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       375     2  0 11:59 ?        00:00:00 [flush-8:0]
root       403     1  0 11:59 ?        00:00:00 upstart-udev-bridge --daemon
root       405     1  0 11:59 ?        00:00:00 udevd --daemon
root       544   405  0 11:59 ?        00:00:00 udevd --daemon
root       559     2  0 11:59 ?        00:00:00 [edac-poller]
root       560   405  0 11:59 ?        00:00:00 udevd --daemon
root       580     2  0 11:59 ?        00:00:00 [kpsmoused]
root       774     2  0 11:59 ?        00:00:00 [hd-audio0]
root       812     2  0 11:59 ?        00:00:00 [hd-audio1]
root       920     2  0 11:59 ?        00:00:00 [jbd2/sda2-8]
root       921     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       922     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       923     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       924     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       940     1  0 11:59 ?        00:00:00 /sbin/mount.ntfs /dev/sda3 /medi
root       943     2  0 11:59 ?        00:00:00 [jbd2/sda4-8]
root       944     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       945     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       946     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       947     2  0 11:59 ?        00:00:00 [ext4-dio-unwrit]
root       963     1  0 11:59 ?        00:00:00 smbd -F
syslog     972     1  0 11:59 ?        00:00:00 rsyslogd -c4
102        986     1  0 11:59 ?        00:00:00 dbus-daemon --system --fork
root       995     1  0 11:59 ?        00:00:00 gdm-binary
avahi     1001     1  0 11:59 ?        00:00:00 avahi-daemon: running [seed-desk
root      1002     1  0 11:59 ?        00:00:00 NetworkManager
avahi     1003  1001  0 11:59 ?        00:00:00 avahi-daemon: chroot helper
root      1005     1  0 11:59 ?        00:00:00 /usr/sbin/modem-manager
root      1007     1  0 11:59 ?        00:00:00 /usr/sbin/console-kit-daemon --n
root      1072   963  0 11:59 ?        00:00:00 smbd -F
root      1075     1  0 11:59 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      1076  1002  0 11:59 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/N
root      1104     1  0 11:59 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root      1107   995  0 11:59 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --
root      1147     1  0 11:59 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1151     1  0 11:59 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1158     1  0 11:59 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1159     1  0 11:59 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1162     1  0 11:59 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1171     1  0 11:59 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root      1244     1  0 11:59 ?        00:00:00 cron
daemon    1245     1  0 11:59 ?        00:00:00 atd
root      1296  1107 10 11:59 tty7     00:03:20 /usr/bin/X :0 -br -verbose -auth
root      1328     1  0 11:59 ?        00:00:00 /usr/sbin/hddtemp -d -l 127.0.0.
root      1347     2  0 11:59 ?        00:00:00 [firegl]
root      1369     1  0 11:59 ?        00:00:00 /usr/sbin/winbindd
root      1379  1369  0 11:59 ?        00:00:00 /usr/sbin/winbindd
root      1513     1  0 11:59 ?        00:00:00 nmbd -D
timidity  1576     1  0 11:59 ?        00:00:00 /usr/bin/timidity -Os -iAD
root      1579     1  0 11:59 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1589  1107  0 11:59 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
seed      1598  1589  0 11:59 ?        00:00:00 gnome-session
seed      1647  1598  0 11:59 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/gpg-
seed      1648  1598  0 11:59 ?        00:00:00 /usr/bin/gpg-agent --daemon --sh
seed      1651     1  0 11:59 ?        00:00:00 /usr/bin/dbus-launch --exit-with
seed      1652     1  0 11:59 ?        00:00:01 /bin/dbus-daemon --fork --print-
seed      1657     1  0 11:59 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
seed      1665     1  0 11:59 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
seed      1668     1  0 11:59 ?        00:00:02 /usr/lib/gnome-settings-daemon/g
seed      1671     1  0 11:59 ?        00:00:00 /usr/lib/gvfs/gvfsd
seed      1676     1  0 11:59 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
seed      1681  1598  0 11:59 ?        00:00:17 compiz --sm-client-id 104b56b7e5
seed      1686     1  2 11:59 ?        00:00:49 /usr/bin/pulseaudio --start --lo
rtkit     1688     1  0 11:59 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
root      1695     1  0 11:59 ?        00:00:00 /usr/lib/policykit-1/polkitd
seed      1717  1598  0 11:59 ?        00:00:12 nautilus --sm-client-id 106acad1
seed      1718  1598  0 11:59 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
seed      1719  1598  0 11:59 ?        00:00:05 avant-window-navigator --startup
seed      1720  1598  0 11:59 ?        00:00:00 /bin/sh /usr/bin/gnome-do
seed      1721  1598  0 11:59 ?        00:00:00 /usr/lib/evolution/2.30/evolutio
seed      1729  1720  0 11:59 ?        00:00:03 /usr/bin/cli /usr/lib/gnome-do/D
seed      1745  1598  0 11:59 ?        00:00:00 python /usr/bin/gtk-redshift -l
seed      1749  1598  0 11:59 ?        00:00:00 nm-applet --sm-disable
seed      1750  1598  0 11:59 ?        00:00:00 /usr/bin/python /usr/bin/fusion-
seed      1751     1  0 11:59 ?        00:00:03 /home/seed/.dropbox-dist/dropbox
seed      1760     1  0 11:59 ?        00:00:00 /usr/bin/nepomukserver -session
seed      1767     1  0 11:59 ?        00:00:00 kdeinit4: kdeinit4 Running...
seed      1770  1745  0 11:59 ?        00:00:00 /usr/bin/redshift -l 39.6 32.5
seed      1772  1767  0 11:59 ?        00:00:00 klauncher --fd=8
seed      1782     1  0 11:59 ?        00:00:00 kdeinit4: kded4 [kdeinit]  
seed      1787     1  0 11:59 ?        00:00:00 /usr/lib/evolution/e-calendar-fa
seed      1851  1686  0 12:00 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
seed      1877     1  0 12:00 ?        00:00:00 /usr/lib/notify-osd/notify-osd
seed      1882     1  0 12:00 ?        00:00:00 /usr/lib/evolution/e-addressbook
seed      1890     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
root      1893     1  0 12:00 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      1895  1893  0 12:00 ?        00:00:00 udisks-daemon: polling /dev/sdc 
seed      1897  1681  0 12:00 ?        00:00:00 /bin/sh -c gtk-window-decorator 
seed      1898  1897  0 12:00 ?        00:00:01 gtk-window-decorator --replace
seed      1912  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
seed      1915     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
seed      1919     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
seed      1922     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
seed      1929  1912  0 12:00 ?        00:00:01 /usr/bin/virtuoso-t +foreground
seed      1931  1719  0 12:00 ?        00:00:02 awn-applet -p /usr/share/avant-w
seed      1933  1719  0 12:00 ?        00:00:07 awn-applet -p /usr/share/avant-w
seed      1934  1719  0 12:00 ?        00:00:00 python /usr/share/avant-window-n
seed      1935  1719  0 12:00 ?        00:00:00 awn-applet -p /usr/share/avant-w
seed      1936  1719  0 12:00 ?        00:00:01 python /usr/share/avant-window-n
seed      1937  1719  0 12:00 ?        00:00:00 python /usr/share/avant-window-n
seed      1938  1719  0 12:00 ?        00:00:07 python /usr/share/avant-window-n
seed      1939  1719  0 12:00 ?        00:00:00 python /usr/share/avant-window-n
seed      1948     1  0 12:00 ?        00:00:00 gnome-screensaver
seed      1953     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
seed      1958     1  0 12:00 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
seed      2016  1598  0 12:00 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-
seed      2067  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
seed      2068  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
seed      2069  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
seed      2070  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
seed      2073  1760  0 12:00 ?        00:00:00 /usr/bin/nepomukservicestub nepo
108       2180     1  0 12:00 ?        00:00:00 /usr/sbin/hald
root      2181  2180  0 12:00 ?        00:00:00 hald-runner
root      2241  2181  0 12:00 ?        00:00:00 hald-addon-input: Listening on /
root      2256  2181  0 12:00 ?        00:00:00 hald-addon-storage: polling /dev
root      2257  2181  0 12:00 ?        00:00:00 hald-addon-storage: polling /dev
root      2258  2181  0 12:00 ?        00:00:00 hald-addon-storage: polling /dev
root      2259  2181  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
108       2260  2181  0 12:00 ?        00:00:00 hald-addon-acpi: listening on ac
root      2261  2181  0 12:00 ?        00:00:00 hald-addon-storage: polling /dev
seed      2289     1  1 12:00 ?        00:00:29 amarok /media/Depo/Müzik/Yerli/A
seed      2304     1  0 12:00 ?        00:00:00 /usr/bin/kglobalaccel
seed      2308     1  0 12:00 ?        00:00:00 /usr/bin/kwalletd
seed      2329  2289  0 12:00 ?        00:00:00 /bin/bash
seed      2338  1767  0 12:00 ?        00:00:00 /usr/lib/kde4/libexec/kio_http_c
seed      2344     1  0 12:00 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.12/
seed      2348  2344  0 12:00 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.12/
seed      2352  2348 10 12:00 ?        00:03:19 /usr/lib/firefox-3.6.12/firefox-
seed      2368  1598  0 12:00 ?        00:00:00 update-notifier
seed      2429  2352  3 12:01 ?        00:01:04 /usr/lib/firefox-3.6.12/plugin-c
root      2684  1369  0 12:11 ?        00:00:00 /usr/sbin/winbindd
seed      2736     1  0 12:15 ?        00:00:02 gnome-terminal
seed      2740  2736  0 12:15 ?        00:00:00 gnome-pty-helper
seed      2741  2736  0 12:15 pts/0    00:00:00 bash
seed      3155  2741  0 12:33 pts/0    00:00:00 ps -ef


```

---

### Post by lanetherif on 2010-10-30
Now, after logging out and logging in, I at least know one windows with this trait. Firefox window also became like the ones I asked about.
What might be the cause?

---

### Post by lanetherif on 2010-10-30
Another update:

After another restart, the formerly opened firefox window appeared like the ones in screenshot and the video tab opened in it resumed. 
I think my problem is about AWN and Gnome...

I still appreciate any ideas...

---

