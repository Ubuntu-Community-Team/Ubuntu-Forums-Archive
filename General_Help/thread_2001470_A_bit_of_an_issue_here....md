---
title: "A bit of an issue here..."
date: 2012-06-10
forum: General Help
---

### Post by Justinelectric on 2012-06-10
I got a little problem, well, actually, it may be a big one, who knows?  Anyway, I started getting a skip when playing audio, so I thought nothing of it.  Tonight, I noticed my "Num Lock" light flickering, using all of my CPU and RAM, then the little orange "X" moved from the left to the right.  I did a hard reboot, and still noticed the X moved and the audio issue.  I am at a total loss of what's wrong here, or how to fix it.  Hoping I don't have to back-up and reinstall.:cry:

---

### Post by hwttdz on 2012-06-11
What do you mean by "little orange x"? 

Also, if you could post the output of "top -b -n 1 -c" it might be enlightening.

---

### Post by ikt on 2012-06-11
Sounds like something might be corrupted or a component of the PC might be dying.

---

### Post by Justinelectric on 2012-06-11
> What do you mean by "little orange x"? 
The X to close a window.
[IMG]https://sphotos.xx.fbcdn.net/hphotos-prn1/s720x720/545739_326407967438441_155389049_n.jpg[/IMG]

Here's what I got.> justin@Justin-Satellite-L755:~$ top -b -n 1 -c
top - 00:15:51 up 52 min,  1 user,  load average: 0.62, 0.68, 0.69
Tasks: 177 total,   1 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.9%us,  1.7%sy,  0.1%ni, 87.2%id,  2.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3996252k total,  2345520k used,  1650732k free,    58720k buffers
Swap:  4140028k total,        0k used,  4140028k free,   837296k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2062 justin    20   0  986m 143m  19m S    6  3.7   1:31.68 /opt/google/chrome/
 1726 justin    20   0 1477m  94m  32m S    2  2.4   0:51.94 compiz             
 2415 justin    20   0  512m  62m  25m S    2  1.6   0:51.16 /opt/google/chrome/
 2867 justin    20   0  498m  23m  13m S    2  0.6   0:42.43 vinagre            
 3282 justin    20   0 17328 1336  944 R    2  0.0   0:00.01 top -b -n 1 -c     
    1 root      20   0 24420 2424 1356 S    0  0.1   0:00.69 /sbin/init         
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 [kthreadd]         
    3 root      20   0     0    0    0 S    0  0.0   0:00.17 [ksoftirqd/0]      
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/0]      
    7 root      RT   0     0    0    0 S    0  0.0   0:00.20 [watchdog/0]       
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 [migration/1]      
    9 root      20   0     0    0    0 S    0  0.0   0:05.70 [kworker/1:0]      
   10 root      20   0     0    0    0 S    0  0.0   0:00.10 [ksoftirqd/1]      
   12 root      RT   0     0    0    0 S    0  0.0   0:00.01 [watchdog/1]       
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 [cpuset]           
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 [khelper]          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 [kdevtmpfs]        
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 [netns]            
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 [sync_supers]      
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 [bdi-default]      
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kintegrityd]      
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kblockd]          
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 [ata_sff]          
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 [khubd]            
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 [md]               
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 [khungtaskd]       
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 [kswapd0]          
   28 root      25   5     0    0    0 S    0  0.0   0:00.00 [ksmd]             
   29 root      39  19     0    0    0 S    0  0.0   0:00.00 [khugepaged]       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 [fsnotify_mark]    
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 [ecryptfs-kthrea]  
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 [crypto]           
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kthrotld]         
   41 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_0]        
   42 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_1]        
   43 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_2]        
   44 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_3]        
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_4]        
   46 root      20   0     0    0    0 S    0  0.0   0:00.00 [scsi_eh_5]        
   71 root       0 -20     0    0    0 S    0  0.0   0:00.00 [devfreq_wq]       
  238 root      20   0     0    0    0 S    0  0.0   0:00.20 [jbd2/sda1-8]      
  239 root       0 -20     0    0    0 S    0  0.0   0:00.00 [ext4-dio-unwrit]  
  322 root      20   0 17224  636  444 S    0  0.0   0:00.13 upstart-udev-bridge
  326 root      20   0 22104 1984  880 S    0  0.0   0:00.06 /sbin/udevd --daemo
  412 root     -51   0     0    0    0 S    0  0.0   0:00.00 [irq/41-mei]       
  437 root       0 -20     0    0    0 S    0  0.0   0:00.00 [cfg80211]         
  527 root      20   0 22140 1496  384 S    0  0.0   0:00.00 /sbin/udevd --daemo
  528 root      20   0 22140 1444  336 S    0  0.0   0:00.00 /sbin/udevd --daemo
  529 root       0 -20     0    0    0 S    0  0.0   0:00.00 [kpsmoused]        
  563 root      20   0     0    0    0 S    0  0.0   0:00.00 [kworker/1:2]      
  682 root      20   0 15180  388  192 S    0  0.0   0:00.00 upstart-socket-brid
  795 messageb  20   0 25076 2364  844 S    0  0.1   0:00.79 dbus-daemon --syste
  816 root      20   0 79036 3204 2404 S    0  0.1   0:00.02 /usr/sbin/modem-man
  817 root      20   0 21180 1724 1440 S    0  0.0   0:00.00 /usr/sbin/bluetooth
  825 root      20   0  232m 5572 4348 S    0  0.1   0:00.51 NetworkManager     
  829 syslog    20   0  243m 1596 1140 S    0  0.0   0:00.07 rsyslogd -c5       
  832 avahi     20   0 32296 1724 1420 S    0  0.0   0:00.11 avahi-daemon: runni
  834 avahi     20   0 32172  468  216 S    0  0.0   0:00.00 avahi-daemon: chroo
  841 root      20   0  197m 4380 3036 S    0  0.1   0:00.59 /usr/lib/policykit-
  862 root      20   0  103m 5876 3272 S    0  0.1   0:00.03 /usr/sbin/cupsd -F 
  867 root      10 -10     0    0    0 S    0  0.0   0:00.00 [krfcommd]         
  872 colord    20   0  480m  11m 8796 S    0  0.3   0:00.16 /usr/lib/x86_64-lin
  880 root      20   0 31692 2312 1740 S    0  0.1   0:00.16 /sbin/wpa_supplican
  910 root       0 -20     0    0    0 S    0  0.0   0:00.00 [hd-audio0]        
  963 root      20   0 19976  968  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
  970 root      20   0 19976  968  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
  976 root      20   0 19976  972  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
  977 root      20   0 19976  972  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
  979 root      20   0 19976  972  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
  993 whoopsie  20   0  199m 5228 3764 S    0  0.1   0:00.11 whoopsie           
  995 root      20   0  4584  944  568 S    0  0.0   0:00.00 acpid -c /etc/acpi/
  997 root      20   0 15972  692  516 S    0  0.0   0:00.69 /usr/sbin/irqbalanc
  998 root      20   0 19104 1020  788 S    0  0.0   0:00.00 cron               
  999 daemon    20   0 16900  372  216 S    0  0.0   0:00.00 atd                
 1017 root       0 -20     0    0    0 S    0  0.0   0:00.00 [iprt]             
 1056 root      20   0  101m 2752 1836 S    0  0.1   0:00.00 /usr/sbin/winbindd 
 1057 root      20   0  264m 3508 2856 S    0  0.1   0:00.01 lightdm            
 1100 root      20   0  194m  22m 9888 S    0  0.6   1:08.42 /usr/bin/X :0 -auth
 1151 root      20   0  101m 1756  832 S    0  0.0   0:00.00 /usr/sbin/winbindd 
 1236 root      20   0 19976  972  812 S    0  0.0   0:00.00 /sbin/getty -8 3840
 1244 root      20   0  118m 3756 3092 S    0  0.1   0:00.10 /usr/lib/accountsse
 1261 root      20   0 1018m 3864 2828 S    0  0.1   0:00.13 /usr/sbin/console-k
 1380 root      20   0  214m 4420 3440 S    0  0.1   0:00.08 /usr/lib/upower/upo
 1511 root      20   0  159m 3692 2936 S    0  0.1   0:00.02 lightdm --session-c
 1544 rtkit     21   1  164m 1348 1116 S    0  0.0   0:00.03 /usr/lib/rtkit/rtki
 1558 root      20   0  7256 1568 1076 S    0  0.0   0:00.00 /sbin/dhclient -d -
 1562 root      20   0     0    0    0 S    0  0.0   0:00.15 [flush-8:0]        
 1563 nobody    20   0 33012 1300 1064 S    0  0.0   0:00.35 /usr/sbin/dnsmasq -
 1649 justin    20   0  511m 3868 3024 S    0  0.1   0:00.06 /usr/bin/gnome-keyr
 1660 justin    20   0  386m  10m 7440 S    0  0.3   0:00.15 gnome-session --ses
 1695 justin    20   0 12484  316    0 S    0  0.0   0:00.00 /usr/bin/ssh-agent 
 1698 justin    20   0 26548  784  476 S    0  0.0   0:00.00 /usr/bin/dbus-launc
 1699 justin    20   0 27736 3360  620 S    0  0.1   0:01.16 //bin/dbus-daemon -
 1711 justin    20   0  839m  19m  12m S    0  0.5   0:01.31 /usr/lib/gnome-sett
 1717 justin    20   0 52372 2520 2112 S    0  0.1   0:00.02 /usr/lib/gvfs/gvfsd
 1719 justin    20   0  203m 2856 2352 S    0  0.1   0:00.00 /usr/lib/gvfs//gvfs
 1734 justin    20   0 57732 3508 2036 S    0  0.1   0:00.08 /usr/lib/x86_64-lin
 1735 justin    20   0 20168  944  772 S    0  0.0   0:01.59 syndaemon -i 2.0 -K
 1740 justin     9 -11  354m 6104 3936 S    0  0.2   0:00.10 /usr/bin/pulseaudio
 1742 justin    20   0 46168 2244 1792 S    0  0.1   0:00.00 /usr/lib/gvfs/gvfsd
 1745 justin    20   0 95940 2992 2304 S    0  0.1   0:00.00 /usr/lib/pulseaudio
 1747 justin    20   0  444m 9448 6616 S    0  0.2   0:00.07 /usr/lib/gnome-sett
 1748 justin    20   0  432m  13m 9908 S    0  0.4   0:00.62 /usr/lib/vino/vino-
 1750 justin    20   0  582m  17m  11m S    0  0.4   0:00.34 nm-applet          
 1753 justin    20   0  398m  12m 8568 S    0  0.3   0:00.09 bluetooth-applet   
 1754 justin    20   0  739m  29m  17m S    0  0.7   0:01.32 nautilus -n        
 1757 justin    20   0  391m  14m  10m S    0  0.4   0:00.24 /usr/lib/policykit-
 1767 justin    20   0  313m 6988 5452 S    0  0.2   0:00.15 /usr/lib/telepathy/
 1773 justin    20   0  390m  13m  10m S    0  0.3   0:00.00 /usr/lib/gnome-onli
 1776 justin    20   0 70292 3660 2956 S    0  0.1   0:00.01 /usr/lib/gvfs/gvfs-
 1780 root      20   0  188m 3860 3028 S    0  0.1   0:00.11 /usr/lib/udisks/udi
 1784 root      20   0 45512  796  444 S    0  0.0   0:00.00 udisks-daemon: not 
 1792 justin    20   0  138m 2528 2028 S    0  0.1   0:00.19 /usr/lib/gvfs/gvfs-
 1795 justin    20   0 60320 2484 1940 S    0  0.1   0:00.00 /usr/lib/gvfs/gvfs-
 1798 justin    20   0 57056 3228 2688 S    0  0.1   0:00.00 /usr/lib/gvfs/gvfsd
 1801 justin    20   0  384m  11m 7592 S    0  0.3   0:01.16 /usr/lib/bamf/bamfd
 1806 justin    20   0 52532 2644 2224 S    0  0.1   0:00.00 /usr/lib/gvfs/gvfsd
 1808 justin    20   0  4392  612  512 S    0  0.0   0:00.00 /bin/sh -c /usr/bin
 1809 justin    20   0  315m  11m 8540 S    0  0.3   0:01.64 /usr/bin/gtk-window
 1819 justin    20   0  525m  20m  10m S    0  0.5   0:01.52 /usr/lib/unity/unit
 1821 justin    20   0  557m 5476 3472 S    0  0.1   0:00.49 /usr/lib/indicator-
 1840 justin    20   0  503m 6720 5060 S    0  0.2   0:00.08 /usr/lib/indicator-
 1841 justin    20   0  517m 6912 5400 S    0  0.2   0:00.07 /usr/lib/indicator-
 1842 justin    20   0  486m  10m 7624 S    0  0.3   0:00.07 /usr/lib/indicator-
 1843 justin    20   0  611m 5168 4036 S    0  0.1   0:00.05 /usr/lib/indicator-
 1844 justin    20   0  652m 6340 4948 S    0  0.2   0:00.05 /usr/lib/indicator-
 1845 justin    20   0  616m 7424 5796 S    0  0.2   0:00.03 /usr/lib/indicator-
 1872 justin    20   0 47844 2744 2288 S    0  0.1   0:00.01 /usr/lib/geoclue/ge
 1915 justin    20   0  156m 5388 4328 S    0  0.1   0:00.10 /usr/lib/ubuntu-geo
 1923 justin    20   0  671m 107m  40m S    0  2.8   1:36.58 /opt/google/chrome/
 1933 justin    20   0  246m 6584 2128 S    0  0.2   0:01.71 /opt/google/chrome/
 1935 justin    20   0  6456  288  184 S    0  0.0   0:00.00 /opt/google/chrome/
 1936 justin    20   0  275m  16m  11m S    0  0.4   0:00.03 /opt/google/chrome/
 1939 justin    20   0  121m 4156 3040 S    0  0.1   0:00.00 /opt/google/chrome/
 1958 justin    20   0  324m 9924 7020 S    0  0.2   0:00.06 /usr/lib/gnome-disk
 1969 justin    20   0  694m  15m 7788 S    0  0.4   0:00.19 /usr/bin/python /us
 1970 justin    20   0  593m 8352 6292 S    0  0.2   0:00.07 /usr/lib/unity-lens
 1971 justin    20   0  792m 6732 5280 S    0  0.2   0:00.09 /usr/lib/unity-lens
 1972 justin    20   0  407m  11m 7820 S    0  0.3   0:00.40 /usr/lib/unity-lens
 2000 justin    20   0  340m 5412 3788 S    0  0.1   0:00.15 /usr/bin/zeitgeist-
 2006 justin    20   0  239m 9168 7012 S    0  0.2   0:00.08 /usr/lib/zeitgeist/
 2008 justin    20   0  408m 6292 4648 S    0  0.2   0:00.17 zeitgeist-datahub  
 2014 justin    20   0 11372  612  512 S    0  0.0   0:00.00 /bin/cat           
 2017 justin    20   0  847m  30m  13m S    0  0.8   0:04.92 /opt/google/chrome/
 2023 justin    20   0  880m  62m  14m S    0  1.6   0:12.05 /opt/google/chrome/
 2030 justin    20   0  508m 4344 3560 S    0  0.1   0:00.03 /usr/lib/unity-lens
 2031 justin    20   0  847m  32m  15m S    0  0.8   0:05.34 /opt/google/chrome/
 2054 justin    20   0  420m  11m 8668 S    0  0.3   0:00.07 telepathy-indicator
 2085 justin    20   0  883m  71m  19m S    0  1.8   0:00.84 /opt/google/chrome/
 2114 justin    20   0  892m  82m  18m S    0  2.1   0:06.00 /opt/google/chrome/
 2134 justin    20   0  867m  48m  18m S    0  1.3   0:01.92 /opt/google/chrome/
 2179 justin    20   0  928m 117m  18m S    0  3.0   0:10.09 /opt/google/chrome/
 2192 justin    20   0  788m  17m 8716 S    0  0.4   0:00.16 /usr/bin/python /us
 2194 justin    20   0  933m  89m  20m S    0  2.3   0:27.17 /opt/google/chrome/
 2216 justin    20   0  307m  10m 7688 S    0  0.3   0:00.29 gnome-screensaver  
 2225 justin    20   0  349m  22m  15m S    0  0.6   0:00.48 /opt/google/chrome/
 2554 justin    20   0  474m  39m 8668 S    0  1.0   0:01.16 /usr/bin/python /us
 2588 justin    20   0  470m  13m 9544 S    0  0.3   0:00.21 update-notifier    
 2622 justin    20   0  282m 3864 3164 S    0  0.1   0:00.06 /usr/lib/deja-dup/d
 2628 justin    20   0  867m  51m  21m S    0  1.3   0:03.06 /opt/google/chrome/
 2665 justin    20   0 1022m 165m  20m S    0  4.2   1:49.18 /opt/google/chrome/
 2751 justin    20   0 2113m 222m  96m S    0  5.7   0:16.90 /usr/bin/python /us
 2770 justin    20   0  372m 5284 4288 S    0  0.1   0:00.01 /usr/lib/gvfs/gvfsd
 2835 justin    20   0  255m 2784 2200 S    0  0.1   0:00.01 /usr/lib/dconf/dcon
 3036 justin    20   0  872m  55m  18m S    0  1.4   0:01.41 /opt/google/chrome/
 3133 root      20   0     0    0    0 S    0  0.0   0:00.37 [kworker/0:0]      
 3141 root      20   0     0    0    0 S    0  0.0   0:00.25 [kworker/u:1]      
 3150 root      20   0     0    0    0 S    0  0.0   0:00.43 [kworker/u:0]      
 3151 root      20   0     0    0    0 S    0  0.0   0:00.06 [kworker/0:2]      
 3159 root      20   0     0    0    0 S    0  0.0   0:00.17 [kworker/u:2]      
 3160 root      20   0     0    0    0 S    0  0.0   0:00.19 [kworker/0:1]      
 3162 root      25   5  123m  19m 7548 S    0  0.5   0:00.19 /usr/bin/python /us
 3213 root      20   0     0    0    0 S    0  0.0   0:00.00 [kworker/1:1]      
 3218 justin    20   0  4392  612  508 S    0  0.0   0:00.00 /bin/sh -c gnome-te
 3219 justin    20   0  517m  16m  11m S    0  0.4   0:00.25 gnome-terminal     
 3223 justin    20   0 14780  828  668 S    0  0.0   0:00.00 gnome-pty-helper   
 3227 justin    20   0 27444 4508 1712 S    0  0.1   0:00.22 bash        

---

### Post by Justinelectric on 2012-06-17
Any ideas?

---

