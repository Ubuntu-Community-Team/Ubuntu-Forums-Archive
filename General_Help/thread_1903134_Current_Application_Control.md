---
title: "Current Application Control"
date: 2012-01-01
forum: General Help
---

### Post by Treyonator56 on 2012-01-01
Hey guys. I installed Kubuntu today, and everything is working fine. The only problem I have is that when I click the widget to see what all applications I have running, it only shows three of them in a drop down menu. Before I updated things, it would open a new window and have previews of all the apps that were open. I've looked through the settings and have found nothing to fix it. Any help will greatly be appreciated. I've been at it for hours, lol.

---

### Post by TeoBigusGeekus on 2012-01-01
Open a terminal and give
```
ps aux
```

---

### Post by Treyonator56 on 2012-01-01
This is what I get:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3316  1516 ?        Ss   16:53   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    16:53   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    16:53   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    16:53   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    16:53   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    16:53   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S<   16:53   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   16:53   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   16:53   0:00 [netns]
root        15  0.0  0.0      0     0 ?        S    16:53   0:00 [sync_supers]
root        16  0.0  0.0      0     0 ?        S    16:53   0:00 [bdi-default]
root        17  0.0  0.0      0     0 ?        S<   16:53   0:00 [kintegrityd]
root        18  0.0  0.0      0     0 ?        S<   16:53   0:00 [kblockd]
root        19  0.0  0.0      0     0 ?        S<   16:53   0:00 [ata_sff]
root        20  0.0  0.0      0     0 ?        S    16:53   0:00 [khubd]
root        21  0.0  0.0      0     0 ?        S<   16:53   0:00 [md]
root        22  0.1  0.0      0     0 ?        S    16:53   0:01 [kworker/1:1]
root        23  0.0  0.0      0     0 ?        S    16:53   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    16:53   0:00 [kswapd0]
root        25  0.0  0.0      0     0 ?        SN   16:53   0:00 [ksmd]
root        26  0.0  0.0      0     0 ?        SN   16:53   0:00 [khugepaged]
root        27  0.0  0.0      0     0 ?        S    16:53   0:00 [fsnotify_mark]
root        28  0.0  0.0      0     0 ?        S    16:53   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   16:53   0:00 [crypto]
root        37  0.0  0.0      0     0 ?        S<   16:53   0:00 [kthrotld]
root       208  0.0  0.0      0     0 ?        S    16:53   0:00 [scsi_eh_0]
root       209  0.0  0.0      0     0 ?        S    16:53   0:00 [scsi_eh_1]
root       210  0.0  0.0      0     0 ?        S    16:53   0:00 [scsi_eh_2]
root       211  0.0  0.0      0     0 ?        S    16:53   0:00 [scsi_eh_3]
root       279  0.0  0.0      0     0 ?        S    16:53   0:00 [jbd2/sda1-8]
root       280  0.0  0.0      0     0 ?        S<   16:53   0:00 [ext4-dio-unwrit]
root       334  0.0  0.0   2648   524 ?        S    16:54   0:00 upstart-udev-bridge --daemon
root       360  0.0  0.1   3080  1312 ?        Ss   16:54   0:00 udevd --daemon
root       592  0.0  0.0   3076   948 ?        S    16:54   0:00 udevd --daemon
root       604  0.0  0.0      0     0 ?        S<   16:54   0:00 [kpsmoused]
root       606  0.0  0.0   3076   892 ?        S    16:54   0:00 udevd --daemon
root       609  0.0  0.0      0     0 ?        S    16:54   0:01 [kworker/1:2]
root       616  0.0  0.0      0     0 ?        S<   16:54   0:00 [cfg80211]
root       726  0.0  0.0   2652   340 ?        S    16:54   0:00 upstart-socket-bridge --daemon
root       749  0.0  0.0      0     0 ?        S<   16:54   0:00 [hd-audio0]
syslog     756  0.0  0.1  29208  1484 ?        Sl   16:54   0:00 rsyslogd -c5
103        773  0.2  0.1   4040  1868 ?        Ss   16:54   0:04 dbus-daemon --system --fork --activation=upstart
root       797  0.0  0.2   6864  2816 ?        S    16:54   0:00 /usr/sbin/modem-manager
avahi      801  0.0  0.1   3316  1436 ?        S    16:54   0:00 avahi-daemon: running [trey-eM350.local]
avahi      803  0.0  0.0   3316   432 ?        S    16:54   0:00 avahi-daemon: chroot helper
root       804  0.0  0.4  27612  4764 ?        Ssl  16:54   0:00 NetworkManager
root       859  0.0  0.0   1968   540 tty4     Ss+  16:54   0:00 /sbin/getty -8 38400 tty4
root       864  0.0  0.0   1968   544 tty5     Ss+  16:54   0:00 /sbin/getty -8 38400 tty5
root       873  0.0  0.0   1968   548 tty2     Ss+  16:54   0:00 /sbin/getty -8 38400 tty2
root       874  0.0  0.0   1968   496 tty3     Ss+  16:54   0:00 /sbin/getty -8 38400 tty3
root       876  0.0  0.0   1968   544 tty6     Ss+  16:54   0:00 /sbin/getty -8 38400 tty6
root       883  0.0  0.0   1984   704 ?        Ss   16:54   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       886  0.0  0.0   4052   944 ?        Ss   16:54   0:00 kdm
root       889  0.0  0.0   2428   876 ?        Ss   16:54   0:00 cron
daemon     890  0.0  0.0   2280   340 ?        Ss   16:54   0:00 atd
root       898  0.0  0.0   3420   628 ?        Ss   16:54   0:00 /usr/sbin/irqbalance
root       910 12.0  3.8  53492 39060 tty7     Ss+  16:54   3:35 /usr/bin/X :0 vt7 -nr -nolisten tcp -auth /var/run/xauth/A:0-7jITPa
root       940  0.0  0.2   7312  2864 ?        Ss   16:54   0:00 /usr/sbin/cupsd -F
root       951  0.0  0.1   4496  1544 ?        Ss   16:54   0:00 /usr/sbin/bluetoothd
root       955  0.0  0.3  23100  3608 ?        Sl   16:54   0:00 /usr/lib/policykit-1/polkitd
root       958  0.0  0.0      0     0 ?        S<   16:54   0:00 [l2cap]
root       961  0.0  0.0      0     0 ?        S<   16:54   0:00 [krfcommd]
root      1031  0.0  0.2   5688  2436 ?        S    16:54   0:00 /sbin/wpa_supplicant -u -s -O /var/run/wpa_supplicant
root      1049  0.0  0.0      0     0 ?        S    16:54   0:00 [flush-8:0]
root      1052  0.0  0.1   5172  1928 ?        S    16:54   0:00 -:0
root      1098  0.0  0.0   1968   484 tty1     Ss+  16:54   0:00 /sbin/getty -8 38400 tty1
root      1103  0.0  0.1   2736  1196 ?        S    16:54   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /va
root      1157  0.0  0.2  27832  2972 ?        Sl   16:54   0:00 /usr/sbin/console-kit-daemon --no-daemon
trey      1230  0.0  0.0   2040   500 ?        Ss   16:54   0:00 /bin/sh /usr/bin/x-session-manager
trey      1276  0.0  0.0   3856    12 ?        Ss   16:54   0:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/tre
trey      1277  0.0  0.0   5032   276 ?        Ss   16:54   0:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/trey/.gnupg/gpg-agent-
trey      1280  0.0  0.0   3748   276 ?        S    16:54   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
trey      1281  0.8  0.1   5160  1868 ?        Ss   16:54   0:14 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      1312  0.0  0.3  23984  3304 ?        Sl   16:54   0:00 /usr/lib/udisks/udisks-daemon
root      1313  0.0  0.0   6320   728 ?        S    16:54   0:00 udisks-daemon: not polling any devices
trey      1347  0.0  0.0   1816    28 ?        S    16:54   0:00 /usr/lib/kde4/libexec/start_kdeinit +kcminit_startup
trey      1348  0.0  1.4  91620 14276 ?        Ss   16:54   0:00 kdeinit4: kdeinit4 Running...                  
trey      1349  0.0  0.8  93016  8612 ?        S    16:54   0:00 kdeinit4: klauncher [kdeinit] --fd=9           
trey      1351  0.1  2.2 200220 23120 ?        Sl   16:54   0:03 kdeinit4: kded4 [kdeinit]                      
trey      1355  0.0  1.3  60356 13256 ?        S    16:54   0:00 /usr/bin/kglobalaccel
trey      1357  0.0  1.9  88164 19716 ?        Sl   16:54   0:00 /usr/bin/kwalletd
root      1361  0.0  0.3  26028  3760 ?        Sl   16:54   0:00 /usr/lib/upower/upowerd
trey      1380  0.0  0.0   1952   244 ?        S    16:54   0:00 kwrapper4 ksmserver
trey      1381  0.0  1.5 117860 15844 ?        Sl   16:54   0:00 kdeinit4: ksmserver [kdeinit]                  
trey      1402  0.3  3.0 151364 30604 ?        Sl   16:54   0:05 kwin -session 10d6107b2ac000132542066100000013950000_1325458365_173987
trey      1444  0.0  1.3  59652 13356 ?        S    16:54   0:00 /usr/bin/kactivitymanagerd
trey      1448  2.0  2.5 285080 25732 ?        Sl   16:54   0:35 /usr/bin/knotify4
trey      1451  0.0  1.3  63548 13836 ?        S    16:54   0:00 /usr/bin/kaccess
trey      1454 13.3  7.2 426256 73988 ?        Sl   16:54   3:54 /usr/bin/plasma-netbook
trey      1462  0.0  0.7  45952  7344 ?        Sl   16:54   0:00 /usr/bin/nepomukserver
trey      1468  0.1  2.3 193760 23824 ?        SNl  16:54   0:03 /usr/bin/nepomukservicestub nepomukstorage
trey      1470  0.1  0.5 163612  5948 ?        S<l  16:54   0:03 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1472  0.0  0.1  19088  1232 ?        SNl  16:54   0:00 /usr/lib/rtkit/rtkit-daemon
trey      1479  0.0  1.3  62420 13296 ?        S    16:54   0:00 /usr/bin/akonaditray -session 10d6107b2ac000132542067200000013950009_132545836
trey      1483  0.0  2.2 291948 23164 ?        Sl   16:54   0:01 /usr/bin/kmix -session 10d6107b2ac000132542067200000013950010_1325458360_28184
trey      1485  0.0  1.2  59712 12872 ?        S    16:54   0:00 /usr/bin/nepomukcontroller -session 10d6107b2ac000132542067300000013950012_132
trey      1492  0.5  3.2  45080 32564 ?        SNl  16:54   0:09 /usr/bin/virtuoso-t +foreground +configfile /tmp/virtuoso_kn1468.ini +wait
trey      1506  0.0  1.2  59948 13112 ?        S    16:54   0:00 /usr/bin/bluedevil-monolithic -session 10d6107b2ac000132543313700000013210048_
trey      1510  1.3  5.5 192552 55984 ?        Sl   16:54   0:23 /usr/bin/kopete -session 10d6107b2ac000132545134400000013210079_1325458360_302
trey      1525  0.0  1.3  59552 13548 ?        S    16:55   0:00 /usr/bin/kuiserver
trey      1529  0.0  0.1   2540  1076 ?        S    16:55   0:00 ksysguardd
trey      1533  0.1  0.4  37672  4772 ?        Sl   16:55   0:02 /usr/bin/akonadi_control
trey      1536  0.0  0.7 167380  7720 ?        Sl   16:55   0:00 akonadiserver
trey      1551  0.0  2.2 194980 23240 ?        Sl   16:55   0:01 /usr/sbin/mysqld --defaults-file=/home/trey/.local/share/akonadi//mysql.conf -
trey      1567  0.1  3.7 107100 38364 ?        S    16:55   0:01 python /usr/bin/printer-applet
trey      1572  0.0  1.4  69820 15056 ?        Sl   16:55   0:00 /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
trey      1579  0.1  1.9  64800 20212 ?        S    16:55   0:02 /usr/bin/klipper
trey      1674  0.0  1.4  58072 15008 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_akonotes_resource akonadi_akonotes_res
trey      1675  0.0  1.4  58684 14620 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_contacts_resource akonadi_contacts_res
trey      1676  0.0  1.4  57784 14728 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_contacts_resource akonadi_contacts_res
trey      1677  0.0  1.4  57784 14732 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_contacts_resource akonadi_contacts_res
trey      1678  0.0  1.4  57668 14628 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_contacts_resource akonadi_contacts_res
trey      1679  0.0  1.4  57668 14628 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_contacts_resource akonadi_contacts_res
trey      1680  0.0  1.4  58212 14948 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_ical_resource akonadi_ical_resource_0
trey      1681  0.0  1.4  58072 15020 ?        Sl   16:55   0:00 /usr/bin/akonadi_agent_launcher akonadi_maildir_resource akonadi_maildir_resou
trey      1682  0.0  1.7  67852 17852 ?        S    16:55   0:00 /usr/bin/akonadi_maildispatcher_agent --identifier akonadi_maildispatcher_agen
trey      1683  0.0  1.7  64488 17288 ?        S    16:55   0:00 /usr/bin/akonadi_nepomuk_calendar_feeder --identifier akonadi_nepomuk_calendar
trey      1686  0.0  1.7  63880 17332 ?        S    16:55   0:00 /usr/bin/akonadi_nepomuk_contact_feeder --identifier akonadi_nepomuk_contact_f
trey      1687  0.0  2.3 105812 23656 ?        S    16:55   0:00 /usr/bin/akonadi_nepomuk_email_feeder --identifier akonadi_nepomuk_email_feede
trey      1720  0.0  0.0      0     0 ?        Z    16:55   0:00 [kopete] <defunct>
trey      1760  0.0  1.6  69888 16460 ?        SN   16:55   0:00 /usr/bin/nepomukservicestub nepomukqueryservice
trey      1762  0.0  1.7  66196 17656 ?        SN   16:55   0:00 /usr/bin/nepomukservicestub nepomukbackupsync
trey      1764  0.0  1.7  86756 17628 ?        SNl  16:55   0:00 /usr/bin/nepomukservicestub nepomukfilewatch
root      1993  0.0  0.0      0     0 ?        S    17:05   0:00 [kworker/u:2]
root      2006  0.0  0.0      0     0 ?        S    17:05   0:00 [kworker/0:1]
root      2012  0.0  0.7  14544  7280 ?        S    17:05   0:00 /usr/bin/python /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
trey      2014  0.0  0.9  44172 10096 ?        S    17:05   0:00 /usr/lib/kde4/libexec/kio_http_cache_cleaner
trey      2064 36.5 11.8 630816 120068 ?       Sl   17:10   5:04 /usr/lib/firefox-8.0/firefox
trey      2079  0.1  1.6  62104 16692 ?        S    17:10   0:00 /usr/lib/mozilla/kmozillahelper
root      2096  0.0  0.0      0     0 ?        S    17:12   0:00 [kworker/0:2]
root      2110  0.0  0.0      0     0 ?        S    17:17   0:00 [kworker/u:0]
root      2122  0.0  0.0      0     0 ?        S    17:20   0:00 [kworker/0:0]
trey      2128  1.4  2.2 120728 22916 ?        Sl   17:21   0:01 /usr/lib/firefox-8.0/plugin-container /usr/lib/flashplugin-installer/libflashp
root      2142  0.0  0.0      0     0 ?        S    17:23   0:00 [kworker/u:1]
trey      2145 17.7  2.3 109768 23772 ?        Rl   17:23   0:00 /usr/bin/konsole
trey      2147 25.3  0.3   7096  3468 pts/0    Ss   17:23   0:00 /bin/bash
trey      2201  0.0  0.1   4756  1120 pts/0    R+   17:24   0:00 ps aux

---

### Post by TeoBigusGeekus on 2012-01-01
Well, these are all your running processes.

---

### Post by Treyonator56 on 2012-01-01
Okay, so how do I get the CAC to go from a drop down menu to an an actual window?

---

### Post by TeoBigusGeekus on 2012-01-01
No idea, sorry; I despise kde...

---

### Post by Treyonator56 on 2012-01-01
Thanks for trying to help...

---

### Post by Treyonator56 on 2012-01-01
Problem Solved. Switching to Ubuntu...

---

