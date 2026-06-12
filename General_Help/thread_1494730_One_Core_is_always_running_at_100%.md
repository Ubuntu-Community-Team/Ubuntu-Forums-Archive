---
title: "One Core is always running at 100%"
date: 2010-05-27
forum: General Help
---

### Post by zombchef on 2010-05-27
Hi,

I have just installed Ubuntu 10.04 on a new Dell. I have an Intel Core 2 Quad processor and I have noticed that one of the cores, sometimes 2, is almost always running at 100%. It is not always the same core and it switches between cores if I use the computer for a while.
I searched the forums and came up with some similar problems and tried typing in the command "top" into terminal, but as a relatively new user I don't know what to do with that information so I am posting it here in the hopes that someone can help me out.

joshuapward@joshuapward:~$ top

top - 07:53:53 up  9:57,  2 users,  load average: 1.91, 1.89, 1.42
Tasks: 199 total,   2 running, 197 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.1%us,  4.1%sy,  0.0%ni, 65.8%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   6126024k total,  2369600k used,  3756424k free,    48284k buffers
Swap: 17946616k total,        0k used, 17946616k free,   741224k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3105 root      20   0 26860 5976 2388 R  100  0.1  21:19.71 backend            
 1055 root      20   0  261m 111m  29m S   35  1.9   3:22.31 Xorg               
 4676 joshuapw  20   0  246m  23m  17m S    4  0.4   0:36.86 gnome-system-mo    
 4557 joshuapw  20   0  502m  84m  29m S    1  1.4   0:41.02 firefox-bin        
 4687 joshuapw  20   0  207m  14m  10m S    0  0.2   0:00.46 gnome-terminal     
 4706 joshuapw  20   0 19216 1460 1052 R    0  0.0   0:01.28 top                
    1 root      20   0 23696 1952 1268 S    0  0.0   0:00.77 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:18.71 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
   15 root      20   0     0    0    0 S    0  0.0   0:00.01 events/0           
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 

The only one that jumps out at me is that Root says it is using 100% CPU, which I didn't notice on other peoples posts.
Also, is it bad for my computer if one of the cores runs so high?

Thank-you in advance for any help you can offer me.

---

### Post by CryptoPaul on 2010-05-27
3105 root 20 0 26860 5976 2388 R 100 0.1 21:19.71 backend 

Looks like you may have ran "System | Administration | System Testing"

There is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

Reboot, then have another look at what top is reporting.

---

### Post by zombchef on 2010-05-27
Thanks so much! That did it.

---

### Post by Megaptera on 2011-08-04
> **CryptoPaul said:**
> https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636[/url]

Reboot, then have another look at what top is reporting.

Just having run system testing, got same symptoms and a reboot solved it.
Just in case this 'bump' helps anyone else.

Thanks CryptoPaul.

---

