---
title: "ubuntu 10.04 64bit slow as a turtle why? 2gb ram amd x2"
date: 2010-08-13
forum: General Help
---

### Post by gabak on 2010-08-13
i have a pc i built amd x2 2gb ram pci-e gf 8500.
that the pc is nt that bad but it remind me at windows time when i was getting slower with time , i got just 2 users one for my wife other for me.
and system monitor tell me i m using 95% of my memory and i using a lot of swaping so the hdd keep on for serveral minutes my netbook with ubuntu 10.04 64 bit is faster than this pc and i got just a asus 1201t amd single procesor and 1gb ram.
I passed janitor also i remover thing from startup application so it will load the minimun but it is still same problem.

vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping	: 1
cpu MHz		: 1800.000
cache size	: 512 KB



free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1988         20          0         10        178
-/+ buffers/cache:       1799        209
Swap:         3151        782       2369
gabe@gabe-desktop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23808  1532 ?        Ss   Aug12   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug12   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug12   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    Aug12   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    Aug12   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    Aug12   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    Aug12   0:03 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    Aug12   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    Aug12   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        R    Aug12   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    Aug12   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    Aug12   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    Aug12   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    Aug12   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    Aug12   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    Aug12   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    Aug12   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    Aug12   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    Aug12   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    Aug12   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    Aug12   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    Aug12   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    Aug12   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    Aug12   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    Aug12   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    Aug12   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    Aug12   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    Aug12   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    Aug12   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    Aug12   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    Aug12   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    Aug12   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    Aug12   0:08 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   Aug12   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    Aug12   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    Aug12   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    Aug12   0:00 [ecryptfs-kthr]
root        41  0.0  0.0      0     0 ?        S    Aug12   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    Aug12   0:00 [crypto/1]
root        55  0.0  0.0      0     0 ?        S    Aug12   0:00 [kstriped]
root        56  0.0  0.0      0     0 ?        S    Aug12   0:00 [kmpathd/0]
root        57  0.0  0.0      0     0 ?        S    Aug12   0:00 [kmpathd/1]
root        58  0.0  0.0      0     0 ?        S    Aug12   0:00 [kmpath_handle]
root        59  0.0  0.0      0     0 ?        S    Aug12   0:00 [ksnapd]
root        60  0.0  0.0      0     0 ?        S    Aug12   0:00 [kondemand/0]
root        61  0.0  0.0      0     0 ?        S    Aug12   0:00 [kondemand/1]
root        62  0.0  0.0      0     0 ?        S    Aug12   0:00 [kconservative]
root        63  0.0  0.0      0     0 ?        S    Aug12   0:00 [kconservative]
root       254  0.0  0.0      0     0 ?        S    Aug12   0:00 [scsi_eh_0]
root       259  0.0  0.0      0     0 ?        S    Aug12   0:00 [scsi_eh_1]
root       262  0.0  0.0      0     0 ?        S    Aug12   0:00 [scsi_eh_2]
root       263  0.0  0.0      0     0 ?        S    Aug12   0:00 [scsi_eh_3]
root       264  0.0  0.0      0     0 ?        S    Aug12   0:01 [scsi_eh_4]
root       265  0.0  0.0      0     0 ?        S    Aug12   0:02 [scsi_eh_5]
root       276  0.0  0.0      0     0 ?        S    Aug12   0:00 [usbhid_resume]
root       299  0.0  0.0      0     0 ?        S    Aug12   0:02 [jbd2/sda1-8]
root       300  0.0  0.0      0     0 ?        S    Aug12   0:00 [ext4-dio-unwr]
root       301  0.0  0.0      0     0 ?        S    Aug12   0:00 [ext4-dio-unwr]
root       344  0.0  0.0  17032   652 ?        S    Aug12   0:00 upstart-udev-br
root       348  0.0  0.0  17124   360 ?        S<s  Aug12   0:00 udevd --daemon
root       606  0.0  0.0      0     0 ?        S    Aug12   0:01 [flush-8:0]
root       613  0.0  0.0      0     0 ?        S    Aug12   0:00 [edac-poller]
root       689  0.0  0.0  94264   852 ?        Ss   Aug12   0:00 smbd -F
syslog     718  0.0  0.0 125972  1084 ?        Sl   Aug12   0:00 rsyslogd -c4
root       733  0.0  0.0      0     0 ?        S    Aug12   0:00 [hd-audio0]
102        797  0.0  0.0  24976  1976 ?        Ss   Aug12   0:03 dbus-daemon --s
root       805  0.0  0.1  76596  2096 ?        Ssl  Aug12   0:00 gdm-binary
avahi      811  0.0  0.0  34056  1088 ?        S    Aug12   0:00 avahi-daemon: r
avahi      812  0.0  0.0  33924   192 ?        Ss   Aug12   0:00 avahi-daemon: c
root       813  0.0  0.0  94264   196 ?        S    Aug12   0:00 smbd -F
root       827  0.0  0.0  87564  1924 ?        Ssl  Aug12   0:00 NetworkManager
root       830  0.0  0.0  57864  1400 ?        S    Aug12   0:00 /usr/sbin/modem
root       836  0.0  0.1 122668  2228 ?        Sl   Aug12   0:00 /usr/sbin/conso
root       904  0.0  0.0  28348   648 ?        S    Aug12   0:00 /sbin/wpa_suppl
root       905  0.0  0.0   6552   496 ?        S    Aug12   0:00 /sbin/dhclient
root       908  0.0  0.0  93460  1400 ?        Sl   Aug12   0:00 /usr/lib/gdm/gd
root       956  0.0  0.0   6076   400 tty4     Ss+  Aug12   0:00 /sbin/getty -8
root       960  0.0  0.0   6076   400 tty5     Ss+  Aug12   0:00 /sbin/getty -8
root       970  0.0  0.0   6076   400 tty2     Ss+  Aug12   0:00 /sbin/getty -8
root       971  0.0  0.0   6076   400 tty3     Ss+  Aug12   0:00 /sbin/getty -8
root       973  0.0  0.0   6076   400 tty6     Ss+  Aug12   0:00 /sbin/getty -8
root       977  0.0  0.0   4424   616 ?        Ss   Aug12   0:00 acpid -c /etc/a
daemon     982  0.0  0.0  18880   272 ?        Ss   Aug12   0:00 atd
root       983  0.0  0.0  21072   596 ?        Ss   Aug12   0:00 cron
root       985  0.0  0.0      0     0 ?        S    Aug12   0:00 [kvm-irqfd-cle]
root       991 53.2  3.7 213964 77876 tty7     Rs+  Aug12 347:57 /usr/bin/X :0 -
root      1086  0.0  0.0  11280   492 ?        Ss   Aug12   0:25 /usr/sbin/irqba
root      1096  0.0  0.0 217264  1056 ?        Sl   Aug12   0:00 /usr/sbin/libvi
clamav    1146  0.0  0.0  46976  1376 ?        Ss   Aug12   0:01 /usr/bin/freshc
nobody    1228  0.0  0.0  21424   532 ?        S    Aug12   0:00 dnsmasq --stric
root      1232  0.0  0.0   5332   352 ?        S    Aug12   0:00 /usr/sbin/hddte
root      1332  0.0  0.0 107740  1324 ?        Sl   Aug12   0:00 /usr/lib/gdm/gd
root      1362  0.0  0.0  37196   780 ?        Ss   Aug12   0:00 /usr/lib/postfi
postfix   1401  0.0  0.0  39420   768 ?        S    Aug12   0:00 qmgr -l -t fifo
root      1430  0.0  0.0  60576   860 ?        Ss   Aug12   0:00 nmbd -D
root      1436  0.0  0.0  65788   692 ?        Ss   Aug12   0:00 /usr/sbin/winbi
gabe      1444  0.0  0.1 167324  3152 ?        Ssl  Aug12   0:00 gnome-session
root      1462  0.0  0.0  65892   612 ?        S    Aug12   0:00 /usr/sbin/winbi
root      1467  0.0  0.0  75388  1492 ?        Ss   Aug12   0:00 /usr/sbin/cupsd
gabe      1554  0.0  0.0  11932   112 ?        Ss   Aug12   0:00 /usr/bin/ssh-ag
gabe      1558  0.0  0.0  26256   376 ?        S    Aug12   0:00 /usr/bin/dbus-l
gabe      1583  0.0  0.0  24472  1716 ?        Ss   Aug12   0:01 /bin/dbus-daemo
root      1608  0.0  0.0   6076   400 tty1     Ss+  Aug12   0:00 /sbin/getty -8
gabe      1610  0.0  0.1  46764  3336 ?        S    Aug12   0:06 /usr/lib/libgco
gabe      1616  0.0  0.3 412300  7180 ?        Ssl  Aug12   0:12 /usr/lib/gnome-
gabe      1617  0.0  0.0  69760  2012 ?        SLl  Aug12   0:00 /usr/bin/gnome-
gabe      1621  0.0  0.0  47992  1460 ?        S    Aug12   0:00 /usr/lib/gvfs/g
gabe      1625  3.8  1.5 300276 32724 ?        S    Aug12  25:00 compiz
gabe      1630  0.0  0.0  86360  1444 ?        Ssl  Aug12   0:06 /usr/lib/gvfs//
gabe      1635  1.2  0.2 344572  4944 ?        S<sl Aug12   7:52 /usr/bin/pulsea
rtkit     1637  0.0  0.0  43636   892 ?        SNl  Aug12   0:00 /usr/lib/rtkit/
root      1641  0.0  0.1  59952  2548 ?        S    Aug12   0:00 /usr/lib/policy
gabe      1649  0.0  0.5 464332 11416 ?        Sl   Aug12   0:17 gnome-panel
gabe      1651  0.0  0.2 314256  5064 ?        Sl   Aug12   0:01 /usr/lib/policy
gabe      1652  1.4  0.2 202308  4972 ?        Sl   Aug12   9:46 avant-window-na
gabe      1655  0.0  0.2 242544  4732 ?        S    Aug12   0:00 nm-applet --sm-
gabe      1662  0.0  0.0  96648  1292 ?        S    Aug12   0:00 /usr/lib/pulsea
gabe      1671  0.0  0.1 136812  2436 ?        S    Aug12   0:00 /usr/lib/gnome-
gabe      1673  0.0  0.1  63828  2144 ?        S    Aug12   0:00 /usr/lib/gvfs/g
root      1675  0.0  0.1  57336  2324 ?        Sl   Aug12   0:01 /usr/lib/udisks
root      1676  0.0  0.0  46692   524 ?        S    Aug12   0:00 udisks-daemon: 
gabe      1678  0.0  0.0 153140  2056 ?        Ssl  Aug12   0:00 /usr/lib/bonobo
gabe      1680  0.0  0.0  55244  1260 ?        S    Aug12   0:00 /usr/lib/gvfs/g
gabe      1683  0.0  0.0 134748  1236 ?        Sl   Aug12   0:01 /usr/lib/gvfs/g
gabe      1685  0.0  0.2 178552  5104 ?        Ss   Aug12   0:06 gnome-screensav
gabe      1696  0.2  0.4 358396  9176 ?        Sl   Aug12   1:26 /usr/lib/gnome-
gabe      1697  0.0  0.2 243332  4244 ?        S    Aug12   0:00 /usr/lib/gnome-
gabe      1699  0.0  0.0  52484  1584 ?        S    Aug12   0:00 /usr/lib/gvfs/g
gabe      1707  0.5  0.3 358264  6480 ?        Sl   Aug12   3:52 /usr/lib/gnome-
gabe      1708  0.0  0.3 430728  7544 ?        Sl   Aug12   0:01 /usr/lib/indica
gabe      1712  0.0  0.2 441060  5848 ?        Sl   Aug12   0:01 /usr/lib/indica
gabe      1713  0.0  0.1 208200  3360 ?        S    Aug12   0:00 /usr/lib/gnome-
gabe      1717  0.0  0.1 176528  2992 ?        S    Aug12   0:00 /usr/lib/gnome-
gabe      1718  0.0  0.2 338804  5796 ?        Sl   Aug12   0:03 awn-applet -p /
gabe      1727  2.2  0.4 361184  8572 ?        Sl   Aug12  14:23 awn-applet -p /
gabe      1730  0.0  0.0   4092   324 ?        Ss   Aug12   0:00 /bin/sh -c /usr
gabe      1731  0.0  0.2 272860  5772 ?        Sl   Aug12   0:04 /usr/bin/gtk-wi
root      1735  0.0  0.0  53576  1624 ?        S    Aug12   0:00 /usr/lib/upower
gabe      1773  0.0  0.0  41620  1296 ?        S    Aug12   0:00 /usr/lib/gvfs/g
gabe      1782  0.0  0.0 146888  2024 ?        S    Aug12   0:00 /usr/lib/indica
gabe      1784  0.0  0.0 138104  1724 ?        S    Aug12   0:00 /usr/lib/indica
gabe      1785  0.0  0.0 219016  2032 ?        S    Aug12   0:00 /usr/lib/indica
gabe      1788  0.0  0.1 140916  2264 ?        S    Aug12   0:00 /usr/lib/indica
gabe      1790  0.0  0.0 143972  2036 ?        S    Aug12   0:00 /usr/lib/indica
gabe      1795  0.0  0.0  47860  1220 ?        S    Aug12   0:00 /usr/lib/gvfs/g
root      1808  0.0  0.0  72200   736 ?        S    Aug12   0:00 /usr/sbin/winbi
gabe      1809  0.0  0.4 394844  9928 ?        SLl  Aug12   0:12 /usr/bin/python
gabe      1810  0.0  0.1 228884  3660 ?        S    Aug12   0:00 python /usr/sha
gabe      1812  0.2  0.1  98540  2988 ?        S    Aug12   1:34 /usr/bin/python
gabe      1813  0.0  0.1 430020  3140 ?        Sl   Aug12   0:00 /usr/lib/evolut
gabe      1822  0.0  0.1 353388  2840 ?        Sl   Aug12   0:00 /usr/lib/evolut
gabe      1846  0.0  0.1 399184  2372 ?        Sl   Aug12   0:00 /usr/lib/evolut
gabe      1917  0.0  0.0   4092   340 ?        S    Aug12   0:00 /bin/sh -e /usr
gabe      1945  0.0  0.0   4092   144 ?        S    Aug12   0:00 /bin/sh -e /usr
gabe      1946  0.1  0.6 180772 12812 ?        Sl   Aug12   0:51 /usr/lib/erlang
gabe      1956  0.0  0.0   3860   348 ?        Ss   Aug12   0:00 heart -pid 1946
gabe      1959  0.2  0.3 101348  7152 ?        SN   Aug12   1:22 /usr/bin/python
gabe      2001  0.0  0.0 148760  1908 ?        Ssl  Aug12   0:00 /usr/lib/couchd
gabe      2002  0.0  0.0 148760  1916 ?        Ssl  Aug12   0:00 /usr/lib/couchd
gabe      2056  0.0  0.2 208236  4724 ?        S    Aug12   0:03 update-notifier
gabe      2061  0.0  0.0   4092   340 ?        S    Aug12   0:00 /bin/sh /usr/li
gabe      2066  0.0  0.0   4092   340 ?        S    Aug12   0:00 /bin/sh /usr/li
gabe      2070  8.1  9.8 1063892 202480 ?      Sl   Aug12  53:10 /usr/lib/firefo
gabe      2221  0.0  0.8 934188 17056 ?        Sl   Aug12   0:34 nautilus
gabe      2248  1.0  0.7 700220 16444 ?        Sl   Aug12   7:02 /usr/bin/python
gabe      2394  0.0  0.0  94152  1564 ?        S    Aug12   0:00 /usr/lib/gvfs/g
108       2742  0.0  0.0  46868  1944 ?        Ssl  Aug12   0:00 /usr/sbin/hald
root      2743  0.0  0.0  22316   816 ?        S    Aug12   0:00 hald-runner
root      2766  0.0  0.0  24436   828 ?        S    Aug12   0:00 hald-addon-inpu
root      2780  0.0  0.0  24432   812 ?        S    Aug12   0:03 hald-addon-stor
root      2781  0.0  0.0  24432   808 ?        S    Aug12   0:01 hald-addon-stor
root      2782  0.0  0.0  24444   724 ?        S    Aug12   0:00 /usr/lib/hal/ha
108       2783  0.0  0.0  26268   700 ?        S    Aug12   0:00 hald-addon-acpi
gabe      3109  1.6  2.1 745136 44296 ?        Sl   Aug12   9:54 /usr/lib/chromi
gabe      3137  0.0  0.0 187412   932 ?        S    Aug12   0:02 /usr/lib/chromi
gabe      3143  0.0  0.0 201040  1452 ?        S    Aug12   0:00 /usr/lib/chromi
gabe      3253  0.0  0.2 877528  5968 ?        Sl   Aug12   0:04 /usr/lib/chromi
root      5841  0.0  0.0  17120   340 ?        S<   Aug12   0:00 udevd --daemon
root      5842  0.0  0.0  17120   296 ?        S<   Aug12   0:00 udevd --daemon
root      6096  0.0  0.0  65788   252 ?        S    Aug12   0:00 /usr/sbin/winbi
gabe      6242  0.0  0.7 313868 14492 ?        Sl   Aug12   0:02 gnome-terminal
gabe      6244  0.0  0.0  14484   600 ?        S    Aug12   0:00 gnome-pty-helpe
gabe      6245  0.0  0.0  21304  1044 pts/0    Ss+  Aug12   0:00 bash
gabe      7204  2.2  1.3 954992 28408 ?        Sl   Aug12  12:37 /usr/lib/chromi
gabe      7278  0.0  0.3 374352  7812 ?        Sl   Aug12   0:02 gedit
gabe      7307  0.0  0.0      0     0 ?        Z    Aug12   0:00 [deb] <defunct>
gabe      7670  0.0  0.7 879256 14436 ?        Sl   00:07   0:28 /usr/lib/chromi
gabe      7869  0.1  2.0 886372 41964 ?        Sl   00:16   0:42 /usr/lib/chromi
gabe      7928  0.3  3.2 909216 66288 ?        Sl   00:28   1:42 /usr/lib/chromi
gabe      7935  2.6  0.3 300636  6452 ?        Sl   00:28  13:38 /usr/lib/chromi
gabe      8199  1.5  0.9 543032 18740 ?        Sl   00:47   7:32 transmission /h
gabe      8283  0.0  0.3 172648  6492 ?        S    00:51   0:01 /usr/lib/notify
gabe      8475  0.0  0.3 306584  7740 ?        S    01:00   0:02 /usr/lib/gnome-
gabe      8501 21.8  3.7 896792 77488 ?        Sl   01:06 104:49 /usr/lib/firefo
root      9732  0.0  0.1  93492  2096 ?        Sl   05:57   0:00 /usr/lib/gdm/gd
root      9735  6.7  3.5 177688 72524 tty8     Ss+  05:57  12:40 /usr/bin/X :1 -
gdm       9757  0.0  0.0  26256   540 ?        S    05:57   0:00 /usr/bin/dbus-l
root      9776  0.0  0.0 109804  1932 ?        Sl   05:57   0:00 /usr/lib/gdm/gd
angie     9790  0.0  0.1  69632  2312 ?        SLl  05:57   0:00 /usr/bin/gnome-
angie     9810  0.0  0.2 167332  4116 ?        Ssl  05:57   0:00 gnome-session
angie     9846  0.0  0.0  11932   272 ?        Ss   05:57   0:00 /usr/bin/ssh-ag
angie     9849  0.0  0.0  26256   548 ?        S    05:57   0:00 /usr/bin/dbus-l
angie     9850  0.0  0.0  24084  1452 ?        Ss   05:57   0:00 /bin/dbus-daemo
angie     9853  0.0  0.2  46600  4596 ?        S    05:57   0:08 /usr/lib/libgco
angie     9859  0.0  0.2 309784  5320 ?        Ss   05:57   0:00 /usr/lib/gnome-
angie     9862  0.0  0.0  47992  1664 ?        S    05:57   0:00 /usr/lib/gvfs/g
angie     9867  0.0  0.0  78028  1664 ?        Ssl  05:57   0:00 /usr/lib/gvfs//
angie     9873  0.0  0.2 176060  4460 ?        S    05:57   0:00 gnome-power-man
angie     9874  0.0  0.2 169164  4132 ?        S    05:57   0:00 bluetooth-apple
angie     9876  3.2  0.1 278720  3592 ?        S<sl 05:57   6:02 /usr/bin/pulsea
angie     9881  0.0  0.4 261600  9172 ?        S    05:57   0:01 gnome-panel
angie     9885  0.0  6.5 738040 135044 ?       S    05:57   0:05 nautilus
angie     9886  1.0  2.2 265620 46052 ?        S    05:57   2:02 /usr/bin/compiz
angie     9888  0.0  0.1 161880  3572 ?        S    05:57   0:00 /usr/lib/policy
angie     9902  0.0  0.0  96648  1844 ?        S    05:57   0:00 /usr/lib/pulsea
angie     9908  0.0  0.0  52348  1724 ?        S    05:57   0:00 /usr/lib/gvfs/g
angie     9910  0.0  0.1  63768  2324 ?        S    05:57   0:00 /usr/lib/gvfs/g
angie     9913  0.0  0.1 152788  2184 ?        Ssl  05:57   0:00 /usr/lib/bonobo
angie     9915  0.0  0.0  55260  1564 ?        S    05:57   0:00 /usr/lib/gvfs/g
angie     9916  0.0  0.2 171660  5836 ?        Ss   05:57   0:00 gnome-screensav
angie     9919  0.0  0.0  69212  1536 ?        Sl   05:57   0:00 /usr/lib/gvfs/g
angie     9930  0.0  0.3 259100  7816 ?        S    05:57   0:00 /usr/lib/gnome-
angie     9931  0.0  0.2 243352  6004 ?        S    05:57   0:00 /usr/lib/gnome-
angie     9932  0.0  0.0   4092   408 ?        Ss   05:57   0:00 /bin/sh -c /usr
angie     9933  0.0  0.3 176684  6356 ?        S    05:57   0:00 /usr/bin/gtk-wi
angie     9945  0.3  0.2 220776  4612 ?        S    05:57   0:35 /usr/lib/gnome-
angie     9947  0.0  0.4 271484  9396 ?        S    05:57   0:00 /usr/lib/indica
angie     9948  0.0  0.3 273184  6608 ?        S    05:57   0:00 /usr/lib/indica
angie     9949  0.0  0.3 306500  6556 ?        S    05:57   0:00 /usr/lib/gnome-
angie     9950  0.0  0.2 208232  4476 ?        S    05:57   0:00 /usr/lib/gnome-
angie     9952  0.0  0.2 176640  4140 ?        S    05:57   0:00 /usr/lib/gnome-
angie     9955  0.0  0.0  41648  1452 ?        S    05:57   0:00 /usr/lib/gvfs/g
angie     9957  0.0  0.1 146888  2320 ?        S    05:57   0:00 /usr/lib/indica
angie     9959  0.0  0.1 219032  2552 ?        S    05:57   0:00 /usr/lib/indica
angie     9964  0.0  0.1 140864  3116 ?        S    05:57   0:00 /usr/lib/indica
angie     9967  0.0  0.1 138076  2368 ?        S    05:57   0:00 /usr/lib/indica
angie     9975  0.0  0.1 143984  2736 ?        S    05:57   0:00 /usr/lib/indica
angie     9988  0.0  0.0  47992  1536 ?        S    05:58   0:00 /usr/lib/gvfs/g
angie     9995  0.0  0.2 331604  4636 ?        Sl   05:58   0:00 /usr/lib/evolut
angie     9996  0.0  0.5 228900 10888 ?        S    05:58   0:00 python /usr/sha
angie    10007  0.0  0.0   4092   428 ?        S    05:58   0:00 /bin/sh /usr/li
angie    10012  0.0  0.0   4092   424 ?        S    05:58   0:00 /bin/sh /usr/li
angie    10016  4.4  8.2 783480 169980 ?       Sl   05:58   8:25 /usr/lib/firefo
angie    10041  0.0  0.3 208100  6772 ?        S    05:58   0:00 update-notifier
angie    10047 19.7 15.4 1010656 317228 ?      Sl   05:58  36:52 /usr/lib/firefo
angie    10353  0.0  0.2 165372  4212 ?        S    06:58   0:00 /usr/lib/notify
postfix  10831  0.0  0.1  39260  2104 ?        S    08:12   0:00 pickup -l -t fi
gabe     11017  2.3  1.8 2671724 37208 ?       Sl   09:04   0:01 C:\Program File
gabe     11020  1.1  0.2   8716  6044 ?        Ss   09:04   0:00 /usr/bin/winese
gabe     11024  0.0  0.1 2642524 2532 ?        Sl   09:04   0:00 C:\windows\syst
gabe     11026  0.1  0.1 2643088 2852 ?        Sl   09:04   0:00 C:\windows\syst
gabe     11035  0.2  0.3 2652556 6600 ?        Ss   09:04   0:00 C:\windows\syst
root     11038  1.1  0.7  95684 15652 ?        S    09:05   0:00 /usr/bin/python
gabe     11047  0.9  0.1  21356  4092 pts/1    Ss   09:05   0:00 bash


top

top - 09:20:16 up 11:08,  4 users,  load average: 2.32, 2.23, 2.26
Tasks: 252 total,   3 running, 249 sleeping,   0 stopped,   0 zombie
Cpu(s): 60.5%us,  7.8%sy,  0.0%ni, 30.9%id,  0.5%wa,  0.3%hi,  0.1%si,  0.0%st
Mem:   2057508k total,  2009924k used,    47584k free,    12320k buffers
Swap:  3227640k total,   757248k used,  2470392k free,   172448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
  991 root      20   0  281m  79m  22m R   73  4.0 358:23.87 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-uKin3e/database -nolisten tcp vt7    
 8501 gabe      20   0  875m  73m 7724 S   22  3.7 108:07.98 /usr/lib/firefox-3.6.8/plugin-container /usr/lib/mozilla/plugins/libflashplayer.so 2070 plugin  
10047 angie     20   0 1030m 339m  10m S   16 16.9  39:01.88 /usr/lib/firefox-3.6.8/plugin-container /usr/lib/mozilla/plugins/libflashplayer.so 10016 plugin 
 2070 gabe      20   0 1039m 209m  15m R    9 10.4  54:40.26 /usr/lib/firefox-3.6.8/firefox-bin                                                              
 1625 gabe      20   0  312m  33m  25m S    5  1.7  25:46.61 compiz                                                                                          
 1635 gabe       9 -11  336m 5192 3568 S    4  0.3   8:13.33 /usr/bin/pulseaudio --start --log-target=syslog                                                 
 1727 gabe      20   0  352m 8712 5160 S    3  0.4  14:47.53 awn-applet -p /usr/share/avant-window-navigator/applets/taskmanager.desktop -u 3 -w 23068716 -i 
 1652 gabe      20   0  197m 4980 3304 S    2  0.2  10:02.44 avant-window-navigator --startup                                                                
10016 angie     20   0  765m 165m  13m S    2  8.2   8:49.27 /usr/lib/firefox-3.6.8/firefox-bin                                                              
 6242 gabe      20   0  306m  15m 7884 S    1  0.8   0:05.41 gnome-terminal                                                                                  
 8199 gabe      20   0  530m  18m 5736 S    1  0.9   7:43.86 transmission /home/gabe/Downloads/WYSIWYG.Web.Builder.v7.1-Lz0.5758009.TPB.torrent              
 1812 gabe      20   0 98540 2976 1644 S    0  0.1   1:36.41 /usr/bin/python /usr/lib/desktopcouch/desktopcouch-service                                      
 9735 root      20   0  173m  69m 8096 S    0  3.5  12:43.67 /usr/bin/X :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-akRdBs/database -nolisten tcp        
 9945 angie     20   0  215m 4496 2756 S    0  0.2   0:38.36 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factor
 1430 root      20   0 60604 1044  820 S    0  0.1   0:00.20 nmbd -D                                                                                         
 1707 gabe      20   0  349m 6424 3980 S    0  0.3   3:57.02 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factor
 1696 gabe      20   0  349m 9512 6088 S    0  0.5   1:28.67 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
 3109 gabe      20   0  727m  42m 9468 S    0  2.1   9:55.10 /usr/lib/chromium-browser/chromium-browser                                                      
11017 gabe      20   0 2609m  35m  19m S    0  1.8   0:02.82 C:\Program Files\RealVNC\VNC4\vncviewer.exe                                                     
11226 gabe      20   0 19352 1504 1032 R    0  0.1   0:00.12 top                                                                                             
    1 root      20   0 23808 1448  864 S    0  0.1   0:00.84 /sbin/init                                                                                      
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 [kthreadd]                                                                                      
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 [migration/0]                                                                                   
    4 root      20   0     0    0    0 S    0  0.0   0:00.47 [ksoftirqd/0]                                                                                   
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/0]                                                                                    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.02 [migration/1]                                                                                   
    7 root      20   0     0    0    0 S    0  0.0   0:03.44 [ksoftirqd/1]                                                                                   
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 [watchdog/1]                                                                                    
    9 root      20   0     0    0    0 S    0  0.0   0:00.11 [events/0]                                                                                      
   10 root      20   0     0    0    0 S    0  0.0   0:00.21 [events/1]                                                                                      
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 [cpuset]                                                                                        
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 [khelper]                                                                                       
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 [netns]                                                                                         
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 [async/mgr]                                                                                     
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 [pm]                                                                                            
   17 root      20   0     0    0    0 S    0  0.0   0:00.01 [sync_supers]                                                                                   
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 [bdi-default]                                                                                   
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 [kintegrityd/0]                                                                                 
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 [kintegrityd/1]                                                                                 
   21 root      20   0     0    0    0 S    0  0.0   0:00.03 [kblockd/0]                                                                                     
   22 root      20   0     0    0    0 S    0  0.0   0:00.38 [kblockd/1]                                                                                     
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 [kacpid]                                                                                        
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 [kacpi_notify]                                                                                  
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 [kacpi_hotplug]                                                                                 
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 [ata/0]                                                                                         
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 [ata/1]                                                                                         
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 [ata_aux]

---

