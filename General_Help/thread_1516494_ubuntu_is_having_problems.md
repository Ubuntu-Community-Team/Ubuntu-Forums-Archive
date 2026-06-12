---
title: "ubuntu is having problems"
date: 2010-06-23
forum: General Help
---

### Post by boonenoob on 2010-06-23
so, i have been using Ubuntu 10.04 for a while now with no problems.
 
  but lately, it takes a long time for the desktop to show up after i login, and the computer is sometimes slow.

  also, when it starts up, it has problems loading the panel applets, some of them don't load.
      
  i have a firewall setup and it is working fine, along with a anti-virus. 

Could anyone help me or recommend a utility to fix my computer?

BTW, it works fine in GNOME failsafe mode

---

### Post by 3Miro on 2010-06-23
Antivirus program works for Windows viruses only, Ubuntu doesn't need AV software (however, if you have a combination of Linux and Windows machines, it makes sense to have it).

What you describe is probably due to a rogue process taking too much resources. When you see your computer is getting slow, open the system monitor (System -> Admin -> System Monitor) and check to see which process is taking too much CPU or too much memory. This will be the first step to figuring out the problem.

You can also open terminal (Apps -> Accessories -> Terminal) and type "top" to see the most CPU hungry processes.

---

### Post by mr clark25 on 2010-06-23
you might also post the output of "ps aux" when your computer starts getting slow.

---

### Post by boonenoob on 2010-06-23
> **mr clark25 said:**
> you might also post the output of "ps aux" when your computer starts getting slow.
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2780  1260 ?        Ss   17:42   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    17:42   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    17:42   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    17:42   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    17:42   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    17:42   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    17:42   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    17:42   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    17:42   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    17:42   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    17:42   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    17:42   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    17:42   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    17:42   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    17:42   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    17:42   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    17:42   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    17:42   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    17:42   0:00 [ata/0]
root        20  0.0  0.0      0     0 ?        S    17:42   0:00 [ata_aux]
root        21  0.0  0.0      0     0 ?        S    17:42   0:00 [ksuspend_usbd]
root        22  0.0  0.0      0     0 ?        S    17:42   0:00 [khubd]
root        23  0.0  0.0      0     0 ?        S    17:42   0:00 [kseriod]
root        24  0.0  0.0      0     0 ?        S    17:42   0:00 [kmmcd]
root        27  0.0  0.0      0     0 ?        S    17:42   0:00 [khungtaskd]
root        28  0.1  0.0      0     0 ?        D    17:42   0:00 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   17:42   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        S    17:42   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        S    17:42   0:00 [ecryptfs-kthr]
root        32  0.0  0.0      0     0 ?        S    17:42   0:00 [crypto/0]
root        39  0.0  0.0      0     0 ?        S    17:42   0:00 [kstriped]
root        40  0.0  0.0      0     0 ?        S    17:42   0:00 [kmpathd/0]
root        41  0.0  0.0      0     0 ?        S    17:42   0:00 [kmpath_handle]
root        42  0.0  0.0      0     0 ?        S    17:42   0:00 [ksnapd]
root        43  0.0  0.0      0     0 ?        S    17:42   0:00 [kondemand/0]
root        44  0.0  0.0      0     0 ?        S    17:42   0:00 [kconservative]
root       209  0.0  0.0      0     0 ?        S    17:42   0:00 [scsi_eh_0]
root       210  0.0  0.0      0     0 ?        S    17:42   0:00 [scsi_eh_1]
root       229  0.0  0.0      0     0 ?        S    17:42   0:00 [jbd2/sda1-8]
root       230  0.0  0.0      0     0 ?        S    17:42   0:00 [ext4-dio-unwr]
root       263  0.0  0.0      0     0 ?        S    17:42   0:00 [flush-8:0]
root       289  0.0  0.1   2312   588 ?        S    17:42   0:00 upstart-udev-br
root       293  0.0  0.0   2640   348 ?        S<s  17:42   0:00 udevd --daemon
root       434  0.0  0.0      0     0 ?        S    17:42   0:00 [ntos_wq]
root       435  0.0  0.0      0     0 ?        S    17:42   0:00 [ndis_wq]
root       436  0.0  0.0      0     0 ?        S    17:42   0:00 [wrapndis_wq]
root       540  0.0  0.0      0     0 ?        S    17:42   0:00 [kpsmoused]
root       570  0.0  0.0      0     0 ?        S    17:42   0:00 [phy0]
syslog     619  0.0  0.3  33784  1184 ?        Sl   17:42   0:00 rsyslogd -c4
root       624  0.0  0.0      0     0 ?        S    17:42   0:00 [radeon/0]
root       626  0.0  0.0      0     0 ?        S    17:42   0:00 [ttm_swap]
102        644  0.3  0.3   3328  1412 ?        Ss   17:42   0:01 dbus-daemon --s
root       661  0.0  0.6  18768  2532 ?        Ssl  17:42   0:00 gdm-binary
avahi      679  0.0  0.3   3060  1200 ?        S    17:42   0:00 avahi-daemon: r
avahi      682  0.0  0.0   2924   268 ?        Ss   17:42   0:00 avahi-daemon: c
root       808  0.0  0.5  19756  1972 ?        Sl   17:42   0:00 /usr/sbin/conso
root       809  0.0  0.5   9452  2092 ?        Ss   17:42   0:00 NetworkManager
root       811  0.0  0.4   4164  1588 ?        S    17:42   0:00 /usr/sbin/modem
root       889  0.0  0.2   4824   796 ?        S    17:42   0:00 /sbin/wpa_suppl
root       919  0.0  0.5  20492  2252 ?        Sl   17:42   0:00 /usr/lib/gdm/gd
root      1056  7.6  2.9  32088 11300 tty7     Rs+  17:42   0:31 /usr/bin/X :0 -
gdm       1257  0.0  0.1   3380   476 ?        S    17:42   0:00 /usr/bin/dbus-l
root      1276  0.0  0.1   1788   460 tty4     Ss+  17:42   0:00 /sbin/getty -8
root      1281  0.0  0.1   1788   464 tty5     Ss+  17:42   0:00 /sbin/getty -8
root      1297  0.0  0.1   1788   460 tty2     Ss+  17:42   0:00 /sbin/getty -8
root      1298  0.0  0.1   1788   460 tty3     Ss+  17:42   0:00 /sbin/getty -8
root      1300  0.0  0.1   1788   464 tty6     Ss+  17:42   0:00 /sbin/getty -8
root      1301  0.0  0.1   2044   492 ?        Ss   17:42   0:00 acpid -c /etc/a
daemon    1303  0.0  0.0   2244   280 ?        Ss   17:42   0:00 atd
root      1304  0.0  0.1   2372   736 ?        Ss   17:42   0:00 cron
Slmodemd  1308  0.0  2.2   8572  8576 ?        SL   17:42   0:00 /usr/sbin/slmod
120       1343  0.0  0.3  26168  1340 ?        Ss   17:42   0:00 /usr/sbin/mix -
root      1398  0.0  0.5  18968  1988 ?        Sl   17:42   0:00 /usr/lib/gdm/gd
root      1400  0.0  0.5   5552  1920 ?        S    17:42   0:00 /usr/lib/upower
rtkit     1406  0.0  0.2  22904   948 ?        SNl  17:43   0:00 /usr/lib/rtkit/
root      1410  0.0  0.6   6364  2480 ?        S    17:43   0:00 /usr/lib/policy
108       1449  0.0  0.5  16820  1968 ?        Ssl  17:43   0:00 /usr/sbin/hald
root      1450  0.0  0.2   3528   992 ?        S    17:43   0:00 hald-runner
root      1480  0.0  0.2   3604  1020 ?        S    17:43   0:00 hald-addon-inpu
root      1484  0.0  0.2   3604   932 ?        S    17:43   0:00 /usr/lib/hal/ha
root      1485  0.0  0.2   3604   932 ?        S    17:43   0:00 /usr/lib/hal/ha
root      1490  0.0  0.2   3600  1056 ?        S    17:43   0:00 /usr/lib/hal/ha
root      1495  0.0  0.2   3616   928 ?        S    17:43   0:00 /usr/lib/hal/ha
108       1496  0.0  0.2   3416   908 ?        S    17:43   0:00 hald-addon-acpi
root      1498  0.0  0.2   3608  1004 ?        S    17:43   0:00 hald-addon-stor
eric      1507  0.0  0.4  23980  1612 ?        Sl   17:43   0:00 /usr/bin/gnome-
eric      1525  0.0  1.3  25872  5264 ?        Ssl  17:43   0:00 gnome-session
eric      1559  0.0  0.0   3280   148 ?        Ss   17:43   0:00 /usr/bin/ssh-ag
eric      1562  0.0  0.1   3380   468 ?        S    17:43   0:00 /usr/bin/dbus-l
eric      1563  0.2  0.3   3320  1384 ?        Ss   17:43   0:00 /bin/dbus-daemo
root      1564  0.0  0.3  16540  1236 ?        S    17:43   0:00 /usr/lib/AntiVi
root      1565  0.1  0.2   2764   876 ?        S    17:43   0:00 /usr/lib/AntiVi
root      1566  0.0  0.1   2760   436 ?        S    17:43   0:00 /usr/lib/AntiVi
eric      1569  0.1  0.9   7648  3764 ?        S    17:43   0:00 /usr/lib/libgco
eric      1575  0.1  1.8  89148  6864 ?        Ss   17:43   0:00 /usr/lib/gnome-
root      1577  0.1  0.2   2764   884 ?        S    17:43   0:00 /usr/lib/AntiVi
root      1578  0.1  0.2   2764   884 ?        S    17:43   0:00 /usr/lib/AntiVi
eric      1580  0.0  0.4   6376  1884 ?        S    17:43   0:00 /usr/lib/gvfs/g
root      1581  0.0  0.1   2760   440 ?        S    17:43   0:00 /usr/lib/AntiVi
root      1583  0.0  0.1   2760   436 ?        S    17:43   0:00 /usr/lib/AntiVi
eric      1587  0.0  0.5  30276  2028 ?        Ssl  17:43   0:00 /usr/lib/gvfs//
eric      1591  1.6  2.5  68292  9616 ?        S    17:43   0:06 compiz
eric      1594  0.1  1.0  94272  4124 ?        S<sl 17:43   0:00 /usr/bin/pulsea
eric      1603  0.0  0.5  10748  2124 ?        S    17:43   0:00 /usr/lib/pulsea
eric      1604  0.2  3.2 118056 12188 ?        Sl   17:43   0:01 gnome-panel
eric      1605  1.6  3.5 174688 13488 ?        Sl   17:43   0:06 nautilus
eric      1606  0.0  1.4  19376  5488 ?        S    17:43   0:00 bluetooth-apple
eric      1607  0.1  3.1  34348 11804 ?        S    17:43   0:00 /usr/bin/python
eric      1608  0.0  1.1  18396  4196 ?        S    17:43   0:00 /usr/lib/policy
root      1611  0.0  0.1   2592   632 ?        S    17:43   0:00 /usr/lib/AntiVi
eric      1612  0.0  2.1  50768  7968 ?        S    17:43   0:00 nm-applet --sm-
eric      1614  0.0  1.5  20036  5692 ?        S    17:43   0:00 gnome-power-man
eric      1615  0.0  0.2   3816   908 ?        S    17:43   0:00 syndaemon -i 0.
eric      1618  0.0  0.6   7736  2392 ?        S    17:43   0:00 /usr/lib/gvfs/g
root      1619  5.0  3.5 125672 13380 ?        Sl   17:43   0:19 /usr/lib/AntiVi
root      1621  0.0  0.5  15628  2220 ?        Sl   17:43   0:00 /usr/lib/udisks
root      1623  0.0  0.1   5176   648 ?        S    17:43   0:00 udisks-daemon: 
eric      1625  0.0  0.4  16948  1644 ?        Sl   17:43   0:00 /usr/lib/gvfs/g
eric      1628  0.0  0.4   7124  1712 ?        S    17:43   0:00 /usr/lib/gvfs/g
eric      1629  0.7  6.3 158140 24056 ?        Ssl  17:43   0:02 /home/eric/.dro
eric      1634  0.0  0.6   6804  2348 ?        S    17:43   0:00 /usr/lib/gvfs/g
eric      1637  0.0  0.6  40940  2608 ?        Ssl  17:43   0:00 /usr/lib/bonobo
eric      1645  0.0  0.4  17820  1732 ?        Ss   17:43   0:00 gnome-screensav
eric      1648  0.0  0.1   1828   420 ?        Ss   17:43   0:00 /bin/sh -c /usr
eric      1649  0.0  2.2  96500  8360 ?        Sl   17:43   0:00 /usr/bin/gtk-wi
eric      1655  0.0  1.5  18904  5776 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1663  0.1  2.6  39804 10096 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1668  0.0  1.8  38172  6868 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1673  0.1  2.4 101192  9112 ?        Sl   17:43   0:00 /usr/lib/gnome-
eric      1681  0.0  1.6  23488  6184 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1689  0.0  0.2   4192  1020 ?        S    17:43   0:00 bash /usr/bin/t
eric      1690  0.0  2.5  48100  9824 ?        Sl   17:43   0:00 /usr/lib/indica
eric      1691  0.0  1.7  23104  6468 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1692  0.0  1.7  33764  6792 ?        S    17:43   0:00 /usr/lib/gnome-
eric      1693  0.0  2.2  47856  8440 ?        S    17:43   0:00 /usr/lib/indica
eric      1694  0.0  1.6  32432  6124 ?        Sl   17:43   0:00 /usr/lib/gnome-
eric      1695  0.0  2.0  32216  7900 ?        S    17:43   0:00 /usr/lib/gnome-
root      1722  0.4  0.1   3484   756 ?        S    17:43   0:01 /usr/lib/AntiVi
eric      1733  0.0  0.4   6376  1756 ?        S    17:43   0:00 /usr/lib/gvfs/g
eric      1734  0.4  2.6  61592 10140 ?        Sl   17:43   0:01 mono /usr/lib/t
eric      1802  0.0  0.8  24300  3188 ?        S    17:43   0:00 /usr/lib/indica
eric      1804  0.0  0.9  85072  3768 ?        S    17:43   0:00 /usr/lib/indica
root      1817  0.5  1.1  22360  4456 ?        S    17:43   0:02 /usr/bin/python
eric      1827  0.0  0.9  17520  3516 ?        S    17:43   0:00 /usr/lib/indica
eric      1853  0.0  2.9  31464 11016 ?        S    17:43   0:00 python /usr/sha
eric      1855  0.3  3.8  69888 14612 ?        SL   17:43   0:01 /usr/bin/python
eric      1857  0.0  1.8  67504  7108 ?        Sl   17:43   0:00 /usr/lib/evolut
root      1858  0.0  0.2  11732   896 ?        Ss   17:43   0:00 /usr/sbin/winbi
root      1877  0.0  0.1  11732   740 ?        S    17:43   0:00 /usr/sbin/winbi
root      1894  0.0  0.3   6696  1448 ?        Ss   17:43   0:00 /usr/sbin/cupsd
root      1896  0.1  1.4  12872  5396 ?        S    17:43   0:00 /usr/bin/python
eric      1904  0.3  2.3  16552  8944 ?        S    17:43   0:01 /usr/bin/python
root      1910  0.0  0.0   2636   360 ?        S<   17:43   0:00 udevd --daemon
root      1913  0.0  0.0   2636   276 ?        S<   17:43   0:00 udevd --daemon
eric      2032  0.0  1.3  79120  5092 ?        Sl   17:44   0:00 /usr/lib/evolut
root      2063  0.0  0.9  28900  3756 ?        Sl   17:44   0:00 /usr/bin/python
eric      2065  0.9  3.8  31780 14728 ?        Sl   17:44   0:03 /usr/bin/python
eric      2079  0.0  2.5  36384  9528 ?        S    17:44   0:00 update-notifier
eric      2088  0.0  1.8  35720  6956 ?        Sl   17:44   0:00 /usr/lib/evolut
eric      2145  0.0  1.0  17984  3944 ?        S    17:44   0:00 /usr/lib/indica
eric      2154  0.0  1.0  18868  3888 ?        S    17:44   0:00 /usr/lib/indica
timidity  2172  0.0  1.4  14532  5576 ?        S    17:44   0:00 /usr/bin/timidi
root      2180  0.0  0.1   1788   516 tty1     Ss+  17:44   0:00 /sbin/getty -8
root      2188  0.0  0.0      0     0 ?        S    17:44   0:00 [irq/21-b43]
root      2269  0.0  0.1   4828   652 ?        Ss   17:45   0:00 wpa_supplicant
root      2306  0.0  0.0      0     0 ?        Z    17:45   0:00 [dhc] <defunct>
root      2333  0.1  2.2  16408  8464 ?        S    17:45   0:00 /usr/bin/python
eric      2340  0.0  0.1   1828   456 ?        S    17:45   0:00 /bin/sh -e /usr
eric      2388  0.0  0.0   1828   248 ?        S    17:45   0:00 /bin/sh -e /usr
eric      2389  0.4  2.0  36012  7688 ?        S    17:45   0:01 /usr/lib/erlang
eric      2404  0.0  0.1   1616   436 ?        Ss   17:45   0:00 heart -pid 2389
root      2426  0.0  0.0   2228   228 ?        Ss   17:45   0:00 /sbin/dhclient
eric      2443  0.0  0.1   1828   448 ?        S    17:45   0:00 /bin/sh -e /usr
eric      2484 22.1  3.8 130380 14524 ?        Sl   17:45   0:57 gnome-system-mo
eric      2488  0.0  0.0   1828   256 ?        S    17:45   0:00 /bin/sh -e /usr
eric      2491  0.1  1.4  33012  5616 ?        S    17:45   0:00 /usr/lib/erlang
eric      2501  0.0  0.1   1616   428 ?        Ss   17:45   0:00 heart -pid 2491
eric      2543  0.0  1.4  17784  5552 ?        S    17:45   0:00 /usr/lib/notify
eric      2561  0.2  2.3  17040  8800 ?        SN   17:45   0:00 /usr/bin/python
eric      2579  0.0  0.4  19368  1792 ?        Ssl  17:45   0:00 /usr/lib/couchd
eric      2735  5.2  8.2 264084 31084 ?        Sl   17:48   0:03 /usr/lib/chromi
eric      2736  0.2  0.7  55556  2712 ?        S    17:48   0:00 /usr/lib/chromi
eric      2738  0.5  1.6  57912  6136 ?        S    17:48   0:00 /usr/lib/chromi
eric      2760  0.4  3.7 104112 14236 ?        Sl   17:48   0:00 /usr/lib/chromi
eric      2768  0.3  2.7 101704 10576 ?        Sl   17:48   0:00 /usr/lib/chromi
eric      2774  0.7  3.9 104828 15044 ?        Sl   17:48   0:00 /usr/lib/chromi
eric      2779  2.2  5.2 110336 19880 ?        Sl   17:48   0:01 /usr/lib/chromi
eric      2785  0.3  3.1 102008 12040 ?        Sl   17:48   0:00 /usr/lib/chromi
eric      2790  0.2  2.8 101840 10932 ?        Sl   17:48   0:00 /usr/lib/chromi
eric      2803  4.6  8.3 115972 31468 ?        Sl   17:48   0:02 /usr/lib/chromi
eric      2816  0.2  2.7  64508 10256 ?        Sl   17:49   0:00 /usr/lib/chromi
eric      2840  4.7  3.6 122408 13876 ?        Rl   17:49   0:00 gnome-terminal
eric      2850  0.0  0.1   1984   696 ?        S    17:49   0:00 gnome-pty-helpe
eric      2851  8.1  0.9   6396  3716 pts/1    Ss   17:49   0:00 bash
eric      2878  0.0  0.2   2712  1036 pts/1    R+   17:49   0:00 ps aux

---

### Post by boonenoob on 2010-06-23
also, java was at like 60-70 percent cpu at startup O_O

---

