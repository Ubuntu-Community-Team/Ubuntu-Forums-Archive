---
title: "CPU always at 100%"
date: 2009-08-16
forum: General Help
---

### Post by Muscovy on 2009-08-16
For the last two weeks or so, the System Monitor displays CPU at 100%, all the time. In Resources, it will account for only perhaps 1/4 of the CPU, most of which is from the System Monitor. What's using the extra 75% of the CPU?

---

### Post by Finalfantasykid on 2009-08-16
```
top
```

paste what you see there.

---

### Post by Muscovy on 2009-08-16
alex@home-desktop:~$ top

top - 13:43:39 up  3:59,  3 users,  load average: 1.30, 1.29, 1.27
Tasks: 116 total,   4 running, 112 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.6%us,  1.7%sy, 89.8%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    477172k total,   457680k used,    19492k free,    45100k buffers
Swap:  1132540k total,     8204k used,  1124336k free,   187240k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
10223 boinc     39  19  7120 5296 1180 R 89.7  1.1  42:39.49 milkyway_0.18_i                                                                                 
11892 alex      20   0  193m  77m  24m R  5.0 16.6   1:33.76 firefox                                                                                         
11581 root      20   0 67292  22m 8196 S  3.3  4.8   1:08.24 Xorg                                                                                            
11920 alex      20   0 35316  15m 9880 R  1.0  3.3   0:02.15 gnome-terminal                                                                                  
12435 alex      20   0  2444 1180  912 R  0.3  0.2   0:00.13 top                                                                                             
    1 root      20   0  3084  556  508 S  0.0  0.1   0:01.34 init                                                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 events/0                                                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                         
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                                                                         
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                                                   
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0                                                                                       
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                                          
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                                          
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.35 ata/0                                                                                           
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 ksuspend_usbd                                                                                   
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 khubd                                                                                           
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                                         
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                                           
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                                                       
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                                                       
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                                         
   24 root      15  -5     0    0    0 S  0.0  0.0   0:00.72 kswapd0                                                                                         
   25 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
   26 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                                                 
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
   30 root      15  -5     0    0    0 S  0.0  0.0   0:00.50 scsi_eh_1                                                                                       
   31 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kstriped                                                                                        
   32 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0                                                                                       
   33 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpath_handlerd                                                                                 
   34 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksnapd                                                                                          
   35 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand/0                                                                                     
   36 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd                                                                                        
  654 root      15  -5     0    0    0 S  0.0  0.0   0:01.13 kjournald                                                                                       
  788 root      16  -4  2220  408  312 S  0.0  0.1   0:00.22 udevd                                                                                           
 1982 root      20   0  1808  448  444 S  0.0  0.1   0:00.00 getty                                                                                           
 1983 root      20   0  1808  448  444 S  0.0  0.1   0:00.00 getty                                                                                           
 1990 root      20   0  1808  448  444 S  0.0  0.1   0:00.00 getty                                                                                           
 1991 root      20   0  1808  448  444 S  0.0  0.1   0:00.00 getty                                                                                           
 1992 root      20   0  1808  448  444 S  0.0  0.1   0:00.00 getty                                                                                           
 2062 root      20   0  2204  644  556 S  0.0  0.1   0:00.00 acpid



  I can't get much out of this, but "89.8%ni" looks like the process/group.

---

### Post by Finalfantasykid on 2009-08-16
Aha!  It looks like you are doing some sort of distributed computing on your computer.  Some sort of galaxy simulator or something by the looks of it.  Just kill that process(boinc) and you should be good.  And maybe check your startup programs and disable that one from running if you see it there.

---

### Post by Muscovy on 2009-08-16
:lolflag: I should have guessed. Untill a while ago I ran BOINC on the computer, but disabled it in some form or another because the info window at logon was bugging everyone. I'll try just making sure BOINC is low priority, other than the System Monitor, nothing suggested that much CPU was used.

---

