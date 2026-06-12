---
title: "high CPU usage in Lucid"
date: 2010-10-10
forum: General Help
---

### Post by Riffer on 2010-10-10
Every once in awhile, generally in the mornings, my machine suddenly starts using close to a 100% of the CPU.  I've checked the System Monitor and can find nothing.  I have a dual core and using the 32 bit version of 10.04 and can see that on one core the CPU goes close to 100% and then flips over to the other core.

Any ideas?  Is there a way to see what is taking up all my CPU?  Also RAM stays normal, around 20%.

---

### Post by Quackers on 2010-10-10
Is Update Manager checking for updates?

---

### Post by sikander3786 on 2010-10-10
> Is there a way to see what is taking up all my CPU?

Type

```
top
```

in terminal and post the output here.

---

### Post by Riffer on 2010-10-10
> **Quackers said:**
> Is Update Manager checking for updates?

To the best of my knowledge it isn't.  When I checked in System monitor Update wasn't running.

---

### Post by Riffer on 2010-10-10
Hope this helps.


```
riffraff@stupid1:~$ top

top - 09:54:11 up 1 day, 16:45,  2 users,  load average: 0.36, 0.40, 0.52
Tasks: 182 total,   2 running, 180 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.4%us,  3.1%sy,  0.0%ni, 92.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2061132k total,  1973684k used,    87448k free,   211056k buffers
Swap: 19603448k total,        0k used, 19603448k free,  1181108k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                              
 1009 root      20   0 70124  53m  15m S    5  2.7  11:00.62 Xorg                                 
 6630 riffraff  20   0 54312  15m  10m S    5  0.8   0:02.73 gnome-terminal                       
 1629 riffraff  20   0 60460  46m  15m S    4  2.3   3:29.88 compiz                               
 5459 riffraff  20   0  368m  92m  28m S    1  4.6  11:03.30 firefox-bin                          
 1451 root      20   0  3636 1208 1028 S    0  0.1   0:08.12 hald-addon-stor                      
 1633 riffraff  20   0  150m  74m  17m S    0  3.7   5:23.08 docky                                
 1652 riffraff  20   0  148m  33m  15m S    0  1.7   0:49.65 dropbox                              
 1864 riffraff  20   0 41772  19m 5132 S    0  1.0   3:33.15 ubuntuone-syncd                      
 6651 riffraff  20   0  2548 1224  904 R    0  0.1   0:00.57 top                                  
    1 root      20   0  2808 1636 1184 S    0  0.1   0:00.49 init                                 
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                             
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                          
    4 root      20   0     0    0    0 S    0  0.0   0:19.05 ksoftirqd/0                          
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                          
    7 root      20   0     0    0    0 S    0  0.0   0:02.82 ksoftirqd/1                          
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                           
    9 root      20   0     0    0    0 S    0  0.0   0:01.38 events/0                             
   10 root      20   0     0    0    0 S    0  0.0   0:00.82 events/1                             
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                               
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                              
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                            
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                   
   17 root      20   0     0    0    0 S    0  0.0   0:00.08 sync_supers                          
   18 root      20   0     0    0    0 S    0  0.0   0:00.12 bdi-default                          
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                        
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1 
```

Please note that my problem stops after 20 minutes and the code you see is when my machine is running normally.

---

### Post by yossell on 2010-10-10
Use top when your chip is running at 100% to find out what is taking up the cycles. On that screenshot it looks like your cpu isn't doing very much.

---

### Post by Riffer on 2010-10-10
Ok will do.  Thank you.  I'll mark this solved for now untill I get that info and then I'll repost.

---

