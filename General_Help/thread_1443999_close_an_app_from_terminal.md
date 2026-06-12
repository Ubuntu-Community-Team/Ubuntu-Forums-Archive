---
title: "close an app from terminal"
date: 2010-03-31
forum: General Help
---

### Post by kwstas on 2010-03-31
hi,

could someone tell me what's the command to close an application firefox for example from the terminal instead of using the "x" button?

is there maybe a way to "monitor" all the given commands during a short period of time?

---

### Post by nmaster on 2010-03-31
> **kwstas said:**
> hi,

could someone tell me what's the command to close an application firefox for example from the terminal instead of using the "x" button?

is there maybe a way to "monitor" all the given commands during a short period of time?

use 'top' to see all current processes. hit 'q' to leave top. use 'kill' or 'killall' to kill one of them.  for example,
```

neal@neal-laptop:/home/neal 
$ top

top - 14:56:17 up 29 min,  1 user,  load average: 1.32, 0.65, 0.43
Tasks: 141 total,   3 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.8%us,  8.9%sy,  0.0%ni, 66.6%id,  0.2%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   3046008k total,  1328852k used,  1717156k free,   127504k buffers
Swap:  3614584k total,        0k used,  3614584k free,   479308k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                
 3259 root      20   0  485m  82m  19m S   30  2.8   1:46.44 Xorg                                                                                                                   
 4890 neal      20   0  503m  49m  29m R   16  1.7   0:03.24 chromium-browse                                                                                                        
 4133 neal      20   0  195m  27m  14m R   12  0.9   2:11.02 npviewer.bin                                                                                                           
 4073 neal      20   0  677m 170m  27m S    9  5.7   2:24.96 firefox                                                                                                                
 3748 neal      20   0 80476  38m  16m S    1  1.3   0:35.34 skype                                                                                                                  
 4850 neal      20   0  135m  68m  22m S    1  2.3   0:04.98 acroread                                                                                                               
   21 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/0                                                                                                                  
 3749 neal      20   0  232m  29m  13m S    0  1.0   0:00.90 python                                                                                                                 
 3752 neal      20   0  187m  15m 8812 S    0  0.5   0:00.82 nm-applet                                                                                                              
 3849 neal      20   0  205m 9932 7832 S    0  0.3   0:04.60 multiload-apple                                                                                                        
neal@neal-laptop:/home/neal 
$ killall chromium-browser 

```

read the man pages for more info.

---

### Post by Boondoklife on 2010-03-31
or try xkill, this will let you just click the window you want to kill.

---

### Post by km0r3 on 2010-03-31
```
$ ps -A | grep firefox
7119 ?        01:08:11 firefox
$ kill -9 7119
$ kill -SIGTERM 7119
$ killall firefox
$ pkill 7119
$ # For unresponsive applications:
$ kill -SIGKILL 7119
```

**Questions?** Use the `man` pages... :)

---

### Post by baha'a on 2010-03-31
from my humble experience I use top then take the program PID (ID) and use 

kill (PID)

and it's gone :)

eg: to kill firefox:

```
top - 01:11:31 up  8:00,  3 users,  load average: 0.15, 0.26, 0.24
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.7%us,  4.3%sy,  0.0%ni, 83.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    444100k total,   394376k used,    49724k free,    27720k buffers
Swap:  1253028k total,    37304k used,  1215724k free,   132104k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1128 root      20   0  222m  41m 7000 S  6.0  9.5  46:39.30 Xorg               
 2965 bahaa     20   0  375m 104m  31m S  5.6 24.0  14:55.14 firefox            
 3416 bahaa     20   0 44984  12m 9696 S  3.3  2.8   0:01.33 gnome-terminal     
 1548 bahaa     20   0 30168  14m 5572 S  0.7  3.3   5:38.49 compiz.real        
 1549 bahaa     20   0 85968  20m  12m S  0.7  4.8   2:31.20 gnome-panel        
 3513 bahaa     20   0  2472 1172  884 R  0.7  0.3   0:00.05 top                
   16 root      15  -5     0    0    0 S  0.3  0.0   0:07.18 ata/0              
   34 root      15  -5     0    0    0 S  0.3  0.0   0:18.49 scsi_eh_1          
 1478 bahaa     20   0 35284  11m 8824 S  0.3  2.6   0:15.60 notify-osd         
 1541 bahaa     20   0  3168  800  732 S  0.3  0.2   0:17.15 syndaemon          
    1 root      20   0  2532 1344 1052 S  0.0  0.3   0:01.37 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.53 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
bahaa@bahaa-laptop:~$ kill 2965

```

---

### Post by Boondoklife on 2010-03-31
> **neal.m.master said:**
> use 'top' to see all current processes. hit 'q' to leave top. use 'kill' or 'killall' to kill one of them.  for example,
```

neal@neal-laptop:/home/neal 
$ top

top - 14:56:17 up 29 min,  1 user,  load average: 1.32, 0.65, 0.43
Tasks: 141 total,   3 running, 138 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.8%us,  8.9%sy,  0.0%ni, 66.6%id,  0.2%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   3046008k total,  1328852k used,  1717156k free,   127504k buffers
Swap:  3614584k total,        0k used,  3614584k free,   479308k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                
 3259 root      20   0  485m  82m  19m S   30  2.8   1:46.44 Xorg                                                                                                                   
 4890 neal      20   0  503m  49m  29m R   16  1.7   0:03.24 chromium-browse                                                                                                        
 4133 neal      20   0  195m  27m  14m R   12  0.9   2:11.02 npviewer.bin                                                                                                           
 4073 neal      20   0  677m 170m  27m S    9  5.7   2:24.96 firefox                                                                                                                
 3748 neal      20   0 80476  38m  16m S    1  1.3   0:35.34 skype                                                                                                                  
 4850 neal      20   0  135m  68m  22m S    1  2.3   0:04.98 acroread                                                                                                               
   21 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/0                                                                                                                  
 3749 neal      20   0  232m  29m  13m S    0  1.0   0:00.90 python                                                                                                                 
 3752 neal      20   0  187m  15m 8812 S    0  0.5   0:00.82 nm-applet                                                                                                              
 3849 neal      20   0  205m 9932 7832 S    0  0.3   0:04.60 multiload-apple                                                                                                        
neal@neal-laptop:/home/neal 
$ killall chromium-browser 

```read the man pages for more info.

Alternatively just press 'k' while in top to bring up a prompt to kill processes by pid

---

### Post by kwstas on 2010-04-01
thank you for your help guys!

what i want to do is to make a script that will terminate the program(firefox) in the appropriate way(like pressing the "x" button of the browser). 

killall does it but i'm not sure if this way is appropriate. i mean does "x" of firefox=killall firefox? (maybe some normal exiting procedures not getting finished by using killall?) 

sorry for being insisting but i try to be cautious on this. 


> is there maybe a way to "monitor" all the given commands during a short period of time? 	

the reason of asking this is to learn exactly about the given commands -options

---

### Post by Boondoklife on 2010-04-01
Perhaps you could explain a little better what exactly you are trying to do.

As far as kill = 'X', This is not the case. But I believe you should be able to get the same "effect" by issuing killall -s 1 firefox-bin.

---

### Post by sky net on 2010-04-01
system > administration > system monitor

---

### Post by km0r3 on 2010-04-01
> system > administration > system monitor

Thread title: [B]close an app from terminal
:)
[/B]

---

