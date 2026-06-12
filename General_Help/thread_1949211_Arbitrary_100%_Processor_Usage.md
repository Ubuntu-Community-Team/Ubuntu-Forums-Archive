---
title: "Arbitrary 100% Processor Usage"
date: 2012-03-29
forum: General Help
---

### Post by KFwLsKvVAs on 2012-03-29
Hello,

I'm having an issue where both of my Ubuntu machines seem to arbitrarily eat up all of my processor power when I'm not doing anything really.  

I've got 2 laptops, both with Ubuntu.  One is 10.10, the other is 11.10.  Both have fluxbox, transset, and xcompmgr installed.  Whey they're working properly, the processor usually sits around 10 - 15 percent, more if I've got lots and lots of tabs open in Opera or Firefox or something.  For some reason though, the processor shoots up to 100% sometimes, and stays that way for hours.  Nothing that I do provokes this.  I've attatched 2 screenshots of conky, one from each machine.  At the time of writing, the 10.10 machine (the one I'm writing on) is behaving normally, as you can tell from the first screenshot.  It's using much less processor power than the other one, even though it's running Opera and Fatrat.  The other machine, having just been booted up, has nothing open aside from shutter (which I used to get the conky screenshot, and which should absolutely not eat up 100% of processor power), and yet the CPU load is consistently between 95% and 100%.  In my experience, this persists until it arbitrarily stops.  Shutting down and rebooting don't remedy it, and killing the processes reported as using the most CPU doesn't remedy it either.  

This is a screenshot of the 10.10 machine running properly.  
[IMG]http://i42.tinypic.com/35d51qu.png[/IMG]

This is a screenshot of the 11.10 machine consuming nearly 100% of processor power.  
[IMG]http://i42.tinypic.com/33eon6p.png[/IMG]

I hope somebody can help shed some light on this problem, it's very frustrating.  Below you will find the output of top from the machine that is not working properly.  

```
top - 16:41:49 up 42 min,  1 user,  load average: 4.27, 3.52, 2.96
Tasks: 130 total,   3 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 33.4%us, 22.7%sy, 42.6%ni,  0.7%id,  0.0%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   2050448k total,  1016272k used,  1034176k free,    71492k buffers
Swap:  2928636k total,        0k used,  2928636k free,   527688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                           
 2300 root      39  19  188m 173m 6348 R   86  8.7  25:08.20 update-apt-xapi                                                                                   
 3072 bonez     20   0 75700 5136 3840 S   39  0.3   7:01.47 conky                                                                                             
 1379 root      20   0 67848  50m  10m R   38  2.5  14:05.14 Xorg                                                                                              
 3552 bonez     20   0  154m  14m  10m S   22  0.7   0:06.75 gnome-terminal                                                                                    
 3634 bonez     20   0  2664 1108  832 R    5  0.1   0:00.45 top                                                                                               
  442 messageb  20   0  4100 1932 1140 S    3  0.1   1:21.05 dbus-daemon                                                                                       
 1276 root      20   0 24448 7040 1916 S    2  0.3   0:25.94 python                                                                                            
 2844 root      20   0     0    0    0 S    2  0.0   0:17.28 kworker/1:0                                                                                       
 3556 root      20   0     0    0    0 S    2  0.0   0:00.60 kworker/0:3                                                                                       
 1359 root      20   0 14696 7496 3580 S    1  0.4   0:11.79 python                                                                                            
 1908 bonez     20   0 11912 5300 4180 S    0  0.3   0:28.00 fluxbox                                                                                           
 1952 bonez     20   0  264m  67m  25m S    0  3.4   3:09.55 cairo-dock                                                                                        
 1957 bonez     20   0  3680 1096  856 S    0  0.1   0:17.27 xcompmgr                                                                                          
 3296 root      20   0     0    0    0 S    0  0.0   0:03.28 kworker/0:0                                                                                       
    1 root      20   0  3320 1888 1260 S    0  0.1   0:09.98 init                                                                                              
    2 root      20   0     0    0    0 S    0  0.0   0:00.02 kthreadd                                                                                          
    3 root      20   0     0    0    0 S    0  0.0   0:00.54 ksoftirqd/0                                                                                       
    5 root      20   0     0    0    0 S    0  0.0   0:04.81 kworker/u:0                                                                                       
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                       
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                       
    9 root      20   0     0    0    0 S    0  0.0   0:00.41 ksoftirqd/1                                                                                       
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                            
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                           
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                             
   15 root      20   0     0    0    0 S    0  0.0   0:00.05 sync_supers                                                                                       
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                       
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                                       
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                                           
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                                           
   20 root      20   0     0    0    0 S    0  0.0   0:00.13 khubd                                                                                             
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                                                
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                        
   24 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                           
   25 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                              
   26 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                                                                        
   27 root      20   0     0    0    0 S    0  0.0   0:00.01 fsnotify_mark                                                                                     
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                   
   29 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                                                            
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                                                          
   47 root      20   0     0    0    0 S    0  0.0   0:00.01 scsi_eh_0  
```

---

### Post by mikewhatever on 2012-03-29
update-apt-xapi is known for hight CPU usage - lots of bugs reports on launchpad. It usually runs soon after start up, and takes a few minutes to complete. Either let it be, or remove the apt-xapian-index package entirely.

According to the top output, conky is another gross offender (might also be responsible for Xorg CPU usage), so you might want to remove it either.

---

### Post by KFwLsKvVAs on 2012-03-29
Thanks for the reply.  

I'll try removing apt-xapian-index and see if that helps.  

Conky shouldn't be using that much CPU, and neither should Xorg.  When things are working normally conky uses between 5% and 8%, and Xorg usually around 10%.  It's only when the CPU is maxed out that they consume what they are in the screenshot.

---

### Post by KFwLsKvVAs on 2012-03-30
Well I uninstalled apt-xapian-index, rebooted, and nothing changed.  The processor was immediately maxed at 100%.  I waited from about the time when I made the first reply until just a few minutes ago and the processor never went back to normal.  I booted back into Windows 7 because I wanted to listen to music and that was impossible in the state that that computer was in, so I am still in need of a fix.  If anybody can help me I'd really appreciate it, I can boot back into Ubuntu at any time if somebody wants me to get the output of any command or to try to do something to remedy this.  I really hope this can be resolved because I really don't like using Windows and it's honestly a show-stopping issue.

---

### Post by mikewhatever on 2012-03-31
Well, you should definitely be posting the output of 'top' every time you talk about high CPU usage. Simply mentioning that it's high is not too usefull.

---

### Post by KFwLsKvVAs on 2012-04-01
Will post new top output tomorrow evening, ~10 PM EST or earlier.

---

### Post by HiImTye on 2012-04-01
the question I have is why is conky taking 39% of your CPU?

---

### Post by KFwLsKvVAs on 2012-04-06
Good question, and I don't really know because it usually only takes something like ~5%.  

All I've got going on in conky is the processes being monitored for cpu usage and memory usage, hard drive input/output graph, cpu load graph, and network down/up graphs.  When things are working properly this barely makes a dent in total CPU usage, but when it starts to go all crazy like this it seems like any application opoen will use way more CPU than it ever has needed when things work normally.  

For example, look at this top output I just took a few minutes ago:

```
top - 10:58:16 up 1 day, 15:23,  2 users,  load average: 3.31, 3.12, 4.29
Tasks: 170 total,   3 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s): 76.2%us, 22.8%sy,  0.0%ni,  0.9%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   2049060k total,  1918236k used,   130824k free,    32104k buffers
Swap:  3227644k total,   212680k used,  3014964k free,   511736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 7121 bonez     20   0 1278m 965m  14m R   78 48.2 383:46.09 opera                                                                                                                                                                           
 1630 root      20   0  125m  74m  10m R   35  3.7 393:46.88 Xorg                                                                                                                                                                            
 2585 bonez     20   0 66928 1704 1284 S   28  0.1 202:42.50 conky                                                                                                                                                                           
30197 bonez     20   0  165m  14m  10m S   18  0.7   0:51.65 gnome-terminal                                                                                                                                                                  
 1868 bonez     20   0 68512  11m 6788 S   14  0.6 171:27.64 compiz                                                                                                                                                                          
26956 bonez     20   0 1156m  45m 4216 S   10  2.3  28:41.29 operapluginwrap                                                                                                                                                                 
30221 bonez     20   0  2620 1160  844 R    5  0.1   0:56.70 top                                                                                                                                                                             
27709 bonez     20   0 82144  19m 6380 S    4  1.0  27:35.70 vidalia                                                                                                                                                                         
 2644 bonez     20   0 23764 1496 1236 S    4  0.1  47:45.72 conky                                                                                                                                                                           
   10 root      20   0     0    0    0 S    1  0.0   1:11.51 events/1                                                                                                                                                                        
   64 root      20   0     0    0    0 S    1  0.0  10:48.46 kondemand/0                                                                                                                                                                     
   65 root      20   0     0    0    0 S    1  0.0  10:27.47 kondemand/1                                                                                                                                                                     
26962 bonez     20   0 18800 3644 2620 S    1  0.2   1:59.19 operapluginwrap                                                                                                                                                                 
26965 bonez     20   0 89444 3136 1312 S    1  0.2   0:58.95 GoogleTalkPlugi                                                                                                                                                                 
    9 root      20   0     0    0    0 S    0  0.0   0:09.34 events/0                                                                                                                                                                        
  384 root      20   0     0    0    0 S    0  0.0   0:09.87 flush-8:0                                                                                                                                                                       
 1870 bonez     20   0  3908  512  492 S    0  0.0   2:42.17 syndaemon                                                                                                                                                                       
 1888 root      20   0  5620  744  548 S    0  0.0   0:47.90 udisks-daemon                                                                                                                                                                   
27713 bonez     20   0 38116  22m 5552 S    0  1.1   3:18.88 tor                                                                                                                                                                             
    1 root      20   0  2888 1380  992 S    0  0.1   0:00.99 init                                                                                                                                                                            
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    3 root      20   0     0    0    0 S    0  0.0   0:59.52 ksoftirqd/0                                                                                                                                                                     
    4 root      RT   0     0    0    0 S    0  0.0   0:02.45 migration/0                                                                                                                                                                     
    5 root      RT   0     0    0    0 S    0  0.0   0:00.22 watchdog/0                                                                                                                                                                      
    6 root      RT   0     0    0    0 S    0  0.0   0:03.48 migration/1                                                                                                                                                                     
    7 root      20   0     0    0    0 S    0  0.0   1:26.13 ksoftirqd/1                                                                                                                                                                     
    8 root      RT   0     0    0    0 S    0  0.0   0:00.21 watchdog/1                                                                                                                                                                      
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                                                                          
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                         
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                                                                                                           
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                                                                                       
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                                                                                              
   17 root      20   0     0    0    0 S    0  0.0   0:01.26 sync_supers                                                                                                                                                                     
   18 root      20   0     0    0    0 S    0  0.0   0:01.71 bdi-default                                                                                                                                                                     
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                                                                                   
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                                                                                   
   21 root      20   0     0    0    0 S    0  0.0   0:22.37 kblockd/0                                                                                                                                                                       [39;49          (B 0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                                                                                   
   21 root      20   0     0    0    0 S    0  0.0   0:22.37 kblockd/0                                                                                                                                                                       
   22 root      20   0     0    0    0 S    0  0.0   0:01.27 kblockd/1                                                                                                                                                                       
   23 root      20   0     0    0    0 S    0  0.0   0:00.04 kacpid                                                                                                                                                                          
   24 root      20   0     0    0    0 S    0  0.0   0:00.06 kacpi_notify                                                                                                                                                                    
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                                                                                   
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                                         
   27 root      20   0     0    0    0 S    0  0.0   0:05.06 ata_sff/0                                                                                                                                                                       
   28 root      20   0     0    0    0 S    0  0.0   0:00.60 ata_sff/1                                                                                                                                                                       
   28 root      20   0     0    0    0 S    0  0.0   0:00.60 ata_sff/1                                                                                                                                                                       
   29 root      20   0     0    0    0 S    0  0.0   0:00.03 khubd                                                                                                                                                                           
   30 root      20   0     0    0    0 S    0  0.0   0:00.01 kseriod                                                                                                                                                                         
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                                                                                                           
   32 root      20   0     0    0    0 S    0  0.0   0:00.22 khungtaskd                                                                                                                                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:29.05 kswapd0                                                                                                                                                                         
   34 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd   
```

As well as this conky screenshot, showing a totally ridiculous 22.98% CPU usage for gedit, 20.39% CPU usage for Xorg, and 18.45% CPU usage for conky:

[IMG]http://i40.tinypic.com/jb779v.png[/IMG]

That is from the computer running 10.10.  It was taken in the gnome 2.x desktop environment with only the default desktop effects turned on.  I'm pretty sure it has nothing to do with compiz or the desktop effects because the same thing occurs when running fluxbox.  

I upgraded my 11.10 computer to 12.04 beta hoping that the upgrade might solve the problem, but it did not.  Here is the output of top from that machine, along with a screenshot of conky which shows the CPU load steady at around ~50%.  This was taken with no programs open (aside from shutter and gnome-terminal).  The only thing that I see that's unusual is kworker, which I don't know what it is or why it's running (but it's only taking up a tiny bit of CPU compared to Xorg and conky).  

```
Tasks: 123 total,   3 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s): 69.3%us, 28.0%sy,  0.0%ni,  2.4%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2049980k total,   831000k used,  1218980k free,   164984k buffers
Swap:  2928636k total,        0k used,  2928636k free,   425788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                           
 5919 bonez     20   0 51060  13m 9132 R   62  0.7   0:02.16 perl                                                              
 1308 root      20   0 71000  52m  11m R   42  2.6  38:37.66 Xorg                                                              
 3688 bonez     20   0 83824 6296 4768 S   30  0.3  48:01.77 conky                                                             
 5784 bonez     20   0  230m  15m  11m S   17  0.8   0:13.26 gnome-terminal                                                    
 5875 bonez     20   0  2840 1156  880 R    4  0.1   0:02.43 top                                                               
 3695 bonez     20   0  3928 1176  924 S    2  0.1   0:23.13 xcompmgr                                                          
 5727 root      20   0     0    0    0 S    2  0.0   0:01.79 kworker/1:1                                                       
 2415 root      20   0     0    0    0 S    1  0.0   1:17.52 kworker/0:1                                                       
 3640 bonez     20   0 11772 5212 4268 S    1  0.3   0:21.56 fluxbox                                                           
  560 messageb  20   0  3920 1732  844 S    1  0.1   1:25.69 dbus-daemon                                                       
 1276 root      20   0  3588  644  496 S    1  0.0   0:25.71 irqbalance                                                        
 1421 root      20   0 25888 7276 2160 S    1  0.4   1:41.27 wicd                                                              
 3685 bonez     20   0  3772 1076  628 S    1  0.1   0:01.08 dbus-daemon                                                       
 3690 bonez     20   0  284m  54m  24m S    1  2.7   0:48.81 cairo-dock                                                        
 3771 bonez     20   0  123m 6004 4876 S    1  0.3   0:01.11 indicator-sound                                                   
 5783 bonez     20   0  333m  42m  17m S    1  2.1   0:25.66 shutter                                                           
 1463 root      20   0 15260 7972 4072 S    0  0.4   0:44.57 wicd-monitor                                                      
 1498 root      20   0  6200 2764 1360 S    0  0.1   0:04.28 apache2                                                           
    1 root      20   0  3648 2104 1348 S    0  0.1   0:14.07 init                                                              
    2 root      20   0     0    0    0 S    0  0.0   0:00.03 kthreadd                                                          
    3 root      20   0     0    0    0 S    0  0.0   0:03.84 ksoftirqd/0                                                       
    5 root      20   0     0    0    0 S    0  0.0   0:12.89 kworker/u:0                                                       
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                       
    7 root      RT   0     0    0    0 S    0  0.0   0:09.75 watchdog/0                                                        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                       
   10 root      20   0     0    0    0 S    0  0.0   0:13.72 ksoftirqd/1                                                       
   12 root      RT   0     0    0    0 S    0  0.0   0:00.45 watchdog/1                                                        
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                            
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.04 kdevtmpfs                                                         
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                             
   17 root      20   0     0    0    0 S    0  0.0   0:00.36 kworker/u:1                                                       
   18 root      20   0     0    0    0 S    0  0.0   0:00.30 sync_supers                                                       
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                       
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                       
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                           
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                           
   23 root      20   0     0    0    0 S    0  0.0   0:00.10 khubd                                                             
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                
   26 root      20   0     0    0    0 S    0  0.0   0:00.04 khungtaskd                                                        
   27 root      20   0     0    0    0 S    0  0.0   0:00.04 kswapd0    
```

And the screenshot:

[IMG]http://i40.tinypic.com/5o134.png[/IMG]

I really hope somebody can help me out with this, I've tried myself to figure it out for a number of days now and haven't been able to.  Also right now it wouldn't be so bad if only one computer was doing it but currently both of them are, making it nearly impossible to even make this post in the first place (let alone get any other work done).  

Thank you in advance to anyone who can help.

---

### Post by KFwLsKvVAs on 2012-04-06
Update: this is also happening on 12.04 in Unity 2D.

---

### Post by KFwLsKvVAs on 2012-04-06
2nd Update: Problem persists after logging out and back in again as well as powering down and then turning the computer back on again.

---

### Post by KFwLsKvVAs on 2012-04-06
Update 3: My 10.10 machine was connected via ethernet to my wireless router, but wireless was still enabled.  I disabled wireless and walked away, and when I came back things were back to normal.  


```
Tasks: 168 total,   1 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.3%us, 13.7%sy, 13.5%ni, 42.7%id,  0.3%wa,  0.0%hi,  1.5%si,  0.0%st
Mem:   2049060k total,  1125540k used,   923520k free,    33080k buffers
Swap:  3227644k total,   107708k used,  3119936k free,   426568k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 1630 root      20   0  117m  69m  10m S    8  3.5 464:39.44 Xorg                                                                                                                                                                            
 2585 bonez     20   0 66928 1704 1284 S    8  0.1 265:15.22 conky                                                                                                                                                                           
30645 bonez     20   0  375m 315m  20m S    6 15.7  30:28.11 opera                                                                                                                                                                           
 1868 bonez     20   0 68976  12m 6892 S    4  0.6 185:28.67 compiz                                                                                                                                                                          
30678 bonez     20   0 1142m  75m  12m S    4  3.8   8:51.80 operapluginwrap                                                                                                                                                                 
    3 root      20   0     0    0    0 S    2  0.0   1:02.36 ksoftirqd/0                                                                                                                                                                     
30823 bonez     20   0  2616 1136  828 R    2  0.1   0:00.01 top                                                                                                                                                                             
    1 root      20   0  2888 1468 1080 S    0  0.1   0:01.20 init                                                                                                                                                                            
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    4 root      RT   0     0    0    0 S    0  0.0   0:02.46 migration/0                                                                                                                                                                     
    5 root      RT   0     0    0    0 S    0  0.0   0:00.24 watchdog/0                                                                                                                                                                      
    6 root      RT   0     0    0    0 S    0  0.0   0:03.49 migration/1                                                                                                                                                                     
    7 root      20   0     0    0    0 S    0  0.0   1:28.48 ksoftirqd/1                                                                                                                                                                     
    8 root      RT   0     0    0    0 S    0  0.0   0:00.22 watchdog/1                                                                                                                                                                      
    9 root      20   0     0    0    0 S    0  0.0   0:12.50 events/0                                                                                                                                                                        
   10 root      20   0     0    0    0 S    0  0.0   1:24.30 events/1                                                                                                                                                                        
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                                                                          
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                         
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                                                                                                           
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                                                                                       
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                                                                                              
   17 root      20   0     0    0    0 S    0  0.0   0:01.49 sync_supers                                                                                                                                                                     
   18 root      20   0     0    0    0 S    0  0.0   0:02.03 bdi-default                                                                                                                                                                     
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                                                                                   
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                                                                                   
   21 root      20   0     0    0    0 S    0  0.0   0:24.34 kblockd/0                                                                                                                                                                       
   22 root      20   0     0    0    0 S    0  0.0   0:01.57 kblockd/1                                                                                                                                                                       
   23 root      20   0     0    0    0 S    0  0.0   0:00.04 kacpid                                                                                                                                                                          
   24 root      20   0     0    0    0 S    0  0.0   0:00.07 kacpi_notify                                                                                                                                                                    
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                                                                                   
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                                         
   27 root      20   0     0    0    0 S    0  0.0   0:05.76 ata_sff/0                                                                                                                                                                       
   28 root      20   0     0    0    0 S    0  0.0   0:00.88 ata_sff/1                                                                                                                                                                       
   29 root      20   0     0    0    0 S    0  0.0   0:00.05 khubd                                                                                                                                                                           
   30 root      20   0     0    0    0 S    0  0.0   0:00.01 kseriod                                                                                                                                                                         
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                                                                                                           
   32 root      20   0     0    0    0 S    0  0.0   0:00.27 khungtaskd                                                                                                                                                                      
   33 root      20   0     0    0    0 S    0  0.0   0:33.13 kswapd0                                                                                                                                                                         
   34 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                                                                                                            
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                                           
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                                           
   37 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                                                                                                 
   38 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/0                                                                                                                                                                        
   39 root      20   0     0    0    0 S    0  0.0   0:00.00 crypto/1                                                                                                                                                                        
   53 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                                                                       
   54 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                                                       
   56 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_2                                                                                                                                                                       
   57 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_3                                                                                                                                                                       
   59 root      20   0     0    0    0 S    0  0.0   0:00.00 kstriped                                                                                                                                                                        
   60 root      20   0     0    0    0 S    0  0.0   0:00.02 kmpathd/0                                                                                                                                                                       
   61 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpathd/1                                                                                                                                                                       
   62 root      20   0     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                                                                                                                                                 
   63 root      20   0     0    0    0 S    0  0.0   0:00.00 ksnapd  
```


I don't for sure if disabling wireless is what fixed it or if it just finished doing whatever it was doing coincidentally.  

I disabled wireless on my 12.04 machine as well because it is also connected via ethernet cable, but it is still performing the same way.  



```
top - 13:50:36 up 34 min,  1 user,  load average: 1.67, 1.36, 1.32
Tasks: 131 total,   2 running, 127 sleeping,   0 stopped,   2 zombie
Cpu(s): 31.3%us, 26.5%sy,  0.0%ni, 41.2%id,  0.0%wa,  0.3%hi,  0.7%si,  0.0%st
Mem:   2049980k total,   845888k used,  1204092k free,   105284k buffers
Swap:  2928636k total,        0k used,  2928636k free,   530336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                           
 3619 bonez     20   0 83808 6236 4760 R   52  0.3   0:26.21 conky                                                                                             
 3382 root      20   0 66636  48m  11m S   43  2.4   1:18.42 Xorg                                                                                              
 3711 bonez     20   0  230m  16m  11m S    8  0.8   0:09.26 gnome-terminal                                                                                    
 3802 bonez     20   0  2840 1156  880 R    5  0.1   0:00.61 top                                                                                               
 3305 root      20   0     0    0    0 S    2  0.0   0:00.18 kworker/1:0                                                                                       
 3393 root      20   0     0    0    0 S    2  0.0   0:01.97 kworker/0:5                                                                                       
 1413 root      20   0 25884 7288 2160 S    2  0.4   0:21.70 wicd                                                                                              
  546 messageb  20   0  4400 2100  844 S    1  0.1   0:44.50 dbus-daemon                                                                                       
 1438 root      20   0 15264 7976 4072 S    1  0.4   0:09.61 wicd-monitor                                                                                      
 3621 bonez     20   0  284m  54m  24m S    1  2.7   0:22.86 cairo-dock                                                                                        
 3626 bonez     20   0  3928 1176  924 S    1  0.1   0:00.98 xcompmgr                                                                                          
 1275 kernoops  20   0  6048  940  716 S    0  0.0   0:02.65 kerneloops                                                                                        
 2354 bonez     20   0 40208  11m 7348 S    0  0.6   0:16.48 tangerine                                                                                         
    1 root      20   0  3652 2112 1352 S    0  0.1   0:11.76 init                                                                                              
    2 root      20   0     0    0    0 S    0  0.0   0:00.02 kthreadd                                                                                          
    3 root      20   0     0    0    0 S    0  0.0   0:01.43 ksoftirqd/0                                                                                       
    5 root      20   0     0    0    0 S    0  0.0   0:06.54 kworker/u:0                                                                                       
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                       
    7 root      RT   0     0    0    0 S    0  0.0   0:09.31 watchdog/0                                                                                        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                       
   10 root      20   0     0    0    0 S    0  0.0   0:00.49 ksoftirqd/1                                                                                       
   12 root      RT   0     0    0    0 S    0  0.0   0:03.85 watchdog/1                                                                                        
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                            
   14 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                           
   15 root      20   0     0    0    0 S    0  0.0   0:00.02 kdevtmpfs                                                                                         
   16 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                             
   17 root      20   0     0    0    0 S    0  0.0   0:00.20 kworker/u:1                                                                                       
   18 root      20   0     0    0    0 S    0  0.0   0:00.04 sync_supers                                                                                       
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                       
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                                       
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                                           
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                                           
   23 root      20   0     0    0    0 S    0  0.0   0:00.08 khubd                                                                                             
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                                                
   26 root      20   0     0    0    0 S    0  0.0   0:00.01 khungtaskd                                                                                        
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                           
   28 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                              
   29 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                                                                        
   30 root      20   0     0    0    0 S    0  0.0   0:00.04 fsnotify_mark                                                                                     
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                   
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                                                            
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                                                          
   50 root      20   0     0    0    0 S    0  0.0   0:00.02 scsi_eh_0                                                                                         

```

Edit: To be clear, the 12.04 machine was exhibiting this problem when it was still 11.10, so I do not believe this is a bug with 12.04.

---

### Post by KFwLsKvVAs on 2012-04-08
Anybody have any ideas about this?

When I turned off the 12.04 computer and let it sit for about a half an hour it seemed to fix it.  Turned it back on and everything was normal again.  I just turned it on again today about 20 minutes ago, things are working normal but I'm going to keep monitoring it to see if it does it again.

---

### Post by KFwLsKvVAs on 2012-04-12
I'm still having this issue intermittently.  Last night I went to sleep and the 11.10 computer was working fine.  When I woke up it was eating 100% processor power again.  Left it off for the day, turned it on a few minutes ago and now it's back to normal.  

I didn't grab top output this morning because I was in a hurry, but I'm reasonably sure it'd look like any of the other top outputs that I posted from earlier.  

Please can somebody help me with this?  It renders the computer completely unusable, and although I'm not going to switch back to windows any time soon this is really disheartening.

---

### Post by KFwLsKvVAs on 2012-04-27
This problem is still happening, at least once a day.  Logging out does not fix it, when it comes up to the login screen the background is very slow to load, and clicking the menu to shut down takes a long time to load (5 to 10 seconds as opposed to immediate when it is working properly).  Shutting down the computer and waiting 15 - 20 minutes is the only thing that solves this problem in a timely fashion (the other solution is to simply wait, sometimes for upwards of 6 hours for it to just go away on its own).  

I could really use some help with this, I've posted top outputs from both of my machines (now both 12.04), and I've run updates.  If I could post output from any other command or from any logs I'd be happy to do so, I just need to know what to post.  

Please somebody help me with this, it renders the computer completely unusable when it occurs (which is a pretty big deal when it happens at least once a day).

---

### Post by nmmarques on 2012-04-28
I had the same issue with 11.10 and now on 12.04. My processor is at 99-100% all the time. I found the cpu process called "nakido"!! I dont what to do!

---

### Post by KFwLsKvVAs on 2012-06-11
Tried switching to Kubuntu to see if there was any improvement.  

I guess the difference now is that it happens predictably.  Watching any videos that are actually on the computer works fine, but streaming anything causes the processor to max out until I shut the whole thing down and wait for about 5 or 10 minutes.  Also it happens when playing a game in wine, as well as when transferring a large amount of files to or from an external drive.  Obviously I can avoid doing all of these things, but that doesn't really solve the problem.  

Actually, now that I think of it, I do have an Ubuntu 10.10 disk around here somewhere.  I don't recall ever having this problem in 10.10, so I guess I'll try installing that and seeing if it fixes it.  

Will report back later.

---

### Post by KFwLsKvVAs on 2012-06-12
I am back.  

For whatever reason with 10.10 installed the problem is gone.  This still kind of sucks because 10.10 isn't supported any more, but for the time being at least my machines are both usable again.  I don't know what exactly the problem is with 11.04 and up, but for whatever reason they do not play nice with either of these Dell Latitude E6400's.  Even though this is sort of solved, it's really not "solved" in the truest sense of the word, so if anybody has any ideas as to why this problem started popping up in 11.04 and carried through to the current release, and why different window managers, different desktop environments, and even different distributions had no effect, I'd be really interested to hear some theories.  

Regards.

---

