---
title: "very high processor usage"
date: 2010-05-02
forum: General Help
---

### Post by alphageek89 on 2010-05-02
i have the system monitor applet on my panel which is showing a constant 70%+ usage at all times even when my firefox and all other applications are closed.I use to have a look at this applet in 9.10 which never showed so much cpu usage.

What details do i need to provide to diagnose this problem.

---

### Post by dino99 on 2010-05-02
need to identify which app(s) or services use cpu

is there boinc used or something else in the background ?

---

### Post by alphageek89 on 2010-05-02
```

varun@varun:~$ top

top - 19:19:05 up  8:04,  2 users,  load average: 2.93, 2.82, 2.55
Tasks: 184 total,   4 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.7%us, 34.8%sy,  0.5%ni, 20.5%id,  0.0%wa,  0.3%hi,  0.2%si,  0.0%st
Mem:   2019952k total,  1689776k used,   330176k free,   183808k buffers
Swap:  2048276k total,     2744k used,  2045532k free,   824552k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1182 root      20   0 84900  33m  17m R   25  1.7  89:57.43 Xorg               
 1537 varun     20   0  266m 222m  10m R   17 11.3  91:28.02 indicator-apple    
 1553 varun     20   0 85152 4532 3620 S   12  0.2  60:34.47 indicator-sound    
 9825 varun     20   0 46724  19m  15m S   10  1.0   0:25.96 gnome-system-mo    
 3956 varun     20   0  415m 144m  31m S    8  7.3   0:43.94 firefox-bin        
 1376 varun     20   0  3664 1968  680 S    6  0.1  27:44.81 dbus-daemon        
 1426 varun     20   0 92096  26m 6632 S    5  1.4  17:01.21 compiz             
 5481 varun     20   0 31848  13m 6920 S    4  0.7  17:41.91 python             
25506 varun     20   0 48216  13m  10m S    2  0.7   0:00.54 gnome-terminal     
  783 syslog    20   0 35456 1164  856 S    2  0.1   8:51.64 rsyslogd           
 1412 varun     20   0 46276  16m  11m S    2  0.8   8:24.27 gnome-panel        
 1414 varun     20   0  117m  33m  15m S    2  1.7   7:51.89 nautilus           
 1421 varun     27   7 54964  12m 2948 S    2  0.6   5:31.80 beagled            
 8964 varun     20   0  132m  24m  12m S    1  1.3  11:19.96 transmission       
  833 root      20   0 18748 3080 2528 S    1  0.2   4:24.46 gdm-binary         
 1397 varun     20   0 89292 8916 6820 S    1  0.4   6:30.97 gnome-settings-    
 1552 varun     20   0 18828 5088 4120 S    1  0.3   5:25.87 indicator-me-se    

```

```

varun@varun:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2796  1540 ?        Ss   11:14   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    11:14   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    11:14   0:02 [migration/0]
root         4  0.0  0.0      0     0 ?        S    11:14   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    11:14   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    11:14   0:02 [migration/1]
root         7  0.0  0.0      0     0 ?        S    11:14   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    11:14   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    11:14   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    11:14   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    11:14   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    11:14   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    11:14   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    11:14   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    11:14   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    11:14   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    11:14   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    11:14   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    11:14   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    11:14   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    11:14   0:00 [kblockd/1]
root        23  0.1  0.0      0     0 ?        S    11:14   0:38 [kacpid]
root        24  0.9  0.0      0     0 ?        S    11:14   4:25 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    11:14   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    11:14   0:03 [ata/0]
root        27  0.0  0.0      0     0 ?        S    11:14   0:03 [ata/1]
root        28  0.0  0.0      0     0 ?        S    11:14   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    11:14   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    11:14   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    11:14   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    11:14   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    11:14   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    11:14   0:05 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   11:14   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    11:14   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    11:14   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    11:14   0:00 [ecryptfs-kthr]
root        41  0.0  0.0      0     0 ?        S    11:14   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    11:14   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    11:14   0:00 [pciehpd]
root        54  0.0  0.0      0     0 ?        S    11:14   0:00 [scsi_eh_0]
root        55  0.0  0.0      0     0 ?        S    11:14   0:18 [scsi_eh_1]
root        56  0.0  0.0      0     0 ?        S    11:14   0:00 [kstriped]
root        57  0.0  0.0      0     0 ?        S    11:14   0:00 [kmpathd/0]
root        58  0.0  0.0      0     0 ?        S    11:14   0:00 [kmpathd/1]
root        59  0.0  0.0      0     0 ?        S    11:14   0:00 [kmpath_handle]
root        60  0.0  0.0      0     0 ?        S    11:14   0:00 [ksnapd]
root        61  0.0  0.0      0     0 ?        S    11:14   0:01 [kondemand/0]
root        62  0.0  0.0      0     0 ?        S    11:14   0:01 [kondemand/1]
root        63  0.0  0.0      0     0 ?        S    11:14   0:00 [kconservative]
root        64  0.0  0.0      0     0 ?        S    11:14   0:00 [kconservative]
root       275  0.0  0.0      0     0 ?        S    11:14   0:00 [khpsbpkt]
root       293  0.0  0.0      0     0 ?        S    11:14   0:00 [knodemgrd_0]
root       306  0.0  0.0      0     0 ?        S    11:14   0:03 [jbd2/sda2-8]
root       307  0.0  0.0      0     0 ?        S    11:14   0:00 [ext4-dio-unwr]
root       308  0.0  0.0      0     0 ?        S    11:14   0:00 [ext4-dio-unwr]
root       339  0.0  0.0      0     0 ?        S    11:14   0:00 [flush-8:0]
root       368  0.0  0.0   2312   780 ?        S    11:14   0:00 upstart-udev-br
root       370  0.0  0.0   2616   604 ?        S<s  11:14   0:00 udevd --daemon
root       626  0.0  0.0      0     0 ?        S    11:14   0:00 [kpsmoused]
root       628  0.0  0.0      0     0 ?        S    11:14   0:00 [bluetooth]
root       657  0.0  0.0      0     0 ?        S    11:14   0:00 [i915]
root       681  0.0  0.0      0     0 ?        S    11:14   0:00 [pccardd]
root       696  0.0  0.0      0     0 ?        S    11:14   0:08 [iwlagn]
root       697  0.0  0.0      0     0 ?        S    11:14   0:03 [phy0]
root       743  0.0  0.0      0     0 ?        S    11:14   0:00 [ktpacpid]
root       759  0.0  0.0   2796   808 ?        Ss   11:14   0:00 /sbin/mount.ntf
root       772  0.2  0.0   3256  1400 ?        Ss   11:14   1:04 /sbin/mount.ntf
syslog     783  1.8  0.0  35456  1164 ?        Sl   11:14   8:53 rsyslogd -c4
102        796  0.0  0.0   3288  1576 ?        Ss   11:14   0:20 dbus-daemon --s
root       801  0.0  0.1  18872  3796 ?        Ssl  11:14   0:00 NetworkManager
root       803  0.0  0.1   4164  2076 ?        S    11:14   0:00 /usr/sbin/modem
avahi      809  0.0  0.0   3056  1556 ?        S    11:14   0:00 avahi-daemon: r
avahi      811  0.0  0.0   2924   480 ?        Ss   11:14   0:00 avahi-daemon: c
root       833  0.9  0.1  18748  3080 ?        Ssl  11:14   4:25 gdm-binary
root       836  0.0  0.0      0     0 ?        S    11:14   0:00 [hd-audio0]
root       858  0.0  0.1  20764  2992 ?        Sl   11:14   0:00 /usr/sbin/conso
root       942  0.0  0.0   1788   512 tty4     Ss+  11:14   0:00 /sbin/getty -8
root       947  0.0  0.0   1788   536 tty5     Ss+  11:14   0:00 /sbin/getty -8
root       955  0.0  0.0   1788   536 tty2     Ss+  11:14   0:00 /sbin/getty -8
root       956  0.0  0.0   1788   540 tty3     Ss+  11:14   0:00 /sbin/getty -8
root       962  0.0  0.0   1788   532 tty6     Ss+  11:14   0:00 /sbin/getty -8
root       969  0.1  0.0   2044   936 ?        Ss   11:14   0:46 acpid -c /etc/a
daemon     973  0.0  0.0   2244   432 ?        Ss   11:14   0:00 atd
root       974  0.0  0.0   2372   884 ?        Ss   11:14   0:00 cron
root       975  0.0  0.0   2612   580 ?        S<   11:14   0:00 udevd --daemon
root       982  0.0  0.1  20484  3168 ?        Sl   11:14   0:00 /usr/lib/gdm/gd
root      1010  0.0  0.0   2612   544 ?        S<   11:14   0:00 udevd --daemon
clamav    1117  0.0  0.0  12100  1544 ?        Ss   11:14   0:00 /usr/bin/freshc
root      1128  0.0  0.1   4824  2040 ?        S    11:14   0:00 /sbin/wpa_suppl
root      1179  0.0  0.0  11732  1116 ?        Ss   11:14   0:00 /usr/sbin/winbi
root      1182 18.6  1.6  64908 34236 tty7     Ss+  11:14  90:25 /usr/bin/X :0 -
root      1183  0.0  0.0  11732   992 ?        S    11:14   0:00 /usr/sbin/winbi
root      1188  0.0  0.0   4048  1328 ?        S<s  11:14   0:00 /usr/sbin/bluet
root      1218  0.0  0.0   6692  1856 ?        Ss   11:14   0:00 /usr/sbin/cupsd
root      1242  0.0  0.0      0     0 ?        S<   11:14   0:00 [krfcommd]
root      1327  0.0  0.0   1788   540 tty1     Ss+  11:14   0:00 /sbin/getty -8
root      1329  0.0  0.1  18964  2916 ?        Sl   11:14   0:00 /usr/lib/gdm/gd
varun     1338  0.0  0.5  38408 10168 ?        Ssl  11:14   0:00 gnome-session
varun     1372  0.0  0.0   3280   320 ?        Ss   11:14   0:00 /usr/bin/ssh-ag
varun     1375  0.0  0.0   3380   756 ?        S    11:14   0:00 /usr/bin/dbus-l
varun     1376  5.7  0.0   3664  1968 ?        Ss   11:14  27:49 /bin/dbus-daemo
varun     1389  0.0  0.2   7692  4132 ?        S    11:15   0:01 /usr/lib/libgco
varun     1394  0.0  0.1  23952  2696 ?        SLl  11:15   0:00 gnome-keyring-d
varun     1397  1.3  0.4  89292  8916 ?        Ss   11:15   6:31 /usr/lib/gnome-
varun     1403  0.0  0.1   6480  2332 ?        S    11:15   0:00 /usr/lib/gvfs/g
varun     1408  0.0  0.1  30276  2604 ?        Ssl  11:15   0:00 /usr/lib/gvfs//
varun     1412  1.7  0.8  46276 17088 ?        S    11:15   8:25 gnome-panel
varun     1414  1.6  1.6 120036 34044 ?        S    11:15   7:52 nautilus
varun     1416  0.0  0.6  35824 13484 ?        S    11:15   0:02 gnome-power-man
varun     1419  0.0  0.7  57532 14628 ?        SL   11:15   0:21 nm-applet --sm-
varun     1421  1.1  0.6  54964 12384 ?        SNl  11:15   5:32 beagled /usr/li
varun     1423  0.0  0.4  36076  9568 ?        S    11:15   0:00 bluetooth-apple
varun     1424  0.0  0.2  18364  5868 ?        S    11:15   0:00 /usr/lib/policy
varun     1426  3.5  1.3  91960 27344 ?        S    11:15  17:04 /usr/bin/compiz
varun     1431  0.0  0.0   3816  1072 ?        S    11:15   0:07 syndaemon -i 0.
root      1436  0.0  0.1   5564  2820 ?        S    11:15   0:01 /usr/lib/upower
varun     1445  0.0  0.1  41516  3432 ?        S    11:15   0:00 /usr/lib/gvfs/g
root      1450  0.0  0.1   6472  3928 ?        S    11:15   0:00 /usr/lib/policy
root      1453  0.0  0.1  15688  2976 ?        Sl   11:15   0:00 /usr/lib/udisks
root      1455  0.0  0.0   5176   868 ?        S    11:15   0:04 udisks-daemon: 
varun     1459  0.0  0.1   6796  2884 ?        S    11:15   0:00 /usr/lib/gvfs/g
varun     1485  0.0  0.1  41924  3544 ?        Ssl  11:15   0:00 /usr/lib/bonobo
varun     1499  0.0  0.1  16920  2264 ?        Sl   11:15   0:00 /usr/lib/gvfs/g
varun     1505  0.0  0.1   7124  2276 ?        S    11:15   0:00 /usr/lib/gvfs/g
varun     1517  0.0  0.6  43184 13952 ?        S    11:15   0:10 /usr/lib/gnome-
varun     1522  0.0  0.5  40132 10540 ?        S    11:15   0:00 /usr/lib/gnome-
varun     1531  0.0  0.6  43592 14080 ?        S    11:15   0:24 /usr/lib/gnome-
varun     1536  0.0  0.6  51024 12956 ?        S    11:15   0:00 /usr/lib/indica
varun     1537 18.9 11.2 273504 228036 ?       Sl   11:15  91:41 /usr/lib/indica
varun     1538  0.0  0.4  23060  8788 ?        S    11:15   0:08 /usr/lib/gnome-
varun     1539  0.0  0.5  24644 11084 ?        S    11:15   0:05 /usr/lib/gnome-
varun     1540  0.0  0.7  49160 14440 ?        S    11:15   0:00 /usr/lib/gnome-
varun     1543  0.0  0.0   1828   508 ?        Ss   11:15   0:00 /bin/sh -c /usr
varun     1544  0.0  0.5  21376 10592 ?        S    11:15   0:03 /usr/bin/gtk-wi
varun     1549  0.0  0.0   6188  1920 ?        S    11:15   0:00 /usr/lib/gvfs/g
varun     1552  1.1  0.2  18828  5088 ?        S    11:15   5:26 /usr/lib/indica
varun     1553 12.5  0.2  85152  4532 ?        S    11:15  60:43 /usr/lib/indica
varun     1557  0.0  0.2  17948  4724 ?        S    11:15   0:00 /usr/lib/indica
varun     1562  0.0  0.2  24296  4224 ?        S    11:15   0:00 /usr/lib/indica
varun     1563  0.0  0.2  17480  4348 ?        S    11:15   0:00 /usr/lib/indica
varun     1577  0.0  0.1   6376  2288 ?        S    11:15   0:00 /usr/lib/gvfs/g
108       1683  0.2  0.1  16792  2400 ?        Ssl  11:15   1:16 /usr/sbin/hald
root      1685  0.0  0.0   3528  1288 ?        S    11:15   0:00 hald-runner
root      1745  0.0  0.0   3604  1236 ?        S    11:15   0:00 hald-addon-inpu
root      1748  0.0  0.0   3604  1196 ?        S    11:15   0:00 /usr/lib/hal/ha
root      1750  0.0  0.0   3604  1200 ?        S    11:15   0:00 /usr/lib/hal/ha
root      1759  0.0  0.0   3600  1172 ?        S    11:15   0:00 /usr/lib/hal/ha
root      1772  0.0  0.0   3608  1208 ?        S    11:15   0:10 hald-addon-stor
root      1773  0.0  0.0   3616  1192 ?        S    11:15   0:00 /usr/lib/hal/ha
108       1775  0.1  0.0   3416  1184 ?        S    11:15   0:50 hald-addon-acpi
varun     1897  0.0  0.2  17912  5632 ?        Ss   11:15   0:01 gnome-screensav
varun     2616  0.0  0.3  18868  7036 ?        S    11:15   0:00 /usr/lib/gnome-
varun     3940  0.0  0.0   1828   560 ?        S    19:15   0:00 /bin/sh /usr/li
varun     3949  0.0  0.0   1828   572 ?        S    19:15   0:00 /bin/sh /usr/li
varun     3956 18.1  7.2 416932 146848 ?       Sl   19:15   0:57 /usr/lib/firefo
varun     5147  0.0  0.0   2712  1064 pts/0    R+   19:20   0:00 ps aux
varun     5340  0.0  0.1  19032  3752 ?        S    12:30   0:00 /usr/lib/gvfs/g
varun     5467  0.0  0.9  95764 18816 ?        SLl  11:15   0:10 /usr/bin/python
varun     5474  0.0  0.4  34588  9056 ?        Sl   11:15   0:00 /usr/lib/evolut
varun     5481  3.6  0.6  31848 13924 ?        S    11:15  17:44 python /usr/sha
varun     5705  0.1  0.5  16508 11004 ?        S    11:15   0:41 /usr/bin/python
varun     6192  0.0  0.0   1828   584 ?        S    11:15   0:00 /bin/sh -e /usr
varun     6228  0.0  0.0   1828   360 ?        S    11:15   0:00 /bin/sh -e /usr
varun     6229  0.4  0.6  68752 12272 ?        Sl   11:15   2:03 /usr/lib/erlang
varun     6283  0.0  0.0   1616   448 ?        Ss   11:15   0:00 heart -pid 6229
varun     6433  0.1  0.5  16996 10460 ?        SN   11:15   0:41 /usr/bin/python
varun     6737  0.0  0.1  20392  3008 ?        Ssl  11:16   0:00 /usr/lib/couchd
varun     7923  0.0  0.9  78368 18568 ?        S    11:51   0:00 /usr/bin/knotif
varun     8320  0.0  0.6  39020 12420 ?        S    11:16   0:03 /usr/lib/notify
varun     8964  2.3  1.2 136116 25560 ?        Sl   11:16  11:21 transmission
varun     9564  0.0  0.5  38432 11776 ?        S    11:16   0:00 update-notifier
root     10145  0.0  0.3  13672  7076 ?        S    11:16   0:00 /usr/bin/python
root     13774  0.0  0.0   2228  1024 ?        S    17:50   0:00 /sbin/dhclient
varun    14361  0.0  0.1   9232  3540 ?        S    17:50   0:00 /usr/lib/telepa
varun    14363  0.0  0.3  20984  7632 ?        S    17:50   0:01 /usr/lib/telepa
varun    25506  0.6  0.6  48344 13676 ?        Sl   19:18   0:00 gnome-terminal
varun    25573  0.0  0.0   1984   716 ?        S    19:18   0:00 gnome-pty-helpe
varun    25575  0.2  0.1   6056  3428 pts/0    Ss   19:18   0:00 bash
varun    27184  0.0  0.9  79920 18988 ?        S    15:20   0:00 akonaditray
varun    31236  0.1  1.8 155480 37116 ?        Sl   14:39   0:20 empathy
varun    31304  0.0  0.1   6960  3764 ?        SL   14:39   0:01 /usr/lib/telepa
varun    31360  0.0  0.7  21160 16104 ?        S    14:39   0:03 /usr/bin/python

```


hope this helps.

---

### Post by rnerwein on 2010-05-02
hi
open a terminal and run "top" to identify which process(es) are consuming your cpu.
interesting too is - in wich state of the cpu is the consumption 
Cpu(s):  2.8%us,  1.0%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st

ciao

---

### Post by rnerwein on 2010-05-02
hi
sorry but i think you have some hardware problems - why do i think that.
your syslogd uses to much cpu time ( not the current time in top i mean your system is up for only 8 hours )
syslog     783  1.8  0.0  35456  1164 ?        Sl   11:14   [COLOR=Red]8:53[/COLOR] rsyslogd -c4

have a look in your /var/log  ( messages, daemon, syslog etc. )
even your processes:
varun     1537 18.9 11.2 273504 228036 ?       Sl   11:15[COLOR=Red]  91:41 [/COLOR]/usr/lib/indica*
have a very strange cpu time.
hope this will help you to locate your problem.
ciao
p.s. close some tabs of firefox will help a little about the swaping of your system. :-)

---

### Post by alphageek89 on 2010-05-02
can all of this by any chance have to do with 10.04 because it certainly wasn't half that much 2 days ago with 9.10

---

### Post by alphageek89 on 2010-05-02
i think i know what was wrong. When i rebooted i got an .ICEauthority error. I fixed that i know my cpu usage has gone down drastically.

```

varun@varun:~$ top

top - 02:25:34 up 2 min,  2 users,  load average: 1.25, 0.53, 0.19
Tasks: 188 total,   2 running, 186 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.6%us,  9.3%sy,  0.8%ni, 65.9%id, 13.1%wa,  0.2%hi,  0.1%si,  0.0%st
Mem:   2019952k total,   664392k used,  1355560k free,    49108k buffers
Swap:  2048276k total,        0k used,  2048276k free,   309476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1704 varun     20   0  316m  87m  26m S    6  4.4   0:12.17 firefox-bin        
 2006 varun     20   0  2540 1124  812 R    4  0.1   0:00.03 top                
    1 root      20   0  2796 1672 1224 S    0  0.1   0:00.44 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm            

```

```

varun@varun:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.2  0.0   2796  1672 ?        Ss   02:23   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    02:23   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    02:23   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    02:23   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    02:23   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    02:23   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    02:23   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    02:23   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    02:23   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    02:23   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    02:23   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    02:23   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    02:23   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    02:23   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    02:23   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    02:23   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    02:23   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    02:23   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    02:23   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    02:23   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    02:23   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    02:23   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    02:23   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    02:23   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    02:23   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    02:23   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    02:23   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    02:23   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    02:23   0:00 [khubd]
root        31  0.2  0.0      0     0 ?        S    02:23   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    02:23   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    02:23   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    02:23   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   02:23   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    02:23   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    02:23   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    02:23   0:00 [ecryptfs-kthr]
root        41  0.0  0.0      0     0 ?        S    02:23   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    02:23   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    02:23   0:00 [pciehpd]
root        54  0.0  0.0      0     0 ?        S    02:23   0:00 [scsi_eh_0]
root        55  0.0  0.0      0     0 ?        S    02:23   0:00 [scsi_eh_1]
root        56  0.0  0.0      0     0 ?        S    02:23   0:00 [kstriped]
root        57  0.0  0.0      0     0 ?        S    02:23   0:00 [kmpathd/0]
root        58  0.0  0.0      0     0 ?        S    02:23   0:00 [kmpathd/1]
root        59  0.0  0.0      0     0 ?        S    02:23   0:00 [kmpath_handle]
root        60  0.0  0.0      0     0 ?        S    02:23   0:00 [ksnapd]
root        61  0.0  0.0      0     0 ?        S    02:23   0:00 [kondemand/0]
root        62  0.0  0.0      0     0 ?        S    02:23   0:00 [kondemand/1]
root        63  0.0  0.0      0     0 ?        S    02:23   0:00 [kconservative]
root        64  0.0  0.0      0     0 ?        S    02:23   0:00 [kconservative]
root       290  0.0  0.0      0     0 ?        S    02:23   0:00 [khpsbpkt]
root       291  0.0  0.0      0     0 ?        S    02:23   0:00 [knodemgrd_0]
root       300  0.0  0.0      0     0 ?        S    02:23   0:00 [jbd2/sda2-8]
root       301  0.0  0.0      0     0 ?        S    02:23   0:00 [ext4-dio-unwr]
root       302  0.0  0.0      0     0 ?        S    02:23   0:00 [ext4-dio-unwr]
root       323  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:0]
root       324  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:1]
root       325  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:2]
root       326  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:3]
root       327  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:4]
root       328  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:5]
root       329  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:6]
root       330  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:7]
root       331  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:8]
root       332  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:9]
root       333  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:10]
root       334  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:11]
root       335  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:12]
root       336  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:13]
root       337  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:14]
root       338  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-1:15]
root       339  0.0  0.0      0     0 ?        S    02:23   0:00 [flush-8:0]
root       365  0.0  0.0   2312   884 ?        S    02:23   0:00 upstart-udev-br
root       368  0.0  0.0   2632  1056 ?        S<s  02:23   0:00 udevd --daemon
root       610  0.0  0.0      0     0 ?        S    02:23   0:00 [kpsmoused]
root       650  0.0  0.0      0     0 ?        S    02:23   0:00 [bluetooth]
root       654  0.0  0.0      0     0 ?        S    02:23   0:00 [pccardd]
root       672  0.0  0.0      0     0 ?        S    02:23   0:00 [i915]
root       701  0.0  0.0      0     0 ?        S    02:23   0:00 [ktpacpid]
root       714  0.0  0.0      0     0 ?        S    02:23   0:00 [iwlagn]
root       719  0.0  0.0      0     0 ?        S    02:23   0:00 [phy0]
root       780  0.0  0.0   2796  1180 ?        Ss   02:23   0:00 /sbin/mount.ntf
root       790  0.0  0.0      0     0 ?        S    02:23   0:00 [hd-audio0]
root       792  0.0  0.0   2796  1140 ?        Ss   02:23   0:00 /sbin/mount.ntf
syslog     804  0.0  0.0  34676  1700 ?        Sl   02:23   0:00 rsyslogd -c4
102        814  0.1  0.0   3308  1632 ?        Ss   02:23   0:00 dbus-daemon --s
root       829  0.0  0.1  18748  3260 ?        Ssl  02:23   0:00 gdm-binary
root       833  0.0  0.2  18872  4064 ?        Ssl  02:23   0:00 NetworkManager
avahi      847  0.0  0.0   3060  1604 ?        S    02:23   0:00 avahi-daemon: r
root       848  0.0  0.1   4164  2336 ?        S    02:23   0:00 /usr/sbin/modem
avahi      851  0.0  0.0   2924   544 ?        Ss   02:23   0:00 avahi-daemon: c
root       863  0.0  0.1  19672  3252 ?        Sl   02:23   0:00 /usr/sbin/conso
root       946  0.0  0.0   2628  1028 ?        S<   02:23   0:00 udevd --daemon
root       948  0.0  0.1  20484  3600 ?        Sl   02:23   0:00 /usr/lib/gdm/gd
root       957  0.0  0.0   2628   948 ?        S<   02:23   0:00 udevd --daemon
root       987  0.0  0.0   1788   560 tty4     Ss+  02:23   0:00 /sbin/getty -8
root       993  0.0  0.0   1788   568 tty5     Ss+  02:23   0:00 /sbin/getty -8
root      1005  0.0  0.0   1788   568 tty2     Ss+  02:23   0:00 /sbin/getty -8
root      1007  0.0  0.0   1788   568 tty3     Ss+  02:23   0:00 /sbin/getty -8
root      1013  0.0  0.0   1788   564 tty6     Ss+  02:23   0:00 /sbin/getty -8
root      1017  0.0  0.0   2044   872 ?        Ss   02:23   0:00 acpid -c /etc/a
root      1046  0.0  0.0   2372   904 ?        Ss   02:23   0:00 cron
daemon    1047  0.0  0.0   2244   432 ?        Ss   02:23   0:00 atd
root      1126  0.0  0.1   4824  2368 ?        S    02:23   0:00 /sbin/wpa_suppl
root      1127  6.2  1.2  51200 25016 tty7     Ss+  02:23   0:09 /usr/bin/X :0 -
clamav    1135  0.0  0.0  12064  1404 ?        Ss   02:23   0:00 /usr/bin/freshc
root      1184  0.0  0.0  11732  1424 ?        Ss   02:23   0:00 /usr/sbin/winbi
root      1187  0.0  0.0  11732  1196 ?        S    02:23   0:00 /usr/sbin/winbi
root      1193  0.0  0.0   4048  1872 ?        S<s  02:23   0:00 /usr/sbin/bluet
root      1221  0.0  0.1   6692  2516 ?        Ss   02:23   0:00 /usr/sbin/cupsd
root      1224  0.0  0.0      0     0 ?        S<   02:23   0:00 [krfcommd]
root      1316  0.0  0.1  18964  3104 ?        Sl   02:23   0:00 /usr/lib/gdm/gd
root      1333  0.0  0.0   1788   568 tty1     Ss+  02:23   0:00 /sbin/getty -8
varun     1340  0.0  0.3  25900  6664 ?        Ssl  02:23   0:00 gnome-session
varun     1374  0.0  0.0   3280   356 ?        Ss   02:23   0:00 /usr/bin/ssh-ag
varun     1377  0.0  0.0   3380   772 ?        S    02:23   0:00 /usr/bin/dbus-l
varun     1378  0.0  0.0   3188  1324 ?        Ss   02:23   0:00 /bin/dbus-daemo
varun     1381  0.2  0.2   7544  4268 ?        S    02:23   0:00 /usr/lib/libgco
varun     1386  0.0  0.1  23952  2648 ?        SLl  02:23   0:00 gnome-keyring-d
varun     1388  0.1  0.4  89344  9520 ?        Ss   02:23   0:00 /usr/lib/gnome-
varun     1392  0.0  0.1   6348  2236 ?        S    02:23   0:00 /usr/lib/gvfs/g
varun     1397  0.0  0.1  30276  2636 ?        Ssl  02:23   0:00 /usr/lib/gvfs//
varun     1400  0.4  0.7  43480 14916 ?        S    02:23   0:00 gnome-panel
varun     1403  0.3  0.9  89732 18820 ?        S    02:23   0:00 nautilus
varun     1404  0.0  0.3  20008  7748 ?        S    02:23   0:00 gnome-power-man
varun     1408  0.3  0.5  54468 11996 ?        SL   02:23   0:00 nm-applet --sm-
varun     1409  0.7  0.9  55236 18960 ?        SNl  02:23   0:01 beagled /usr/li
varun     1412  0.1  0.2  94356  4676 ?        S<sl 02:23   0:00 /usr/bin/pulsea
varun     1413  0.0  0.4  36072  9692 ?        S    02:23   0:00 bluetooth-apple
varun     1416  0.0  0.2  18364  6040 ?        S    02:23   0:00 /usr/lib/policy
rtkit     1417  0.0  0.0  22904  1220 ?        SNl  02:23   0:00 /usr/lib/rtkit/
varun     1418  1.7  1.3  81808 26988 ?        R    02:23   0:02 /usr/bin/compiz
varun     1419  0.6  1.3  73788 27136 ?        Sl   02:23   0:01 beagle-search /
root      1428  0.0  0.1   5564  2924 ?        S    02:23   0:00 /usr/lib/upower
root      1430  0.1  0.1   6444  4012 ?        S    02:23   0:00 /usr/lib/policy
varun     1446  0.0  0.1   6796  2980 ?        S    02:23   0:00 /usr/lib/gvfs/g
varun     1455  0.0  0.1  41884  3472 ?        Ssl  02:23   0:00 /usr/lib/bonobo
varun     1502  0.0  0.5  40160 10920 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1503  0.0  0.1  40492  3480 ?        S    02:23   0:00 /usr/lib/gvfs/g
varun     1504  0.1  0.6  41696 12920 ?        S    02:23   0:00 /usr/lib/gnome-
root      1507  0.0  0.1  15648  3056 ?        Sl   02:23   0:00 /usr/lib/udisks
root      1508  0.0  0.0   5176   880 ?        S    02:23   0:00 udisks-daemon: 
varun     1509  0.0  0.1  10748  2996 ?        S    02:23   0:00 /usr/lib/pulsea
varun     1516  0.0  0.0   1828   508 ?        Ss   02:23   0:00 /bin/sh -c /usr
varun     1517  0.1  0.4  20480  9864 ?        S    02:23   0:00 /usr/bin/gtk-wi
varun     1521  0.0  0.0   3816  1076 ?        S    02:23   0:00 syndaemon -i 0.
varun     1523  0.0  0.1  16920  2320 ?        Sl   02:23   0:00 /usr/lib/gvfs/g
varun     1526  0.0  0.1   7124  2368 ?        S    02:23   0:00 /usr/lib/gvfs/g
varun     1536  0.1  0.5  24700 10736 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1537  0.1  0.5  24520 10624 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1538  0.0  0.6  32344 13712 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1540  0.0  0.4  23056  8832 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1561  0.0  0.0   6152  1936 ?        S    02:23   0:00 /usr/lib/gvfs/g
varun     1562  0.0  0.1   6376  2376 ?        S    02:23   0:00 /usr/lib/gvfs/g
108       1570  0.1  0.2  16792  4320 ?        Ssl  02:23   0:00 /usr/sbin/hald
root      1571  0.0  0.0   3528  1300 ?        S    02:23   0:00 hald-runner
root      1601  0.0  0.0   3604  1252 ?        S    02:23   0:00 hald-addon-inpu
root      1603  0.0  0.0   3604  1240 ?        S    02:23   0:00 /usr/lib/hal/ha
root      1604  0.0  0.0   3604  1248 ?        S    02:23   0:00 /usr/lib/hal/ha
root      1612  0.0  0.0   3600  1208 ?        S    02:23   0:00 /usr/lib/hal/ha
root      1614  0.0  0.0   3616  1236 ?        S    02:23   0:00 /usr/lib/hal/ha
108       1615  0.0  0.0   3416  1168 ?        S    02:23   0:00 hald-addon-acpi
root      1620  0.0  0.0   3608  1244 ?        S    02:23   0:00 hald-addon-stor
varun     1625  0.0  0.1  17772  2664 ?        Ss   02:23   0:00 gnome-screensav
root      1635  0.0  0.0   2228  1016 ?        S    02:23   0:00 /sbin/dhclient
varun     1647  0.1  0.5  37964 11572 ?        S    02:23   0:00 /usr/lib/notify
varun     1691  0.0  0.3  18868  7140 ?        S    02:23   0:00 /usr/lib/gnome-
varun     1695  0.0  0.0   1828   560 ?        S    02:24   0:00 /bin/sh /usr/li
varun     1700  0.0  0.0   1828   572 ?        S    02:24   0:00 /bin/sh /usr/li
varun     1704 12.3  4.3 324344 87952 ?        Sl   02:24   0:15 /usr/lib/firefo
varun     1764  0.6  1.0  95460 20664 ?        SLl  02:24   0:00 /usr/bin/python
varun     1766  0.4  0.5  16508 11612 ?        S    02:24   0:00 /usr/bin/python
varun     1767  0.0  0.5  34584 10952 ?        Sl   02:24   0:00 /usr/lib/evolut
varun     1768  0.1  0.7  31448 15144 ?        S    02:24   0:00 python /usr/sha
varun     1841  0.0  0.0   1828   588 ?        S    02:24   0:00 /bin/sh -e /usr
varun     1869  0.0  0.0   1828   364 ?        S    02:24   0:00 /bin/sh -e /usr
varun     1870  0.6  0.5  68748 11172 ?        Sl   02:24   0:00 /usr/lib/erlang
varun     1880  0.0  0.0   1616   448 ?        Ss   02:24   0:00 heart -pid 1870
varun     1883  0.2  0.5  16996 10492 ?        SN   02:24   0:00 /usr/bin/python
varun     1920  0.0  0.1  19368  3516 ?        Ssl  02:24   0:00 /usr/lib/couchd
varun     1952  0.1  0.5  38304 11856 ?        S    02:24   0:00 update-notifier
root      1956  0.1  0.3  13672  8044 ?        S    02:24   0:00 /usr/bin/python
root      1975  0.3  0.5  16408 11112 ?        S    02:24   0:00 /usr/bin/python
varun     1988  1.5  0.6  48220 13532 ?        Rl   02:25   0:00 gnome-terminal
varun     1989  0.0  0.0   1984   712 ?        S    02:25   0:00 gnome-pty-helpe
varun     1990  0.8  0.1   6056  3428 pts/0    Ss   02:25   0:00 bash
varun     2009  0.0  0.0   2712  1064 pts/0    R+   02:26   0:00 ps aux


```


thanks...

---

### Post by yarox on 2010-05-07
Hi alphageek89,

> i think i know what was wrong. When i rebooted i got an .ICEauthority error. I fixed that i know my cpu usage has gone down drastically.

I also have this same problem. How did you manage to fix your .ICEauthority error?

I've tried the solutions posted [here]("http://ubuntuforums.org/showthread.php?t=1460747&highlight=.ICEauthority+error") and [here]("http://ubuntuforums.org/showthread.php?t=1081730"), but none of them seem to work for me.

Thanks.

EDIT:
I managed to have it working so, never mind.

---

