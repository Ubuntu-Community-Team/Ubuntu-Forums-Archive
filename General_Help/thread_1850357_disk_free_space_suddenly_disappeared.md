---
title: "disk free space suddenly disappeared/"
date: 2011-09-26
forum: General Help
---

### Post by subehsharma on 2011-09-26
I am using Ubuntu 11.04 and was watching a movie on vlc when i got a pop-up message that the disk is running low on free space. I closed vlc and checked the free space and to my shock, it shows 88MB left. 

I restarted my browser but the free space hasn't been recovered. i Don't know what has happenned suddenly.

subsharm@subsharm:~$ top

top - 20:20:52 up 7 min,  2 users,  load average: 0.25, 0.31, 0.22
Tasks: 149 total,   2 running, 145 sleeping,   0 stopped,   2 zombie
Cpu(s):  4.2%us,  0.3%sy,  0.0%ni, 95.0%id,  0.3%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2022792k total,  1032620k used,   990172k free,    67664k buffers
Swap:  3905532k total,        0k used,  3905532k free,   483940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4810 subsharm  20   0  756m 119m  36m S    7  6.1   0:28.47 firefox-bin        
 1268 root      20   0  398m  36m 9540 S    2  1.9   0:21.75 Xorg               
 6574 subsharm  20   0  327m  15m  11m S    2  0.8   0:00.25 gnome-terminal     
 6635 subsharm  20   0 19352 1328  960 R    1  0.1   0:00.03 top                
   10 root      20   0     0    0    0 R    0  0.0   0:01.70 kworker/0:1        
    1 root      20   0 24004 2204 1360 S    0  0.1   0:00.68 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.11 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.90 kworker/0:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.17 ksoftirqd/1        
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/u:1        
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers

---

### Post by TeoBigusGeekus on 2011-09-26
Can you post us the output of 
```
df -h
```
?

---

### Post by subehsharma on 2011-09-26
It might sound stupid, but i rebooted my laptop for the second time and now the free space has been recovered on its own. Earlier it was showing 88MB and not its showing 8.1 GB. God knows what has happened.

 Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G   11G  8.2G  56% /
none                  981M  708K  980M   1% /dev
none                  988M  168K  988M   1% /dev/shm
none                  988M  216K  988M   1% /var/run
none                  988M     0  988M   0% /var/lock

---

### Post by matt_symes on 2011-09-26
Hi

> **subehsharma said:**
> It might sound stupid, but i rebooted my laptop for the second time and now the free space has been recovered on its own. Earlier it was showing 88MB and not its showing 8.1 GB. God knows what has happened.

 Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G   11G  8.2G  56% /
none                  981M  708K  980M   1% /dev
none                  988M  168K  988M   1% /dev/shm
none                  988M  216K  988M   1% /var/run
none                  988M     0  988M   0% /var/lock

Your /tmp directory gets wiped at each boot (as (IIRC) on a standard Ubuntu install it is stored in memory). I suspect the file was in your /tmp directory.

Kind regards

---

