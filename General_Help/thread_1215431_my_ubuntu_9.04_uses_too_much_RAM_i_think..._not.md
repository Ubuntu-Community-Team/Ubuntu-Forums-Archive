---
title: "my ubuntu 9.04 uses too much RAM i think... not?"
date: 2009-07-17
forum: General Help
---

### Post by flotheboy on 2009-07-17
Hello guys, i have installed Ubuntu 9.04 fresh install, my visual effects are setted to normal, NVIDIA G force 4 mx 440 was installed with envy and it works very good ( direct rendering YES) 2 hard disks: one 20 GB wich is linux partition and one of 40 GB wich have 2 NTFS C:\WINDOWS and D:\ . Everything works very good but i think that ubuntu uses very much ram: 

top - 12:41:29 up 43 min,  2 users,  load average: 1.14, 1.20, 0.84
Tasks: 113 total,   3 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.8%us,  7.3%sy,  0.0%ni, 30.2%id,  0.0%wa,  0.0%hi, 11.6%si,  0.0%st
[B]Mem:    767940k total,   605796k used,   162144k free,    36972k buffers
Swap:  1502036k total,        0k used,  1502036k free,   318276k cached[/B]

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6961 flo       20   0  204m  72m  26m R 30.2  9.6   1:58.89 firefox            
 3023 root      20   0  105m  37m  10m S 12.3  5.1   4:14.81 Xorg               
 4563 flo       20   0 99.9m  29m 7796 S 11.6  3.9   3:19.35 compiz.real        
 6536 flo       20   0 98.3m  25m  15m S 10.3  3.4   2:50.17 audacious          
 7144 flo       20   0 34004  14m 9424 R  3.7  1.9   0:02.63 gnome-terminal     
 4564 flo       20   0 37764  20m  13m S  0.7  2.7   0:09.81 gnome-panel        
 4565 flo       20   0 67684  23m  14m S  0.3  3.1   0:06.45 nautilus           
 4630 flo       20   0 16520 2936 1772 S  0.3  0.4   0:05.47 gnome-screensav    
 7163 flo       20   0  2444 1168  912 R  0.3  0.2   0:01.31 top                
    1 root      20   0  3084 1892  564 S  0.0  0.2   0:01.24 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            

Is that normal for ubuntu?
Regards, FLO

---

### Post by Mighty_Joe on 2009-07-17
[Linux Ate My RAM!!!!]("http://www.linuxatemyram.com/")

---

### Post by CatKiller on 2009-07-17
Remember, empty memory is wasted memory.

EDIT: Good link, btw.

---

### Post by binbash on 2009-07-17
With firefox, it is normal.

---

### Post by csabo2 on 2009-07-17
I wouldnt worry about the memory usage. linux has proper memory management.  some apps i've noticed arent very good at not eating it all, however, as he said unused ram is wasted ram. as long is its freed when you need it theres no worry :)

---

