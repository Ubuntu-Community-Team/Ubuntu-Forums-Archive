---
title: "Ubuntu 10.04 is using too much RAM"
date: 2011-01-26
forum: General Help
---

### Post by homerj742 on 2011-01-26
Hello all, 

I scoped the forums and none of the solutions I found helped me (ie removing a ton of stuff). Here's a peak at some memory usage:

free -m
```
             total       used       free     shared    buffers     cached
Mem:          8001       1688       6313          0         96        831
-/+ buffers/cache:        760       7241
Swap:         2055          0       2055

```


Top
```
top - 17:23:26 up  2:30,  2 users,  load average: 0.04, 0.16, 0.12
Tasks: 243 total,   1 running, 242 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  0.6%sy,  0.0%ni, 97.7%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   8193620k total,  1717124k used,  6476496k free,    98468k buffers
Swap:  2104472k total,        0k used,  2104472k free,   851944k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4332 root      20   0  220m  89m  20m S    3  1.1   4:21.81 Xorg               
 7984 aamir     20   0  302m  15m  11m S    3  0.2   0:00.96 gnome-terminal     
 4938 aamir     20   0  899m 134m  33m S    2  1.7   8:26.84 firefox-bin        
 7993 aamir     20   0 19352 1484 1028 R    1  0.0   0:00.15 top                
   23 root     -50  -5     0    0    0 S    0  0.0   0:24.53 sirq-tasklet/1     
  751 root     -51  -5     0    0    0 S    0  0.0   0:02.50 irq/18-ohci_hcd    
  761 root     -51  -5     0    0    0 S    0  0.0   0:04.28 irq/12-i8042       
    1 root      20   0 23792 1952 1248 S    0  0.0   0:00.71 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root     -50  -5     0    0    0 S    0  0.0   0:00.00 sirq-high/0        
    5 root     -50  -5     0    0    0 S    0  0.0   0:00.00 sirq-timer/0       
    6 root     -50  -5     0    0    0 S    0  0.0   0:00.59 sirq-net-tx/0      
    7 root     -50  -5     0    0    0 S    0  0.0   0:12.67 sirq-net-rx/0      
    8 root     -50  -5     0    0    0 S    0  0.0   0:00.09 sirq-block/0       
    9 root     -50  -5     0    0    0 S    0  0.0   0:00.01 sirq-tasklet/0     
   10 root     -50  -5     0    0    0 S    0  0.0   0:00.00 sirq-sched/0       

```

Any help would be greatly appreciated, thank you!

---

### Post by tcrapper on 2011-01-26
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

According to free -m only 760 MB is being used.
Notice the "-/+ buffers/cache:" part.


```
-/+ buffers/cache:        760       7241
```

---

### Post by homerj742 on 2011-01-26
why does it need 760MB of RAM? I only have the OS, terminal, and firefox running.

---

### Post by pl@yer on 2011-01-26
*nix systems use any unused RAM for disk caching. This should give you the memory use by processes in percentage.
```

perc=$(ps -auxf|cut -b20-25|grep -v [A-Z]);perc=$(echo $perc|sed -e 's/\ /\ \+\ /g');echo $perc|bc

```
That should give you an idea of actual memory usage by processes on your system.

running pmap on processes will give you lots of info. This will run it on all processes to get the total memory usage/process
```

prids=$(ps -ef|cut -b10-15|sed -e 's/\ //g'|grep -v PID|more);pmap $prids|egrep ':|total'

```

The real gauge of memory use is swap used. Try using nmon or vmstat.

A good way to gauge your memory is page faults. 

When a program needs to read some data from the disk it is typically read to a memory page and the program references that page (because ram is faster than disk). 

The system may reclaim that memory page for another program. 

Then when the original program goes to pickup the data again from memory it isn't there. This causes a hard page fault, which is when the system is forced to re-read from the disk to RAM.

Hard pauge faults are the thing you want to avoid most and if you are short on RAM you will see more of them.

---

