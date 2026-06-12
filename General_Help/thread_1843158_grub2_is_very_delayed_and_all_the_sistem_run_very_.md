---
title: "grub2 is very delayed and all the sistem run very slow"
date: 2011-09-13
forum: General Help
---

### Post by Devosv on 2011-09-13
I was using Ubuntu 10.10 (x64) on my laptop, and it worked with any issues. Since a few weeks ago I reisntall everything, including Windows 7, and I installed the new Ubuntu 11.04 (x64).

But now, everything looks to run very very slow... Manytimes the grub delays too much to load (many minutes), and in that cases is practically imposible to use Ubuntu, something that don't happen with Windows. With Firefox (6) is the same, just it blocks frequently by itself (the display turns grey), even when the laptop is inactive. For me, it don't have sense, since I have 4GB of memory, and the partition of Ubuntu have more than 30 GB of free space...

Something similar happen with the terminal... Many times, when I open it, I must wait for the comand line, it delay to appear (!), and recentely I just realized that the system is runing a lot of processes... With the old Ubuntu, in a long day of work, the PID that I see whe I ran my codes never were more than 4000; now, after of less of an hour of work, and after of run 3 or 4 of my codes, the PID always go over 10.000! When I run 11.04 on my laptop, it heats a lot (more than usual)

I reinstalled again Ubuntu 11.04, but everything is the same... I looked a lot for a solution, but I cann't find something...

Someone have a clue?

Thanks.

Best regards!

---

### Post by 2F4U on 2011-09-13
It may help if you could provide a list of that processes running on your machne.

---

### Post by Devosv on 2011-09-13
> **2F4U said:**
> It may help if you could provide a list of that processes running on your machne.


Hi 2F4U!

Well, after a top command, I see this

top - 10:34:00 up 7 min,  2 users,  load average: 1.84, 0.99, 0.53
Tasks: 179 total,   2 running, 174 sleeping,   0 stopped,   3 zombie
Cpu(s):  6.9%us,  2.2%sy,  0.2%ni, 53.3%id, 37.3%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3853104k total,  1885752k used,  1967352k free,    70240k buffers
Swap:  3228668k total,        0k used,  3228668k free,   662172k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+    COMMAND                                                                                                    
 1381 carlosma  20   0  699m  54m  22m R   24  1.4   0:18.38 compiz                                                                                                     
  868 root      20   0  172m  27m  13m S    9  0.7   0:27.38 Xorg                                                                                                       
 2159 carlosma  20   0  360m  17m  11m S    3  0.5   0:01.38 gnome-terminal                                                                                             
 1403 carlosma  20   0  539m  23m  16m D    1  0.6   0:00.96 nautilus                                                                                                   
 1427 carlosma  20   0  877m  61m  22m S    1  1.6   0:11.85 cairo-dock                                                                                                 
  732 avahi     20   0 32788 2412 1464 S    1  0.1   0:00.96 avahi-daemon                                                                                               
 1435 carlosma  20   0  615m  50m  17m S    1  1.3   0:02.83 dropbox                                                                                                    
 1646 carlosma  20   0  411m  17m  10m S    0  0.5   0:01.56 unity-panel-ser                                                                                            
 2227 carlosma  20   0 19352 1380  968 R    0  0.0   0:00.42 top                                                                                                        
 2259 carlosma  20   0  630m  74m  25m S    0  2.0   0:06.59 emesene                                                                                                    
  189 root      20   0     0    0    0 S    0  0.0   0:00.15 kworker/u:3                                                                                                
  586 root      20   0     0    0    0 S    0  0.0   0:00.31 kworker/1:2                                                                                                
  614 root      20   0     0    0    0 S    0  0.0   0:00.38 kworker/0:2                                                                                                
  718 messageb  20   0 24720 2204  856 S    0  0.1   0:00.54 dbus-daemon                                                                                                
 1185 root      20   0  140m 4664 3280 S    0  0.1   0:00.13 upowerd                                                                                                    
 1353 carlosma  20   0 26432 2720  660 S    0  0.1   0:00.81 dbus-daemon                                                                                                
 1390 carlosma  20   0 22608  956  768 S    0  0.0   0:00.13 syndaemon                                                                                                  
 1430 carlosma  20   0  361m  11m 8408 S    0  0.3   0:00.20 gnome-power-man                                                                                            
 1900 carlosma  20   0  109m  17m 4760 S    0  0.5   0:00.77 desktopcouch-se                                                                                            
 1966 carlosma  30  10  117m  17m 3208 S    0  0.5   0:00.42 desktopcouch-se                                                                                            
 2108 carlosma  20   0  372m  48m  12m S    0  1.3   0:01.69 ubuntuone-syncd                                                                                            
    1 root      20   0 24096 2212 1356 S    0  0.1   0:01.14 init                                                                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                   
    3 root      20   0     0    0    0 S    0  0.0   0:00.03 ksoftirqd/0                                                                                                
    4 root      20   0     0    0    0 S    0  0.0   0:00.03 kworker/0:0                                                                                                
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                
    9 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1                                                                                                
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                                                                
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                                                                
   13 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/2                                                                                                
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3                                                                                                
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/3:0                                                                                                
   16 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/3                                                                                                
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                     
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                    



Is it enough? 

Thanks!

---

### Post by 2F4U on 2011-09-13
This shows that there are just 179 processes running, which is not even  near that large numbers you said. Compiz seems to use considerable  memory and cpu resources. What graphics card do you have?

---

### Post by Devosv on 2011-09-13
> **2F4U said:**
> This shows that there are just 179 processes running, which is not even  near that large numbers you said. Compiz seems to use considerable  memory and cpu resources. What graphics card do you have?

The large number of processes I see it after a while... I just started to use my laptop today... My graphics card is an Intel Corporation Core Processor Integrated Graphics (and my processor is a Intel i5 )

---

### Post by Devosv on 2011-09-14
After three hours of work, using only firefox and kile (that crush constantly too), I see this in the top... At this moment 177 processes running, but the PID goes in 20.000 ... For me, it is strange!


top - 01:38:31 up  5:32,  2 users,  load average: 1.04, 2.80, 3.22
Tasks: 177 total,   1 running, 174 sleeping,   0 stopped,   2 zombie
Cpu(s):  6.7%us,  3.1%sy,  0.0%ni, 88.8%id,  1.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3853104k total,  1698248k used,  2154856k free,    71012k buffers
Swap:  3228668k total,   154608k used,  3074060k free,   753208k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
 1450 carlosma  20   0  724m  67m  15m S   11  1.8  12:59.32 compiz                                                                                                     
 1104 root      20   0  186m  30m 8276 S    7  0.8  32:45.47 Xorg                                                                                                       
22078 carlosma  20   0  458m  26m  19m S    6  0.7   0:26.21 gnome-system-mo                                                                                            
 1707 carlosma  20   0  506m  96m  11m S    2  2.6   1:19.92 unity-panel-ser                                                                                            
 1497 carlosma  20   0  630m  63m  10m S    1  1.7   0:10.15 dropbox                                                                                                    
22515 carlosma  20   0  360m  16m  11m S    1  0.4   0:00.44 gnome-terminal                                                                                             
 1474 carlosma  20   0 1035m 173m  13m S    1  4.6   8:09.53 cairo-dock                                                                                                 
 1421 carlosma  20   0 28744 4460  640 S    1  0.1   0:33.53 dbus-daemon                                                                                                
 1562 carlosma  20   0  231m 8032 6792 S    0  0.2   0:06.37 applet.py                                                                                                  
 1957 carlosma  20   0  110m 7496 3056 S    0  0.2   0:21.89 desktopcouch-se                                                                                            
 2042 carlosma  30  10  117m 7888 2388 S    0  0.2   0:24.15 desktopcouch-se                                                                                            
20516 root      20   0     0    0    0 S    0  0.0   0:00.21 kworker/3:0                                                                                                
21401 root      20   0     0    0    0 S    0  0.0   0:00.24 kworker/2:1                                                                                                
22603 carlosma  20   0 19352 1372  968 R    0  0.0   0:00.05 top

---

