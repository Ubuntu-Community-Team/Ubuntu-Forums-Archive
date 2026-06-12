---
title: "Kubuntu's Network Manager - no eth0"
date: 2011-06-01
forum: General Help
---

### Post by iclestu on 2011-06-01
A little odd, well maybe....

Should I be able to see eth0 in the Network Connections control program that ships with Kubuntu?

Its not there. See screen-shot.

eth0 definitely exists and I can access the Internet no probs but it doesn't show in the above.

ifconfig gives:

```
 sudo ifconfig
eth0      Link encap:Ethernet  HWaddr d4:85:64:0a:0d:75  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d685:64ff:fe0a:d75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163169716 (163.1 MB)  TX bytes:9768600 (9.7 MB)
          Interrupt:41 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2160 (2.1 KB)  TX bytes:2160 (2.1 KB)

```

---

### Post by Zorael on 2011-06-01
I believe what's listed there are profiles.

Add a new one!

---

### Post by iclestu on 2011-06-02
> **Zorael said:**
> I believe what's listed there are profiles.

Add a new one!

yeah ok - I am feeling suitably foolish ;)

Got to learn tho :)

---

### Post by iclestu on 2011-06-02
yeah - ok.....

so I set up a new (basic) profile. Set connect automatically to 'yes', but.....

Its not connected (it says last used - never) but I am still connected to my network.

what am i missing here?

---

### Post by iclestu on 2011-06-02
the plot thickens....

having forced it to connect through my newly created eth0 profile, it does. I reboot then it connects through the original connection and still leaves my manually connected profile unused (save for the once when i forced it)....

Surely there should be some default profile that I can edit? no? I had been under the impression that this was eth0 and THINK I can remember it appearing in gnome before i switched to kubuntu but that was a while ago.....

So, I think that all I have done is create an ALTERNATIVE profile that i happen to have named (rather confusingly) eth0 and that the actual profile my system uses to connect at start up is hidden somewhere? No? Am I missing the point?

---

### Post by mastablasta on 2011-06-02
perhaps your porfile was left over from Ubuntu?
 
you could try to see what processes are running in background.
 
as these are mostly GUI interfaces you are talking about while linux doens't need a GUI to connect.

---

### Post by iclestu on 2011-06-02
> **mastablasta said:**
> perhaps your porfile was left over from Ubuntu?
 
you could try to see what processes are running in background.
 
as these are mostly GUI interfaces you are talking about while linux doens't need a GUI to connect.

thanks for your reply....

i recently did a fresh install using only kubuntu and have not installed gnome since so dont think there is a profile left over.

process in background done with sudo ps aux is as follows. Not really sure what I am looking for though?
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3040  1792 ?        Ss   10:40   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    10:40   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    10:40   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    10:40   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    10:40   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    10:40   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S<   10:40   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   10:40   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   10:40   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    10:40   0:00 [kworker/u:1]
root        15  0.0  0.0      0     0 ?        S    10:40   0:00 [sync_supers]
root        16  0.0  0.0      0     0 ?        S    10:40   0:00 [bdi-default]
root        17  0.0  0.0      0     0 ?        S<   10:40   0:00 [kintegrityd]
root        18  0.0  0.0      0     0 ?        S<   10:40   0:00 [kblockd]
root        19  0.0  0.0      0     0 ?        S<   10:40   0:00 [kacpid]
root        20  0.0  0.0      0     0 ?        S<   10:40   0:00 [kacpi_notify]
root        21  0.0  0.0      0     0 ?        S<   10:40   0:00 [kacpi_hotplug]
root        22  0.0  0.0      0     0 ?        S<   10:40   0:00 [ata_sff]
root        23  0.0  0.0      0     0 ?        S    10:40   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        S<   10:40   0:00 [md]
root        26  0.0  0.0      0     0 ?        S    10:40   0:00 [khungtaskd]
root        27  0.0  0.0      0     0 ?        S    10:40   0:00 [kswapd0]
root        28  0.0  0.0      0     0 ?        SN   10:40   0:00 [ksmd]
root        29  0.0  0.0      0     0 ?        S    10:40   0:00 [fsnotify_mark]
root        30  0.0  0.0      0     0 ?        S<   10:40   0:00 [aio]
root        31  0.0  0.0      0     0 ?        S    10:40   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S<   10:40   0:00 [crypto]
root        36  0.0  0.0      0     0 ?        S<   10:40   0:00 [kthrotld]
root        38  0.0  0.0      0     0 ?        S<   10:40   0:00 [kmpathd]
root        39  0.0  0.0      0     0 ?        S<   10:40   0:00 [kmpath_handlerd]
root        40  0.0  0.0      0     0 ?        S<   10:40   0:00 [kondemand]
root        41  0.0  0.0      0     0 ?        S<   10:40   0:00 [kconservative]
root       137  0.0  0.0      0     0 ?        S    10:40   0:00 [scsi_eh_0]
root       151  0.0  0.0      0     0 ?        S    10:40   0:00 [scsi_eh_1]
root       152  0.0  0.0      0     0 ?        S    10:40   0:00 [scsi_eh_2]
root       156  0.0  0.0      0     0 ?        S    10:40   0:00 [scsi_eh_3]
root       157  0.0  0.0      0     0 ?        S    10:40   0:00 [kworker/u:3]
root       198  0.0  0.0      0     0 ?        S<   10:40   0:00 [ttm_swap]
root       261  0.0  0.0      0     0 ?        S    10:40   0:00 [jbd2/sda5-8]
root       262  0.0  0.0      0     0 ?        S<   10:40   0:00 [ext4-dio-unwrit]
root       314  0.0  0.0   2412   608 ?        S    10:40   0:00 upstart-udev-bridge --daemon
root       323  0.0  0.0   2860  1104 ?        S<s  10:40   0:00 udevd --daemon
root       424  0.0  0.0   2984  1124 ?        S<   10:40   0:00 udevd --daemon
root       425  0.0  0.0   2984  1128 ?        S<   10:40   0:00 udevd --daemon
root       521  0.0  0.0      0     0 ?        S<   10:40   0:00 [kpsmoused]
root       554  0.0  0.0   2412   352 ?        S    10:40   0:00 upstart-socket-bridge --daemon
root       637  0.0  0.1   5652  2236 ?        Ss   10:40   0:00 /usr/sbin/sshd -D
syslog     649  0.0  0.0  28664  1476 ?        Sl   10:40   0:00 rsyslogd -c4
root       651  0.0  0.0      0     0 ?        S<   10:40   0:00 [hd-audio0]
102        670  0.0  0.1   3612  1876 ?        Ss   10:40   0:03 dbus-daemon --system --fork --activation=upstart
root       679  0.0  0.0   3716   960 ?        Ss   10:40   0:00 kdm
avahi      684  0.0  0.0   3132  1676 ?        S    10:40   0:00 avahi-daemon: running [stewart-desktop.local]
avahi      685  0.0  0.0   3016   432 ?        S    10:40   0:00 avahi-daemon: chroot helper
root       686  0.0  0.2  26388  4340 ?        Ssl  10:40   0:00 NetworkManager
root       689  0.0  0.1   4660  2460 ?        S    10:40   0:00 /usr/sbin/modem-manager
root       693  0.0  0.2  25528  4024 ?        Sl   10:40   0:00 /usr/lib/policykit-1/polkitd
root       722  4.0  2.1  49820 39388 tty7     Ss+  10:40   2:56 /usr/bin/X :0 vt7 -nr -nolisten tcp -auth /var/run/xauth/A:0-eBXe2b
root       734  0.0  0.0   5172  1508 ?        S    10:40   0:00 /sbin/wpa_supplicant -u -s
root       772  0.0  0.0   1872   572 tty4     Ss+  10:40   0:00 /sbin/getty -8 38400 tty4
root       780  0.0  0.0   1872   568 tty5     Ss+  10:40   0:00 /sbin/getty -8 38400 tty5
root       789  0.0  0.0   1872   572 tty2     Ss+  10:40   0:00 /sbin/getty -8 38400 tty2
root       796  0.0  0.0   1872   576 tty3     Ss+  10:40   0:00 /sbin/getty -8 38400 tty3
root       798  0.0  0.0   1872   576 tty6     Ss+  10:40   0:00 /sbin/getty -8 38400 tty6
root       802  0.0  0.0   1864   672 ?        Ss   10:40   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       810  0.0  0.0   3156   644 ?        Ss   10:40   0:00 /usr/sbin/irqbalance
root       831  0.0  0.0   2268   848 ?        Ss   10:40   0:00 cron
daemon     832  0.0  0.0   2132   352 ?        Ss   10:40   0:00 atd
root       834  0.0  0.4  10432  7620 ?        S    10:40   0:00 ddclient - sleeping for 160 seconds
root       852  0.0  0.1   4812  2100 ?        S    10:40   0:00 -:0
root       854  0.0  0.0  13380  1496 ?        Ss   10:40   0:00 /usr/sbin/winbindd
root       959  0.0  0.0      0     0 ?        S    10:40   0:00 [flush-8:0]
root       961  0.0  0.0  13380  1088 ?        S    10:40   0:00 /usr/sbin/winbindd
root       986  0.0  0.1   7308  3308 ?        Ss   10:40   0:00 /usr/sbin/cupsd -F
root      1002  0.0  0.0   2552  1200 ?        S    10:40   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/
root      1043  0.0  0.0   1872   576 tty1     Ss+  10:40   0:00 /sbin/getty -8 38400 tty1
root      1097  0.0  0.1  27192  3296 ?        Sl   10:41   0:00 /usr/sbin/console-kit-daemon --no-daemon
stewart   1170  0.0  0.0   1912   556 ?        Ss   10:41   0:00 /bin/sh /usr/bin/startkde
stewart   1218  0.0  0.0   3340  1148 ?        S    10:41   0:00 /usr/local/lexmark/legacy/bin/demond lexmark
stewart   1219  0.0  0.0   3368   188 ?        Ss   10:41   0:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/stewart/.
stewart   1220  0.0  0.0   4724   368 ?        Ss   10:41   0:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/stewart/.gnupg/gpg-agent-inf
stewart   1223  0.0  0.0   3456   560 ?        S    10:41   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
stewart   1224  0.0  0.1   4360  1900 ?        Ss   10:41   0:01 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      1250  0.0  0.1  23332  3516 ?        Sl   10:41   0:01 /usr/lib/udisks/udisks-daemon
root      1251  0.0  0.0   5564   720 ?        S    10:41   0:00 udisks-daemon: polling /dev/sr0
stewart   1278  0.0  0.0   1700    56 ?        S    10:41   0:00 /usr/lib/kde4/libexec/start_kdeinit +kcminit_startup
stewart   1279  0.0  0.7  82004 14304 ?        Ss   10:41   0:00 kdeinit4: kdeinit4 Running...                  
stewart   1280  0.0  0.4  84084  8760 ?        S    10:41   0:00 kdeinit4: klauncher [kdeinit] --fd=9           
stewart   1282  0.0  1.2 219632 23140 ?        Sl   10:41   0:01 kdeinit4: kded4 [kdeinit]                      
stewart   1288  0.0  0.7  77544 12632 ?        S    10:41   0:00 /usr/bin/kglobalaccel
root      1291  0.0  0.2  17716  3636 ?        Sl   10:41   0:00 /usr/lib/upower/upowerd
stewart   1344  0.0  0.0   1832   244 ?        S    10:41   0:00 kwrapper4 ksmserver
stewart   1345  0.0  0.8 126536 14544 ?        Sl   10:41   0:00 kdeinit4: ksmserver [kdeinit]                  
stewart   1363  1.9  2.4 188856 43396 ?        Sl   10:41   1:26 kwin -session 101ac1ba1bc10f000129166004100000015970000_1307007626_56993
stewart   1368  0.0  0.7  76696 14224 ?        S    10:41   0:00 /usr/bin/kactivitymanagerd
stewart   1372  1.8  1.3 284004 25080 ?        Sl   10:41   1:21 /usr/bin/knotify4
stewart   1375  0.6  3.5 394980 63272 ?        Sl   10:41   0:26 /usr/bin/plasma-desktop
stewart   1383  0.0  0.7  76456 12924 ?        S    10:41   0:00 /usr/bin/kuiserver
stewart   1385  0.0  0.0   2408  1044 ?        S    10:41   0:00 ksysguardd
stewart   1388  0.0  0.2  36776  4216 ?        Sl   10:41   0:00 /usr/bin/akonadi_control
stewart   1391  0.0  0.3 118136  7132 ?        Sl   10:41   0:00 akonadiserver
stewart   1393  0.0  1.2 193376 23148 ?        Sl   10:41   0:01 /usr/sbin/mysqld --defaults-file=/home/stewart/.local/share/akonadi//mysql.conf --da
stewart   1399  0.0  0.7  80244 13656 ?        S    10:41   0:00 /usr/bin/kaccess
stewart   1413  0.0  0.4  45492  7640 ?        Sl   10:41   0:00 /usr/bin/nepomukserver
stewart   1416  0.2  2.5 319096 45836 ?        Sl   10:41   0:11 /usr/bin/krunner
stewart   1418  0.0  1.1 198532 20700 ?        SNl  10:41   0:00 /usr/bin/nepomukservicestub nepomukstorage
stewart   1425  0.0  0.4 170484  7380 ?        S<sl 10:41   0:01 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1429  0.0  0.0  18888  1176 ?        SNl  10:41   0:00 /usr/lib/rtkit/rtkit-daemon
stewart   1443  0.0  1.2 301548 22136 ?        Sl   10:41   0:00 /usr/bin/kmix -session 101ac1ba1bc10f000129166005400000015970013_1307007625_894618
stewart   1445  0.0  0.7  79352 12636 ?        S    10:41   0:00 /usr/bin/akonaditray -session 101ac1ba1bc10f000129484647300000034660021_1307007625_8
stewart   1455  0.0  0.9  82056 17148 ?        S    10:41   0:00 /usr/bin/akonadi_ical_resource --identifier akonadi_ical_resource_0
stewart   1456  0.0  0.9  82052 17152 ?        S    10:41   0:00 /usr/bin/akonadi_ical_resource --identifier akonadi_ical_resource_1
stewart   1457  0.0  0.9  80280 16512 ?        S    10:41   0:00 /usr/bin/akonadi_maildir_resource --identifier akonadi_maildir_resource_0
stewart   1458  0.0  0.9  80628 16724 ?        S    10:41   0:00 /usr/bin/akonadi_maildispatcher_agent --identifier akonadi_maildispatcher_agent
stewart   1459  0.0  0.9  79952 16708 ?        S    10:41   0:00 /usr/bin/akonadi_nepomuk_contact_feeder --identifier akonadi_nepomuk_contact_feeder
stewart   1461  0.0  0.9  79996 16372 ?        S    10:41   0:00 /usr/bin/akonadi_vcard_resource --identifier akonadi_vcard_resource_0
stewart   1470  0.0  1.8 165924 32744 ?        Sl   10:41   0:02 /usr/bin/kopete -session 101ac1ba1bc10f000130699889900000013900084_1307007625_896869
stewart   1480  0.0  0.7  76508 13540 ?        S    10:41   0:00 /usr/bin/nepomukcontroller -session 101ac1ba1bc10f000130699998600000014040016_130700
stewart   1504  0.0  1.2 125900 22872 ?        Sl   10:41   0:00 /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
stewart   1517  0.0  2.1 117760 38080 ?        S    10:41   0:00 python /usr/bin/printer-applet
stewart   1520  0.0  0.7  77104 14300 ?        S    10:41   0:00 /usr/bin/klipper
stewart   1548  0.0  1.7  41248 31552 ?        SNl  10:41   0:03 /usr/bin/virtuoso-t +foreground +configfile /tmp/virtuoso_hX1418.ini +wait
stewart   1584  0.0  0.9  95240 16416 ?        SN   10:41   0:00 /usr/bin/nepomukservicestub nepomukqueryservice
stewart   1585  0.0  0.9  95628 16860 ?        SNl  10:41   0:00 /usr/bin/nepomukservicestub nepomukfilewatch
stewart   1586  0.0  0.9  87300 16804 ?        SNl  10:41   0:00 /usr/bin/nepomukservicestub nepomukremovablestorageservice
stewart   1587  0.0  0.9  99316 16980 ?        SNl  10:41   0:00 /usr/bin/nepomukservicestub nepomukbackupsync
root      2208  0.0  0.0      0     0 ?        S    11:07   0:01 [kworker/1:2]
stewart   2240  0.6  3.7 245012 68152 ?        Sl   11:27   0:10 /usr/bin/kontact
stewart   2244  0.0  0.6  89076 12300 ?        S    11:27   0:00 kdeinit4: kio_imap4 [kdeinit] imaps local:/tmp/ksocket-stewart/klauncherMT1280.slave
stewart   2246  0.0  0.9 107644 17340 ?        S    11:27   0:00 /usr/bin/korgac -icon korgac
root      2259  0.0  0.0      0     0 ?        S    11:33   0:00 [kworker/0:2]
stewart   2263  3.3  2.7 172268 48680 ?        Sl   11:39   0:28 /usr/bin/kile
stewart   2267  0.0  0.2   7248  3884 pts/1    Ss+  11:39   0:00 /bin/bash
stewart   2327  0.2  1.6 156624 30000 ?        Sl   11:39   0:02 /usr/bin/okular TMA03.pdf
stewart   2335  5.4  5.7 789284 104004 ?       Sl   11:40   0:42 /usr/lib/firefox-4.0.1/firefox-bin
stewart   2348  0.0  0.1   8016  2684 ?        S    11:40   0:00 /usr/lib/libgconf2-4/gconfd-2
stewart   2362  0.0  0.8  77240 15164 ?        S    11:40   0:00 /usr/lib/mozilla/kmozillahelper
root      2373  0.0  0.0      0     0 ?        S    11:44   0:00 [kworker/1:1]
root      2374  0.1  0.0      0     0 ?        S    11:44   0:00 [kworker/0:0]
root      2384  0.0  0.0      0     0 ?        S    11:49   0:00 [kworker/1:0]
stewart   2385  0.9  1.3  71188 23644 ?        Sl   11:49   0:02 /usr/bin/xsane
root      2392  0.0  0.0      0     0 ?        S    11:49   0:00 [kworker/0:1]
stewart   2406  1.6  1.1 124604 20860 ?        Rl   11:52   0:00 /usr/bin/konsole
stewart   2408  0.4  0.2   7252  3884 pts/2    Ss   11:52   0:00 /bin/bash
root      2464  1.5  0.1   5612  1820 pts/2    S+   11:53   0:00 sudo ps aux
root      2465  0.0  0.0   4708  1160 pts/2    R+   11:53   0:00 ps aux

```

---

