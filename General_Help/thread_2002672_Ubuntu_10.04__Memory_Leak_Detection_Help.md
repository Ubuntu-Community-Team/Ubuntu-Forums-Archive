---
title: "Ubuntu 10.04 :: Memory Leak Detection Help"
date: 2012-06-13
forum: General Help
---

### Post by own3mall on 2012-06-13
Hi All,

I've noticed that my server's memory usage continues to climb over the days.  When the system first boots, only 1GB of RAM is being used.  However, as days pass, the memory usage gets higher.  Also, I cannot determine which application is using the memory, as top does not show it.

Here's some information regarding the running processes along with what top shows:

ps -ef:

```

JohnDoe@dns4:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun06 ?        00:00:03 /sbin/init
root         2     0  0 Jun06 ?        00:00:00 [kthreadd]
root         3     2  0 Jun06 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 Jun06 ?        00:00:00 [kworker/0:0]
root         6     2  0 Jun06 ?        00:00:00 [migration/0]
root         7     2  0 Jun06 ?        00:00:00 [migration/1]
root         8     2  0 Jun06 ?        00:00:00 [kworker/1:0]
root         9     2  0 Jun06 ?        00:00:00 [ksoftirqd/1]
root        10     2  0 Jun06 ?        00:01:58 [kworker/0:1]
root        11     2  0 Jun06 ?        00:00:00 [migration/2]
root        13     2  0 Jun06 ?        00:00:00 [ksoftirqd/2]
root        14     2  0 Jun06 ?        00:00:00 [migration/3]
root        16     2  0 Jun06 ?        00:00:00 [ksoftirqd/3]
root        17     2  0 Jun06 ?        00:00:00 [cpuset]
root        18     2  0 Jun06 ?        00:00:00 [khelper]
root        19     2  0 Jun06 ?        00:00:00 [kdevtmpfs]
root        20     2  0 Jun06 ?        00:00:00 [netns]
root        21     2  0 Jun06 ?        00:00:01 [sync_supers]
root        22     2  0 Jun06 ?        00:00:00 [bdi-default]
root        23     2  0 Jun06 ?        00:00:00 [kintegrityd]
root        24     2  0 Jun06 ?        00:00:00 [kblockd]
root        25     2  0 Jun06 ?        00:00:00 [ata_sff]
root        26     2  0 Jun06 ?        00:00:00 [khubd]
root        27     2  0 Jun06 ?        00:00:00 [md]
root        28     2  0 Jun06 ?        00:01:23 [kworker/1:1]
root        30     2  0 Jun06 ?        00:00:48 [kworker/3:1]
root        31     2  0 Jun06 ?        00:00:00 [khungtaskd]
root        32     2  0 Jun06 ?        00:00:10 [kswapd0]
root        33     2  0 Jun06 ?        00:00:00 [ksmd]
root        34     2  0 Jun06 ?        00:00:00 [fsnotify_mark]
root        35     2  0 Jun06 ?        00:00:00 [ecryptfs-kthrea]
root        36     2  0 Jun06 ?        00:00:00 [crypto]
root        40     2  0 Jun06 ?        00:00:00 [kmpathd]
root        41     2  0 Jun06 ?        00:00:00 [kmpath_handlerd]
root       143     2  0 Jun06 ?        00:00:00 [scsi_eh_0]
root       150     2  0 Jun06 ?        00:00:00 [scsi_eh_1]
root       160     2  0 Jun06 ?        00:00:00 [kworker/u:2]
root       162     2  0 Jun06 ?        00:00:00 [scsi_eh_2]
root       165     2  0 Jun06 ?        00:00:00 [scsi_eh_3]
root       176     2  0 Jun06 ?        00:00:00 [scsi_eh_4]
root       183     2  0 Jun06 ?        00:00:00 [scsi_eh_5]
root       208     2  0 Jun06 ?        00:00:00 [kworker/u:5]
root       275     2  0 Jun06 ?        00:00:42 [jbd2/sda6-8]
root       276     2  0 Jun06 ?        00:00:00 [ext4-dio-unwrit]
JohnDoe       300 32766  4 Jun09 pts/1    04:43:00 ./mohaa_lnxded +set dedicated 1
root       318     1  0 Jun06 ?        00:00:00 upstart-udev-bridge --daemon
root       323     1  0 Jun06 ?        00:00:00 udevd --daemon
JohnDoe       373     1  0 Jun09 ?        00:00:02 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       375   373  1 Jun09 pts/2    01:50:50 ./mohaa_lnxded +set dedicated 1
nx         453 31839  0 23:13 ?        00:00:00 netcat 127.0.0.1 6000
JohnDoe       459     1  0 Jun09 ?        00:00:03 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       461   459  1 Jun09 pts/3    01:35:19 ./mohaa_lnxded +set dedicated 1
nx         515 32645  0 23:13 ?        00:00:00 python /usr/bin/nx-session-launc
root       533   323  0 Jun06 ?        00:00:00 udevd --daemon
root       534   323  0 Jun06 ?        00:00:00 udevd --daemon
JohnDoe       551     1  0 Jun09 ?        00:00:14 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       553   551  3 Jun09 pts/4    02:52:56 ./mohaa_lnxded +set dedicated 1
root       573     2  0 Jun06 ?        00:00:00 [kpsmoused]
root       582     1  0 Jun06 ?        00:00:04 smbd -F
root       589     1  0 Jun06 ?        00:00:00 /usr/sbin/sshd -D
JohnDoe       593   515  0 23:13 ?        00:00:00 /usr/bin/ck-launch-session /usr/
syslog     603     1  0 Jun06 ?        00:00:23 rsyslogd -c4
root       608     2  0 Jun06 ?        00:00:00 [hd-audio0]
JohnDoe       624   593  0 23:13 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/ck-l
JohnDoe       633   593  0 23:13 ?        00:00:00 gnome-session
JohnDoe       636     1  0 23:13 ?        00:00:00 /usr/bin/dbus-launch --exit-with
JohnDoe       637     1  0 23:13 ?        00:00:00 /bin/dbus-daemon --fork --print-
JohnDoe       642     1  0 23:13 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
JohnDoe       648     1  0 23:13 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
JohnDoe       649     1  0 23:13 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
JohnDoe       653     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfsd
JohnDoe       657   633  0 23:13 ?        00:00:00 nm-applet --sm-disable
JohnDoe       658   633  0 23:13 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
JohnDoe       659   633  0 23:13 ?        00:00:00 metacity --replace
JohnDoe       661   633  0 23:13 ?        00:00:00 gnome-panel
JohnDoe       662   633  0 23:13 ?        00:00:00 nautilus
JohnDoe       663   633  0 23:13 ?        00:00:01 /usr/lib/vino/vino-server --sm-d
JohnDoe       664   633  0 23:13 ?        00:00:00 gnome-power-manager
JohnDoe       670     1  0 23:13 ?        00:00:00 /usr/bin/pulseaudio --start --lo
JohnDoe       672   670  0 23:13 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
JohnDoe       678     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
JohnDoe       681     1  0 23:13 ?        00:00:00 /usr/lib/bonobo-activation/bonob
JohnDoe       686     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
JohnDoe       693     1  0 23:13 ?        00:00:00 /usr/lib/gnome-panel/wnck-applet
JohnDoe       697     1  0 23:13 ?        00:00:00 /usr/lib/lunar-applet/lunar-appl
JohnDoe       701     1  0 23:13 ?        00:00:00 /usr/lib/indicator-applet/indica
JohnDoe       703     1  0 23:13 ?        00:00:00 /usr/lib/gnome-panel/notificatio
JohnDoe       705     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
JohnDoe       707     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
root       710   582  0 Jun06 ?        00:00:00 smbd -F
102        711     1  0 Jun06 ?        00:00:00 dbus-daemon --system --fork
JohnDoe       718     1  0 23:14 ?        00:00:00 gnome-screensaver
JohnDoe       720     1  0 23:14 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
JohnDoe       723     1  0 23:14 ?        00:00:00 /usr/lib/indicator-application/i
JohnDoe       725     1  0 23:14 ?        00:00:00 /usr/lib/indicator-sound/indicat
JohnDoe       727     1  0 23:14 ?        00:00:00 /usr/lib/indicator-messages/indi
JohnDoe       729     1  0 23:14 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
root       732     2  0 Jun06 ?        00:00:21 [flush-8:0]
JohnDoe       742   633  0 23:14 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-
avahi      753     1  0 Jun06 ?        00:00:00 avahi-daemon: running [dns4.loca
avahi      754   753  0 Jun06 ?        00:00:00 avahi-daemon: chroot helper
root       757     1  0 Jun06 ?        00:00:00 NetworkManager
root       759     1  0 Jun06 ?        00:00:00 /usr/sbin/modem-manager
root       761     1  0 Jun06 ?        00:00:00 /usr/sbin/console-kit-daemon --n
JohnDoe       769     1  6 23:14 ?        00:00:06 /usr/bin/python2.6 /usr/bin/upda
root       827     1  0 Jun06 ?        00:00:00 /sbin/wpa_supplicant -u -s
JohnDoe       831   633  0 23:14 ?        00:00:00 update-notifier
root       836     1  0 23:14 ?        00:00:00 /usr/bin/python /usr/lib/system-
root       838     1  0 23:14 ?        00:00:00 /usr/bin/python /usr/sbin/aptd
postfix    852  2069  0 23:15 ?        00:00:00 cleanup -z -t unix -u -c
postfix    853  2069  0 23:15 ?        00:00:00 proxymap -t unix -u
postfix    854  2069  0 23:15 ?        00:00:00 trivial-rewrite -n rewrite -t un
postfix    855  2069  0 23:15 ?        00:00:00 smtp -t unix -u -c
postfix    862  2069  0 23:15 ?        00:00:00 bounce -z -t unix -u -c
JohnDoe       907   769  0 23:15 ?        00:00:00 /usr/bin/gksu --desktop /usr/sha
root       908   907  6 23:15 ?        00:00:02 /usr/sbin/synaptic --hide-main-w
root       916   908  0 23:15 pts/6    00:00:00 /usr/sbin/synaptic --hide-main-w
root       923     1  0 Jun06 ?        00:00:00 /usr/sbin/vsftpd
root       926     1  0 23:15 pts/6    00:00:00 dbus-launch --autolaunch 4bc7c8f
root       927     1  0 23:15 ?        00:00:00 /bin/dbus-daemon --fork --print-
root       929     1  0 Jun06 ?        00:00:05 nmbd -D
root       930     1  0 23:15 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
root       974     1  0 Jun06 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       976     1  0 Jun06 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1000     1  0 Jun06 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1003     1  0 Jun06 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1019     1  0 Jun06 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root      1027     1  0 Jun06 ?        00:00:01 cron
daemon    1034     1  0 Jun06 ?        00:00:00 atd
bind      1162     1  0 Jun06 ?        00:00:00 /usr/sbin/named -u bind
root      1182     1  0 Jun06 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1329  2361  0 23:15 ?        00:00:00 sleep 20
amavis    1420     1  0 Jun06 ?        00:00:06 amavisd (master)
amavis    1472  1420  0 Jun06 ?        00:00:00 amavisd (virgin child)
amavis    1473  1420  0 Jun06 ?        00:00:00 amavisd (virgin child)
root      1540   916  0 23:16 pts/7    00:00:00 /usr/bin/dpkg --status-fd 34 --c
root      1550  1540  3 23:16 pts/7    00:00:00 /usr/bin/perl -w /usr/share/debc
root      1562  1550  0 23:16 pts/7    00:00:00 /bin/bash -e /var/lib/dpkg/info/
JohnDoe      1640     1  5 23:16 ?        00:00:00 gnome-terminal
JohnDoe      1641  1640  0 23:16 ?        00:00:00 gnome-pty-helper
JohnDoe      1642  1640  6 23:16 pts/8    00:00:00 bash
mysql     1663  1562  4 23:16 pts/7    00:00:00 /usr/sbin/mysqld --bootstrap --u
JohnDoe      1677  1642  0 23:16 pts/8    00:00:00 ps -ef
clamav    1727     1  0 Jun06 ?        00:00:05 /usr/sbin/clamd
clamav    1832     1  0 Jun06 ?        00:01:02 /usr/bin/freshclam -d --quiet
root      1845     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1846  1845  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1849  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1850  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1851  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1852  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1853  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1866     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1867  1866  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
root      1886     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1887  1886  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
root      1900     1  0 Jun06 ?        00:00:01 /usr/sbin/courierlogger -pid=/va
root      1901  1900  0 Jun06 ?        00:00:03 /usr/sbin/couriertcpd -maxprocs=
root      1920     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1921  1920  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
JohnDoe      1954     1  0 Jun06 ?        00:00:02 SCREEN -d -m -t ogp_agent -c ogp
JohnDoe      1961  1954  0 Jun06 pts/0    00:00:01 /usr/bin/perl ./ogp_agent.pl
root      1963     1  0 Jun06 ?        00:02:12 /usr/bin/php5-fpm --fpm-config /
www-data  1964  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1965  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1966  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1967  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1968  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1969  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1970  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1971  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1972  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1973  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
root      1976     1  0 Jun06 ?        00:00:20 /usr/bin/perl -wT /usr/sbin/pop-
root      2069     1  0 Jun06 ?        00:00:11 /usr/lib/postfix/master
postfix   2074  2069  0 Jun06 ?        00:00:04 qmgr -l -t fifo -u
root      2101     1  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2102  2101  0 Jun06 ?        00:00:30 /usr/sbin/saslauthd -a pam -m /v
root      2103  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2105  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2106  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2120     1  0 Jun06 ?        00:00:01 /usr/sbin/winbindd
root      2143     1  0 Jun06 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root      2144  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
root      2190     1  0 Jun06 ?        00:00:16 /usr/sbin/apache2 -k start
117       2205     1  0 Jun06 ?        00:00:04 /usr/sbin/murmurd -ini /etc/mumb
root      2361     1  0 Jun06 ?        00:00:00 /bin/bash /var/www/new/ehcp/ehcp
root      2372     1  0 Jun06 tty1     00:00:00 /sbin/getty -8 38400 tty1
postfix   2668  2069  0 Jun06 ?        00:00:01 tlsmgr -l -t unix -u -c
root      4003     1  0 Jun06 ?        00:00:00 /usr/lib/policykit-1/polkitd
rtkit     4012     1  0 Jun06 ?        00:00:06 /usr/lib/rtkit/rtkit-daemon
root      4018     1  0 Jun06 ?        00:00:00 /usr/lib/upower/upowerd
107       4057     1  0 Jun06 ?        00:00:04 /usr/sbin/hald
root      4058  4057  0 Jun06 ?        00:00:00 hald-runner
root      4085  4058  0 Jun06 ?        00:00:00 hald-addon-input: Listening on /
root      4096     2  0 Jun06 ?        00:00:00 [kworker/3:2]
root      4104  4058  0 Jun06 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       4105  4058  0 Jun06 ?        00:00:00 hald-addon-acpi: listening on ac
root      4116     1  0 Jun06 ?        00:00:09 /usr/lib/udisks/udisks-daemon
root      4117  4116  0 Jun06 ?        00:00:00 udisks-daemon: not polling any d
root      4984  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
root      5001  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
www-data 11473  2190  0 Jun10 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 13876  2190  0 Jun10 ?        00:00:00 /usr/sbin/apache2 -k start
root     16704     2  0 Jun11 ?        00:00:23 [kworker/2:2]
root     25531     2  0 02:00 ?        00:00:14 [kworker/2:1]
www-data 25824  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25825  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25826  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25828  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25829  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25831  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25833  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25834  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
root     28107     1  0 07:25 ?        00:00:10 /usr/sbin/spamd --create-prefs -
root     28111 28107  0 07:25 ?        00:00:00 spamd child
root     28112 28107  0 07:25 ?        00:00:00 spamd child
root     31330   582  0 21:18 ?        00:00:00 smbd -F
postfix  31771  2069  0 23:13 ?        00:00:00 pickup -l -t fifo -u -c -o conte
root     31772   589  0 23:13 ?        00:00:00 sshd: nx [priv]     
nx       31838 31772  0 23:13 ?        00:00:00 sshd: nx@notty      
nx       31839 31838  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32003 31839  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32004 32003  0 23:13 ?        00:00:00 /usr/bin/expect /usr/lib/nx/nxno
nx       32006 32004  0 23:13 pts/5    00:00:00 ssh -2 -x -l JohnDoe 127.0.0.1 -o N
root     32011   589  0 23:13 ?        00:00:00 sshd: JohnDoe [priv]   
JohnDoe     32073 32011  0 23:13 ?        00:00:00 sshd: JohnDoe@notty    
JohnDoe     32074 32073  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
nx       32373 31839  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32376 32373  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32377 32373  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32383 32376  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32384 32376  0 23:13 ?        00:00:00 tee -a /var/log/nxserver.log
JohnDoe     32385 32074  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32387 32385  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32640 32387  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32645 32387  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32648 32640  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32649 32640  0 23:13 ?        00:00:00 tee /home/JohnDoe/.nx/
JohnDoe     32650 32640  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32700 32648  8 23:13 ?        00:00:11 /usr/bin/nxagent -persistent -D
JohnDoe     32766     1  0 Jun09 ?        00:00:04 SCREEN -d -m -t OGP_HOME_0000000


```

Top:

```

JohnDoe@dns4:~$ top

top - 23:17:54 up 6 days,  1:50,  2 users,  load average: 0.22, 0.26, 0.15
Tasks: 229 total,   2 running, 227 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7%us,  2.9%sy,  0.0%ni, 93.3%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   4062848k total,  3875964k used,   186884k free,    97540k buffers
Swap: 14647292k total,    11368k used, 14635924k free,  1764476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                       
  553 JohnDoe      20   0  219m 210m 3244 R    5  5.3 173:02.31 mohaa_lnxded                                                                  
32700 JohnDoe      20   0 90460  53m  10m S    4  1.4   0:19.86 nxagent                                                                       
 1640 JohnDoe      20   0 44940  12m 9976 S    4  0.3   0:01.91 gnome-terminal                                                                
  300 JohnDoe      20   0  231m 220m 1916 S    2  5.6 283:02.01 mohaa_lnxded                                                                  
  461 JohnDoe      20   0  276m 265m 3216 S    2  6.7  95:20.76 mohaa_lnxded                                                                  
  375 JohnDoe      20   0  196m 186m 3140 S    1  4.7 110:52.01 mohaa_lnxded                                                                  
  648 JohnDoe      20   0 88844 9048 6948 S    0  0.2   0:00.34 gnome-settings-                                                               
 2247 JohnDoe      20   0  2592 1164  828 R    0  0.0   0:00.09 top                                                                           
    1 root      20   0  2844 1552 1164 S    0  0.0   0:03.22 init                                                                          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/0                                                                   
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0                                                                   
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                   
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                   
    8 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0                                                                   
    9 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1                                                                   
   10 root      20   0     0    0    0 S    0  0.0   1:58.41 kworker/0:1                                                                   


```

Any ideas what might be causing this?  How should I troubleshoot this further to determine the cause?

Please let me know.  Any help is appreciated.

---

### Post by idoitprone on 2012-06-13
> **own3mall said:**
> Hi All,

I've noticed that my server's memory usage continues to climb over the days.  When the system first boots, only 1GB of RAM is being used.  However, as days pass, the memory usage gets higher.  Also, I cannot determine which application is using the memory, as top does not show it.

Here's some information regarding the running processes along with what top shows:

ps -ef:

```

JohnDoe@dns4:~$ ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Jun06 ?        00:00:03 /sbin/init
root         2     0  0 Jun06 ?        00:00:00 [kthreadd]
root         3     2  0 Jun06 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 Jun06 ?        00:00:00 [kworker/0:0]
root         6     2  0 Jun06 ?        00:00:00 [migration/0]
root         7     2  0 Jun06 ?        00:00:00 [migration/1]
root         8     2  0 Jun06 ?        00:00:00 [kworker/1:0]
root         9     2  0 Jun06 ?        00:00:00 [ksoftirqd/1]
root        10     2  0 Jun06 ?        00:01:58 [kworker/0:1]
root        11     2  0 Jun06 ?        00:00:00 [migration/2]
root        13     2  0 Jun06 ?        00:00:00 [ksoftirqd/2]
root        14     2  0 Jun06 ?        00:00:00 [migration/3]
root        16     2  0 Jun06 ?        00:00:00 [ksoftirqd/3]
root        17     2  0 Jun06 ?        00:00:00 [cpuset]
root        18     2  0 Jun06 ?        00:00:00 [khelper]
root        19     2  0 Jun06 ?        00:00:00 [kdevtmpfs]
root        20     2  0 Jun06 ?        00:00:00 [netns]
root        21     2  0 Jun06 ?        00:00:01 [sync_supers]
root        22     2  0 Jun06 ?        00:00:00 [bdi-default]
root        23     2  0 Jun06 ?        00:00:00 [kintegrityd]
root        24     2  0 Jun06 ?        00:00:00 [kblockd]
root        25     2  0 Jun06 ?        00:00:00 [ata_sff]
root        26     2  0 Jun06 ?        00:00:00 [khubd]
root        27     2  0 Jun06 ?        00:00:00 [md]
root        28     2  0 Jun06 ?        00:01:23 [kworker/1:1]
root        30     2  0 Jun06 ?        00:00:48 [kworker/3:1]
root        31     2  0 Jun06 ?        00:00:00 [khungtaskd]
root        32     2  0 Jun06 ?        00:00:10 [kswapd0]
root        33     2  0 Jun06 ?        00:00:00 [ksmd]
root        34     2  0 Jun06 ?        00:00:00 [fsnotify_mark]
root        35     2  0 Jun06 ?        00:00:00 [ecryptfs-kthrea]
root        36     2  0 Jun06 ?        00:00:00 [crypto]
root        40     2  0 Jun06 ?        00:00:00 [kmpathd]
root        41     2  0 Jun06 ?        00:00:00 [kmpath_handlerd]
root       143     2  0 Jun06 ?        00:00:00 [scsi_eh_0]
root       150     2  0 Jun06 ?        00:00:00 [scsi_eh_1]
root       160     2  0 Jun06 ?        00:00:00 [kworker/u:2]
root       162     2  0 Jun06 ?        00:00:00 [scsi_eh_2]
root       165     2  0 Jun06 ?        00:00:00 [scsi_eh_3]
root       176     2  0 Jun06 ?        00:00:00 [scsi_eh_4]
root       183     2  0 Jun06 ?        00:00:00 [scsi_eh_5]
root       208     2  0 Jun06 ?        00:00:00 [kworker/u:5]
root       275     2  0 Jun06 ?        00:00:42 [jbd2/sda6-8]
root       276     2  0 Jun06 ?        00:00:00 [ext4-dio-unwrit]
JohnDoe       300 32766  4 Jun09 pts/1    04:43:00 ./mohaa_lnxded +set dedicated 1
root       318     1  0 Jun06 ?        00:00:00 upstart-udev-bridge --daemon
root       323     1  0 Jun06 ?        00:00:00 udevd --daemon
JohnDoe       373     1  0 Jun09 ?        00:00:02 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       375   373  1 Jun09 pts/2    01:50:50 ./mohaa_lnxded +set dedicated 1
nx         453 31839  0 23:13 ?        00:00:00 netcat 127.0.0.1 6000
JohnDoe       459     1  0 Jun09 ?        00:00:03 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       461   459  1 Jun09 pts/3    01:35:19 ./mohaa_lnxded +set dedicated 1
nx         515 32645  0 23:13 ?        00:00:00 python /usr/bin/nx-session-launc
root       533   323  0 Jun06 ?        00:00:00 udevd --daemon
root       534   323  0 Jun06 ?        00:00:00 udevd --daemon
JohnDoe       551     1  0 Jun09 ?        00:00:14 SCREEN -d -m -t OGP_HOME_0000000
JohnDoe       553   551  3 Jun09 pts/4    02:52:56 ./mohaa_lnxded +set dedicated 1
root       573     2  0 Jun06 ?        00:00:00 [kpsmoused]
root       582     1  0 Jun06 ?        00:00:04 smbd -F
root       589     1  0 Jun06 ?        00:00:00 /usr/sbin/sshd -D
JohnDoe       593   515  0 23:13 ?        00:00:00 /usr/bin/ck-launch-session /usr/
syslog     603     1  0 Jun06 ?        00:00:23 rsyslogd -c4
root       608     2  0 Jun06 ?        00:00:00 [hd-audio0]
JohnDoe       624   593  0 23:13 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/ck-l
JohnDoe       633   593  0 23:13 ?        00:00:00 gnome-session
JohnDoe       636     1  0 23:13 ?        00:00:00 /usr/bin/dbus-launch --exit-with
JohnDoe       637     1  0 23:13 ?        00:00:00 /bin/dbus-daemon --fork --print-
JohnDoe       642     1  0 23:13 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
JohnDoe       648     1  0 23:13 ?        00:00:00 /usr/lib/gnome-settings-daemon/g
JohnDoe       649     1  0 23:13 ?        00:00:00 /usr/bin/gnome-keyring-daemon --
JohnDoe       653     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfsd
JohnDoe       657   633  0 23:13 ?        00:00:00 nm-applet --sm-disable
JohnDoe       658   633  0 23:13 ?        00:00:00 /usr/lib/policykit-1-gnome/polki
JohnDoe       659   633  0 23:13 ?        00:00:00 metacity --replace
JohnDoe       661   633  0 23:13 ?        00:00:00 gnome-panel
JohnDoe       662   633  0 23:13 ?        00:00:00 nautilus
JohnDoe       663   633  0 23:13 ?        00:00:01 /usr/lib/vino/vino-server --sm-d
JohnDoe       664   633  0 23:13 ?        00:00:00 gnome-power-manager
JohnDoe       670     1  0 23:13 ?        00:00:00 /usr/bin/pulseaudio --start --lo
JohnDoe       672   670  0 23:13 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
JohnDoe       678     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-mo
JohnDoe       681     1  0 23:13 ?        00:00:00 /usr/lib/bonobo-activation/bonob
JohnDoe       686     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
JohnDoe       693     1  0 23:13 ?        00:00:00 /usr/lib/gnome-panel/wnck-applet
JohnDoe       697     1  0 23:13 ?        00:00:00 /usr/lib/lunar-applet/lunar-appl
JohnDoe       701     1  0 23:13 ?        00:00:00 /usr/lib/indicator-applet/indica
JohnDoe       703     1  0 23:13 ?        00:00:00 /usr/lib/gnome-panel/notificatio
JohnDoe       705     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volum
JohnDoe       707     1  0 23:13 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-mo
root       710   582  0 Jun06 ?        00:00:00 smbd -F
102        711     1  0 Jun06 ?        00:00:00 dbus-daemon --system --fork
JohnDoe       718     1  0 23:14 ?        00:00:00 gnome-screensaver
JohnDoe       720     1  0 23:14 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
JohnDoe       723     1  0 23:14 ?        00:00:00 /usr/lib/indicator-application/i
JohnDoe       725     1  0 23:14 ?        00:00:00 /usr/lib/indicator-sound/indicat
JohnDoe       727     1  0 23:14 ?        00:00:00 /usr/lib/indicator-messages/indi
JohnDoe       729     1  0 23:14 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
root       732     2  0 Jun06 ?        00:00:21 [flush-8:0]
JohnDoe       742   633  0 23:14 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-
avahi      753     1  0 Jun06 ?        00:00:00 avahi-daemon: running [dns4.loca
avahi      754   753  0 Jun06 ?        00:00:00 avahi-daemon: chroot helper
root       757     1  0 Jun06 ?        00:00:00 NetworkManager
root       759     1  0 Jun06 ?        00:00:00 /usr/sbin/modem-manager
root       761     1  0 Jun06 ?        00:00:00 /usr/sbin/console-kit-daemon --n
JohnDoe       769     1  6 23:14 ?        00:00:06 /usr/bin/python2.6 /usr/bin/upda
root       827     1  0 Jun06 ?        00:00:00 /sbin/wpa_supplicant -u -s
JohnDoe       831   633  0 23:14 ?        00:00:00 update-notifier
root       836     1  0 23:14 ?        00:00:00 /usr/bin/python /usr/lib/system-
root       838     1  0 23:14 ?        00:00:00 /usr/bin/python /usr/sbin/aptd
postfix    852  2069  0 23:15 ?        00:00:00 cleanup -z -t unix -u -c
postfix    853  2069  0 23:15 ?        00:00:00 proxymap -t unix -u
postfix    854  2069  0 23:15 ?        00:00:00 trivial-rewrite -n rewrite -t un
postfix    855  2069  0 23:15 ?        00:00:00 smtp -t unix -u -c
postfix    862  2069  0 23:15 ?        00:00:00 bounce -z -t unix -u -c
JohnDoe       907   769  0 23:15 ?        00:00:00 /usr/bin/gksu --desktop /usr/sha
root       908   907  6 23:15 ?        00:00:02 /usr/sbin/synaptic --hide-main-w
root       916   908  0 23:15 pts/6    00:00:00 /usr/sbin/synaptic --hide-main-w
root       923     1  0 Jun06 ?        00:00:00 /usr/sbin/vsftpd
root       926     1  0 23:15 pts/6    00:00:00 dbus-launch --autolaunch 4bc7c8f
root       927     1  0 23:15 ?        00:00:00 /bin/dbus-daemon --fork --print-
root       929     1  0 Jun06 ?        00:00:05 nmbd -D
root       930     1  0 23:15 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
root       974     1  0 Jun06 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       976     1  0 Jun06 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1000     1  0 Jun06 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1003     1  0 Jun06 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1019     1  0 Jun06 ?        00:00:00 acpid -c /etc/acpi/events -s /va
root      1027     1  0 Jun06 ?        00:00:01 cron
daemon    1034     1  0 Jun06 ?        00:00:00 atd
bind      1162     1  0 Jun06 ?        00:00:00 /usr/sbin/named -u bind
root      1182     1  0 Jun06 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1329  2361  0 23:15 ?        00:00:00 sleep 20
amavis    1420     1  0 Jun06 ?        00:00:06 amavisd (master)
amavis    1472  1420  0 Jun06 ?        00:00:00 amavisd (virgin child)
amavis    1473  1420  0 Jun06 ?        00:00:00 amavisd (virgin child)
root      1540   916  0 23:16 pts/7    00:00:00 /usr/bin/dpkg --status-fd 34 --c
root      1550  1540  3 23:16 pts/7    00:00:00 /usr/bin/perl -w /usr/share/debc
root      1562  1550  0 23:16 pts/7    00:00:00 /bin/bash -e /var/lib/dpkg/info/
JohnDoe      1640     1  5 23:16 ?        00:00:00 gnome-terminal
JohnDoe      1641  1640  0 23:16 ?        00:00:00 gnome-pty-helper
JohnDoe      1642  1640  6 23:16 pts/8    00:00:00 bash
mysql     1663  1562  4 23:16 pts/7    00:00:00 /usr/sbin/mysqld --bootstrap --u
JohnDoe      1677  1642  0 23:16 pts/8    00:00:00 ps -ef
clamav    1727     1  0 Jun06 ?        00:00:05 /usr/sbin/clamd
clamav    1832     1  0 Jun06 ?        00:01:02 /usr/bin/freshclam -d --quiet
root      1845     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1846  1845  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1849  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1850  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1851  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1852  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1853  1846  0 Jun06 ?        00:00:00 /usr/lib/courier/courier-authlib
root      1866     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1867  1866  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
root      1886     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1887  1886  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
root      1900     1  0 Jun06 ?        00:00:01 /usr/sbin/courierlogger -pid=/va
root      1901  1900  0 Jun06 ?        00:00:03 /usr/sbin/couriertcpd -maxprocs=
root      1920     1  0 Jun06 ?        00:00:00 /usr/sbin/courierlogger -pid=/va
root      1921  1920  0 Jun06 ?        00:00:00 /usr/sbin/couriertcpd -address=0
JohnDoe      1954     1  0 Jun06 ?        00:00:02 SCREEN -d -m -t ogp_agent -c ogp
JohnDoe      1961  1954  0 Jun06 pts/0    00:00:01 /usr/bin/perl ./ogp_agent.pl
root      1963     1  0 Jun06 ?        00:02:12 /usr/bin/php5-fpm --fpm-config /
www-data  1964  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1965  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1966  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1967  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1968  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1969  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1970  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1971  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1972  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
www-data  1973  1963  0 Jun06 ?        00:00:00 /usr/bin/php5-fpm --fpm-config /
root      1976     1  0 Jun06 ?        00:00:20 /usr/bin/perl -wT /usr/sbin/pop-
root      2069     1  0 Jun06 ?        00:00:11 /usr/lib/postfix/master
postfix   2074  2069  0 Jun06 ?        00:00:04 qmgr -l -t fifo -u
root      2101     1  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2102  2101  0 Jun06 ?        00:00:30 /usr/sbin/saslauthd -a pam -m /v
root      2103  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2105  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2106  2101  0 Jun06 ?        00:00:31 /usr/sbin/saslauthd -a pam -m /v
root      2120     1  0 Jun06 ?        00:00:01 /usr/sbin/winbindd
root      2143     1  0 Jun06 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cup
root      2144  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
root      2190     1  0 Jun06 ?        00:00:16 /usr/sbin/apache2 -k start
117       2205     1  0 Jun06 ?        00:00:04 /usr/sbin/murmurd -ini /etc/mumb
root      2361     1  0 Jun06 ?        00:00:00 /bin/bash /var/www/new/ehcp/ehcp
root      2372     1  0 Jun06 tty1     00:00:00 /sbin/getty -8 38400 tty1
postfix   2668  2069  0 Jun06 ?        00:00:01 tlsmgr -l -t unix -u -c
root      4003     1  0 Jun06 ?        00:00:00 /usr/lib/policykit-1/polkitd
rtkit     4012     1  0 Jun06 ?        00:00:06 /usr/lib/rtkit/rtkit-daemon
root      4018     1  0 Jun06 ?        00:00:00 /usr/lib/upower/upowerd
107       4057     1  0 Jun06 ?        00:00:04 /usr/sbin/hald
root      4058  4057  0 Jun06 ?        00:00:00 hald-runner
root      4085  4058  0 Jun06 ?        00:00:00 hald-addon-input: Listening on /
root      4096     2  0 Jun06 ?        00:00:00 [kworker/3:2]
root      4104  4058  0 Jun06 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
107       4105  4058  0 Jun06 ?        00:00:00 hald-addon-acpi: listening on ac
root      4116     1  0 Jun06 ?        00:00:09 /usr/lib/udisks/udisks-daemon
root      4117  4116  0 Jun06 ?        00:00:00 udisks-daemon: not polling any d
root      4984  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
root      5001  2120  0 Jun06 ?        00:00:00 /usr/sbin/winbindd
www-data 11473  2190  0 Jun10 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 13876  2190  0 Jun10 ?        00:00:00 /usr/sbin/apache2 -k start
root     16704     2  0 Jun11 ?        00:00:23 [kworker/2:2]
root     25531     2  0 02:00 ?        00:00:14 [kworker/2:1]
www-data 25824  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25825  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25826  2190  0 02:27 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25828  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25829  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25831  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25833  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 25834  2190  0 02:28 ?        00:00:00 /usr/sbin/apache2 -k start
root     28107     1  0 07:25 ?        00:00:10 /usr/sbin/spamd --create-prefs -
root     28111 28107  0 07:25 ?        00:00:00 spamd child
root     28112 28107  0 07:25 ?        00:00:00 spamd child
root     31330   582  0 21:18 ?        00:00:00 smbd -F
postfix  31771  2069  0 23:13 ?        00:00:00 pickup -l -t fifo -u -c -o conte
root     31772   589  0 23:13 ?        00:00:00 sshd: nx [priv]     
nx       31838 31772  0 23:13 ?        00:00:00 sshd: nx@notty      
nx       31839 31838  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32003 31839  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32004 32003  0 23:13 ?        00:00:00 /usr/bin/expect /usr/lib/nx/nxno
nx       32006 32004  0 23:13 pts/5    00:00:00 ssh -2 -x -l JohnDoe 127.0.0.1 -o N
root     32011   589  0 23:13 ?        00:00:00 sshd: JohnDoe [priv]   
JohnDoe     32073 32011  0 23:13 ?        00:00:00 sshd: JohnDoe@notty    
JohnDoe     32074 32073  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
nx       32373 31839  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32376 32373  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32377 32373  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32383 32376  0 23:13 ?        00:00:00 /bin/bash /usr/bin/nxserver
nx       32384 32376  0 23:13 ?        00:00:00 tee -a /var/log/nxserver.log
JohnDoe     32385 32074  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32387 32385  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32640 32387  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32645 32387  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32648 32640  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32649 32640  0 23:13 ?        00:00:00 tee /home/JohnDoe/.nx/
JohnDoe     32650 32640  0 23:13 ?        00:00:00 /bin/bash /usr/lib/nx/nxnode --s
JohnDoe     32700 32648  8 23:13 ?        00:00:11 /usr/bin/nxagent -persistent -D
JohnDoe     32766     1  0 Jun09 ?        00:00:04 SCREEN -d -m -t OGP_HOME_0000000


```Top:

```

JohnDoe@dns4:~$ top

top - 23:17:54 up 6 days,  1:50,  2 users,  load average: 0.22, 0.26, 0.15
Tasks: 229 total,   2 running, 227 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.7%us,  2.9%sy,  0.0%ni, 93.3%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   4062848k total,  3875964k used,   186884k free,    97540k buffers
Swap: 14647292k total,    11368k used, 14635924k free,  1764476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                       
  553 JohnDoe      20   0  219m 210m 3244 R    5  5.3 173:02.31 mohaa_lnxded                                                                  
32700 JohnDoe      20   0 90460  53m  10m S    4  1.4   0:19.86 nxagent                                                                       
 1640 JohnDoe      20   0 44940  12m 9976 S    4  0.3   0:01.91 gnome-terminal                                                                
  300 JohnDoe      20   0  231m 220m 1916 S    2  5.6 283:02.01 mohaa_lnxded                                                                  
  461 JohnDoe      20   0  276m 265m 3216 S    2  6.7  95:20.76 mohaa_lnxded                                                                  
  375 JohnDoe      20   0  196m 186m 3140 S    1  4.7 110:52.01 mohaa_lnxded                                                                  
  648 JohnDoe      20   0 88844 9048 6948 S    0  0.2   0:00.34 gnome-settings-                                                               
 2247 JohnDoe      20   0  2592 1164  828 R    0  0.0   0:00.09 top                                                                           
    1 root      20   0  2844 1552 1164 S    0  0.0   0:03.22 init                                                                          
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                      
    3 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/0                                                                   
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0                                                                   
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                   
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                   
    8 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0                                                                   
    9 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1                                                                   
   10 root      20   0     0    0    0 S    0  0.0   1:58.41 kworker/0:1                                                                   


```Any ideas what might be causing this?  How should I troubleshoot this further to determine the cause?

Please let me know.  Any help is appreciated.

use the top command but we have to change it to memory

```
top
shift + f
n
enter
```

---

### Post by own3mall on 2012-06-14
> **idoitprone said:**
> use the top command but we have to change it to memory

```
top
shift + f
n
enter
```

Thanks.  However, the figures don't add up... what else is using memory?  It seems that not all processes are shown.

---

### Post by idoitprone on 2012-06-14
> **own3mall said:**
> Thanks.  However, the figures don't add up... what else is using memory?  It seems that not all processes are shown.

how ram are you using

```
free -m
```

---

