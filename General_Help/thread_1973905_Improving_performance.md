---
title: "Improving performance?"
date: 2012-05-05
forum: General Help
---

### Post by tiffy1 on 2012-05-05
This is my startup list and my running processes. What can I safely disable on my laptop to reduce battery usage and increase performance?

```
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
4 S root         1     0  0  80   0 -   713 poll_s May04 ?        00:00:02 /sbin/init
1 S root         2     0  0  80   0 -     0 kthrea May04 ?        00:00:00 [kthreadd]
1 S root         3     2  0  80   0 -     0 run_ks May04 ?        00:00:01 [ksoftirqd/0]
1 S root         6     2  0 -40   - -     0 cpu_st May04 ?        00:00:00 [migration/0]
5 S root         7     2  0 -40   - -     0 watchd May04 ?        00:00:00 [watchdog/0]
1 S root        13     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [cpuset]
1 S root        14     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [khelper]
5 S root        15     2  0  80   0 -     0 devtmp May04 ?        00:00:00 [kdevtmpfs]
1 S root        16     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [netns]
1 S root        17     2  0  80   0 -     0 bdi_sy May04 ?        00:00:00 [sync_supers]
1 S root        18     2  0  80   0 -     0 bdi_fo May04 ?        00:00:00 [bdi-default]
1 S root        19     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [kintegrityd]
1 S root        20     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [kblockd]
1 S root        21     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [ata_sff]
1 S root        22     2  0  80   0 -     0 hub_th May04 ?        00:00:00 [khubd]
1 S root        23     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [md]
1 S root        25     2  0  80   0 -     0 watchd May04 ?        00:00:00 [khungtaskd]
1 S root        26     2  0  80   0 -     0 kswapd May04 ?        00:00:08 [kswapd0]
1 S root        27     2  0  85   5 -     0 ksm_sc May04 ?        00:00:00 [ksmd]
1 S root        28     2  0  99  19 -     0 khugep May04 ?        00:00:00 [khugepaged]
1 S root        29     2  0  80   0 -     0 fsnoti May04 ?        00:00:00 [fsnotify_mark]
1 S root        30     2  0  80   0 -     0 ecrypt May04 ?        00:00:00 [ecryptfs-kthrea]
1 S root        31     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [crypto]
1 S root        39     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [kthrotld]
1 S root        41     2  0  80   0 -     0 scsi_e May04 ?        00:00:00 [scsi_eh_0]
1 S root        42     2  0  80   0 -     0 scsi_e May04 ?        00:00:00 [scsi_eh_1]
1 S root        43     2  0  80   0 -     0 scsi_e May04 ?        00:00:00 [scsi_eh_2]
1 S root        44     2  0  80   0 -     0 scsi_e May04 ?        00:00:00 [scsi_eh_3]
1 S root        67     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [devfreq_wq]
1 S root       218     2  0  80   0 -     0 scsi_e May04 ?        00:00:00 [scsi_eh_4]
1 S root       219     2  0  80   0 -     0 usb_st May04 ?        00:00:01 [usb-storage]
1 S root       273     2  0  80   0 -     0 kjourn May04 ?        00:00:02 [jbd2/sda1-8]
1 S root       274     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [ext4-dio-unwrit]
1 S root       316     1  0  80   0 -   591 poll_s May04 ?        00:00:00 upstart-udev-bridge --daemon
5 S root       321     1  0  76  -4 -   672 poll_s May04 ?        00:00:00 udevd --daemon
1 S root       497     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [kpsmoused]
1 S root       551     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [cfg80211]
1 S root       554     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [led_workqueue]
1 S root       704     2  0  60 -20 -     0 rescue May04 ?        00:00:00 [hd-audio0]
5 S syslog     785     1  0  80   0 -  7111 poll_s May04 ?        00:00:00 rsyslogd -c4
5 S 104        852     1  0  80   0 -   801 poll_s May04 ?        00:00:39 dbus-daemon --system --fork
1 S root       881     2  0  80   0 -     0 bdi_wr May04 ?        00:00:03 [flush-8:0]
0 S root       966     1  0  80   0 -   460 n_tty_ May04 tty4     00:00:00 /sbin/getty -8 38400 tty4
0 S root       970     1  0  80   0 -   460 n_tty_ May04 tty5     00:00:00 /sbin/getty -8 38400 tty5
0 S root       976     1  0  80   0 -   460 n_tty_ May04 tty2     00:00:00 /sbin/getty -8 38400 tty2
0 S root       977     1  0  80   0 -   460 n_tty_ May04 tty3     00:00:00 /sbin/getty -8 38400 tty3
0 S root       979     1  0  80   0 -   460 n_tty_ May04 tty6     00:00:00 /sbin/getty -8 38400 tty6
1 S daemon     991     1  0  80   0 -   574 restar May04 ?        00:00:00 atd
4 S root      1016     1  0  80   0 -  4705 poll_s May04 ?        00:00:00 /usr/sbin/console-kit-daemon --no-daemon
0 S postgres  1088     1  0  80   0 - 10072 poll_s May04 ?        00:00:00 /opt/metasploit/postgresql/bin/postgres -D /opt/metasploit/postgresql/data -p 7337
1 S postgres  1097  1088  0  80   0 - 10072 poll_s May04 ?        00:00:03 postgres: writer process                                                          
1 S postgres  1098  1088  0  80   0 - 10072 poll_s May04 ?        00:00:02 postgres: wal writer process                                                      
1 S postgres  1099  1088  0  80   0 - 10137 poll_s May04 ?        00:00:00 postgres: autovacuum launcher process                                             
1 S postgres  1100  1088  0  80   0 -  2148 poll_s May04 ?        00:00:01 postgres: stats collector process                                                 
4 S root      1138     1  0  80   0 -  1367 wait   May04 tty1     00:00:00 /bin/login --     
4 S root      1168  1138  0  80   0 -  1160 wait   May04 tty1     00:00:00 -bash
1 S root      1193     1  0  80   0 -   571 poll_s May04 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
1 S root      1257     1  0  80   0 -   571 poll_s May04 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
0 S root      1318  1168  0  80   0 -  1070 wait   May04 tty1     00:00:00 /bin/bash /usr/bin/startx
4 S root      1335  1318  0  80   0 -   777 wait   May04 tty1     00:00:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc :0 -auth /tmp/serverauth.WyuZXX8xzE
4 S root      1336  1335  1  79  -1 - 13422 poll_s May04 tty7     00:16:53 /usr/bin/X -nolisten tcp :0 -auth /tmp/serverauth.WyuZXX8xzE
4 S root      1351  1335  0  80   0 -   899 wait   May04 tty1     00:00:00 /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session x-session-manager
1 S root      1385  1351  0  80   0 -   833 poll_s May04 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session x-session-manager
0 S root      1394  1351  0  80   0 -  1071 wait   May04 tty1     00:00:00 /bin/sh /usr/bin/x-session-manager
1 S root      1397     1  0  80   0 -   858 poll_s May04 tty1     00:00:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
1 S root      1398     1  0  80   0 -   874 poll_s May04 ?        00:00:07 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
1 S root      1437     1  0  80   0 -   417 pipe_w May04 tty1     00:00:00 /usr/lib/kde4/libexec/start_kdeinit +kcminit_startup
1 S root      1438     1  0  80   0 - 17881 poll_s May04 ?        00:00:00 kdeinit4: kdeinit4 Running...                  
0 S root      1439  1438  0  80   0 - 10436 poll_s May04 ?        00:00:00 klauncher --fd=9
1 S root      1441     1  0  80   0 - 33034 poll_s May04 ?        00:00:11 kdeinit4: kded4 [kdeinit]                      
1 S root      1445     1  0  80   0 - 18805 poll_s May04 ?        00:00:01 /usr/bin/kglobalaccel
5 S 109       1450     1  0  80   0 -  3705 poll_s May04 ?        00:00:04 /usr/sbin/hald
0 S root      1451  1450  0  80   0 -   896 poll_s May04 ?        00:00:00 hald-runner
0 S root      1454  1394  0  80   0 -   451 unix_s May04 tty1     00:00:00 kwrapper4 ksmserver
0 S root      1456  1438  0  80   0 - 28729 poll_s May04 ?        00:00:00 ksmserver
4 S root      1477  1456  0  80   0 - 55371 poll_s May04 ?        00:07:08 kwin -session 10627400000129830255900000176850000_1300473552_918262
0 S root      1478  1451  0  80   0 -   915 poll_s May04 ?        00:00:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event6 /dev/input/event5 /dev/input/event1 /dev/input/event2 /dev/input/event9 /dev/input/event3 /dev/input/event0 /dev/input/event8
0 S root      1480  1451  0  80   0 -   914 poll_s May04 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight
0 S root      1482  1451  0  80   0 -   915 poll_s May04 ?        00:00:00 /usr/lib/hal/hald-addon-rfkill-killswitch
0 S root      1519  1451  0  80   0 -   916 poll_s May04 ?        00:00:01 hald-addon-storage: polling /dev/sdb (every 2 sec)
0 S root      1527  1451  0  80   0 -   918 poll_s May04 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
4 S 109       1528  1451  0  80   0 -   867 acpi_b May04 ?        00:00:00 hald-addon-acpi: listening on acpi kernel interface /proc/acpi/event
5 S root      1570     1  0  80   0 - 43396 poll_s May04 ?        00:00:06 /usr/bin/knotify4
5 S root      1572     1  0  80   0 - 64633 poll_s May04 ?        00:03:22 /usr/bin/plasma-desktop
1 S root      1592     1  0  80   0 - 18770 poll_s May04 ?        00:00:00 /usr/bin/kuiserver
1 S root      1653     1  0  80   0 - 19333 poll_s May04 ?        00:00:01 /usr/bin/kaccess
5 S root      1661     1  0  80   0 - 54835 poll_s May04 ?        00:00:11 /usr/bin/krunner
1 S root      1662     1  0  80   0 - 19029 poll_s May04 ?        00:00:00 /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1 -session 10627400000129830256100000176850006_1300473552_907562
1 S root      1667     1  0  80   0 - 48113 poll_s May04 ?        00:00:03 /usr/bin/kmix
4 S root      1670     1  0  80   0 -  1581 poll_s May04 ?        00:00:00 /usr/lib/policykit-1/polkitd
1 S root      1671     1  0  80   0 - 18729 poll_s May04 ?        00:00:00 /usr/bin/klipper
5 S root      2289     1  0  80   0 -  5900 poll_s May04 ?        00:00:55 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
0 S root      2294  2289  0  80   0 -  3271 poll_s May04 ?        00:00:25 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
0 S root      2298     1  0  80   0 -  1607 poll_s May04 ?        00:00:00 /usr/lib/gvfs/gvfsd
0 S root      2402  1438  0  80   0 - 10225 poll_s May04 ?        00:00:01 /usr/lib/kde4/libexec/kio_http_cache_cleaner
1 S root      2407     1  0  80   0 - 18764 poll_s May04 ?        00:00:00 /usr/bin/kwalletd
0 S root      7822     1  0  80   0 -  8363 poll_s 01:45 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
4 S root      7826     1  0  80   0 -  3416 poll_s 01:45 ?        00:00:00 /usr/lib/udisks/udisks-daemon
1 S root      7827  7826  0  80   0 -  1309 poll_s 01:45 ?        00:00:00 udisks-daemon: polling /dev/sdb
0 S root      7829     1  0  80   0 -  4251 poll_s 01:45 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
0 S root      7832     1  0  80   0 -  1827 poll_s 01:45 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1 S root     15626     1  0  80   0 -   605 hrtime 01:52 ?        00:00:00 cron
0 S root     15996  1438  0  80   0 - 18690 poll_s 01:56 ?        00:00:00 kcmshell4 powerdevilconfig
1 S root     16297     1  0  80   0 -  3272 poll_s 01:58 ?        00:00:00 /usr/sbin/winbindd
1 S root     16299 16297  0  80   0 -  3272 poll_s 01:58 ?        00:00:00 /usr/sbin/winbindd
1 S root     17673     2  0  80   0 -     0 worker 02:18 ?        00:00:00 [kworker/u:2]
1 S root     18326     2  0  80   0 -     0 worker 02:23 ?        00:00:00 [kworker/0:0]
1 S root     18776     2  0  80   0 -     0 worker 02:24 ?        00:00:00 [kworker/u:1]
1 S root     19379     2  0  80   0 -     0 worker 02:28 ?        00:00:00 [kworker/0:1]
1 S root     19783     2  0  80   0 -     0 worker 02:34 ?        00:00:00 [kworker/0:2]
1 S root     19997     2  0  80   0 -     0 bdi_wr 02:35 ?        00:00:00 [flush-8:16]
1 S root     19998     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:0]
1 S root     19999     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:3]
1 S root     20000     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:4]
1 S root     20001     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:5]
1 S root     20002     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:6]
1 S root     20003     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:7]
1 S root     20004     2  0  80   0 -     0 worker 02:35 ?        00:00:00 [kworker/u:8]
1 S root     20007     2  0 -40   - -     0 cpu_st 10:54 ?        00:00:00 [migration/1]
1 S root     20008     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/1:4]
1 S root     20009     2  0  80   0 -     0 run_ks 10:54 ?        00:00:00 [ksoftirqd/1]
5 S root     20010     2  0 -40   - -     0 watchd 10:54 ?        00:00:00 [watchdog/1]
1 S root     20011     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/1:0]
1 S root     20012     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:9]
1 S root     20013     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:10]
1 S root     20014     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:11]
1 S root     20015     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:12]
1 S root     20016     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:13]
1 S root     20017     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:14]
1 S root     20018     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:15]
1 S root     20019     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:16]
1 S root     20020     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:17]
1 S root     20021     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:18]
1 S root     20022     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:19]
1 S root     20023     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:20]
1 S root     20024     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:21]
1 S root     20025     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:22]
1 S root     20026     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:23]
1 S root     20027     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:24]
1 S root     20028     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:25]
1 S root     20029     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:26]
1 S root     20030     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:27]
1 S root     20031     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:28]
1 S root     20032     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:29]
1 S root     20033     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:30]
1 S root     20034     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:31]
1 S root     20035     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:32]
1 S root     20036     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:33]
1 S root     20037     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:34]
1 S root     20038     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:35]
1 S root     20039     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:36]
1 S root     20040     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:37]
1 S root     20041     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:38]
1 S root     20042     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/u:39]
1 S root     20043     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/0:3]
1 S root     20044     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/0:4]
1 S root     20045     2  0  80   0 -     0 worker 10:54 ?        00:00:00 [kworker/1:1]
5 S root     20050   321  0  78  -2 -   671 poll_s 10:54 ?        00:00:00 udevd --daemon
5 S root     20051   321  0  78  -2 -   671 poll_s 10:54 ?        00:00:00 udevd --daemon
4 S root     20075     1  0  80   0 -  6871 poll_s 10:54 ?        00:00:00 /usr/sbin/packagekitd
5 S root     20294     1  0  80   0 -  1222 poll_s 10:54 ?        00:00:00 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/944452529c24 -D wext
4 Z root     20301  2289  0  80   0 -     0 exit   10:54 ?        00:00:00 [dhclient] <defunct>
1 S root     20320     1  0  80   0 -   570 poll_s 10:54 ?        00:00:00 /sbin/dhclient -cf /var/lib/wicd/dhclient.conf wlan0
5 S root     20326     1  3  80   0 - 24997 poll_s 10:54 ?        00:00:01 /usr/bin/konsole
0 S root     20331 20326  0  80   0 -  1155 wait   10:54 pts/1    00:00:00 /bin/bash
0 S root     20354  1438 16  80   0 - 21781 poll_s 10:54 ?        00:00:02 /usr/bin/kwrite /media/BT5R2BOOT/Text File
4 R root     20365 20331  0  80   0 -   690 -      10:55 pts/1    00:00:00 ps -leadf

alsa-mixer-save             off
apache2                     on
apparmor                    on
apport                      off
atd                         off
avahi-daemon                off
binfmt-support              off
bootlogd                    off
bridge-network-interface    off
casper                      0
console-setup               off
cron                        off
cryptdisks                  0
cryptdisks-early            0
cryptdisks-enable           off
cryptdisks-udev             off
cups                        off
dbus                        off
decnet                      off
dmesg                       off
dns-clean                   on
ecryptfs-utils-restore      off
ecryptfs-utils-save         off
failsafe-x                  off
fancontrol                  on
farpd                       off
framework-postgres          2345
gpsd                        off
grub-common                 on
gssd                        off
hostname                    off
hwclock                     off
hwclock-save                off
idmapd                      off
irqbalance                  off
kdm                         off
killprocs                   on
lm-sensors                  on
metasploit-postgres         2345
module-init-tools           off
mysql                       off
network-interface           off
network-interface-security  off
networking                  off
ondemand                    on
openbsd-inetd               off
openvpn                     off
pcmciautils                 on
pcscd                       off
plymouth                    off
plymouth-log                off
plymouth-splash             off
plymouth-stop               off
portmap                     off
portmap-boot                off
portmap-wait                off
pppd-dns                    on
procps                      off
pure-ftpd                   off
rc.local                    on
rcS                         off
rinetd                      off
rsync                       on
rsyslog                     off
screen-cleanup              off
sendsigs                    0
snort                       off
ssh                         off
start-ypbind                off
statd                       off
statd-mounting              off
stop-bootlogd               off
stop-bootlogd-single        off
udev                        off
udev-finish                 off
udevmonitor                 off
udevtrigger                 off
ufw                         off
umountfs                    0
umountnfs.sh                0
umountroot                  0
unattended-upgrades         0
urandom                     0S
wicd                        off
winbind                     on
wpa-ifupdown                0
x11-common                  on
xplico                      off
ypbind                      off
yppasswdd                   off
ypserv                      off
ypxfrd                      off
```

---

### Post by hal8000 on 2012-05-05
This is just a start for you:

[http://www.addictivetips.com/ubuntu-linux-tips/manage-ubuntu-services-with-boot-up-manager/](http://www.addictivetips.com/ubuntu-linux-tips/manage-ubuntu-services-with-boot-up-manager/)

Load boot-up-manager.

If you dont have bluetooth, then dont load bluetooth services.
If you use an external router with builtin firewall, and are happy then you may decide to stop apparmour from loading, etc.

For each service in the list, you need to use google.
Hopefully someone may provide a better link or blog to someone who has streamlined their startup services.

---

