---
title: "gdl_fs_crawler running on 100%"
date: 2011-03-13
forum: General Help
---

### Post by lapsus on 2011-03-13
Hi all,
I have a problem with my laptop running Lucid Lynx.
Directly after I start my computer gdl_fs_crawler runs almost on 100% CPU. When I kill it, it starts again. Probably it is launched by another program, but I have no idea which one.
In a previous thread I found it was because of vino-server, but on my laptop it does not work. :confused:
Do you have any idea? 
Thank you.

Here is part of my top output:
2503 balaz     20   0  108m  52m 3832 S   96  5.3   0:21.62 gdl_fs_crawler                                                                                                         
 2147 balaz     20   0  127m  24m  15m S    1  2.5   0:07.29 chromium-browse                                                                                                        
 1208 root      20   0 69200  28m  11m S    1  2.8   0:18.05 Xorg                                                                                                                   
   36 root      20   0     0    0    0 S    0  0.0   0:01.22 kswapd0                                                                                                                
 1644 balaz     20   0 82004  25m 7992 S    0  2.6   0:03.34 compiz                                                                                                                 
 1673 balaz     20   0  9776 3396 2928 S    0  0.3   0:00.34 gdl_service                                                                                                            
 2053 balaz     20   0  294m  92m  32m S    0  9.3   0:15.04 chromium-browse                                                                                                        
 2274 balaz     20   0  167m  25m  17m S    0  2.6   0:02.71 konsole                                                                                                                
 2598 balaz     20   0  2548 1240  924 R    0  0.1   0:00.04 top                                                                                                                    
    1 root      20   0  2812 1668 1204 S    0  0.2   0:00.43 init                                                                                                                   
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                               
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                            
    4 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0                                                                                                            
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                             
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1

---

### Post by skada on 2011-03-13
I think that is google desktop crawler. Try uninstalling/modifying it.
You can use pstree to see process tree (if that helps).

---

### Post by lapsus on 2011-03-13
I thought that this is used to gnome development library, isn't it?
I am not sure if I can uninstall it.

---

### Post by skada on 2011-03-13
it is from google most probably at '/opt/google/desktop/bin/' though you can find it out.
use 'ps -A | grep gdl_fs_crawler'to find out what is PID.
use 'ls -ls /proc/INSERT_PID_OF_THE_PROCESS_HERE/exe' to find out symlink to the process from disk.
it also updates crontab. so you can check there too and disable it from running.
Do tell me what happens :)

---

### Post by Debugger0 on 2012-04-13
Instead of disabling it, you can use the tool 'cpulimit' to lower the abmount of cpu consumption:

$> cpulimit -p <PID> -l <percentage>

e. g. 

$> cpulimit -p 5014 -l 20

This will limit the cpu usage to 20 percent.....


Martin

---

