---
title: "Low on memory warning with 200G free space"
date: 2010-01-23
forum: General Help
---

### Post by Jonners59 on 2010-01-23
I have a 300G hard drive which I have partitioned in to two 150G partitions.  In one of the 150 G partitions it is further sub divided in to 2.  One is used for Windows Vista 32bit Home Prem, and was the original OS on the machine, the other was created for my Ubuntu installation and is about 60G.

All documents for both OS are stored in the 150G partition.

I am running Ubuntu almost all the time, but have recently been getting warning messages that my machine is low on memory, yet I have over 200G or spare, unused capacity.  This can only be in the partition of c 60G reserved for the Ubuntu, but I can not understand why the warning as no files are stored there and the memory utility says it has 50G free.  Screen shots of the analysed enclosed.

Can any one help explain the problem and how I can fix it.  As you can guess in simple terms I am not a techie.  Thank you.

---

### Post by d3v1150m471c on 2010-01-23
Put this in your terminal and tell me what you get. 
```

free

```

---

### Post by Jonners59 on 2010-01-23
total                          used                         free                         shared                       buffers                    cached
Mem:       2056652            2040632           16020                                   0                                634544                       772840
     -/+ buffers/cache:     633248    1423404
Swap:       262136                      0        262136

---

### Post by d3v1150m471c on 2010-01-23
When your computer is saying low on memory it's talking about your RAM, and not your Hard Disk space.

---

### Post by d3v1150m471c on 2010-01-23
CRAP... sorry lol... no I was correct the first time. Your computer is telling me it's running a buttload of stuff in the background. What all do you have running?

---

### Post by Jonners59 on 2010-01-23
OK, could make sense.  How do I get a list.....

---

### Post by d3v1150m471c on 2010-01-23
```

ps -aux

```
let me know what it says, please

---

### Post by Jonners59 on 2010-01-23
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  19428  1840 ?        Ss   22:26   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   22:26   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   22:26   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   22:26   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   22:26   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   22:26   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   22:26   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   22:26   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        R<   22:26   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   22:26   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   22:26   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   22:26   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   22:26   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S<   22:26   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S<   22:26   0:00 [kintegrityd/0]
root        16  0.0  0.0      0     0 ?        S<   22:26   0:00 [kintegrityd/1]
root        17  0.0  0.0      0     0 ?        S<   22:26   0:00 [kblockd/0]
root        18  0.0  0.0      0     0 ?        S<   22:26   0:00 [kblockd/1]
root        19  0.0  0.0      0     0 ?        S<   22:26   0:00 [kacpid]
root        20  0.0  0.0      0     0 ?        S<   22:26   0:00 [kacpi_notify]
root        21  0.0  0.0      0     0 ?        S<   22:26   0:00 [kacpi_hotplug]
root        22  0.0  0.0      0     0 ?        S<   22:26   0:00 [ata/0]
root        23  0.0  0.0      0     0 ?        S<   22:26   0:00 [ata/1]
root        24  0.0  0.0      0     0 ?        S<   22:26   0:00 [ata_aux]
root        25  0.0  0.0      0     0 ?        S<   22:26   0:00 [ksuspend_usbd]
root        26  0.0  0.0      0     0 ?        S<   22:26   0:00 [khubd]
root        27  0.0  0.0      0     0 ?        S<   22:26   0:00 [kseriod]
root        28  0.0  0.0      0     0 ?        S<   22:26   0:00 [kmmcd]
root        29  0.0  0.0      0     0 ?        S<   22:26   0:00 [bluetooth]
root        30  0.0  0.0      0     0 ?        S    22:26   0:00 [khungtaskd]
root        31  0.0  0.0      0     0 ?        S    22:26   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S    22:26   0:00 [pdflush]
root        33  0.0  0.0      0     0 ?        S<   22:26   0:01 [kswapd0]
root        34  0.0  0.0      0     0 ?        S<   22:26   0:00 [aio/0]
root        35  0.0  0.0      0     0 ?        S<   22:26   0:00 [aio/1]
root        36  0.0  0.0      0     0 ?        S<   22:26   0:00 [ecryptfs-kthr]
root        37  0.0  0.0      0     0 ?        S<   22:26   0:00 [crypto/0]
root        38  0.0  0.0      0     0 ?        S<   22:26   0:00 [crypto/1]
root        53  0.0  0.0      0     0 ?        S<   22:26   0:00 [scsi_eh_0]
root        54  0.0  0.0      0     0 ?        S<   22:26   0:02 [scsi_eh_1]
root        62  0.0  0.0      0     0 ?        S<   22:26   0:00 [kstriped]
root        63  0.0  0.0      0     0 ?        S<   22:26   0:00 [kmpathd/0]
root        64  0.0  0.0      0     0 ?        S<   22:26   0:00 [kmpathd/1]
root        65  0.0  0.0      0     0 ?        S<   22:26   0:00 [kmpath_handle]
root        66  0.0  0.0      0     0 ?        S<   22:26   0:00 [ksnapd]
root        67  0.0  0.0      0     0 ?        R<   22:26   0:00 [kondemand/0]
root        68  0.0  0.0      0     0 ?        S<   22:26   0:00 [kondemand/1]
root        69  0.0  0.0      0     0 ?        S<   22:26   0:00 [kconservative]
root        70  0.0  0.0      0     0 ?        S<   22:26   0:00 [kconservative]
root        71  0.0  0.0      0     0 ?        S<   22:26   0:00 [krfcommd]
root       289  0.0  0.0      0     0 ?        S<   22:26   0:00 [khpsbpkt]
root       341  0.0  0.0      0     0 ?        S<   22:26   0:00 [knodemgrd_0]
root       427  0.2  0.0  16488  1252 ?        Ss   22:26   0:08 mount.ntfs -o l
root       434  0.0  0.0      0     0 ?        S<   22:26   0:02 [loop0]
root       436  0.0  0.0      0     0 ?        S<   22:26   0:00 [kjournald2]
root       494  0.0  0.0  12768   944 ?        S    22:26   0:00 upstart-udev-br
root       496  0.0  0.0  17452  1268 ?        S<s  22:26   0:00 udevd --daemon
root       741  0.0  0.0      0     0 ?        S<   22:26   0:00 [kpsmoused]
root       744  0.0  0.0      0     0 ?        S<   22:26   0:00 [tifm]
root       792  0.0  0.0      0     0 ?        S<   22:26   0:00 [hd-audio0]
root       798  0.0  0.0      0     0 ?        S<   22:26   0:00 [pccardd]
root       800  0.0  0.0      0     0 ?        S<   22:26   0:00 [iwl3945]
root       801  0.0  0.0      0     0 ?        S<   22:26   0:00 [phy0]
102        876  0.0  0.0  24260  1840 ?        Ss   22:26   0:00 dbus-daemon --s
107        889  0.0  0.2  34080  4648 ?        Ss   22:26   0:00 hald --daemon=y
avahi      890  0.0  0.0  31884  1612 ?        Ss   22:26   0:00 avahi-daemon: r
root       891  0.0  0.2  89400  4272 ?        Ssl  22:26   0:00 NetworkManager
root       893  0.0  0.1  74948  3760 ?        Ss   22:26   0:00 gdm-binary
root       895  0.0  0.0   8192   612 ?        Ss   22:26   0:00 dd bs=1 if=/pro
avahi      902  0.0  0.0  31760   548 ?        Ss   22:26   0:00 avahi-daemon: c
syslog     903  0.0  0.0 125880  1896 ?        Sl   22:26   0:00 rsyslogd -c4
root       905  0.0  0.1  51476  2352 ?        S    22:26   0:00 /usr/sbin/modem
root       909  0.0  0.1 120216  3196 ?        Ssl  22:26   0:00 /usr/sbin/conso
root       977  0.0  0.0  20056  1316 ?        S    22:26   0:00 hald-runner
root      1014  0.0  0.0  17448  1228 ?        S<   22:26   0:00 udevd --daemon
root      1040  0.0  0.0  17448  1164 ?        S<   22:26   0:00 udevd --daemon
root      1097  0.0  0.0   5988   604 tty4     Ss+  22:26   0:00 /sbin/getty -8
root      1101  0.0  0.0   5988   608 tty5     Ss+  22:26   0:00 /sbin/getty -8
root      1110  0.0  0.0   5988   608 tty2     Ss+  22:26   0:00 /sbin/getty -8
root      1123  0.0  0.0   5988   608 tty3     Ss+  22:26   0:00 /sbin/getty -8
root      1150  0.0  0.0   5988   608 tty6     Ss+  22:26   0:00 /sbin/getty -8
root      1168  0.0  0.0   4352  1120 ?        Ss   22:26   0:00 acpid -c /etc/a
root      1179  0.0  0.1  28216  2728 ?        S    22:26   0:00 /sbin/wpa_suppl
daemon    1180  0.0  0.0  16512   464 ?        Ss   22:26   0:00 atd
root      1186  0.0  0.0  18708   992 ?        Ss   22:26   0:00 cron
root      1193  0.0  0.1  76868  3892 ?        S    22:26   0:00 /usr/lib/gdm/gd
root      1237  4.9  3.0 149652 61900 tty7     Ss+  22:26   2:52 /usr/bin/X :0 -
clamav    1239  0.0  0.0  30068  1216 ?        Ss   22:26   0:00 /usr/bin/freshc
root      1348  0.0  0.0  22172  1216 ?        S    22:26   0:00 /usr/lib/hal/ha
root      1350  0.0  0.0  22172  1220 ?        S    22:26   0:00 /usr/lib/hal/ha
root      1362  0.0  0.0  22172  1236 ?        S    22:26   0:00 /usr/lib/hal/ha
root      1367  0.0  0.0  22188  1216 ?        S    22:26   0:00 /usr/lib/hal/ha
107       1368  0.0  0.0  26080  1216 ?        S    22:26   0:00 hald-addon-acpi
root      1384  0.0  0.0  22180  1240 ?        S    22:26   0:01 hald-addon-stor
root      1385  0.0  0.0  22180  1244 ?        S    22:26   0:00 hald-addon-inpu
root      1419  0.0  0.0 118212   996 ?        Ss   22:26   0:00 /usr/sbin/nvtvd
root      1440  0.0  0.0  63468  1680 ?        Ss   22:26   0:00 /usr/sbin/winbi
root      1442  0.0  0.0  63468  1440 ?        S    22:26   0:00 /usr/sbin/winbi
nobody    1462  0.0  0.0  29452  1444 ?        S<s  22:26   0:00 /usr/sbin/gpsd
root      1477  0.0  0.0  31204  1728 ?        S    22:26   0:00 /usr/sbin/odccm
root      1501  0.0  0.1  75120  2904 ?        Ss   22:26   0:00 /usr/sbin/cupsd
timidity  1689  0.0  0.3 104204  7156 ?        S    22:26   0:00 /usr/bin/timidi
root      1693  0.0  0.0   5988   608 tty1     Ss+  22:26   0:00 /sbin/getty -8
gdm       1733  0.0  0.0  26156   784 ?        S    22:26   0:00 /usr/bin/dbus-l
root      1737  0.0  0.1  47132  2960 ?        S    22:26   0:00 /usr/lib/device
root      1787  0.0  0.1  89304  3360 ?        S    22:26   0:00 /usr/lib/gdm/gd
jonathan  1831  0.0  0.3 166796  7644 ?        Ssl  22:27   0:00 gnome-session
jonathan  1871  0.0  0.0  36060   708 ?        Ss   22:27   0:00 /usr/bin/ssh-ag
jonathan  1874  0.0  0.0  26156   788 ?        S    22:27   0:00 /usr/bin/dbus-l
jonathan  1875  0.0  0.0  24084  1608 ?        Ss   22:27   0:00 /bin/dbus-daemo
jonathan  1879  0.0  0.2 206548  4920 ?        Ssl  22:27   0:00 /usr/bin/pulsea
jonathan  1884  0.0  0.1  94308  3424 ?        S    22:27   0:00 /usr/lib/pulsea
jonathan  1886  0.1  0.3  46592  6444 ?        S    22:27   0:06 /usr/lib/libgco
jonathan  1891  0.0  0.7 343356 15720 ?        Ssl  22:27   0:01 /usr/lib/gnome-
jonathan  1895  0.0  0.1 101120  3668 ?        SLl  22:27   0:00 gnome-keyring-d
jonathan  1899  0.0  0.4 195288  8820 ?        Ss   22:27   0:00 seahorse-daemon
jonathan  1904  0.0  0.1  43220  2372 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  1908  0.0  0.6 211752 14300 ?        S    22:27   0:01 /usr/lib/notify
jonathan  1911  0.0  0.1  83824  2800 ?        Ssl  22:27   0:00 /usr/lib/gvfs//
jonathan  1915  0.1  0.7 280380 14596 ?        Sl   22:27   0:03 metacity
jonathan  1927  0.2  1.2 354640 26112 ?        S    22:27   0:09 gnome-panel
jonathan  1929  0.0  0.0  19772  1032 ?        S    22:27   0:01 syndaemon -i 0.
jonathan  1930  0.3  1.6 579192 34640 ?        S    22:27   0:11 nautilus
jonathan  1932  0.0  0.1 144312  4092 ?        Ssl  22:27   0:00 /usr/lib/bonobo
jonathan  1940  0.0  0.4 154576  8276 ?        S    22:27   0:00 bluetooth-apple
jonathan  1945  0.0  0.8 243364 16468 ?        S    22:27   0:00 nm-applet --sm-
jonathan  1950  0.0  0.9 221800 19500 ?        S    22:27   0:00 python /usr/sha
jonathan  1952  0.0  0.3 162696  7844 ?        S    22:27   0:00 /usr/lib/gnome-
jonathan  1954  0.0  0.4 157264  8924 ?        S    22:27   0:00 gnome-power-man
jonathan  1956  0.0  0.6 190228 12744 ?        S    22:27   0:00 update-notifier
jonathan  1958  0.0  0.5 259596 11956 ?        S    22:27   0:00 gnome-volume-co
jonathan  1959  0.0  0.6 201008 13588 ?        S    22:27   0:00 /usr/lib/policy
jonathan  1960  0.0  0.4 272072 10024 ?        Ss   22:27   0:00 /usr/bin/synce-
root      1962  0.0  0.2  59084  4124 ?        S    22:27   0:00 /usr/lib/policy
jonathan  1963  0.0  0.1 170888  3092 ?        Ss   22:27   0:00 gnome-screensav
root      1965  0.0  0.1  50896  3300 ?        S    22:27   0:00 /usr/lib/device
root      1966  0.0  0.0  42180   828 ?        S    22:27   0:00 devkit-disks-da
jonathan  1970  0.0  0.6 240840 14272 ?        S    22:27   0:00 /usr/lib/gnome-
jonathan  1972  0.0  0.1  70688  3496 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  1975  0.0  0.1  58268  3520 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  1977  0.0  0.1  50504  2484 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  1981  0.0  0.7 250096 15216 ?        S    22:27   0:00 /usr/lib/indica
root      1987  0.0  0.0   6464  1080 ?        S    22:27   0:00 /sbin/dhclient
jonathan  1991  0.0  0.1  95384  3736 ?        S    22:27   0:00 /usr/lib/indica
jonathan  1993  0.0  0.1  42172  2360 ?        S    22:27   0:00 /usr/lib/indica
jonathan  1995  0.0  0.1  51092  3044 ?        S    22:27   0:00 /usr/lib/indica
jonathan  2009  0.0  0.1  34848  2104 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  2011  0.0  0.1  43224  2484 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  2079  0.0  5.3 453168 110704 ?       Sl   22:27   0:02 /usr/lib/evolut
jonathan  2083  0.0  0.6 418056 13680 ?        Sl   22:27   0:00 /usr/lib/evolut
jonathan  2102  0.0  0.6 429216 14108 ?        Sl   22:27   0:00 /usr/lib/evolut
jonathan  2134  0.2  0.8 106384 17560 ?        Sl   22:27   0:08 /usr/bin/python
jonathan  2201  0.0  0.0   4004   632 ?        S    22:27   0:00 /bin/sh -e /usr
jonathan  2228  0.0  0.0   4004   364 ?        S    22:27   0:00 /bin/sh -e /usr
jonathan  2229  1.3  0.8 108636 16488 ?        Sl   22:27   0:47 /usr/lib/erlang
jonathan  2239  0.0  0.0   3772   492 ?        Ss   22:27   0:00 heart -pid 2229
jonathan  2256  0.0  0.1  78984  3896 ?        S    22:27   0:00 /usr/lib/gvfs/g
jonathan  2258  5.5  6.0 874140 123536 ?       Sl   22:27   3:10 /usr/lib/firefo
jonathan  2319  0.0  0.1  74448  3984 ?        Ss   22:27   0:00 /usr/lib/couchd
jonathan  2389  6.4  3.0 903156 62104 ?        Sl   22:28   3:41 /usr/lib/jvm/ja
jonathan  2468  0.5  0.8  72016 18288 ?        S    22:28   0:19 /usr/lib/nsplug
root      2966  1.1  0.0  15224  1380 ?        Ss   23:11   0:09 /sbin/mount.ntf
jonathan  3066  6.5  0.7 230116 15584 ?        Rl   23:25   0:00 gnome-terminal
jonathan  3067  0.0  0.0  14396   784 ?        S    23:25   0:00 gnome-pty-helpe
jonathan  3068  2.8  0.2  21416  4176 pts/0    Ss   23:25   0:00 bash
jonathan  3087  0.0  0.0  15164  1140 pts/0    R+   23:25   0:00 ps -aux

---

### Post by d3v1150m471c on 2010-01-23
Humor me and tell me what this says. Hopefully we'll get to the bottom of this. 
```

df -h

```

---

### Post by d3v1150m471c on 2010-01-23
Your computer is telling me conflicting data. It says all your ram is being used up yet your processes are fairly normal. In other words it should be showing me that you're running a buttload of stuff in the background but you're not. This is a hardware issue. I'm 99% sure. You need to do a hard reset and see if it fixes the issue as computers can become confused with managing power to all their chips and whatnot. If this doesn't fix it then something is unfortunately probably broken in your hardware.

---

### Post by Jonners59 on 2010-01-23
I'm still there.

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  782M  96% /
udev                 1005M  264K 1004M   1% /dev
none                 1005M  336K 1004M   1% /dev/shm
none                 1005M  212K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda2              98G   42G   57G  43% /host
/dev/sda5             149G  3.2G  146G   3% /media/Documents

---

### Post by falconindy on 2010-01-23
This is not a RAM usage warning. This is indeed low disk space. Notice that its a Wubi install -- as per your original screenshots of the disk space analyzer, you've got 16.6gb dedicated to Ubuntu and you're running at 90%+ capacity. It doesn't matter how much space you have available for Windows because you're required to create a separate filesystem on top of Windows for Ubuntu to run in.

You can start by cleaning up downloaded packages:
```
sudo apt-get autoclean && sudo apt-get clean
```
And then check for any stray log files that might be taking up a lot of space:
```
ls -lh /var/log
```

---

### Post by Jonners59 on 2010-01-23
OK Done that.  Any way of increasing the space available...


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del firefox-3.5-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [93.5kB]
Del bind9-host 1:9.6.1.dfsg.P1-3ubuntu0.2 [66.2kB]
Del gnome-screensaver 2.28.0-0ubuntu3.2 [4,186kB]
Del dnsutils 1:9.6.1.dfsg.P1-3ubuntu0.2 [157kB]
Del xulrunner-1.9.1-gnome-support 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [47.8kB]
Del libisccfg50 1:9.6.1.dfsg.P1-3ubuntu0.2 [51.2kB]
Del firefox-3.5-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 [206kB]
Del libgssapi-krb5-2 1.7dfsg~beta3-1ubuntu0.1 [114kB]
Del libkrb5-3 1.7dfsg~beta3-1ubuntu0.1 [354kB]
Del firefox 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.4kB]
Del transmission-common 1.75-0ubuntu2.1 [176kB]
Del liblwres50 1:9.6.1.dfsg.P1-3ubuntu0.2 [47.3kB]
Del firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 [960kB]
Del transmission-gtk 1.75-0ubuntu2.1 [318kB]
Del firefox-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 [73.3kB]
Del libdns50 1:9.6.1.dfsg.P1-3ubuntu0.2 [14.5kB]
Del acroread 9.2-1karmic1 [63.5MB]
Del libisc50 1:9.6.1.dfsg.P1-3ubuntu0.2 [167kB]
Del libdns53 1:9.6.1.dfsg.P1-3ubuntu0.2 [656kB]
Del libisccc50 1:9.6.1.dfsg.P1-3ubuntu0.2 [29.1kB]
Del xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 [9,101kB]
Del libbind9-50 1:9.6.1.dfsg.P1-3ubuntu0.2 [33.2kB]
Del libkrb5support0 1.7dfsg~beta3-1ubuntu0.1 [41.4kB]
Del libk5crypto3 1.7dfsg~beta3-1ubuntu0.1 [110kB]
jonathan@ubuntu:~$ ls -lh /var/log
total 13M
drwxr-xr-x 2 root              root    4.0K 2009-10-17 05:46 apparmor
drwxr-xr-x 2 root              root    4.0K 2009-10-27 17:58 apt
-rw-r----- 1 syslog            adm      22K 2010-01-23 23:56 auth.log
-rw-r----- 1 syslog            adm      31K 2010-01-17 09:17 auth.log.1
-rw-r----- 1 syslog            adm     3.8K 2010-01-10 08:19 auth.log.2.gz
-rw-r----- 1 root              adm       31 2009-10-27 17:56 boot
-rw-r--r-- 1 root              root     40K 2009-10-27 17:57 bootstrap.log
-rw-rw-r-- 1 root              utmp       0 2009-10-27 17:56 btmp
-rw-r--r-- 1 root              root       0 2010-01-04 07:30 checkbox.log
-rw-r--r-- 1 root              root     55K 2010-01-04 07:30 checkbox.log.1
drwxr-xr-x 2 clamav            clamav  4.0K 2010-01-17 09:42 clamav
drwxr-xr-x 2 root              root    4.0K 2010-01-17 09:42 ConsoleKit
drwxr-xr-x 2 root              root    4.0K 2010-01-23 15:37 cups
-rw-r----- 1 syslog            adm     397K 2010-01-23 23:56 daemon.log
-rw-r----- 1 syslog            adm     604K 2010-01-17 09:41 daemon.log.1
-rw-r----- 1 syslog            adm      49K 2010-01-10 08:44 daemon.log.2.gz
-rw-r----- 1 syslog            adm     544K 2010-01-23 22:27 debug
-rw-r----- 1 syslog            adm     446K 2010-01-17 09:13 debug.1
-rw-r----- 1 syslog            adm      40K 2010-01-10 08:22 debug.2.gz
drwxr-xr-x 2 root              root    4.0K 2009-10-23 17:41 dist-upgrade
-rw-r--r-- 1 root              root    3.4K 2010-01-23 22:26 dkms_autoinstaller
-rw-r----- 1 root              adm      47K 2010-01-23 22:26 dmesg
-rw-r----- 1 root              adm      47K 2010-01-23 21:55 dmesg.0
-rw-r----- 1 root              adm      13K 2010-01-23 20:48 dmesg.1.gz
-rw-r----- 1 root              adm      13K 2010-01-23 15:13 dmesg.2.gz
-rw-r----- 1 root              adm      13K 2010-01-22 19:36 dmesg.3.gz
-rw-r----- 1 root              adm      13K 2010-01-22 15:29 dmesg.4.gz
-rw-r--r-- 1 root              root    1.5M 2010-01-23 22:06 dpkg.log
drwxrwx--- 2 root              dialout 4.0K 2006-06-21 05:57 efax
-rw-r--r-- 1 root              root     32K 2010-01-03 23:32 faillog
-rw-r--r-- 1 root              root    2.2K 2009-10-27 18:13 fontconfig.log
drwxr-xr-x 2 root              root    4.0K 2009-10-27 17:56 fsck
drwxrwx--T 2 root              gdm     4.0K 2010-01-23 22:26 gdm
drwxr-xr-x 2 root              root    4.0K 2010-01-03 21:15 installer
-rw-r--r-- 1 root              root       0 2010-01-05 07:20 jockey.log
-rw-r--r-- 1 root              root     28K 2010-01-05 07:20 jockey.log.1
-rw-r--r-- 1 root              root    6.9K 2010-01-04 07:30 jockey.log.2.gz
-rw-r----- 1 syslog            adm     1.9M 2010-01-23 23:11 kern.log
-rw-r----- 1 syslog            adm     1.5M 2010-01-17 09:24 kern.log.1
-rw-r----- 1 syslog            adm     317K 2010-01-10 08:29 kern.log.2.gz
-rw-rw-r-- 1 root              utmp    286K 2010-01-03 23:32 lastlog
-rw-r----- 1 syslog            adm      88K 2010-01-23 22:26 lpr.log
-rw-r----- 1 syslog            adm      81K 2010-01-17 09:12 lpr.log.1
-rw-r----- 1 syslog            adm     3.5K 2010-01-10 08:14 lpr.log.2.gz
-rw-r----- 1 syslog            adm        0 2010-01-03 21:20 mail.err
-rw-r----- 1 syslog            adm        0 2010-01-03 21:20 mail.info
-rw-r----- 1 syslog            adm        0 2010-01-03 21:20 mail.log
-rw-r----- 1 syslog            adm        0 2010-01-03 21:20 mail.warn
-rw-r----- 1 syslog            adm     1.4M 2010-01-23 23:11 messages
-rw-r----- 1 syslog            adm     1.1M 2010-01-17 09:42 messages.1
-rw-r----- 1 syslog            adm     257K 2010-01-10 08:44 messages.2.gz
-rw-r--r-- 1 root              root       0 2010-01-03 23:14 MountManager.log
drwxr-xr-x 2 root              root    4.0K 2010-01-03 21:20 news
-rw-r--r-- 1 root              root     45K 2010-01-23 22:26 pm-powersave.log
-rw-r--r-- 1 root              root     92K 2010-01-12 07:13 popularity-contest
-rw-r--r-- 1 root              root     94K 2010-01-05 07:21 popularity-contest.0
-rw-r--r-- 1 root              root      41 2010-01-05 07:21 popularity-contest.1.gz
-rw-r--r-- 1 root              root       0 2010-01-10 14:19 ppp-connect-errors
-rw-r--r-- 1 root              root       0 2009-10-27 17:57 pycentral.log
drwxr-xr-x 3 root              root    4.0K 2010-01-17 09:42 samba
drwxr-xr-x 2 speech-dispatcher root    4.0K 2009-10-13 06:27 speech-dispatcher
-rw-r----- 1 syslog            adm     319K 2010-01-23 23:56 syslog
-rw-r----- 1 syslog            adm     303K 2010-01-23 15:36 syslog.1
-rw-r----- 1 syslog            adm      72K 2010-01-22 07:13 syslog.2.gz
-rw-r----- 1 syslog            adm      71K 2010-01-21 08:09 syslog.3.gz
-rw-r----- 1 syslog            adm     144K 2010-01-20 07:37 syslog.4.gz
-rw-r----- 1 syslog            adm      37K 2010-01-18 07:33 syslog.5.gz
-rw-r----- 1 syslog            adm      38K 2010-01-17 09:41 syslog.6.gz
-rw-r----- 1 syslog            adm      73K 2010-01-16 10:51 syslog.7.gz
-rw-r--r-- 1 root              root    186K 2010-01-23 22:26 udev
drwxr-xr-x 2 root              root    4.0K 2010-01-20 07:38 unattended-upgrades
-rw-r----- 1 syslog            adm      18K 2010-01-23 22:26 user.log
-rw-r----- 1 syslog            adm     5.0K 2010-01-17 09:12 user.log.1
-rw-r----- 1 syslog            adm     3.4K 2010-01-10 08:15 user.log.2.gz
-rw-rw-r-- 1 root              utmp    345K 2010-01-23 23:50 wtmp
-rw-r--r-- 1 root              root     14K 2010-01-23 22:26 Xorg.0.log
-rw-r--r-- 1 root              root     14K 2010-01-23 22:25 Xorg.0.log.old
jonathan@ubuntu:~$ ^C

---

### Post by Jonners59 on 2010-01-23
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   14G  1.3G  92% /
udev                 1005M  264K 1004M   1% /dev
none                 1005M  336K 1004M   1% /dev/shm
none                 1005M  212K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda2              98G   42G   57G  43% /host
/dev/sda5             149G  3.2G  146G   3% /media/Documents

---

### Post by falconindy on 2010-01-23
Hmm... use the disk usage analyzer to drill down through "/ -> Hosts -> Ubuntu -> Disks" to find out where all that space is being occupied. 16gb is an awful lot of space to be used by a root partition. I've been exceedingly conservative with my install  (non-Ubuntu), but my root partition is only 3gb.

---

### Post by Jonners59 on 2010-01-24
If I am not mistaken it's the root disk = 16G  See attachments

Why are these partitions and not folders?  If they were folders then size does not matter so much.

Going through the analyser there are many folders/partitions that show red...  Is that a problem?

Anyway screen shots enclosed for you.

---

### Post by falconindy on 2010-01-24
My bad... host is apparently the Windows side so all you're seeing are the image files for the boot and root disks. What we're interested in is actually at the bottom of those screenshots where you see usr/ home/ etc/ ....

---

### Post by Saiko Berry on 2010-01-24
They create partitions of those things so that if your system gets ruined you can easilly recreate the data sectors by mounting the partitions over a newly installed version of ubuntu.

We need to know more about where data is allocated on your ubuntu install, since Wubi is a program essentially..

If worst comes to worst, seriously, just dualboot windows over ubuntu. Wubi is horrible..

---

### Post by luffy_chan_19 on 2010-01-24
yeah when your computer says low on memory it ussualy means. you are running too much stuff close some stuff and your computer wont display this message, you might have too many things loading at startup as well, etc there is a significant difference between memmory and storage. it would tell you low on disk space if you were low on HDD space, and then it would tell you how much space you have left and suggest some cleanup options

---

### Post by Jonners59 on 2010-01-24
> **falconindy said:**
> My bad... host is apparently the Windows side so all you're seeing are the image files for the boot and root disks. What we're interested in is actually at the bottom of those screenshots where you see usr/ home/ etc/ ....

I'm not sure what you need:  Do you want me to go to user and scan and show all levels???  Or just show the current level, but include the lines below?

Just spent an hour going through a HUGE list.  No way can I get all these screen shots so I am assuming I have misunderstood you.
:confused:

---

### Post by Jonners59 on 2010-01-24
> **luffy_chan_19 said:**
> yeah when your computer says low on memory it ussualy means. you are running too much stuff close some stuff and your computer wont display this message, you might have too many things loading at startup as well, etc there is a significant difference between memmory and storage. it would tell you low on disk space if you were low on HDD space, and then it would tell you how much space you have left and suggest some cleanup options

It did say how much was left and to remove some files, suggesting empty the watebasket.  With falconindy's support we have checked the running app and he seems to think that there is not too much, see below....

Could you explain more, help me check and help with a fix please....

---

### Post by Jonners59 on 2010-01-24
> **Saiko Berry said:**
> They create partitions of those things so that if your system gets ruined you can easilly recreate the data sectors by mounting the partitions over a newly installed version of ubuntu.

We need to know more about where data is allocated on your ubuntu install, since Wubi is a program essentially..

If worst comes to worst, seriously, just dualboot windows over ubuntu. Wubi is horrible..

1. That's interesting.  How would I repair in this way

2. And how do you "dualboot windows over ubuntu???  Sounds interesting

---

### Post by falconindy on 2010-01-24
> **Jonners59 said:**
> 1. That's interesting.  How would I repair in this way

2. And how do you "dualboot windows over ubuntu???  Sounds interesting
[[img]http://omploader.org/tM2NnZw[/img]](http://omploader.org/vM2NnZw)
Ok, I'm an idiot... look at the red outlined section. Notice the first three listings where you have 9.3GB in /home and 4GB in /usr. That's nearly 14gb combined. I don't think your documents are being stored where you think they are. /usr is where applications live, and /home is for users on the system to store their personal files.

Saiko Berry is misleading you -- not sure what their reference to "recreating sectors" means. The way Wubi works is this:
1) Write out a bunch of zeroes to a file in an area of empty disk of user specified size (in your case its 17gb).
2) Format this file with a Linux based file system, such as Ext4
3) Using what's known as a "block loopback device", mount the file as a useable filesystem and install Ubuntu within it. This essentially simulates a hard drive with this formatted file.

Because of this, you essentially end up with a filesystem on top of a filesystem (e.g. Ext4 on top of NTFS). You have the "benefit" of having everything neatly quarantined within the loopback, but it also means extra overhead in order to access it.

Dual booting is a more robust solution wherein you install Ubuntu on a separate partition from Windows and use a bootloader such as Grub to decide where the computer boots into. Bootloaders and partitioning can be a little overwhelming to the uninitiated, so Wubi is a semi-reasonable middle ground.

---

### Post by Jonners59 on 2010-01-25
> **falconindy said:**
> [[IMG]http://omploader.org/tM2NnZw[/IMG]]("http://omploader.org/vM2NnZw")
Ok, I'm an idiot... look at the red outlined section. Notice the first three listings where you have 9.3GB in /home and 4GB in /usr. That's nearly 14gb combined. I don't think your documents are being stored where you think they are. /usr is where applications live, and /home is for users on the system to store their personal files.

OK.
I know files are kept in the separate 150G part ion, in windows labelled E and not shown above.  No question of that.
I did crate 2 partitions for the 2 OS, one each, but from what you show here when ubuntu installs it integrates with the Windows install in some way.  I ran System Monitor.  It showed 2 drives/partitions (not all).  Note dev/loop0 is 16G with only 1.9G free.  I clicked this and it had the folders you mentioned.. See second screenshot.  The other drive had a mix of Windows and Ubuntu folders, but should be just Windows, but it has plenty of space so I am not too fussed.

I would need to open in Windows to find these files to know where exactly they have been created by the Ubuntu install.
So that said.  I hate waste, so what is making them so large, if they need not be and how can I make the folder bigger.  IF it is where it should be, in the partition I created for it (Ubuntu) then it SHOULD have 60G to play with, not just 16G.????

Hope I am reading you correctly in this.

PS the other stuff, many thanks, very interesting.  Bit beyond my skill set, certainly for now!

---

### Post by Jonners59 on 2010-01-28
Any further thoughts and advise, please?

---

### Post by Jonners59 on 2010-02-01
[SIZE=5][B]HELP ME PLEASE SOMEONE!!!!!!!

How do I increase storage in existing folders - see below?
[/B][/SIZE]

---

