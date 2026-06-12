---
title: "system becomes unresponsive"
date: 2010-01-26
forum: General Help
---

### Post by rotogenray on 2010-01-26
For some reason, after a while of browsing the internet, the system will slow to a crawl and become basically unresponsive.

Even if I manage to close firefox, the smallest application will use a significant amount of the processor. Looking at my system monitor right now, I'm barely registering any activity at all with two browser windows open and the system idling otherwise.

Here's the output of top at startup

top - 13:46:47 up 2 min,  2 users,  load average: 1.22, 0.63, 0.24
Tasks: 123 total,   2 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us,  0.8%sy,  0.0%ni, 96.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    969268k total,   462712k used,   506556k free,    13208k buffers
Swap:  1253028k total,        0k used,  1253028k free,   237360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5690 root      20   0 66096  30m 7772 S    2  3.2   0:02.76 Xorg               
 6121 jacob     20   0 58156  29m 9228 R    1  3.2   0:02.80 compiz.real        
 6033 jacob     20   0 28484 5752 3304 S    1  0.6   0:00.16 pulseaudio         
 6047 jacob     20   0 15200 2608 1728 S    1  0.3   0:00.10 gnome-screensav    
 6225 jacob     20   0 74620  20m  10m S    1  2.1   0:00.86 gnome-terminal     
 6245 jacob     20   0  2308 1120  852 R    1  0.1   0:00.16 top                
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            


Here's top when the system is bogging- I tried to get a few instances-

jacob@ubuntu:~$ top

top - 11:58:39 up 14:03,  2 users,  load average: 13.72, 7.77, 3.95
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.4%us,  1.8%sy,  0.0%ni, 38.8%id, 41.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    969268k total,   958008k used,    11260k free,     1548k buffers
Swap:  1253028k total,   473844k used,   779184k free,    34492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6403 jacob     20   0  705m  93m  10m D   36  9.9 183:35.40 firefox            
 6299 jacob     20   0  744m 686m 683m S    1 72.6  11:49.32 compiz.real        
 5890 root      20   0  114m  18m 4744 S    0  1.9  19:03.82 Xorg               
    1 root      20   0  2844  232  232 S    0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.34 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid      jacob@ubuntu:~$ top

top - 11:58:39 up 14:03,  2 users,  load average: 13.72, 7.77, 3.95
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.4%us,  1.8%sy,  0.0%ni, 38.8%id, 41.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    969268k total,   958008k used,    11260k free,     1548k buffers
Swap:  1253028k total,   473844k used,   779184k free,    34492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6403 jacob     20   0  705m  93m  10m D   36  9.9 183:35.40 firefox            
 6299 jacob     20   0  744m 686m 683m S    1 72.6  11:49.32 compiz.real        
 5890 root      20   0  114m  18m 4744 S    0  1.9  19:03.82 Xorg               
    1 root      20   0  2844  232  232 S    0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.34 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid      jacob@ubuntu:~$ top

top - 11:58:39 up 14:03,  2 users,  load average: 13.72, 7.77, 3.95
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.4%us,  1.8%sy,  0.0%ni, 38.8%id, 41.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    969268k total,   958008k used,    11260k free,     1548k buffers
Swap:  1253028k total,   473844k used,   779184k free,    34492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6403 jacob     20   0  705m  93m  10m D   36  9.9 183:35.40 firefox            
 6299 jacob     20   0  744m 686m 683m S    1 72.6  11:49.32 compiz.real        
 5890 root      20   0  114m  18m 4744 S    0  1.9  19:03.82 Xorg               
    1 root      20   0  2844  232  232 S    0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.34 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
jacob@ubuntu:~$ top

top - 11:58:39 up 14:03,  2 users,  load average: 13.72, 7.77, 3.95
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.4%us,  1.8%sy,  0.0%ni, 38.8%id, 41.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    969268k total,   958008k used,    11260k free,     1548k buffers
Swap:  1253028k total,   473844k used,   779184k free,    34492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6403 jacob     20   0  705m  93m  10m D   36  9.9 183:35.40 firefox            
 6299 jacob     20   0  744m 686m 683m S    1 72.6  11:49.32 compiz.real        
 5890 root      20   0  114m  18m 4744 S    0  1.9  19:03.82 Xorg               
    1 root      20   0  2844  232  232 S    0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.34 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid      jacob@ubuntu:~$ top

top - 11:58:39 up 14:03,  2 users,  load average: 13.72, 7.77, 3.95
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.4%us,  1.8%sy,  0.0%ni, 38.8%id, 41.7%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:    969268k total,   958008k used,    11260k free,     1548k buffers
Swap:  1253028k total,   473844k used,   779184k free,    34492k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6403 jacob     20   0  705m  93m  10m D   36  9.9 183:35.40 firefox            
 6299 jacob     20   0  744m 686m 683m S    1 72.6  11:49.32 compiz.real        
 5890 root      20   0  114m  18m 4744 S    0  1.9  19:03.82 Xorg               
    1 root      20   0  2844  232  232 S    0  0.0   0:01.38 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:01.16 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.18 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.20 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.10 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.34 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid 

I'm not sure how to interpret any of this, but the last time I tried looking up a fix to this problem it was suggested that the symptoms are that of a hardware problem- overheating. I've felt the heatsink on the cpu while it's lugging, and it's as cool to the touch.

Help please?

**edit**
my computer has an AMD athalon 64 x2 dual core 3800+ with 946mb of ram, and I'm using ubuntu 8.04... in case that helps anyone

---

### Post by 3rdalbum on 2010-01-26
According to this, Compiz is using 72% of your RAM when the system gets slow. That's a major memory leak right there - it's causing your system to swap to disk, which is making your computer slow.

Try turning off some of your Compiz plugins in "CompizConfig Settings Manager" (assuming you have turned them on in this program) and see if this fixes the problem. Some of the plugins from the "unsupported" package may be causing this to occur.

Switching to the default Gnome window manager will also solve the problem:

```
metacity --replace
```

(or switch Visual Effects to "None").

EDIT: Just noticed you're using 8.04 - your "CompizConfig Settings Manager" might be named "Advanced Desktop Effects" under the Preferences menu.

---

