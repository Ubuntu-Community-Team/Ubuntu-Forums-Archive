---
title: "Annoying whistle every half hour. Make it stop!"
date: 2011-07-30
forum: General Help
---

### Post by Prodoc on 2011-07-30
Hi,

A whistle is being played every half hour for quite some time now and it is driven me nuts because I can't find out where it is coming from.

It is a sound of two short whistles after each other which is being played on a 30 minutes interval. It is not being played exactly on the hour so I guess it has to do with the time my system boots. E.g. sometimes it is played on 10 minutes past the hour and then again an half hour later on 40 minutes past the hour. On a different day it is played on the hour and then again 30 minutes past the hour, etc.

No matter what I'm doing at the time, the sound is always played. During programming, playing a game or movie full-screen, browsing, etc.

I've searched for all mp3, ogg and wav files on my system and played them one by one but I can't find the audio file that is being played.

No visual notification is being displayed either.

OS: Ubuntu 11.04 (x86)
Desktop: classic Gnome

Here is a typical list of processes running when it occurs (retrieved with "top -b -n1"):
```
top - 00:29:09 up 12:26,  2 users,  load average: 0.17, 0.29, 0.19
Tasks: 222 total,   1 running, 218 sleeping,   1 stopped,   2 zombie
Cpu(s):  3.4%us,  1.8%sy,  0.1%ni, 94.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4117364k total,  2598660k used,  1518704k free,    94452k buffers
Swap:  5156860k total,    24292k used,  5132568k free,   666320k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2367 forage    20   0  104m  13m 2892 S    4  0.3  15:13.21 beam.smp           
 1369 root      20   0  324m 128m  76m S    2  3.2  15:13.69 Xorg               
 2053 forage    20   0 90672  51m  17m S    2  1.3   8:44.98 compiz             
19823 forage    20   0  2628 1152  828 R    2  0.0   0:00.02 top                
    1 root      20   0  3048 1496 1132 S    0  0.0   0:01.75 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:02.28 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.57 ksoftirqd/1        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   13 root      20   0     0    0    0 S    0  0.0   0:00.36 ksoftirqd/2        
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   16 root      20   0     0    0    0 S    0  0.0   0:00.19 ksoftirqd/3        
   17 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/4        
   19 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/4        
   20 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/5        
   21 root      20   0     0    0    0 S    0  0.0   0:06.39 kworker/5:0        
   22 root      20   0     0    0    0 S    0  0.0   0:00.14 ksoftirqd/5        
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   25 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   27 root      20   0     0    0    0 S    0  0.0   0:00.14 sync_supers        
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd        
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd            
   31 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid             
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   33 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug      
   34 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff            
   35 root      20   0     0    0    0 S    0  0.0   0:00.03 khubd              
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                 
   37 root      20   0     0    0    0 S    0  0.0   0:00.02 khungtaskd         
   38 root      20   0     0    0    0 S    0  0.0   0:02.14 kswapd0            
   39 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd               
   40 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark      
   41 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                
   42 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   43 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto             
   47 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld           
   51 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd            
   52 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd    
   53 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand          
   54 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative      
  167 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
  168 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
  173 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
  178 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3          
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_4          
  182 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5          
  183 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6          
  184 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_7          
  205 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:8        
  209 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_8          
  210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_9          
  211 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:9        
  299 root      20   0     0    0    0 S    0  0.0   0:02.62 jbd2/sdb5-8        
  300 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit    
  350 root      20   0  2412  448  448 S    0  0.0   0:00.07 upstart-udev-br    
  400 root      16  -4  2884  360  352 S    0  0.0   0:00.03 udevd              
  561 root      18  -2  3012  424  372 S    0  0.0   0:00.00 udevd              
  562 root      18  -2  3012  368  364 S    0  0.0   0:00.00 udevd              
  640 root      20   0     0    0    0 S    0  0.0   0:00.00 jbd2/sdc1-8        
  646 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit    
  857 root      20   0  2412  208  204 S    0  0.0   0:00.01 upstart-socket-    
  939 root      20   0     0    0    0 S    0  0.0   0:01.84 flush-8:16         
  947 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0          
  980 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio1          
 1055 root       0 -20     0    0    0 S    0  0.0   0:00.00 kdmflush           
 1056 root       0 -20     0    0    0 S    0  0.0   0:00.00 kcryptd_io         
 1057 root       0 -20     0    0    0 S    0  0.0   0:00.00 kcryptd            
 1076 root      20   0     0    0    0 S    0  0.0   0:00.01 jbd2/dm-0-8        
 1077 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit    
 1097 root      20   0 16624 1744 1664 S    0  0.0   0:00.01 smbd               
 1103 root      20   0  5652 1432 1428 S    0  0.0   0:00.00 sshd               
 1118 syslog    20   0 28512  948  896 S    0  0.0   0:00.11 rsyslogd           
 1143 messageb  20   0  3600 1676  840 S    0  0.0   0:01.05 dbus-daemon        
 1162 root      20   0 18040 2800 2640 S    0  0.1   0:00.01 gdm-binary         
 1180 avahi     20   0  3152 1348 1228 S    0  0.0   0:00.07 avahi-daemon       
 1183 avahi     20   0  3016  188  172 S    0  0.0   0:00.00 avahi-daemon       
 1189 root      20   0 16624  380  324 S    0  0.0   0:00.00 smbd               
 1190 root      20   0  7212 1812 1756 S    0  0.0   0:00.01 cupsd              
 1212 root      20   0 26388 3348 2964 S    0  0.1   0:00.15 NetworkManager     
 1223 root      20   0 27088 2520 2512 S    0  0.1   0:00.21 console-kit-dae    
 1226 root      20   0  4660 1796 1672 S    0  0.0   0:00.01 modem-manager      
 1229 root      20   0  1872  488  484 S    0  0.0   0:00.00 getty              
 1233 root      20   0 23304 3040 2504 S    0  0.1   0:00.14 polkitd            
 1235 root      20   0  1872  488  484 S    0  0.0   0:00.00 getty              
 1310 root      20   0  1872  488  484 S    0  0.0   0:00.00 getty              
 1312 root      20   0  1872  488  484 S    0  0.0   0:00.00 getty              
 1316 root      20   0  1872  488  484 S    0  0.0   0:00.00 getty              
 1319 root      20   0  1864  472  468 S    0  0.0   0:00.00 acpid              
 1323 daemon    20   0  2132  236  224 S    0  0.0   0:00.00 atd                
 1324 root      20   0  2268  760  688 S    0  0.0   0:00.06 cron               
 1334 root      20   0  3156  568  492 S    0  0.0   0:10.53 irqbalance         
 1346 root      20   0 19864 3320 2920 S    0  0.1   0:00.01 gdm-simple-slav    
 1355 root      20   0  5172  836  836 S    0  0.0   0:00.00 wpa_supplicant     
 1410 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl             
 1411 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl             
 1412 root      20   0     0    0    0 S    0  0.0   0:00.00 firegl             
 1413 root      20   0 13388  632  444 S    0  0.0   0:00.03 winbindd           
 1428 root      20   0 13492  456  308 S    0  0.0   0:00.01 winbindd           
 1641 root      20   0  1872  492  484 S    0  0.0   0:00.00 getty              
 1647 root      20   0  2552 1056  784 S    0  0.0   0:00.00 dhclient           
 1693 root      20   0 17720 3464 2716 S    0  0.1   0:00.08 upowerd            
 1697 rtkit     21   1 19912 1148  952 S    0  0.0   0:00.44 rtkit-daemon       
 1874 root      20   0  9388 1328  656 S    0  0.0   0:00.40 nmbd               
 1950 ntp       20   0  4916 1812 1372 S    0  0.0   0:02.59 ntpd               
 1953 root      20   0 26040 4720 3492 S    0  0.1   0:00.04 gdm-session-wor    
 1956 root      20   0 13540  632  464 S    0  0.0   0:00.00 winbindd           
 1968 forage    20   0 43852 3268 2636 S    0  0.1   0:00.26 gnome-keyring-d    
 1987 forage    20   0 36412 7332 5800 S    0  0.2   0:00.24 gnome-session      
 2020 forage    20   0  3368  192    0 S    0  0.0   0:00.16 ssh-agent          
 2023 forage    20   0  3456  556  336 S    0  0.0   0:00.00 dbus-launch        
 2024 forage    20   0  5884 2948  672 S    0  0.1   0:13.41 dbus-daemon        
 2029 forage    20   0  9884 4608 2380 S    0  0.1   0:09.43 gconfd-2           
 2038 forage    20   0  101m  13m 8176 S    0  0.3   0:30.01 gnome-settings-    
 2043 forage    20   0  7784 2360 1928 S    0  0.1   0:00.08 gvfsd              
 2048 forage    20   0 30976 2284 1676 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 2056 forage     9 -11  110m 7092 4320 S    0  0.2   5:53.68 pulseaudio         
 2066 forage    20   0  129m  20m  14m S    0  0.5   0:25.96 nautilus           
 2067 forage    20   0 46368 8288 6656 S    0  0.2   0:00.98 gnome-power-man    
 2070 forage    20   0 55052  10m 8724 S    0  0.3   0:00.42 tracker-status-    
 2072 forage    20   0 18648  12m 3316 S    0  0.3   5:13.22 tracker-store      
 2073 forage    20   0  135m  12m 9.8m S    0  0.3   0:00.22 nm-applet          
 2074 forage    20   0 78380  18m 8616 S    0  0.5   0:00.40 indicator-weath    
 2075 forage    20   0 49484 5140 3832 S    0  0.1   0:00.30 zeitgeist-datah    
 2076 forage    20   0 40104 8248 6308 S    0  0.2   0:00.04 evolution-alarm    
 2077 forage    39  19 50356 9444 3636 S    0  0.2   0:18.94 tracker-miner-f    
 2080 forage    20   0 27524 6300 5028 S    0  0.2   0:00.02 polkit-gnome-au    
 2086 forage    20   0 1173m 373m 7316 S    0  9.3   3:48.97 java               
 2088 forage    20   0 35576  15m 5196 S    0  0.4   0:00.70 zeitgeist-daemo    
 2089 forage    20   0  278m  35m  17m S    0  0.9   0:30.56 empathy            
 2090 forage    20   0  1912  520  452 S    0  0.0   0:00.04 runLinux.sh        
 2096 forage    20   0  120m  18m  14m S    0  0.5   1:04.79 transmission-gt    
 2102 forage    20   0  108m  16m  11m S    0  0.4   0:24.31 gnome-panel        
 2117 forage    20   0 30192  10m 8360 S    0  0.3   0:15.08 notify-osd         
 2141 forage    20   0 20792 3300 2652 S    0  0.1   0:00.00 gconf-helper       
 2145 forage    20   0  8132 2836 2328 S    0  0.1   0:00.01 gvfsd-trash        
 2149 forage    20   0  9176 3456 2660 S    0  0.1   0:00.42 gvfs-gdu-volume    
 2154 root      20   0 23408 3468 2656 S    0  0.1   0:01.42 udisks-daemon      
 2155 root      20   0  5564  720  452 S    0  0.0   0:04.49 udisks-daemon      
 2157 forage    20   0  8620 4400 3064 S    0  0.1   0:01.05 mission-control    
 2162 forage    20   0  3916  512  440 S    0  0.0   0:00.00 cat                
 2176 forage    20   0 25164 7764 4240 S    0  0.2   0:00.52 telepathy-haze     
 2179 forage    20   0     0    0    0 Z    0  0.0   0:00.00 zeitgeist <defunct>
 2183 forage    20   0 18208 2164 1776 S    0  0.1   0:00.00 gvfs-afc-volume    
 2195 forage    20   0  8516 2444 1868 S    0  0.1   0:00.00 gvfs-gphoto2-vo    
 2201 forage    20   0 35316 3532 2836 S    0  0.1   0:00.01 bonobo-activati    
 2207 forage    20   0  1912  492  428 S    0  0.0   0:00.00 sh                 
 2209 forage    20   0 30616  10m 8088 S    0  0.3   0:24.60 unity-window-de    
 2217 forage    20   0 35328 4376 3508 S    0  0.1   0:00.14 telepathy-logge    
 2220 forage    20   0 88484  13m  10m S    0  0.3   0:31.78 wnck-applet        
 2225 forage    20   0 86980  10m 7644 S    0  0.3   0:00.16 trashapplet        
 2233 forage    20   0 22392 2336 1956 S    0  0.1   0:00.00 dconf-service      
 2241 forage    20   0 88372  12m 9960 S    0  0.3   0:00.31 indicator-apple    
 2244 forage    20   0  102m  12m 9.9m S    0  0.3   0:01.31 indicator-apple    
 2245 forage    20   0  140m  18m  13m S    0  0.5   0:10.09 clock-applet       
 2246 forage    20   0 83456 8460 6480 S    0  0.2   0:00.23 notification-ar    
 2254 forage    20   0 19208  11m 3560 S    0  0.3   0:56.36 desktopcouch-se    
 2275 forage    20   0 24352  16m 4472 S    0  0.4   0:03.98 telepathy-butte    
 2277 forage    20   0  100m  18m 9380 S    0  0.5   0:06.70 telepathy-gabbl    
 2279 forage    20   0  8676 3336 2580 S    0  0.1   0:00.12 telepathy-idle     
 2282 forage    20   0  7644 2124 1660 S    0  0.1   0:00.01 gvfsd-metadata     
 2291 forage    20   0 61248 4952 3940 S    0  0.1   0:00.29 indicator-me-se    
 2293 forage    20   0 51772 5332 4240 S    0  0.1   0:00.02 indicator-sessi    
 2318 forage    20   0 43132 4748 3796 S    0  0.1   0:00.35 indicator-messa    
 2320 forage    20   0  118m 5720 4504 S    0  0.1   0:01.10 indicator-sound    
 2321 forage    20   0 40496 4064 3240 S    0  0.1   0:00.11 indicator-appli    
 2356 forage    20   0  1912  568  468 S    0  0.0   0:00.00 couchdb            
 2365 forage    20   0  1912  308  204 S    0  0.0   0:00.00 couchdb            
 2392 forage    20   0  1700  252  200 S    0  0.0   0:00.46 heart              
 2414 forage    20   0  7788 2412 1952 S    0  0.1   0:00.00 gvfsd-burn         
 2430 forage    30  10 19644  10m 2248 S    0  0.3   0:59.59 desktopcouch-se    
 2431 forage    20   0     0    0    0 Z    0  0.0   0:00.07 desktopco <defunct>
 2436 forage    20   0 27384 4072 1588 S    0  0.1   0:00.05 couchjs            
 2500 root      20   0     0    0    0 S    0  0.0   0:00.60 flush-ecryptfs-    
 2566 forage    20   0 29748 7544 5680 S    0  0.2   0:03.11 gnome-screensav    
 2576 forage    20   0 19716 6436 4940 S    0  0.2   0:00.35 gdu-notificatio    
 2580 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:2        
 2584 forage    20   0 33560  15m 7836 S    0  0.4   0:01.96 applet.py          
 2592 forage    20   0 88024  12m 9612 S    0  0.3   0:01.31 update-notifier    
 2617 forage    20   0  843m 317m  28m S    0  7.9  40:38.78 firefox-bin        
 2629 forage    20   0  610m 189m  27m S    0  4.7   4:19.66 thunderbird-bin    
 2676 root      20   0     0    0    0 S    0  0.0   0:02.98 kworker/4:2        
 2766 forage    20   0  236m  38m  14m S    0  1.0   0:48.00 plugin-containe    
 3629 forage    20   0 67060 8680 6108 S    0  0.2   0:14.84 bamfdaemon         
 6221 forage    20   0  5192 1592 1088 S    0  0.0   0:00.13 bash               
 6454 forage    20   0 1397m 212m  19m S    0  5.3   1:39.82 java               
 6500 forage    20   0 21020  904  740 S    0  0.0   0:10.74 adb                
 7870 forage    20   0 59520 8244 6184 S    0  0.2   0:00.06 gvfsd-http         
11542 root      20   0     0    0    0 S    0  0.0   0:00.14 kworker/2:2        
11667 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/4:0        
12415 root      20   0     0    0    0 S    0  0.0   0:01.56 kworker/3:0        
17106 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/5:2        
17716 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0        
17829 root      20   0     0    0    0 S    0  0.0   0:00.66 kworker/2:1        
19378 root      20   0     0    0    0 S    0  0.0   0:00.31 kworker/1:2        
19396 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19420 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19426 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19450 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19456 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19486 root      20   0     0    0    0 S    0  0.0   0:00.01 kworker/0:2        
19508 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19514 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19560 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19566 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19616 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19622 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19686 root      20   0     0    0    0 S    0  0.0   0:00.11 kworker/0:1        
19694 forage    20   0 98332  14m  10m S    0  0.4   0:02.58 gnome-terminal     
19698 forage    20   0  2068  696  572 S    0  0.0   0:00.00 gnome-pty-helpe    
19699 forage    20   0  7936 4588 1544 S    0  0.1   0:00.25 bash               
19756 forage    20   0  4256  828  688 T    0  0.0   0:00.08 less               
19778 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19784 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              
19792 forage    20   0  1912  544  468 S    0  0.0   0:00.00 sh                 
19812 forage    20   0  3896  512  444 S    0  0.0   0:00.00 sleep              
19816 forage    20   0  1912  508  440 S    0  0.0   0:00.00 sh                 
19817 forage    20   0 22616 6592 4392 S    0  0.2   0:00.01 php                
19818 forage    20   0  3896  508  444 S    0  0.0   0:00.00 sleep              

```

Please tell me which application is causing this or help me locate it so I can finally disable it. It is driving me nuts!

---

### Post by SoFl W on 2011-07-30
email notification?  Past alarm or reminder of some kind?  (snoozed for ever 1/2 hour)

---

### Post by whitethorn on 2011-07-30
Have you checked if there's something in crontab?

```
crontab -e
```

You might also want to check in roots crontab (add a sudo to the above command)
You can also check in /etc/cron.(d/...)

---

### Post by Prodoc on 2011-07-30
> **SoFl W said:**
> email notification?
Can't really be, no e-mails came in or they where already read.

> **SoFl W said:**
> Past alarm or reminder of some kind?  (snoozed for ever 1/2 hour)
Sounds logical. That could only be Thunderbird. I've got the [Ubuntu Unity Messaging Menu Integration](https://addons.mozilla.org/en-us/thunderbird/addon/messaging-menu-integration/) add-on for Thunderbird installed but that one doesn't look likely. No audio files are included in the add-on file/folder. Nor do any other extensions. I'll close Thunderbird down just in case and wait half an hour, but I don't expect it to make a difference. Also because it happens when no reminder has been displayed after launch.

> **whitethorn said:**
> Have you checked if there's something in crontab?
Good point. Both user and root contabs are empty though.

Does there happen to be a way to log all sound output somehow? So all processes that try to produce a sound get listed when it occurs?

---

### Post by Prodoc on 2011-07-30
Found the bloody bastard...

Closing Thunderbird did stop it. It turned out to be the Lightning add-on in combination with the Provider for Google Calendar add-on. The last one refreshes the Google calendar every 30 minutes. For some screwed-up reason Lightning finds it necessary to play the alarm notification sound twice when this happens even though nothing has changed.

Thanks for setting on the right trail. I'm off to fix the bloody issue now.

---

### Post by Prodoc on 2011-07-30
Good news, it was a known issue and it has been addressed in the latest update of the Lightning add-on: [http://weblogs.mozillazine.org/calendar/2011/07/please_try_1_0b5.html](http://weblogs.mozillazine.org/calendar/2011/07/please_try_1_0b5.html)

---

