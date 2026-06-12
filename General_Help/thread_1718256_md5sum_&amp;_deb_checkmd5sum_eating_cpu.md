---
title: "md5sum &amp; deb_checkmd5sum eating cpu?"
date: 2011-03-31
forum: General Help
---

### Post by d3v1150m471c on 2011-03-31
This is super annoying. I kill the two processes and they come right back up again like some greek hydra. I don't know what process is actually spawning them, top is giving me inaccurate reports as my cpu runs at 80-100% while they're going. What is it so i can kill it?
```

18344 d3v11     20   0  4236 1320 1112 S  9.7  0.0   0:04.46 arpshell                                    
22966 root      30  10  1796  536  456 R  7.8  0.0   0:00.04 md5sum                                      
22720 d3v11     20   0  2548 1120  812 R  1.9  0.0   0:00.02 top                                         
28853 d3v11     20   0  437m 107m  33m S  1.9  3.9   0:44.76 firefox-bin                                 
    1 root      20   0  2812 1640 1140 S  0.0  0.1   0:00.56 init                                        
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                    
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                 
    4 root      20   0     0    0    0 S  0.0  0.0   0:05.25 ksoftirqd/0                                 
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                  
    6 root      20   0     0    0    0 S  0.0  0.0   0:23.29 events/0                                    
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                      
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                     
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                       
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                   
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                          
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.12 sync_supers                                 
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.24 bdi-default                                 
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                               
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.86 kblockd/0                                   
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                      
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                               
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata/0                                       
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                     
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                               
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.04 khubd                                       
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.15 kseriod                                     
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                       
   27 root      20   0     0    0    0 S  0.0  0.0   0:00.04 khungtaskd                                  
   28 root      20   0     0    0    0 S  0.0  0.0   0:03.50 kswapd0                                     
   29 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                        
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 aio/0                                       
   31 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea        

```

that's far from accurate but that might help ^, TIA

---

