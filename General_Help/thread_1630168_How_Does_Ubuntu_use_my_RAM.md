---
title: "How Does Ubuntu use my RAM"
date: 2010-11-24
forum: General Help
---

### Post by hurdevan on 2010-11-24
Well what does Ubuntu do with ram? I know that Ubuntu is not stingy with it. And I like that. But, what I don't like is when Ubuntu starts putting memory pages into the swap causing programs to be slow when they start running again; for example, gnome-do.

Of course the simple solution to this problem is to turn of Compiz and use Openbox instead of Metacity because my problems only exist when they are running. But I absolutely love Compiz and I would like to continue use it.

However, using Compiz(mainly) tends to take a huge draw from the system that I cannot identify.

Running "free -m" gives me: 
> 
             total       used       free     shared    buffers     cached
Mem:          1001        981         19          0          5        269
-/+ buffers/cache:        706        294
Swap:         1609        376       1233


In theory, if I add the Used + Free + Shared + Buffers + Cached it should all equal the Total. Write.... Please Tell me if that is not how that works.

However, 981 + 19 + 0 + 5 + 269 = 1,274 not 1001 or a just a Gig.

Anyhow, I am trying to figure out a logical conclusions why all of my RAM  + 376 of Swap is being used. There are no application that use alot of ram besides firefox(100Mb) so I cannot think of why so much is being used.




And if yall want here is a "ps aux" output

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2880  1216 ?        Ss   08:23   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    08:23   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    08:23   0:01 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    08:23   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    08:23   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    08:23   0:02 [events/0]
root         7  0.0  0.0      0     0 ?        S    08:23   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    08:23   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    08:23   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    08:23   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    08:23   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    08:23   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    08:23   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    08:23   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    08:23   0:01 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    08:23   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    08:23   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    08:23   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    08:23   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    08:23   0:02 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    08:23   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    08:23   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    08:23   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    08:23   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    08:23   0:05 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   08:23   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    08:23   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    08:23   0:00 [ecryptfs-kthr]
root        30  0.0  0.0      0     0 ?        S    08:23   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    08:23   0:00 [scsi_eh_0]
root        38  0.0  0.0      0     0 ?        S    08:23   0:04 [scsi_eh_1]
root        42  0.0  0.0      0     0 ?        S    08:23   0:00 [kstriped]
root        43  0.0  0.0      0     0 ?        S    08:23   0:00 [kmpathd/0]
root        44  0.0  0.0      0     0 ?        S    08:23   0:00 [kmpath_handle]
root        45  0.0  0.0      0     0 ?        S    08:23   0:00 [ksnapd]
root        46  0.0  0.0      0     0 ?        S    08:23   0:18 [kondemand/0]
root        47  0.0  0.0      0     0 ?        S    08:23   0:00 [kconservative]
root       241  0.0  0.0      0     0 ?        S    08:23   0:01 [jbd2/sda1-8]
root       242  0.0  0.0      0     0 ?        S    08:23   0:00 [ext4-dio-unwr]
root       275  0.0  0.0      0     0 ?        S    08:23   0:01 [flush-8:0]
root       304  0.0  0.0   2396   328 ?        S    08:23   0:00 upstart-udev-br
root       306  0.0  0.0   2748   260 ?        S<s  08:23   0:00 udevd --daemon
root       450  0.0  0.0   2744   240 ?        S<   08:23   0:00 udevd --daemon
root       475  0.0  0.0      0     0 ?        S    08:23   0:00 [kpsmoused]
root       476  0.0  0.0   2744   240 ?        S<   08:23   0:00 udevd --daemon
root       587  0.0  0.0      0     0 ?        S    08:24   0:00 [cfg80211]
root       621  0.0  0.0      0     0 ?        S    08:24   0:00 [pccardd]
root       635  0.0  0.0      0     0 ?        S    08:24   0:00 [ktpacpid]
root       669  0.0  0.0      0     0 ?        S    08:24   0:00 [radeon/0]
root       670  0.0  0.0      0     0 ?        S    08:24   0:01 [ttm_swap]
root       674  0.0  0.0      0     0 ?        S    08:24   0:00 [pccardd]
root       677  0.0  0.0      0     0 ?        S    08:24   0:02 [ipw2200/0]
root       710  0.0  0.0  16720   972 ?        Ss   08:24   0:00 smbd -F
root       717  0.0  0.0      0     0 ?        S<   08:24   0:10 [kslowd000]
syslog     721  0.0  0.0  33572   508 ?        Sl   08:24   0:00 rsyslogd -c4
root       723  0.0  0.0      0     0 ?        S<   08:24   0:10 [kslowd001]
102        743  0.0  0.1   3480  1444 ?        Ss   08:24   0:03 dbus-daemon --s
root       761  0.0  0.2  19544  2188 ?        Ssl  08:24   0:00 gdm-binary
root       765  0.0  0.2  19256  2732 ?        Ssl  08:24   0:05 NetworkManager
avahi      772  0.0  0.1   3140  1036 ?        S    08:24   0:00 avahi-daemon: r
avahi      775  0.0  0.0   3016   160 ?        S    08:24   0:00 avahi-daemon: c
root       782  0.0  0.1   4432  1668 ?        S    08:24   0:00 /usr/sbin/modem
root       785  0.0  0.0  16720   108 ?        S    08:24   0:00 smbd -F
root       808  0.0  0.1  20096  1980 ?        Sl   08:24   0:00 /usr/sbin/conso
root       816  0.0  0.0   4904   992 ?        S    08:24   0:00 /sbin/wpa_suppl
root       886  0.0  0.1  21540  2048 ?        Sl   08:24   0:00 /usr/lib/gdm/gd
root       962  0.0  0.0   7036   856 ?        Ss   08:24   0:00 /usr/sbin/cupsd
root       981  0.0  0.0   1860   416 tty4     Ss+  08:24   0:00 /sbin/getty -8
root       987  0.0  0.0   1860   420 tty5     Ss+  08:24   0:00 /sbin/getty -8
root       997  0.0  0.0   1860   420 tty2     Ss+  08:24   0:00 /sbin/getty -8
root       999  0.0  0.0   1860   420 tty3     Ss+  08:24   0:00 /sbin/getty -8
root      1003  0.0  0.0   1860   420 tty6     Ss+  08:24   0:00 /sbin/getty -8
root      1006  0.0  0.0   2380   468 ?        Ss   08:24   0:00 acpid -c /etc/a
root      1058  0.0  0.0   2460   672 ?        Ss   08:24   0:00 cron
daemon    1059  0.0  0.0   2320   140 ?        Ss   08:24   0:00 atd
root      1082  0.0  0.0   1840   340 ?        S    08:24   0:00 /usr/sbin/hddte
root      1097  0.0  0.0   3096   516 ?        Ss   08:24   0:01 /usr/sbin/netda
root      1111  6.1  7.5 110460 77776 tty7     Ss+  08:24  35:36 /usr/bin/X :0 -
root      1112  0.0  0.0  13340   648 ?        Ss   08:24   0:00 /usr/sbin/winbi
root      1193  0.0  0.0  13408   328 ?        S    08:24   0:00 /usr/sbin/winbi
root      1254  0.0  0.0   1860   420 tty1     Ss+  08:24   0:00 /sbin/getty -8
gdm       1273  0.0  0.0   3460   288 ?        S    08:24   0:00 /usr/bin/dbus-l
root      1301  0.0  0.1  25652  1868 ?        Sl   08:24   0:00 /usr/lib/gdm/gd
root      1305  0.0  0.3  10044  3616 ?        S    08:24   0:03 /usr/lib/upower
root      1326  0.0  0.2   7020  2856 ?        S    08:24   0:01 /usr/lib/policy
root      1389  0.0  0.0  13592   776 ?        S    08:24   0:00 /usr/sbin/winbi
evan      1392  0.0  0.1  24984  1512 ?        Sl   08:24   0:00 /usr/bin/gnome-
evan      1411  0.0  0.4  36064  4780 ?        Ssl  08:24   0:00 gnome-session
evan      1446  0.0  0.0   3352    16 ?        Ss   08:24   0:00 /usr/bin/ssh-ag
evan      1449  0.0  0.0   3460   288 ?        S    08:24   0:00 /usr/bin/dbus-l
evan      1450  0.1  0.1   5016  1996 ?        Ss   08:24   1:07 /bin/dbus-daemo
evan      1455  0.0  0.3   9380  3804 ?        S    08:24   0:10 /usr/lib/libgco
evan      1460  0.1  0.3  24472  3700 ?        Sl   08:24   1:07 /usr/lib/at-spi
evan      1461  0.2  0.7 101284  7488 ?        Ssl  08:24   1:21 /usr/lib/gnome-
evan      1468  0.0  0.2  50856  2480 ?        Ssl  08:24   0:00 /usr/lib/bonobo
evan      1470  0.0  0.1   7552  1740 ?        S    08:24   0:00 /usr/lib/gvfs/g
evan      1477  0.0  0.1  30656  1168 ?        Ssl  08:24   0:00 /usr/lib/gvfs//
evan      1484  0.0  0.2  15344  2316 ?        SNl  08:24   0:00 /usr/bin/deskto
evan      1486  0.0  0.3  20724  3688 ?        S    08:24   0:00 /usr/lib/policy
evan      1487  0.3  0.7  70648  7964 ?        Sl   08:24   1:47 compiz
evan      1489  0.0  0.7 262964  7876 ?        Sl   08:24   0:02 nm-applet --sm-
evan      1493  0.0  0.0   1900   332 ?        S    08:24   0:00 /bin/sh /usr/bi
evan      1495  0.0  0.3  95840  3672 ?        S<sl 08:24   0:19 /usr/bin/pulsea
rtkit     1497  0.0  0.0  22996   852 ?        SNl  08:24   0:00 /usr/lib/rtkit/
evan      1519  0.2  1.5  61680 16000 ?        SLl  08:24   1:24 /usr/bin/python
evan      1531  0.1  2.2 131784 22872 ?        SLl  08:24   0:40 /usr/bin/cli /u
evan      1532  0.0  1.2 232980 12452 ?        Ssl  08:24   0:21 /home/evan/.dro
evan      1540  0.0  0.1  20684  1780 ?        Sl   08:24   0:00 /usr/lib/pulsea
evan      1552  0.0  0.1  27956  1844 ?        Ss   08:24   0:00 gnome-screensav
evan      1554  0.0  0.2   8784  2468 ?        S    08:24   0:00 /usr/lib/gvfs/g
root      1556  0.0  0.2  16088  2424 ?        Sl   08:24   0:01 /usr/lib/udisks
root      1557  0.0  0.0   2300   560 ?        S    08:24   0:00 /sbin/dhclient
root      1558  0.0  0.0   5616   496 ?        S    08:24   0:06 udisks-daemon: 
evan      1562  0.0  0.1  18000  1620 ?        Sl   08:24   0:01 /usr/lib/gvfs/g
evan      1565  0.0  0.1   8192  1588 ?        S    08:24   0:00 /usr/lib/gvfs/g
evan      1657  0.0  0.1   7428  1736 ?        S    08:24   0:00 /usr/lib/gvfs/g
root      1694  0.0  0.0   9360   996 ?        Ss   08:25   0:00 nmbd -D
evan      1702  0.0  0.5  34012  5596 ?        S    08:25   0:07 /usr/bin/python
evan      1714  0.0  0.0   1900   328 ?        Ss   08:25   0:00 /bin/sh -c /usr
evan      1715  0.0  0.8 109284  8440 ?        Sl   08:25   0:05 /usr/bin/gtk-wi
evan      1756  0.0  0.7  76432  8000 ?        Sl   08:25   0:04 /usr/lib/notify
evan      1820  0.0  0.0      0     0 ?        Zs   08:28   0:00 [gno] <defunct>
evan      1823  0.0  0.2  19848  2192 ?        Sl   08:28   0:00 /usr/lib/gvfs/g
evan      2524  0.0  0.5  30768  5832 ?        Sl   09:37   0:01 /usr/bin/python
evan      2527  0.0  0.0   3900   116 ?        S    09:38   0:00 /bin/cat
evan      2530  0.0  0.7  32852  7744 ?        S    09:38   0:00 /usr/bin/python
evan      2890  0.1  1.2 195140 12484 ?        Sl   09:42   0:49 gnome-panel
evan      2919  0.0  0.7 138128  7180 ?        Sl   09:42   0:00 /usr/bin/gnote
evan      2920  0.0  0.5 112660  6128 ?        Sl   09:42   0:00 /usr/lib/byzanz
evan      2922  0.0  1.1 218928 11332 ?        Sl   09:42   0:21 /usr/lib/gnome-
evan      2923  0.0  0.8 163088  8400 ?        Sl   09:42   0:01 /usr/lib/indica
evan      2924  0.0  0.5  31220  5160 ?        Sl   09:42   0:00 /usr/lib/gnome-
evan      2925  0.0  0.9 156864  9952 ?        Sl   09:42   0:17 /usr/lib/gnome-
evan      2926  0.0  1.2 213084 12772 ?        Sl   09:42   0:02 python /usr/lib
evan      2948  0.0  0.2  18064  2444 ?        S    09:42   0:00 /usr/lib/indica
evan      2950  0.0  0.2  87268  2796 ?        S    09:42   0:00 /usr/lib/indica
evan      2952  0.0  0.2  15720  2080 ?        S    09:42   0:00 /usr/lib/indica
evan      3033  0.0  0.7 146856  7652 ?        Sl   09:53   0:03 evolution task:
evan      4304  0.5  2.7 271496 28568 ?        Sl   13:42   1:21 nautilus --no-d
evan      4309  0.0  0.2   7804  2248 ?        S    13:42   0:00 /usr/lib/gvfs/g
evan      4311  0.0  0.1   7452  1708 ?        S    13:42   0:00 /usr/lib/gvfs/g
evan      4406  0.0  0.5  36188  5512 ?        S    13:55   0:00 python /usr/sha
evan      4987  0.0  0.0   1900   400 ?        S    15:45   0:00 /bin/sh /usr/li
evan      4991  0.0  0.0   1900   396 ?        S    15:45   0:00 /bin/sh /usr/li
evan      4995  4.4 10.2 618888 104656 ?       Sl   15:45   6:02 /usr/lib/firefo
evan      5066  0.0  1.1  84504 11420 ?        Sl   15:46   0:00 /usr/lib/firefo
evan      5079  0.0  2.0 225908 21252 ?        Sl   15:47   0:03 /usr/bin/python
evan      5083  0.0  0.0   2056   616 ?        S    15:47   0:00 gnome-pty-helpe
evan      5084  0.0  0.3   7524  3552 pts/1    Ss+  15:47   0:00 /bin/bash
evan      5808  0.1  1.2 172156 12992 ?        Sl   16:02   0:12 /usr/bin/gnome-
evan      5812  0.0  0.0   2056   624 ?        S    16:02   0:00 gnome-pty-helpe
evan      5813  0.0  0.3   7528  3612 pts/2    Ss   16:02   0:00 /bin/bash
root      5867  0.0  0.1  10092  1396 pts/2    S    16:02   0:00 su
root      5876  0.0  0.1   5252  1400 pts/2    S    16:02   0:00 bash
evan      5970  0.0  1.2 155968 12328 ?        Sl   16:11   0:05 /usr/lib/gnome-
evan      5979  0.1  1.1 155860 11428 ?        Sl   16:12   0:09 /usr/lib/gnome-
evan      6041  0.1  1.7 183612 18016 ?        Sl   16:17   0:07 gedit /usr/bin/
evan      6102  0.0  0.2  21340  2096 ?        Sl   16:22   0:00 /usr/lib/d-conf
evan      6111 14.8  1.3 161892 14028 ?        Sl   16:23  14:27 gnome-system-mo
evan      6276  0.0  1.2 156940 13244 ?        Sl   16:32   0:01 gcalctool
root      6673  0.0  0.1   4592  1072 pts/2    R+   18:00   0:00 ps aux

```


Cheers and thanks all

---

### Post by sisco311 on 2010-11-24
[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by KazaRgr on 2010-11-24
well i have same problems with system monitor's ram usage, even on openbox session (no gnome at all), after fresh boot it says about 350-450mb used ram and if u add everything that is running, it goess about 60-70mb & the same in gnome but with smaller difference (about 150mb)..

i didnt read the whole article in the link, but i got the point: ubuntu has an anorthodox way of showing its ram usage :P

---

### Post by hurdevan on 2010-11-25
Great Article..

So then, I should ask why does Compiz use so much ram that it causes running programs to be put in swap?

---

### Post by hurdevan on 2010-11-25
Oh, one more thing.

I just noticed that after closed all running process that my swap is HALF way full. It jumped 400MB since my first post and while I was at a party.

> 
             total       used       free     shared    buffers     cached
Mem:          1001        981         19          0         26        398
-/+ buffers/cache:        556        444
Swap:         1609        805        804



That is my free -m with no programs running except the start up programs.Yet, I am still using 600MB.


Oh and thanks very much

---

### Post by jocko on 2010-11-25
It is a bit weird that your computer uses that much swap while you still have 40% available ram.
You could see what happens if you tune down the tendency to swap (swappiness).
To turn down the swappiness to 0 (which will only use swap when there is very little available ram, default is 60 and max is 100):```
sudo sysctl vm.swappiness=0
```This change is not permanent and will be lost if you reboot.

To make it permanent:```
gksudo gedit /etc/sysctl.conf
```Add this line to the end of the file:```
vm.swappiness = 0
```To purge the swap:
```
sudo swapoff -a
sudo swapon -a
```Run it for a few hours or days to see if things are better or worse. If setting it to 0 leads to problems, try other numbers (lower than 60).

---

### Post by hurdevan on 2010-11-25
Great.. Thanks.

I will do that see whats happens.


Cheers

---

### Post by hurdevan on 2010-11-25
Ok everything worked so much better. ish...
My computer still likes to use 60% to 70% of the ram on process(not cached.) I really don't know where it goes because a all my process don't add up to 600Mb. Firefox and xorg are the highest(40MB AND 100mb) and just a couple process are in the teens and the rest are just blips. 

But my computer worked perfectly despite that fact. :-) Until that is, I closed the lid of my computer for an hour. When I opened the lid it was hell. My CPU nothing but stuck on IOwaits and I had to restart my computer.

At that time, I had 8 files, with no more then 100 lines in each file, open in gedit. Additionally, firefox was open and with just that my computer was a goner.

Oh yea, there was 32Mb in the swap

I really


Thanks and cheers

---

### Post by libssd on 2010-11-25
As long as it's not using swap, don't worry. You can tune this to some extent:

```
sudo gedit /etc/sysctl.conf
```

Here are the values I am using: 
```
   vm.swappiness = 1
   vm.vfs_cache_pressure = 50
   vm.dirty_writeback_centisecs = 20000
   vm.dirty_ratio = 90
   vm.dirty_background_ratio = 1
```

That said, when I had "only" 1gb of RAM, performance fell off a cliff when swap started being used; after going to 2gb of RAM, I have yet to see swap being used.

Ref: [http://help.ubuntu.com/community/SwapFaq](http://help.ubuntu.com/community/SwapFaq)

---

### Post by hurdevan on 2010-11-28
Hey Thanks all. 
I have fixed my swap problem.
However, There still is a memory leak.
The memory leak is only a problem when Compiz is running. 
I am darn sure there is a leak because the mem used by the application will slowly increase and stop around 80%(used by application) when only firefox is open. The rest of my mem is always used being used as cache. Firefox typically does not get over 150Mb. Also, all other running programs(roots as well) don't add up to 800Mb. So I have no clue where it goes.

This memory leak, in my opinion, has been here since Ubuntu 9.10. Thats when I started fed up with Ubuntu. I have posted my thoughts here before, but people only told me that Ubuntu used it as a cache. But, that is not really the case here. That when I got really fed up. 

Every time I go back to 9.04 my computer works great. But, I always git tired of the outdated programs and end of going back. I have also visited Fedora Core has the same issue when Compiz is running.

Any help would be great.

It could be a issue between my computer and ubuntu?

---

### Post by libssd on 2010-11-28
> **hurdevan said:**
> Every time I go back to 9.04 my computer works great. But, I always git tired of the outdated programs and end of going back. I have also visited Fedora Core has the same issue when Compiz is running.
If you see a similar memory leak with Fedora Core, that suggests the problem is with Compiz, not with Ubuntu. What happens if you turn off Compiz? I have always disabled all desktop effects for performance reasons in 9.04, 9.10, and 10.04. (Netbook, needs every bit of performance help it can get.)

What "outdated" programs are you stuck with in 9.04? When I was still running 9.04, I had no problem upgrading almost everything that I use to newer versions. The only issue I had was with the disk utility (palimpsest) that came with 10.04.

---

### Post by hurdevan on 2010-11-28
In 9.04 I could not update programs to the same versions that 9.10 or later had without manually updating a bunch of dependencies and braking my system.

After killing compiz and gtk-windows-decorator(Which Compiz uses) got back almost 200MB or ram uses by running processes and also any space the cache took up. Both programs only were about 16Mb each; but, compiz was running two sessions.  Still, I am missing allot of ram. On average, 9.04 only used 200-300MB of ram. Now on average I am using 800MB by programs.

---

### Post by libssd on 2010-11-28
Interesting. Immediately after boot (no Compiz, no visual effects), System Monitor reports that 10.04 uses about 142MiB of RAM. I just opened Chrome (3 tabs), and (using Open Office 3.3) 2 spreadsheets, 2 word processing docs, plus two PDF files, and a terminal window, and System Manager shows only a little more than 400MiB of memory (20%) in use.

I've always wondered why System Monitor and free -m seem to report such different numbers:

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003       1109        894          0         33        672
-/+ buffers/cache:        403       1600
Swap:         1492          0       1492

```

---

### Post by hurdevan on 2010-11-29
I think its because System Monitor does not use Megabytes but Mebibytes. Notice its Mib. I do believe that it is the system of measurements used by hard drives since they are not bound by the 8bit rule.

Hey does anybody know if there is anyway to examine the ram and see what process is responsible for putting what where?

---

### Post by hurdevan on 2010-12-04
I am still having the issue.
But now that I have been running Compiz more I have realized that when I reach 80% of ram used by programs then the system will lockup on IO waits.
Also, the ram usage will increase only when the computer is being used. 

So, out of curiosity I created a program that would log the ps aux output every hour. I then restarted the computer and ran compiz untill the mem reached about 75%. Again, I restarted the computer and used openbox. I logged about 5 hours for each. Then I took the logs and calculated the average of each programs mem usage for each Compiz and Openbox session.
I also took the overall average all the programs from each Compiz and Openbox statistics 

Well, guess which had a lower average.

Compix Average: 0.858010651629073
Opebox Average: 0.883755144032922

Not by much but...

```

/sbin/init -- 0.1 -- 0.1
avahi-daemon: -- 0 -- 0
/usr/sbin/modem-manager -- 0.2 -- 0.2
/sbin/wpa_supplicant -- 0.175 -- 0.2
smbd -- 0.185714285714286 -- 0.2
/sbin/getty -- 0 -- 0
acpid -- 0 -- 0.1
anacron -- 0 --
atd -- 0 -- 0
/usr/sbin/netdaemon -- 0 -- 0
/usr/sbin/winbindd -- 0.133333333333333 -- 0.133333333333333
gdm-binary -- 0.3 -- 0.3
/usr/sbin/console-kit-daemon -- 0.2 -- 0.3
/usr/lib/gdm/gdm-simple-slave -- 0.3 -- 0.3
/usr/bin/X -- 4.15 -- 4.1
/usr/sbin/cupsd -- 0.2 -- 0.2
/bin/sh -- 0 -- 0
sleep -- 0 --
/usr/bin/dbus-launch -- 0 -- 0
/usr/lib/gdm/gdm-session-worker -- 0.4 -- 0.4
/usr/lib/upower/upowerd -- 0.4 -- 0.4
/usr/lib/policykit-1/polkitd -- 0.3 -- 0.383333333333333
/usr/bin/gnome-keyring-daemon -- 0.2 -- 0.2
gnome-session -- 0.58 -- 0.7
/usr/bin/ssh-agent -- 0 -- 0
/bin/dbus-daemon -- 0.075 -- 0.0833333333333333
/usr/lib/libgconf2-4/gconfd-2 -- 0.375 -- 0.383333333333333
/usr/lib/gnome-settings-daemon/gnome-settings-daemon -- 1.15 -- 1.25
/usr/lib/at-spi/at-spi-registryd -- 0.5 -- 0.5
/usr/lib/bonobo-activation/bonobo-activation-server -- 0.3 -- 0.3
/usr/lib/gvfs/gvfsd -- 0.2 -- 0.2
/usr/lib/gvfs//gvfs-fuse-daemon -- 0.2 -- 0.2
/usr/bin/pulseaudio -- 0.38 -- 0.4
/usr/bin/python -- 2.07142857142857 -- 1.92666666666667
/usr/bin/desktopnova-daemon -- 0.275 -- 0.283333333333333
/usr/lib/rtkit/rtkit-daemon -- 0.1 -- 0.1
/usr/bin/perl -- 0.1 -- 0.1
compiz -- 1.675 --
nm-applet -- 1.15 -- 1.08333333333333
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 -- 0.6 -- 0.666666666666667
gnome-panel -- 1.35 -- 1.26666666666667
upstart-udev-bridge -- 0 -- 0
udevd -- 0.0333333333333333 -- 0.0333333333333333
rsyslogd -- 0.1 -- 0.1
NetworkManager -- 0.4 -- 0.4
/usr/bin/cli -- 3.23333333333333 -- 3.44
/usr/lib/pulseaudio/pulse/gconf-helper -- 0.3 -- 0.2
/home/evan/.dropbox-dist/dropbox -- 3.5 -- 3.5
gnome-screensaver -- 0.2 -- 0.2
/usr/lib/gvfs/gvfs-gdu-volume-monitor -- 0.3 -- 0.3
/sbin/dhclient -- 0 -- 0
/usr/lib/udisks/udisks-daemon -- 0.3 -- 0.3
udisks-daemon: -- 0 -- 0
/usr/lib/gvfs/gvfs-afc-volume-monitor -- 0.2 -- 0.2
/usr/lib/gvfs/gvfs-gphoto2-volume-monitor -- 0.2 -- 0.2
/usr/bin/gtk-window-decorator -- 1.1 --
nmbd -- 0.1 -- 0.1
/usr/lib/gnome-panel/wnck-applet -- 1.36666666666667 -- 1.34
/usr/lib/byzanz/byzanz-applet -- 1 -- 1
/usr/bin/gnote -- 1.8 -- 1.8
/usr/lib/gnome-panel/sensors-applet -- 1.2 -- 1.2
/usr/lib/gnome-applets/multiload-applet-2 -- 1.5 -- 1.02
/usr/lib/gnome-panel/clock-applet -- 1.5 -- 1.82
/usr/lib/indicator-applet/indicator-applet -- 1.3 -- 1.2
/usr/lib/gnome-panel/notification-area-applet -- 0.8 -- 0.8
/usr/lib/notify-osd/notify-osd -- 1.3 -- 0.7
/usr/lib/gvfs/gvfsd-metadata -- 0.2 -- 0.2
/usr/lib/indicator-sound/indicator-sound-service -- 0.5 -- 0.5
/usr/lib/indicator-application/indicator-application-service -- 0.3 -- 0.3
/usr/lib/indicator-messages/indicator-messages-service -- 0.4 -- 0.4
/usr/lib/firefox-4.0-4.0b8pre/firefox-4.0-bin -- 17.9 -- 20.225
/usr/lib/firefox-4.0-4.0b8pre/plugin-container -- 1.55 -- 1.5875
/opt/google/talkplugin/GoogleTalkPlugin -- 0.8 -- 0.8
nautilus -- 3.1 -- 3.1
/usr/lib/gvfs/gvfsd-trash -- 0.2 -- 0.2
/usr/lib/gvfs/gvfsd-burn -- 0.2 -- 0.2

```

---

