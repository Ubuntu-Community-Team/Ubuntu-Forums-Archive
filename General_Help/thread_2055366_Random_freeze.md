---
title: "Random freeze"
date: 2012-09-09
forum: General Help
---

### Post by TrueAncalagon on 2012-09-09
Hi, I'm here to ask you some advice and help, because I can't figure what is happening to my system. This problem live with me for ubuntu 10.04 I think, and I haven't found a solution. Now I've come to the limit and I can't support this situation.

I discussed with the italian forum but... nothing. So I will report all the logs, all the ideas and hope that someone will figure out what the hell may I do to solve.

First of all, my pc:
motheboard MSI P43-NEO3, Intel QuadCore 9550, 4GB RAM Kingstone Hyper-V, nVidia GTX570 Amp!, HDD WD RAPTOR 10'000rpm 150GB + Samsung 600GB 7200rpm. 

OS: Ubuntu 12.04 64bit + Windows Seven ultimate

The problem: when I'm not working, I'm a gamer and I reboot my pc in windows. There, I don't get any problem that you will read about. I have stressed and tested my cpu, gpu and hdd, but nothing happened under windows. Under linux, there is another story. The only thing that I can say is "the system fall in freeze". This mean that gnome3 start to "lag", to "slow down" and after those "first signs", let's say after 4-6 seconds the system totaly freeze for 4-7 minutes. In the 90% of cases I can move only the mouse pointer. Then something seams to work for 2-3 secconds and then another freeze. I have tried install KDE, LXDE, nothing. I have tested suse, ubuntu, arch and fedora. Nothing, the problem is still there. I have used ubuntu with nvidia driver, without, with official driver and comunity driver. Nothing change. I have stressed my cpu and gpu under linux, nothing happened. 

Some logs: syslog don't show nothing under the "freeze time", nothing strange. But here is some syslogs taken after the freeze
```
Jun 12 07:13:31 otadesk gnome-session[2104]: WARNING: App 'gnome-settings-daemon.desktop' respawning too quickly
Jun 12 07:13:31 otadesk gnome-session[2104]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```

```
Jul 24 18:35:28 otadesk dbus[938]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 24 18:35:28 otadesk dbus[938]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
```

Some "ps aux" durring the problem:
after 10 sec
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24544  2080 ?        Ss   Aug01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug01   0:01 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/2]
root        15  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/2]
root        16  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/2]
root        17  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/3]
root        19  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/3]
root        20  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/3]
root        21  0.0  0.0      0     0 ?        S<   Aug01   0:00 [cpuset]
root        22  0.0  0.0      0     0 ?        S<   Aug01   0:00 [khelper]
root        23  0.0  0.0      0     0 ?        S    Aug01   0:00 [kdevtmpfs]
root        24  0.0  0.0      0     0 ?        S<   Aug01   0:00 [netns]
root        25  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:1]
root        26  0.0  0.0      0     0 ?        S    Aug01   0:00 [sync_supers]
root        27  0.0  0.0      0     0 ?        S    Aug01   0:00 [bdi-default]
root        28  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kintegrityd]
root        29  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kblockd]
root        30  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ata_sff]
root        31  0.0  0.0      0     0 ?        S    Aug01   0:00 [khubd]
root        32  0.0  0.0      0     0 ?        S<   Aug01   0:00 [md]
root        35  0.0  0.0      0     0 ?        S    Aug01   0:02 [kworker/3:1]
root        36  0.0  0.0      0     0 ?        S    Aug01   0:00 [khungtaskd]
root        37  0.0  0.0      0     0 ?        S    Aug01   0:03 [kswapd0]
root        38  0.0  0.0      0     0 ?        SN   Aug01   0:00 [ksmd]
root        39  0.0  0.0      0     0 ?        SN   Aug01   0:00 [khugepaged]
root        40  0.0  0.0      0     0 ?        S    Aug01   0:00 [fsnotify_mark]
root        41  0.0  0.0      0     0 ?        S    Aug01   0:00 [ecryptfs-kthr]
root        42  0.0  0.0      0     0 ?        S<   Aug01   0:00 [crypto]
root        50  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kthrotld]
root        51  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_0]
root        52  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:2]
root        54  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_2]
root        55  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_3]
root        58  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_4]
root        59  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_5]
root        81  0.0  0.0      0     0 ?        S<   Aug01   0:00 [devfreq_wq]
root       220  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_6]
root       221  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_7]
root       242  0.0  0.0      0     0 ?        D    Aug01   0:00 [jbd2/sda1-8]
root       243  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       335  0.0  0.0  17224   560 ?        S    Aug01   0:00 upstart-udev-br
root       368  0.0  0.0  22012  1636 ?        Ss   Aug01   0:00 /sbin/udevd --d
root       723  0.0  0.0      0     0 ?        R    Aug01   0:04 [kworker/3:2]
root       773  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kpsmoused]
root       780  0.0  0.0  15180   324 ?        S    Aug01   0:00 upstart-socket-
root       843  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio0]
root       846  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio1]
root       892  0.0  0.0      0     0 ?        D    Aug01   0:06 [jbd2/sda6-8]
root       893  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       896  0.0  0.0      0     0 ?        S    Aug01   0:00 [jbd2/sdb2-8]
root       897  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       914  0.0  0.0  22800  1100 ?        Ss   Aug01   0:00 /sbin/mount.ntf
root       939  0.0  0.0  49948  1512 ?        Ss   Aug01   0:00 /usr/sbin/sshd
102        949  0.0  0.0  24964  2068 ?        Ss   Aug01   0:00 dbus-daemon --s
root       968  0.0  0.0  79036  2432 ?        Ss   Aug01   0:00 /usr/sbin/modem
root       969  0.0  0.0  21180  1396 ?        Ss   Aug01   0:00 /usr/sbin/bluet
syslog     974  0.0  0.0 249464  1084 ?        Sl   Aug01   0:01 rsyslogd -c5
root       980  0.0  0.0 238056  3588 ?        Ssl  Aug01   0:00 NetworkManager
root       983  0.0  0.0      0     0 ?        S<   Aug01   0:00 [krfcommd]
avahi     1004  0.0  0.0  32300  1304 ?        S    Aug01   0:00 avahi-daemon: r
avahi     1005  0.0  0.0  32172   388 ?        S    Aug01   0:00 avahi-daemon: c
root      1011  0.0  0.0 104612  3296 ?        Ss   Aug01   0:00 /usr/sbin/cupsd
root      1015  0.0  0.0 195516  3500 ?        Sl   Aug01   0:00 /usr/lib/policy
colord    1019  0.0  0.1 500072  6116 ?        Sl   Aug01   0:00 /usr/lib/x86_64
root      1096  0.0  0.0  19984   888 tty4     Ss+  Aug01   0:00 /sbin/getty -8
root      1105  0.0  0.0  19984   884 tty5     Ss+  Aug01   0:00 /sbin/getty -8
root      1136  0.0  0.0  19984   880 tty2     Ss+  Aug01   0:00 /sbin/getty -8
root      1137  0.0  0.0  19984   884 tty3     Ss+  Aug01   0:00 /sbin/getty -8
root      1139  0.0  0.0  19984   884 tty6     Ss+  Aug01   0:00 /sbin/getty -8
root      1146  0.0  0.0   4452   784 ?        Ss   Aug01   0:00 acpid -c /etc/a
root      1153  0.0  0.0  15972   672 ?        Ss   Aug01   0:03 /usr/sbin/irqba
whoopsie  1159  0.0  0.1 202564  4056 ?        Ssl  Aug01   0:00 whoopsie
root      1161  0.0  0.0  19104   988 ?        Ss   Aug01   0:00 cron
daemon    1163  0.0  0.0  16900   360 ?        Ss   Aug01   0:00 atd
root      1168  0.0  0.0 270656  2856 ?        Ssl  Aug01   0:00 lightdm
root      1191  1.6  1.5 193348 61300 tty7     Ss+  Aug01   8:44 /usr/bin/X :0 -
root      1213  0.0  0.0   4836  1060 ?        D    Aug01   0:01 /usr/sbin/hddte
root      1238  0.0  0.0 103644  2108 ?        Ss   Aug01   0:00 /usr/sbin/winbi
root      1242  0.0  0.0 103644  1656 ?        S    Aug01   0:00 /usr/sbin/winbi
root      1274  0.0  0.1  21148  5380 ?        SNs  Aug01   0:12 /usr/sbin/prelo
root      2123  0.0  0.0  77800  1736 tty1     Ss   Aug01   0:00 /bin/login -- 
root      2133  0.0  0.0 161012  2852 ?        Sl   Aug01   0:00 lightdm --sessi
root      2136  0.0  0.0 121524  3024 ?        Sl   Aug01   0:00 /usr/lib/accoun
root      2144  0.0  0.0 2093832 3356 ?        Sl   Aug01   0:00 /usr/sbin/conso
otacon    2219  0.0  0.1 396308  7312 ?        Ssl  Aug01   0:00 gnome-session -
nobody    2220  0.0  0.0  33028  1148 ?        S    Aug01   0:01 /usr/sbin/dnsma
otacon    2327  0.0  0.0  12484   316 ?        Ss   Aug01   0:00 /usr/bin/ssh-ag
otacon    2330  0.0  0.0  26680   740 ?        S    Aug01   0:00 /usr/bin/dbus-l
otacon    2331  0.0  0.0  26464  2736 ?        Ss   Aug01   0:04 //bin/dbus-daem
otacon    2342  0.0  0.1 590664  4152 ?        SLl  Aug01   0:00 /usr/bin/gnome-
otacon    2348  0.0  0.3 682576 13412 ?        Sl   Aug01   0:06 /usr/lib/gnome-
root      2354  0.0  0.0 219888  3296 ?        Sl   Aug01   0:00 /usr/lib/upower
otacon    2416  0.0  0.0  52548  2088 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2437  0.0  0.0      0     0 ?        S    03:42   0:01 [kworker/2:0]
otacon    2462  0.0  0.0 273436  2340 ?        Sl   Aug01   0:00 /usr/lib/gvfs//
otacon    2529  0.0  0.0 369800  3172 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2533  2.4  4.2 1948308 172572 ?      Sl   Aug01  12:55 /usr/bin/gnome-
root      2536  0.0  0.0      0     0 ?        S    Aug01   0:03 [flush-8:0]
otacon    2544  0.6  0.1 437268  6624 ?        S<l  Aug01   3:19 /usr/bin/pulsea
rtkit     2546  0.0  0.0 168864  1204 ?        SNl  Aug01   0:00 /usr/lib/rtkit/
otacon    2554  0.0  0.0  95940  1916 ?        S    Aug01   0:00 /usr/lib/pulsea
otacon    2556  0.0  0.0  58428  3460 ?        S    Aug01   0:00 /usr/lib/x86_64
otacon    2563  0.3  0.7 627784 29172 ?        Sl   Aug01   1:54 mono /usr/lib/d
otacon    2564  0.1  0.4 612860 19256 ?        Sl   Aug01   0:56 /usr/bin/python
otacon    2573  0.0  0.4 625664 17704 ?        Sl   Aug01   0:01 synapse --start
otacon    2574  0.0  0.2 621944 10756 ?        Sl   Aug01   0:00 nm-applet
otacon    2580  0.1  0.8 1104600 32736 ?       Sl   Aug01   1:01 nautilus -n
otacon    2581  2.9  6.5 5083244 266040 ?      Sl   Aug01  15:42 /usr/lib/jvm/ja
otacon    2590  0.0  0.0 218352  3584 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2592  0.0  0.0 201980  3620 ?        Sl   Aug01   0:00 /usr/lib/udisks
root      2593  0.0  0.0  45512   776 ?        S    Aug01   0:00 udisks-daemon: 
otacon    2596  0.0  0.0  60328  1996 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2598  0.0  0.0 142068  1808 ?        Sl   Aug01   0:00 /usr/lib/gvfs/g
otacon    2615  0.0  0.1 341168  5756 ?        Sl   Aug01   0:01 /usr/bin/zeitge
otacon    2618  0.0  0.0  57340  2800 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2644  0.0  0.3 247716 15896 ?        Sl   Aug01   0:00 /usr/lib/zeitge
otacon    2649  0.0  0.0  52548  2164 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2651  0.0  0.0  11380   328 ?        S    Aug01   0:00 /bin/cat
otacon    2660  0.0  0.0  46316  2028 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2684  0.0  0.1 426264  6872 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2688  0.0  0.1 321520  4208 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2692  0.0  0.2 567484 10632 ?        SLl  Aug01   0:00 /usr/lib/gnome-
otacon    2704  0.0  0.3 854204 15240 ?        Sl   Aug01   0:00 /usr/lib/evolut
otacon    2712  0.0  0.0 291056  3368 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2803  0.0  0.2 433924  9752 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    3323  0.0  0.1 310804  6620 ?        Sl   Aug01   0:00 gnome-screensav
otacon    3338  0.0  0.8 739668 32488 ?        Sl   Aug01   0:01 pidgin
otacon    3425  0.5  0.2 686588 12072 ?        Sl   Aug01   2:54 psensor
otacon    4095  0.0  0.0 262208  2496 ?        Sl   Aug01   0:00 /usr/lib/dconf/
otacon    4099  0.0  0.2 504576 10968 ?        Sl   Aug01   0:00 update-notifier
root      4613  0.0  0.0  26680   744 ?        S    Aug01   0:00 dbus-launch --a
root      4614  0.0  0.0  23808   644 ?        Ss   Aug01   0:00 //bin/dbus-daem
root      6763  0.0  0.0      0     0 ?        S    05:42   0:00 [kworker/2:1]
root     21730  0.0  0.0      0     0 ?        S    06:32   0:00 [kworker/0:1]
root     25006  0.0  0.0      0     0 ?        S    06:43   0:00 [kworker/1:0]
root     28466  0.0  0.0      0     0 ?        S    06:54   0:00 [kworker/1:1]
root     28742  0.0  0.0  22008  1168 ?        S    Aug01   0:00 /sbin/udevd --d
root     28743  0.0  0.0  22008  1164 ?        S    Aug01   0:00 /sbin/udevd --d
root     29261  0.0  0.0      0     0 ?        S    06:57   0:00 [kworker/0:0]
otacon   30466  5.1  2.3 1591624 94712 ?       Sl   07:01   0:16 /usr/bin/vlc /h
otacon   30527  0.0  0.0   4392   448 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30535  0.0  0.0   4392   528 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30539  0.0  0.0  24000   952 ?        S    07:01   0:00 /usr/bin/xprop
root     30826  0.0  0.0      0     0 ?        S    07:02   0:00 [kworker/0:2]
otacon   31356  0.0  0.1  31248  7160 tty1     S+   Aug01   0:00 -bash
otacon   31727  0.3  0.4 582864 18604 ?        Sl   07:05   0:00 gnome-terminal
otacon   31862  0.0  0.0  11360   352 ?        S    07:05   0:00 sleep 50
otacon   32037  0.0  0.0  14780   844 ?        S    07:06   0:00 gnome-pty-helpe
otacon   32038  0.8  0.1  27700  4540 pts/2    Ss+  07:06   0:00 bash
otacon   32042  0.8  0.1  27700  4616 pts/3    Ss   07:06   0:00 bash
otacon   32242  0.0  0.0  22360  1264 pts/3    R+   07:06   0:00 ps aux
```

after 2 mins
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24544  2080 ?        Ss   Aug01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug01   0:01 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/2]
root        15  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/2]
root        16  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/2]
root        17  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/3]
root        19  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/3]
root        20  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/3]
root        21  0.0  0.0      0     0 ?        S<   Aug01   0:00 [cpuset]
root        22  0.0  0.0      0     0 ?        S<   Aug01   0:00 [khelper]
root        23  0.0  0.0      0     0 ?        S    Aug01   0:00 [kdevtmpfs]
root        24  0.0  0.0      0     0 ?        S<   Aug01   0:00 [netns]
root        25  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:1]
root        26  0.0  0.0      0     0 ?        S    Aug01   0:00 [sync_supers]
root        27  0.0  0.0      0     0 ?        S    Aug01   0:00 [bdi-default]
root        28  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kintegrityd]
root        29  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kblockd]
root        30  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ata_sff]
root        31  0.0  0.0      0     0 ?        S    Aug01   0:00 [khubd]
root        32  0.0  0.0      0     0 ?        S<   Aug01   0:00 [md]
root        35  0.0  0.0      0     0 ?        S    Aug01   0:02 [kworker/3:1]
root        36  0.0  0.0      0     0 ?        S    Aug01   0:00 [khungtaskd]
root        37  0.0  0.0      0     0 ?        S    Aug01   0:03 [kswapd0]
root        38  0.0  0.0      0     0 ?        SN   Aug01   0:00 [ksmd]
root        39  0.0  0.0      0     0 ?        SN   Aug01   0:00 [khugepaged]
root        40  0.0  0.0      0     0 ?        S    Aug01   0:00 [fsnotify_mark]
root        41  0.0  0.0      0     0 ?        S    Aug01   0:00 [ecryptfs-kthr]
root        42  0.0  0.0      0     0 ?        S<   Aug01   0:00 [crypto]
root        50  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kthrotld]
root        51  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_0]
root        52  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:2]
root        54  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_2]
root        55  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_3]
root        58  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_4]
root        59  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_5]
root        81  0.0  0.0      0     0 ?        S<   Aug01   0:00 [devfreq_wq]
root       220  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_6]
root       221  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_7]
root       242  0.0  0.0      0     0 ?        D    Aug01   0:00 [jbd2/sda1-8]
root       243  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       335  0.0  0.0  17224   560 ?        S    Aug01   0:00 upstart-udev-br
root       368  0.0  0.0  22012  1636 ?        Ss   Aug01   0:00 /sbin/udevd --d
root       723  0.0  0.0      0     0 ?        S    Aug01   0:04 [kworker/3:2]
root       773  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kpsmoused]
root       780  0.0  0.0  15180   324 ?        S    Aug01   0:00 upstart-socket-
root       843  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio0]
root       846  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio1]
root       892  0.0  0.0      0     0 ?        D    Aug01   0:06 [jbd2/sda6-8]
root       893  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       896  0.0  0.0      0     0 ?        S    Aug01   0:00 [jbd2/sdb2-8]
root       897  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       914  0.0  0.0  22800  1100 ?        Ss   Aug01   0:00 /sbin/mount.ntf
root       939  0.0  0.0  49948  1512 ?        Ss   Aug01   0:00 /usr/sbin/sshd
102        949  0.0  0.0  24964  2068 ?        Ss   Aug01   0:00 dbus-daemon --s
root       968  0.0  0.0  79036  2432 ?        Ss   Aug01   0:00 /usr/sbin/modem
root       969  0.0  0.0  21180  1396 ?        Ss   Aug01   0:00 /usr/sbin/bluet
syslog     974  0.0  0.0 249464  1084 ?        Sl   Aug01   0:01 rsyslogd -c5
root       980  0.0  0.0 238056  3588 ?        Ssl  Aug01   0:00 NetworkManager
root       983  0.0  0.0      0     0 ?        S<   Aug01   0:00 [krfcommd]
avahi     1004  0.0  0.0  32300  1304 ?        S    Aug01   0:00 avahi-daemon: r
avahi     1005  0.0  0.0  32172   388 ?        S    Aug01   0:00 avahi-daemon: c
root      1011  0.0  0.0 104612  3296 ?        Ss   Aug01   0:00 /usr/sbin/cupsd
root      1015  0.0  0.0 195516  3500 ?        Sl   Aug01   0:00 /usr/lib/policy
colord    1019  0.0  0.1 500072  6116 ?        Sl   Aug01   0:00 /usr/lib/x86_64
root      1096  0.0  0.0  19984   888 tty4     Ss+  Aug01   0:00 /sbin/getty -8
root      1105  0.0  0.0  19984   884 tty5     Ss+  Aug01   0:00 /sbin/getty -8
root      1136  0.0  0.0  19984   880 tty2     Ss+  Aug01   0:00 /sbin/getty -8
root      1137  0.0  0.0  19984   884 tty3     Ss+  Aug01   0:00 /sbin/getty -8
root      1139  0.0  0.0  19984   884 tty6     Ss+  Aug01   0:00 /sbin/getty -8
root      1146  0.0  0.0   4452   784 ?        Ss   Aug01   0:00 acpid -c /etc/a
root      1153  0.0  0.0  15972   672 ?        Ss   Aug01   0:03 /usr/sbin/irqba
whoopsie  1159  0.0  0.1 202564  4056 ?        Ssl  Aug01   0:00 whoopsie
root      1161  0.0  0.0  19104   988 ?        Ss   Aug01   0:00 cron
daemon    1163  0.0  0.0  16900   360 ?        Ss   Aug01   0:00 atd
root      1168  0.0  0.0 270656  2856 ?        Ssl  Aug01   0:00 lightdm
root      1191  1.6  1.5 193348 61300 tty7     Ss+  Aug01   8:44 /usr/bin/X :0 -
root      1213  0.0  0.0   4836  1060 ?        S    Aug01   0:01 /usr/sbin/hddte
root      1238  0.0  0.0 103644  2108 ?        Ss   Aug01   0:00 /usr/sbin/winbi
root      1242  0.0  0.0 103644  1656 ?        S    Aug01   0:00 /usr/sbin/winbi
root      1274  0.0  0.1  21148  5380 ?        SNs  Aug01   0:12 /usr/sbin/prelo
root      2123  0.0  0.0  77800  1736 tty1     Ss   Aug01   0:00 /bin/login -- 
root      2133  0.0  0.0 161012  2852 ?        Sl   Aug01   0:00 lightdm --sessi
root      2136  0.0  0.0 121524  3024 ?        Sl   Aug01   0:00 /usr/lib/accoun
root      2144  0.0  0.0 2093832 3356 ?        Sl   Aug01   0:00 /usr/sbin/conso
otacon    2219  0.0  0.1 396308  7312 ?        Ssl  Aug01   0:00 gnome-session -
nobody    2220  0.0  0.0  33028  1148 ?        S    Aug01   0:01 /usr/sbin/dnsma
otacon    2327  0.0  0.0  12484   316 ?        Ss   Aug01   0:00 /usr/bin/ssh-ag
otacon    2330  0.0  0.0  26680   740 ?        S    Aug01   0:00 /usr/bin/dbus-l
otacon    2331  0.0  0.0  26464  2736 ?        Ss   Aug01   0:04 //bin/dbus-daem
otacon    2342  0.0  0.1 590664  4152 ?        SLl  Aug01   0:00 /usr/bin/gnome-
otacon    2348  0.0  0.3 682576 13412 ?        Sl   Aug01   0:06 /usr/lib/gnome-
root      2354  0.0  0.0 219888  3296 ?        Sl   Aug01   0:00 /usr/lib/upower
otacon    2416  0.0  0.0  52548  2088 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2437  0.0  0.0      0     0 ?        S    03:42   0:01 [kworker/2:0]
otacon    2462  0.0  0.0 273436  2340 ?        Sl   Aug01   0:00 /usr/lib/gvfs//
otacon    2529  0.0  0.0 369800  3172 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2533  2.4  4.2 1948308 171548 ?      Sl   Aug01  12:58 /usr/bin/gnome-
root      2536  0.0  0.0      0     0 ?        D    Aug01   0:03 [flush-8:0]
otacon    2544  0.6  0.1 437268  6496 ?        S<l  Aug01   3:19 /usr/bin/pulsea
rtkit     2546  0.0  0.0 168864  1204 ?        SNl  Aug01   0:00 /usr/lib/rtkit/
otacon    2554  0.0  0.0  95940  1916 ?        S    Aug01   0:00 /usr/lib/pulsea
otacon    2556  0.0  0.0  58428  3460 ?        S    Aug01   0:00 /usr/lib/x86_64
otacon    2563  0.3  0.7 627784 29172 ?        Sl   Aug01   1:54 mono /usr/lib/d
otacon    2564  0.1  0.4 612860 19256 ?        Sl   Aug01   0:56 /usr/bin/python
otacon    2573  0.0  0.4 625664 17704 ?        Sl   Aug01   0:01 synapse --start
otacon    2574  0.0  0.2 621944 10756 ?        Sl   Aug01   0:00 nm-applet
otacon    2580  0.1  0.8 1104600 32736 ?       Sl   Aug01   1:01 nautilus -n
otacon    2581  2.9  6.5 5083244 265424 ?      Sl   Aug01  15:42 /usr/lib/jvm/ja
otacon    2590  0.0  0.0 218352  3584 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2592  0.0  0.0 201980  3620 ?        Sl   Aug01   0:00 /usr/lib/udisks
root      2593  0.0  0.0  45512   776 ?        S    Aug01   0:00 udisks-daemon: 
otacon    2596  0.0  0.0  60328  1996 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2598  0.0  0.0 142068  1808 ?        Sl   Aug01   0:00 /usr/lib/gvfs/g
otacon    2615  0.0  0.1 341168  5756 ?        Sl   Aug01   0:01 /usr/bin/zeitge
otacon    2618  0.0  0.0  57340  2800 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2644  0.0  0.3 247716 15896 ?        Sl   Aug01   0:00 /usr/lib/zeitge
otacon    2649  0.0  0.0  52548  2164 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2651  0.0  0.0  11380   328 ?        S    Aug01   0:00 /bin/cat
otacon    2660  0.0  0.0  46316  2028 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2684  0.0  0.1 426264  6872 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2688  0.0  0.1 321520  4208 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2692  0.0  0.2 567484 10632 ?        SLl  Aug01   0:00 /usr/lib/gnome-
otacon    2704  0.0  0.3 854204 15240 ?        Sl   Aug01   0:00 /usr/lib/evolut
otacon    2712  0.0  0.0 291056  3368 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2803  0.0  0.2 433924  9752 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    3323  0.0  0.1 310804  6620 ?        Sl   Aug01   0:00 gnome-screensav
otacon    3338  0.0  0.8 739668 32488 ?        Sl   Aug01   0:01 pidgin
otacon    3425  0.5  0.2 686588 12072 ?        Sl   Aug01   2:54 psensor
otacon    4095  0.0  0.0 262208  2496 ?        Sl   Aug01   0:00 /usr/lib/dconf/
otacon    4099  0.0  0.2 504576 10968 ?        Sl   Aug01   0:00 update-notifier
root      4613  0.0  0.0  26680   744 ?        S    Aug01   0:00 dbus-launch --a
root      4614  0.0  0.0  23808   644 ?        Ss   Aug01   0:00 //bin/dbus-daem
root      6763  0.0  0.0      0     0 ?        S    05:42   0:00 [kworker/2:1]
root     21730  0.0  0.0      0     0 ?        S    06:32   0:00 [kworker/0:1]
root     25006  0.0  0.0      0     0 ?        S    06:43   0:00 [kworker/1:0]
root     28466  0.0  0.0      0     0 ?        S    06:54   0:00 [kworker/1:1]
root     28742  0.0  0.0  22008  1168 ?        S    Aug01   0:00 /sbin/udevd --d
root     28743  0.0  0.0  22008  1164 ?        S    Aug01   0:00 /sbin/udevd --d
root     29261  0.0  0.0      0     0 ?        S    06:57   0:00 [kworker/0:0]
otacon   30466  4.8  2.3 1591624 94788 ?       Sl   07:01   0:16 /usr/bin/vlc /h
otacon   30527  0.0  0.0   4392   448 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30535  0.0  0.0   4392   528 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30539  0.0  0.0  24000   952 ?        S    07:01   0:00 /usr/bin/xprop
root     30826  0.0  0.0      0     0 ?        S    07:02   0:00 [kworker/0:2]
otacon   31356  0.0  0.1  31248  7160 tty1     S+   Aug01   0:00 -bash
otacon   31727  0.2  0.4 582864 18604 ?        Dl   07:05   0:00 gnome-terminal
otacon   32037  0.0  0.0  14780   844 ?        S    07:06   0:00 gnome-pty-helpe
otacon   32038  0.3  0.1  27700  4540 pts/2    Ss+  07:06   0:00 bash
otacon   32042  0.3  0.1  27700  4616 pts/3    Ss   07:06   0:00 bash
otacon   32254  0.0  0.0  11360   348 ?        S    07:06   0:00 sleep 50
otacon   32406  0.0  0.0  22360  1264 pts/3    R+   07:07   0:00 ps aux
```

after 5 mins
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24544  2080 ?        Ss   Aug01   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Aug01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    Aug01   0:01 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/1]
root        12  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/1]
root        13  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/2]
root        15  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/2]
root        16  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/2]
root        17  0.0  0.0      0     0 ?        S    Aug01   0:00 [migration/3]
root        19  0.0  0.0      0     0 ?        S    Aug01   0:00 [ksoftirqd/3]
root        20  0.0  0.0      0     0 ?        S    Aug01   0:00 [watchdog/3]
root        21  0.0  0.0      0     0 ?        S<   Aug01   0:00 [cpuset]
root        22  0.0  0.0      0     0 ?        S<   Aug01   0:00 [khelper]
root        23  0.0  0.0      0     0 ?        S    Aug01   0:00 [kdevtmpfs]
root        24  0.0  0.0      0     0 ?        S<   Aug01   0:00 [netns]
root        25  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:1]
root        26  0.0  0.0      0     0 ?        S    Aug01   0:00 [sync_supers]
root        27  0.0  0.0      0     0 ?        S    Aug01   0:00 [bdi-default]
root        28  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kintegrityd]
root        29  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kblockd]
root        30  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ata_sff]
root        31  0.0  0.0      0     0 ?        S    Aug01   0:00 [khubd]
root        32  0.0  0.0      0     0 ?        S<   Aug01   0:00 [md]
root        35  0.0  0.0      0     0 ?        S    Aug01   0:02 [kworker/3:1]
root        36  0.0  0.0      0     0 ?        S    Aug01   0:00 [khungtaskd]
root        37  0.0  0.0      0     0 ?        S    Aug01   0:03 [kswapd0]
root        38  0.0  0.0      0     0 ?        SN   Aug01   0:00 [ksmd]
root        39  0.0  0.0      0     0 ?        SN   Aug01   0:00 [khugepaged]
root        40  0.0  0.0      0     0 ?        S    Aug01   0:00 [fsnotify_mark]
root        41  0.0  0.0      0     0 ?        S    Aug01   0:00 [ecryptfs-kthr]
root        42  0.0  0.0      0     0 ?        S<   Aug01   0:00 [crypto]
root        50  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kthrotld]
root        51  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_0]
root        52  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S    Aug01   0:00 [kworker/u:2]
root        54  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_2]
root        55  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_3]
root        58  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_4]
root        59  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_5]
root        81  0.0  0.0      0     0 ?        S<   Aug01   0:00 [devfreq_wq]
root       220  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_6]
root       221  0.0  0.0      0     0 ?        S    Aug01   0:00 [scsi_eh_7]
root       242  0.0  0.0      0     0 ?        S    Aug01   0:00 [jbd2/sda1-8]
root       243  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       335  0.0  0.0  17224   560 ?        S    Aug01   0:00 upstart-udev-br
root       368  0.0  0.0  22012  1636 ?        Ss   Aug01   0:00 /sbin/udevd --d
root       723  0.0  0.0      0     0 ?        R    Aug01   0:04 [kworker/3:2]
root       773  0.0  0.0      0     0 ?        S<   Aug01   0:00 [kpsmoused]
root       780  0.0  0.0  15180   324 ?        S    Aug01   0:00 upstart-socket-
root       843  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio0]
root       846  0.0  0.0      0     0 ?        S<   Aug01   0:00 [hd-audio1]
root       892  0.0  0.0      0     0 ?        D    Aug01   0:06 [jbd2/sda6-8]
root       893  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       896  0.0  0.0      0     0 ?        S    Aug01   0:00 [jbd2/sdb2-8]
root       897  0.0  0.0      0     0 ?        S<   Aug01   0:00 [ext4-dio-unwr]
root       914  0.0  0.0  22800  1100 ?        Ss   Aug01   0:00 /sbin/mount.ntf
root       939  0.0  0.0  49948  1512 ?        Ss   Aug01   0:00 /usr/sbin/sshd
102        949  0.0  0.0  24964  2068 ?        Ss   Aug01   0:00 dbus-daemon --s
root       968  0.0  0.0  79036  2432 ?        Ss   Aug01   0:00 /usr/sbin/modem
root       969  0.0  0.0  21180  1396 ?        Ss   Aug01   0:00 /usr/sbin/bluet
syslog     974  0.0  0.0 249464  1084 ?        Sl   Aug01   0:01 rsyslogd -c5
root       980  0.0  0.0 238056  3588 ?        Ssl  Aug01   0:00 NetworkManager
root       983  0.0  0.0      0     0 ?        S<   Aug01   0:00 [krfcommd]
avahi     1004  0.0  0.0  32300  1304 ?        S    Aug01   0:00 avahi-daemon: r
avahi     1005  0.0  0.0  32172   388 ?        S    Aug01   0:00 avahi-daemon: c
root      1011  0.0  0.0 104612  3296 ?        Ss   Aug01   0:00 /usr/sbin/cupsd
root      1015  0.0  0.0 195516  3500 ?        Sl   Aug01   0:00 /usr/lib/policy
colord    1019  0.0  0.1 500072  6116 ?        Sl   Aug01   0:00 /usr/lib/x86_64
root      1096  0.0  0.0  19984   888 tty4     Ss+  Aug01   0:00 /sbin/getty -8
root      1105  0.0  0.0  19984   884 tty5     Ss+  Aug01   0:00 /sbin/getty -8
root      1136  0.0  0.0  19984   880 tty2     Ss+  Aug01   0:00 /sbin/getty -8
root      1137  0.0  0.0  19984   884 tty3     Ss+  Aug01   0:00 /sbin/getty -8
root      1139  0.0  0.0  19984   884 tty6     Ss+  Aug01   0:00 /sbin/getty -8
root      1146  0.0  0.0   4452   784 ?        Ss   Aug01   0:00 acpid -c /etc/a
root      1153  0.0  0.0  15972   672 ?        Ss   Aug01   0:03 /usr/sbin/irqba
whoopsie  1159  0.0  0.1 202564  4056 ?        Ssl  Aug01   0:00 whoopsie
root      1161  0.0  0.0  19104   988 ?        Ss   Aug01   0:00 cron
daemon    1163  0.0  0.0  16900   360 ?        Ss   Aug01   0:00 atd
root      1168  0.0  0.0 270656  2856 ?        Ssl  Aug01   0:00 lightdm
root      1191  1.6  1.5 193348 61300 tty7     Rs+  Aug01   8:45 /usr/bin/X :0 -
root      1213  0.0  0.0   4836  1060 ?        S    Aug01   0:01 /usr/sbin/hddte
root      1238  0.0  0.0 103644  2108 ?        Ss   Aug01   0:00 /usr/sbin/winbi
root      1242  0.0  0.0 103644  1656 ?        S    Aug01   0:00 /usr/sbin/winbi
root      1274  0.0  0.1  21148  5380 ?        SNs  Aug01   0:12 /usr/sbin/prelo
root      2123  0.0  0.0  77800  1736 tty1     Ss   Aug01   0:00 /bin/login -- 
root      2133  0.0  0.0 161012  2852 ?        Sl   Aug01   0:00 lightdm --sessi
root      2136  0.0  0.0 121524  3024 ?        Sl   Aug01   0:00 /usr/lib/accoun
root      2144  0.0  0.0 2093832 3356 ?        Sl   Aug01   0:00 /usr/sbin/conso
otacon    2219  0.0  0.1 396308  7312 ?        Ssl  Aug01   0:00 gnome-session -
nobody    2220  0.0  0.0  33028  1148 ?        S    Aug01   0:01 /usr/sbin/dnsma
otacon    2327  0.0  0.0  12484   316 ?        Ss   Aug01   0:00 /usr/bin/ssh-ag
otacon    2330  0.0  0.0  26680   740 ?        S    Aug01   0:00 /usr/bin/dbus-l
otacon    2331  0.0  0.0  26464  2736 ?        Ss   Aug01   0:04 //bin/dbus-daem
otacon    2342  0.0  0.1 590664  4152 ?        SLl  Aug01   0:00 /usr/bin/gnome-
otacon    2348  0.0  0.3 682576 13412 ?        Sl   Aug01   0:06 /usr/lib/gnome-
root      2354  0.0  0.0 219888  3296 ?        Sl   Aug01   0:00 /usr/lib/upower
otacon    2416  0.0  0.0  52548  2088 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2437  0.0  0.0      0     0 ?        S    03:42   0:01 [kworker/2:0]
otacon    2462  0.0  0.0 273436  2340 ?        Sl   Aug01   0:00 /usr/lib/gvfs//
otacon    2529  0.0  0.0 369800  3172 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2533  2.4  4.2 1948308 171548 ?      Rl   Aug01  13:01 /usr/bin/gnome-
root      2536  0.0  0.0      0     0 ?        D    Aug01   0:03 [flush-8:0]
otacon    2544  0.6  0.1 437268  6496 ?        S<l  Aug01   3:20 /usr/bin/pulsea
rtkit     2546  0.0  0.0 168864  1204 ?        SNl  Aug01   0:00 /usr/lib/rtkit/
otacon    2554  0.0  0.0  95940  1916 ?        S    Aug01   0:00 /usr/lib/pulsea
otacon    2556  0.0  0.0  58432  3460 ?        D    Aug01   0:00 /usr/lib/x86_64
otacon    2563  0.3  0.7 627784 29172 ?        Sl   Aug01   1:54 mono /usr/lib/d
otacon    2564  0.1  0.4 612860 19256 ?        Sl   Aug01   0:56 /usr/bin/python
otacon    2573  0.0  0.4 625664 17704 ?        Sl   Aug01   0:01 synapse --start
otacon    2574  0.0  0.2 621944 10756 ?        Sl   Aug01   0:00 nm-applet
otacon    2580  0.1  0.8 1104600 32736 ?       Sl   Aug01   1:01 nautilus -n
otacon    2581  2.9  6.5 5083244 265004 ?      Sl   Aug01  15:43 /usr/lib/jvm/ja
otacon    2590  0.0  0.0 218352  3584 ?        S    Aug01   0:00 /usr/lib/gvfs/g
root      2592  0.0  0.0 201980  3620 ?        Sl   Aug01   0:00 /usr/lib/udisks
root      2593  0.0  0.0  45512   776 ?        S    Aug01   0:00 udisks-daemon: 
otacon    2596  0.0  0.0  60328  1996 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2598  0.0  0.0 142068  1808 ?        Sl   Aug01   0:00 /usr/lib/gvfs/g
otacon    2615  0.0  0.1 341168  5756 ?        Sl   Aug01   0:01 /usr/bin/zeitge
otacon    2618  0.0  0.0  57340  2800 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2644  0.0  0.3 247716 15896 ?        Sl   Aug01   0:00 /usr/lib/zeitge
otacon    2649  0.0  0.0  52548  2164 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2651  0.0  0.0  11380   328 ?        S    Aug01   0:00 /bin/cat
otacon    2660  0.0  0.0  46316  2028 ?        S    Aug01   0:00 /usr/lib/gvfs/g
otacon    2684  0.0  0.1 426264  6872 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    2688  0.0  0.1 321520  4208 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2692  0.0  0.2 567484 10632 ?        SLl  Aug01   0:00 /usr/lib/gnome-
otacon    2704  0.0  0.3 854204 15240 ?        Sl   Aug01   0:00 /usr/lib/evolut
otacon    2712  0.0  0.0 291056  3368 ?        Sl   Aug01   0:00 /usr/lib/telepa
otacon    2803  0.0  0.2 433924  9752 ?        Sl   Aug01   0:00 /usr/lib/gnome-
otacon    3323  0.0  0.1 310804  6620 ?        Sl   Aug01   0:00 gnome-screensav
otacon    3338  0.0  0.8 739668 32488 ?        Sl   Aug01   0:01 pidgin
otacon    3425  0.5  0.2 686588 12072 ?        Sl   Aug01   2:54 psensor
otacon    4095  0.0  0.0 262208  2496 ?        Sl   Aug01   0:00 /usr/lib/dconf/
otacon    4099  0.0  0.2 504576 10968 ?        Sl   Aug01   0:00 update-notifier
root      4613  0.0  0.0  26680   744 ?        S    Aug01   0:00 dbus-launch --a
root      4614  0.0  0.0  23808   644 ?        Ss   Aug01   0:00 //bin/dbus-daem
root      6763  0.0  0.0      0     0 ?        S    05:42   0:00 [kworker/2:1]
root     25006  0.0  0.0      0     0 ?        S    06:43   0:00 [kworker/1:0]
root     28466  0.0  0.0      0     0 ?        S    06:54   0:00 [kworker/1:1]
root     28742  0.0  0.0  22008  1168 ?        S    Aug01   0:00 /sbin/udevd --d
root     28743  0.0  0.0  22008  1164 ?        S    Aug01   0:00 /sbin/udevd --d
root     29261  0.0  0.0      0     0 ?        S    06:57   0:00 [kworker/0:0]
otacon   30466  4.5  2.3 1591624 94788 ?       Sl   07:01   0:16 /usr/bin/vlc /h
otacon   30527  0.0  0.0   4392   448 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30535  0.0  0.0   4392   528 ?        S    07:01   0:00 /bin/sh /usr/bi
otacon   30539  0.0  0.0  24000   952 ?        S    07:01   0:00 /usr/bin/xprop
root     30826  0.0  0.0      0     0 ?        S    07:02   0:00 [kworker/0:2]
otacon   31356  0.0  0.1  31248  7160 tty1     S+   Aug01   0:00 -bash
otacon   31727  0.2  0.4 582864 18604 ?        Sl   07:05   0:00 gnome-terminal
otacon   32037  0.0  0.0  14780   844 ?        S    07:06   0:00 gnome-pty-helpe
otacon   32038  0.2  0.1  27700  4540 pts/2    Ss+  07:06   0:00 bash
otacon   32042  0.2  0.1  27700  4616 pts/3    Ss   07:06   0:00 bash
otacon   32517  0.0  0.0  11360   352 ?        S    07:07   0:00 sleep 50
root     32518  0.0  0.0      0     0 ?        S    07:07   0:00 [kworker/0:1]
otacon   32559  0.0  0.0  22360  1268 pts/3    R+   07:07   0:00 ps aux
```

Here we can see that in every ps aux there are over 11 kworker procces and he work for ACPI. One user from the italian community has an idea about. He said that from the kernel 2.6.36 there is a bug that someone have about the bad managment of ACPI of the kernel. I have read some pages of the discussion abotu "needs-upstream-testing" but no one have a solution there that solve the problem. Some link about this topic:
[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/717919[/HTML]
[HTML]http://ubuntuforums.org/showthread.php?t=1853783[/HTML]

Someone have said that the only solution is to downgrade to the kernel 2.6.35 and stay ther for eternity... but it's not a solution.

---

### Post by TrueAncalagon on 2012-09-10
No one have any idea?

---

### Post by paviel on 2012-09-10
"CRITICAL: We failed, but the fail whale is dead. Sorry...."

It looks like that

[http://askubuntu.com/questions/86746/gnome-shell-stopped-working-after-last-update](http://askubuntu.com/questions/86746/gnome-shell-stopped-working-after-last-update)

read and try the solutions proposed.

---

### Post by TrueAncalagon on 2012-09-15
I have removed the two extentions from /usr/share/gnome&#8209;shell/extensions like said in the guide but the problem is always there

---

### Post by TrueAncalagon on 2012-10-08
So, there is no solution isn't it? Is this mean that I must format my hdd and say goodby to linux because it does not work... and no one know how to solce the problem that affect hundreds of people... mm.. so sad

---

### Post by idoitprone on 2012-10-08
```
free -m
```

please post the results

---

### Post by TrueAncalagon on 2012-10-09
free -m 
```
             total       used       free     shared    buffers     cached
Mem:          3826       1906       1920          0         88        788
-/+ buffers/cache:       1029       2797
Swap:         1905          0       1905

```

---

### Post by idoitprone on 2012-10-10
> **TrueAncalagon said:**
> free -m 
```
             total       used       free     shared    buffers     cached
Mem:          3826       1906       1920          0         88        788
-/+ buffers/cache:       1029       2797
Swap:         1905          0       1905

```


this means i can throw out the obvious swapless install

It is a common system freeze problem that will not show up in system logs because the freeze is normal behavior, since the system ran out of resources that instant

however you have swap so i cannot diagnose your problem at this instant

btw, acpi power bug is not really a problem with linux. Ther kernel developers basically said that motherboard manufactorers are mis representing their motherboard supported features. It shouldnt affect you but if you really want to see if that is the problem then add

```
acpi=force
``` to the grub boot option to see

---

### Post by TrueAncalagon on 2012-10-10
I have added acpi=force but the system boot normaly. Boh, we will see

EDIT: ok, after 40 min the system simply turn off. So I returned to put acpi=noirq like before

---

### Post by idoitprone on 2012-10-12
> **TrueAncalagon said:**
> I have added acpi=force but the system boot normaly. Boh, we will see

EDIT: ok, after 40 min the system simply turn off. So I returned to put acpi=noirq like before

If you need acpi=noirq, then I am wondering if your motherboard have problems. I heard MSI mobo are pretty bad. This guy had problems installing linux [http://osx86.co/archive/index.php/t-4418.html](http://osx86.co/archive/index.php/t-4418.html)

Please do not follow that guy and flash your mobo. Just use it for windows unless you really want linux. Your mobo might stop working properly

Linux support standard conforming motherboards. If it is nonconforming, then Linux will not be able to use the features properly.

It a hardware problem not Linux

I will say use Windows, because the motherboard is not properly tested again acpi standard

Here are the boot parameters Doc
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
```

    acpi=        [HW,ACPI,X86]             Advanced Configuration and Power Interface             Format: { force | off | strict | noirq | rsdt }             force -- enable ACPI if default was off             off -- disable ACPI if default was on             noirq -- do not use ACPI for IRQ routing             strict -- Be less tolerant of platforms that are not                 strictly ACPI specification compliant.             rsdt -- prefer RSDT over (default) XSDT             copy_dsdt -- copy DSDT to memory              See also Documentation/power/pm.txt, pci=noacpi
```Remember. Kernel Developers do not necessary have your hardware setup, so it is difficult for them to test it

---

### Post by TrueAncalagon on 2012-10-28
So the problem is mi mobo? But my pc run 90% of the time linux and the rest windows... if my mobo have some problem is there a way to fix it or to disable some function on linux to run normaly the system?

---

