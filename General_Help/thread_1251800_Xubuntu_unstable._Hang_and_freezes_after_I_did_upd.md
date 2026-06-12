---
title: "Xubuntu unstable. Hang and freezes after I did update"
date: 2009-08-28
forum: General Help
---

### Post by slope on 2009-08-28
I have a xubuntu hardy 8.04 that have been running for some times. Never had stability issues like this before. Cause of traveling computer been turned off for the past 5-6 months. When I got back home I turned it on. 150 updates or so. Good boy as I am I did follow up and did my update. 

**Status now after update. **

[LIST=1]
[*]Unstable system
[*]Works just fine for an hour or two after boot, then suddenly hangz
[*]Nothing noticeable are taking place before each freeze
[*]Hang/freeze can occur with close to zero load as well
[*]hardware all the same no changes, no newly added usb
[/LIST]

**From terminal**
```
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s): 16.7%us,  0.2%sy,  0.0%ni, 83.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,   853040k used,  7341272k free,    19500k buffers
Swap: 14651272k total,        0k used, 14651272k free,   392144k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                    
 7395 root      20   0  902m  27m 9.9m R   54  0.3   5:22.51 Xorg                                                                                                                       
 8044 stian     20   0  216m  26m  14m S    9  0.3   0:47.54 gnome-system-mo                                                                                                            
 8024 stian     20   0 91568  10m 7644 S    3  0.1   0:16.86 npviewer.bin                                                                                                               
 7991 stian     20   0  620m 209m  25m S    0  2.6   0:27.00 firefox                                                                                                                    
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init                                                                                                                       
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                   
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                
    4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0                                                                                                                
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                 
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                                
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                 
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2                                                                                                                
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2                                                                                                                
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2                                                                                                                 
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3                                                                                                                
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3                                                                                                                
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3                                                                                                                 
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                                                   
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/2                                                                                                                   
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/3                                                                                                                   
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                    
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                                                  
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                                  
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/2                                                                                                                  
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/3                                                                                                                  
   60 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                     
   61 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                               
  191 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                    
  248 root      20   0     0    0    0 S    0  0.0   0:00.02 pdflush                                                                                                                    
  249 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                    
  250 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                    
  293 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                      
  294 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                      
  295 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/2                                                                                                                      
  296 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/3                                                                                                                      
 1743 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                              
 1745 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                      
 1806 root      15  -5     0    0    0 S    0  0.0   0:00.04 ata/0                                                                                                                      
 1819 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                                                      
 1820 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                   
 1825 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/2                                                                                                                      
 1830 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/3                                                                                                                      
 1831 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux    
```

I would hate to do a clean install. This 8.04 have worked too long and too well to go out with the bathwater. I **need to fix this without reinstalling xubuntu so pls help**

I did notice that even when not running more then say Firefox I can see that two of 4 CPU are using between 1 and 40 %. One light web page should not cause that much CPU usage.

---

### Post by slope on 2009-08-28
I searched alot a found a few posts blaming Firefox.
-Well Opera it is then I thought.

Got the latest Opera and thought it was just all good.

I am seeing cpu up against 99 % with close to no load :(

```
stian@quadcore:~$ top

top - 10:44:27 up  1:21,  2 users,  load average: 1.05, 1.05, 0.91
Tasks: 145 total,   3 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.1%us,  0.3%sy,  0.0%ni, 76.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,   842116k used,  7352196k free,    28992k buffers
Swap: 14651272k total,        0k used, 14651272k free,   533248k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7395 root      20   0  912m  46m  10m R   85  0.6  27:23.02 Xorg               
 8044 stian     20   0  219m  26m  14m S   10  0.3   3:38.23 gnome-system-mo    
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
stian@quadcore:~$ top

top - 10:44:35 up  1:21,  2 users,  load average: 0.97, 1.03, 0.90
Tasks: 145 total,   3 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.1%us,  0.2%sy,  0.0%ni, 75.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,   841864k used,  7352448k free,    28996k buffers
Swap: 14651272k total,        0k used, 14651272k free,   533248k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7395 root      20   0  912m  46m  10m R   88  0.6  27:29.89 Xorg               
 8044 stian     20   0  219m  26m  14m S    9  0.3   3:39.00 gnome-system-mo    
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
stian@quadcore:~$ top

top - 10:51:53 up  1:28,  2 users,  load average: 1.19, 1.11, 0.97
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.6%us,  0.2%sy,  0.0%ni, 74.9%id,  0.0%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   8194312k total,   942324k used,  7251988k free,    29704k buffers
Swap: 14651272k total,        0k used, 14651272k free,   536428k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7395 root      20   0  916m  47m  11m R   88  0.6  33:48.70 Xorg               
 8044 stian     20   0  219m  26m  14m S    8  0.3   4:11.07 gnome-system-mo    
 8778 stian     20   0  348m 111m  18m S    3  1.4   0:22.59 opera              
 9006 stian     20   0 18992 1284  932 R    1  0.0   0:00.04 top                
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
stian@quadcore:~$ top

top - 10:53:04 up  1:29,  2 users,  load average: 1.14, 1.10, 0.98
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s): 25.1%us,  0.3%sy,  0.0%ni, 74.2%id,  0.3%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8194312k total,   943908k used,  7250404k free,    29740k buffers
Swap: 14651272k total,        0k used, 14651272k free,   536820k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7395 root      20   0  915m  47m  11m R   87  0.6  34:49.45 Xorg               
 8044 stian     20   0  219m  26m  14m S    8  0.3   4:16.56 gnome-system-mo    
 8778 stian     20   0  348m 112m  18m S    6  1.4   0:26.36 opera              
 9007 stian     20   0 18992 1284  932 R    1  0.0   0:00.08 top                
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
stian@quadcore:~$ top

top - 10:55:54 up  1:32,  2 users,  load average: 1.25, 1.15, 1.01
Tasks: 148 total,   2 running, 146 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.4%us,  0.3%sy,  0.0%ni, 86.6%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,  1044740k used,  7149572k free,    30672k buffers
Swap: 14651272k total,        0k used, 14651272k free,   567632k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7395 root      20   0 1052m  81m  36m R   88  1.0  37:14.56 Xorg               
 8044 stian     20   0  219m  27m  14m S   10  0.3   4:30.34 gnome-system-mo    
 8778 stian     20   0  397m 129m  18m S    4  1.6   0:39.31 opera              
 9010 stian     39  19  191m  50m  10m S    4  0.6   0:03.10 operapluginwrap    
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.20 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
stian@quadcore:~$ top

top - 11:05:47 up  1:42,  2 users,  load average: 1.12, 1.09, 1.08
Tasks: 152 total,   2 running, 150 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.4%us,  0.3%sy,  0.9%ni, 85.8%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,  1183340k used,  7010972k free,    31992k buffers
Swap: 14651272k total,        0k used, 14651272k free,   552660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9081 stian     39  19  223m  50m  10m S   99  0.6   3:21.33 operapluginwrap    
 7395 root      20   0  924m  57m  12m S   34  0.7  41:44.49 Xorg               
 9136 stian     39  19  128m  28m  10m R   22  0.4   0:21.31 operapluginwrap    
 8044 stian     20   0  219m  27m  15m S    6  0.3   4:57.10 gnome-system-mo    
    1 root      20   0  4020  884  600 S    0  0.0   0:00.92 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.22 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
stian@quadcore:~$ 

```

This is BAD. Need help this is urgent.

---

### Post by P4man on 2009-08-28
Xorg is eating up your cpu cycles. Does it also happen after a fresh boot? What videodrivers are you using ?

---

### Post by slope on 2009-08-28
Well just after posting last post system froze again. just after fresh boot things are fine and smooth. system degrades within two hours it seems.

```
stian@quadcore:~$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.93 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.03 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.26 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +2.94 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.14 V
fan1:       1558 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:       1305 RPM  (min =    0 RPM)
temp1:       +41.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp2:       +44.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
temp3:       +25.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (crit = +100.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +43.0°C  (crit = +100.0°C)                  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +39.0°C  (crit = +100.0°C)                  

stian@quadcore:~$ top

top - 11:18:39 up 2 min,  2 users,  load average: 0.57, 0.44, 0.18
Tasks: 142 total,   1 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.0%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,   500664k used,  7693648k free,    13588k buffers
Swap: 14651272k total,        0k used, 14651272k free,   267368k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6966 root      20   0  870m  17m 8920 S    1  0.2   0:02.00 Xorg               
    1 root      20   0  4020  884  600 S    0  0.0   0:01.06 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
stian@quadcore:~$ top

top - 11:21:39 up 5 min,  2 users,  load average: 0.28, 0.33, 0.18
Tasks: 142 total,   1 running, 141 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.2%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8194312k total,   629428k used,  7564884k free,    15740k buffers
Swap: 14651272k total,        0k used, 14651272k free,   320088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6966 root      20   0  875m  22m 9284 S    1  0.3   0:06.10 Xorg               
 7633 stian     20   0  487m  89m  24m S    1  1.1   0:04.39 firefox            
    1 root      20   0  4020  884  600 S    0  0.0   0:01.06 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
stian@quadcore:~$ 

```

As you see here I did a boot cause system froze. Now it all seems good.
One or two hours from now it will hang again.

-Btw using opera did nothing for me.

---

### Post by slope on 2009-08-28
Sry I was in a hurry there. Here are details for videocard:

```
 *-display               
       description: VGA compatible controller
       product: GeForce 8600 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

Should be fine, yes?

And why is xorg eating all CPU? I run Intel q6600 and 8 GB of ram in addition to video card.
That must be plenty of power to run Xubuntu with xfce. I have no effects added. No fancy 3D Cube or anything.

Is there a way to check why xorg causes trouble?

---

### Post by P4man on 2009-08-28
Looks like a bug and memory leak in xorg. Nice upgrade they gave you :s

I assume your system is "up to date" now ?

---

### Post by slope on 2009-08-28
Yes. System is up to date.

I did check to see if there where any broken updates but all ok.

I disabled nvidia drivers and rebooted. Tried using envy to install correct driver but the automated process in Envy crashes. When doing it the manual way envy tells me to use 173.14.12.

Nvidia on their site says to use 	
185.18.36 from 21 of august this year. I will tr the older one first and see if that might help.

Other then the drivers I have no clue what to do to prevent xorg to eat all my cpu.

---

### Post by P4man on 2009-08-28
Using envy is not the best idea ... It tends to break things.

Its not certain nvidia drivers are to blame here. Perhaps you can try using the nv drivers for a while, and see if the memory keeps ballooning. If it does, then changing nvidia drivers won't help, as the issue is with xorg. 

If thats the case, perhaps you can revert to an older version of xorg and file a bug report.

---

### Post by slope on 2009-08-28
Arrrghhhh - getting frustrated!!

Now Envy will not install drivers neither auto mode or manual mode.

-Guess I will try apps - system - hardware drivers. Let see what happens now then. 

**Btw. How can I display what drivers are in use by the videocard?**

I tried 
```
lspci -v
```

But that did not show me the driver version running now after autamatic driver install.

---

### Post by slope on 2009-08-28
Ok if you think Envy is bad I will agree with you.
It does ot seem to be able to install drivers anyway so out it goes

For others following this thread struggling with same issues:

```
sudo dpkg -P envyng-qt
```

removes Envy completely.

---

### Post by P4man on 2009-08-28
have a look at xorg.conf. If is says driver="nvidia', then its using the binary drivers. Replace it with "nv" to use the opensource ones.  

To check whats in use now, you can also check the xorg log file:

cat var/log/Xorg.0.log

Look for LoadModule: "nvidia" or LoadModule: "nv" or LoadModule: "vesa" somehwere half way that file

---

### Post by slope on 2009-08-28
Can you pls give me that in small steps? I would prefer to use terminal cause at the moment I can hadly read the screen.

After messing with the drivers I now boot up with screen res of 600x400 or something like that on a 22" LCD. Makes everything blurry.

Can't seem to undo this either.

First I need to get screen back to native resolution...-How?

I hope tips I get is for terminal cause I have a hard time reading anything on the screen now :-)

---

### Post by slope on 2009-08-28
Hmm. Now it is messed up totally.
When I finally get to the login screen after boot I can not see anything except horizontal lines and blue color.

How can I now log in?

[LIST=1]
[*]Can I remote log in from a laptop, if yes how pls?

[*]Is there anything I can do from bios to at least get my 600x400 screen back?

[*]Is there a "windows safe mode" trick I can use so I can log in?
[/LIST]


-Now I am getting desperate. I have work that I need to complete on this machine.........


Well I just typed my un and pwd and in I got. But the screen is useless and it is all horizontal lines with some colors. Not readable. How do I fix xorg or some default drivers now?

---

### Post by P4man on 2009-08-28
Press control alt f1 to get to a console
find out out what driver you are using (nvidia, nv or vesa).
To do that type in the console:

sudo nano /etc/X11/xorg.conf

find the "driver" .  May look like this:

> Section "Device"
   Identifier     "Device0"
**   Driver         "nvidia"**
   VendorName     "NVIDIA Corporation"
   BoardName      "GeForce Go 7300"
EndSection

Try changing it to **nv** (opensource nvida) or **vesa** (which is somewhat like "failsafe")
> 
Section "Device"
   Identifier     "Device0"
**   Driver         "vesa"**
   VendorName     "NVIDIA Corporation"
   BoardName      "GeForce Go 7300"
EndSection

to save changes press control x

---

### Post by slope on 2009-08-28
Thx but at the moment I can not do anything. Take a look at the photo of my screen and you see why:

[[IMG]http://thumbnails14.imagebam.com/4699/188fe846987654.gif[/IMG]](http://www.imagebam.com/image/188fe846987654)

Only thing that might work is terminal commands. But if there is a lot of y/n that will not work either.

Maybe remote desktop?

---

### Post by P4man on 2009-08-28
did you try control+alt+F1 as I suggested above? It should give you a full screen, non graphical terminal. The commands I gave where for terminal too.

---

### Post by slope on 2009-08-28
Oopsie. Missed that one.

-Ok I have a terminal window.

Output is:

```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname     "vesa"
    Busid         "PCI:1:0:0:"
    Driver        "vesa"
    Screen  0
EndSection 
```


How can I get back nvidia drivers via terminal?

---

### Post by P4man on 2009-08-28
vesa gives you a garbled screen? thats not good.. can you post the sections monitor and screen too? 

To try the "nv" drivers, just replace "vesa" with "nv", 
**edit: and remove the boardname** probably not necessary, but do it anyway

and restart x:

> sudo /etc/init.d/gdm restart

To try the binary nvidia drivers, you could try:

> sudo nvidia-xconfig

---

### Post by slope on 2009-08-28
> **P4man said:**
> vesa gives you a garbled screen? thats not good.. can you post the sections monitor and screen too? 

To try the "nv" drivers, just replace "vesa" with "nv", 
**edit: and remove the boardname** probably not necessary, but do it anyway

and restart x:



Yes! this worked well P4man! :-) 

Thx a lot. I got my desktop back and it seems to be working. 
Now I can continue testing drivers nowing that if I mess up once again there is a workaround.

Thx a lot. Will post here when I have completed the drivers issues.

---

### Post by slope on 2009-08-28
Ok here are my videocard now:

```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8600 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0

```

And from the xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"	
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
EndSection
```

As of now it does not seem like the cpu is going to the moon so I just pray it is all ok now and let this rest for now.

If pc hangs again I will take this further and post here for sure so other can follow if needed.

-Again thx for your help and moral support man :lolflag:

---

### Post by slope on 2009-08-29
It is now more then 18 hours since last reboot. Everything seems fine.
Even had a few instances of vmware running where I put some load on Cpu without problems. After changing the drivers I have not seen xorg acting up and consume all CPU.

This after more then 18 hours of running:

```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                    
 6925 root      20   0  437m  84m  16m S    4  1.1   9:25.11 Xorg                                                                                                                       
 7784 stian     10 -10 1708m 692m 679m S    2  8.7  18:22.80 vmware-vmx                                                                                                                 
 7105 stian     20   0  846m 381m  26m S    1  4.8  11:04.75 firefox                                                                                                                    
 7108 stian     20   0  134m  14m 7264 S    1  0.2   0:06.40 xfce4-mixer-plu                                                                                                            
 7268 stian     20   0 18992 1304  932 R    0  0.0   1:44.39 top                                                                                                                        
    1 root      20   0  4020  888  600 S    0  0.0   0:01.08 init                                                                                                                       
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                   
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                
    4 root      15  -5     0    0    0 S    0  0.0   0:03.94 ksoftirqd/0                                                                                                                
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                 
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                
    7 root      15  -5     0    0    0 S    0  0.0   0:00.34 ksoftirqd/1                                                                                                                
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                 
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2                                                                                                                
   10 root      15  -5     0    0    0 S    0  0.0   0:00.50 ksoftirqd/2                                                                                                                
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2                                                                                                                 
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3                                                                                                                
   13 root      15  -5     0    0    0 S    0  0.0   0:00.34 ksoftirqd/3                                                                                                                
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3                                                                                                                 
   15 root      15  -5     0    0    0 S    0  0.0   0:00.36 events/0                                                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.12 events/1                                                                                                                   
   17 root      15  -5     0    0    0 S    0  0.0   0:00.14 events/2                                                                                                                   
   18 root      15  -5     0    0    0 S    0  0.0   0:00.12 events/3                                                                                                                   
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                    
   54 root      15  -5     0    0    0 S    0  0.0   0:04.92 kblockd/0                                                                                                                  
   55 root      15  -5     0    0    0 S    0  0.0   0:00.20 kblockd/1                                                                                                                  
   56 root      15  -5     0    0    0 S    0  0.0   0:00.36 kblockd/2                                                                                                                  
   57 root      15  -5     0    0    0 S    0  0.0   0:00.18 kblockd/3                                                                                                                  
   60 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                     
   61 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                               
  191 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                    
  250 root      15  -5     0    0    0 S    0  0.0   0:02.28 kswapd0                                                                                                                    
  293 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                      
  294 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                      
  295 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/2                                                                                                                      
  296 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/3                                                                                                                      
 1761 root      15  -5     0    0    0 S    0  0.0   0:02.98 ata/0                                                                                                                      
 1762 root      15  -5     0    0    0 S    0  0.0   0:00.14 ata/1                                                                                                                      
 1763 root      15  -5     0    0    0 S    0  0.0   0:00.32 ata/2                                                                                                                      
 1764 root      15  -5     0    0    0 S    0  0.0   0:00.16 ata/3                                                                                                                      
 1765 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                    
 1846 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                              
 1851 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                      
 1876 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                                   
 2530 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                  
stian@quadcore:~$ 

```

Thx for the help P4man.

---

