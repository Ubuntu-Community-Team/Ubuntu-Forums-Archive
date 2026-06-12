---
title: "High Memory Usage..."
date: 2011-06-02
forum: General Help
---

### Post by kasl33 on 2011-06-02
**My question (followed by specs and information):**

If "top" and "free -m" are both correct, what's the deal?

-----

**I have a Dell XPS L501X with the following specs:**

Intel i7-Q740
8 GB DDR3 RAM
640GB 7200 RPM HDD
Nvidia GeForce GT 435M (2 GB) Video Card

Running **Ubuntu 11.04** (**32-Bit** for compatibility with apps) and the **2.6.38-8-generic-pae kernel**

-----

I'm Running 3 Virtual Machines in VMware - The total memory allocated to these VM's is 3.0 GB of RAM. I noticed my system running really slow, so I ran a couple of commands, and here is my output.

**Output of top:**

[FONT="Courier New"]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                          
 2241 kris      20   0 1625m 1.5g 1.4g S   13 18.7  17:50.72 vmware-vmx                                                                       
  969 root      20   0 74432  50m  18m S    8  0.6   4:43.06 Xorg                                                                             
 2237 kris      20   0 1629m 1.4g 1.4g S    7 17.6  11:28.75 vmware-vmx                                                                       
 1560 kris      20   0  270m  95m  25m S    6  1.2   3:45.46 compiz                                                                           
 2226 kris      20   0  255m 197m 184m S    2  2.5   4:07.39 vmware-vmx                                                                       
 4736 kris      20   0  380m  59m  28m S    1  0.7   0:25.64 chrome                                                                           
 4898 kris      20   0  179m  67m  21m S    1  0.8   0:15.54 chrome                                                                           
   53 root      20   0     0    0    0 S    1  0.0   0:13.31 kswapd0                                                                          
 4744 root      20   0     0    0    0 S    1  0.0   0:00.41 kworker/0:0                                                                      
 1531 kris      20   0  5456 2616  668 S    1  0.0   0:04.72 dbus-daemon                                                                      
 1651 kris      20   0  110m  17m  10m S    1  0.2   0:16.95 unity-panel-ser                                                                  
 2088 kris      20   0  179m  42m  21m S    1  0.5   1:18.16 vmware                                                                           
 4734 kris      20   0  2632 1176  868 R    1  0.0   0:01.77 top                                                                              
 4908 root      20   0     0    0    0 S    1  0.0   0:00.27 kworker/4:2                                                                      
  809 root      20   0     0    0    0 D    0  0.0   0:21.38 jbd2/sda7-8                                                                      
 1266 root      20   0     0    0    0 S    0  0.0   0:22.14 flush-8:0                                                                        
 1545 kris      20   0  170m  11m 8284 S    0  0.1   0:03.84 gnome-settings-                                                                  
 1564 kris      20   0  134m  31m  14m S    0  0.4   0:12.01 nautilus                                                                         
 1605 kris      20   0 74204  11m 9016 S    0  0.1   0:07.08 notify-osd                                                                       
 1649 kris      20   0 30232  10m 7700 S    0  0.1   0:03.96 unity-window-de                                                                  
 2119 kris      20   0  116m  23m  14m S    0  0.3   0:23.46 vmware-tray                                                                      
 4343 root      20   0     0    0    0 S    0  0.0   0:00.91 kworker/1:0                                                                      
 4641 root      20   0     0    0    0 S    0  0.0   0:00.15 kworker/5:2                                                                      
 4673 kris      20   0 92832  13m  10m S    0  0.2   0:01.05 gnome-terminal                                                                   
    1 root      20   0  3024 1684 1116 S    0  0.0   0:01.45 init                                                                             
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd                                                                         
    3 root      20   0     0    0    0 S    0  0.0   0:00.27 ksoftirqd/0                                                                      
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                      
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                      
    9 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/1                                                                      
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                                      
   13 root      20   0     0    0    0 S    0  0.0   0:00.08 ksoftirqd/2                                                                      
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3   [/FONT] 

**Output of "free -m"**


[FONT="Courier New"]kris@UM:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7997       7737        260          0         14       6983
-/+ buffers/cache:        738       7258
Swap:         2859          0       2859[/FONT]

---

### Post by kasl33 on 2011-06-19
Since the time I posted this, I have come across a very useful command.

As root (meaning you have to run sudo passwd root, create a root password, then run su - (that's su "hyphen")and enter roots password), run this command:

sync; echo 3 > /proc/sys/vm/drop_caches

---

