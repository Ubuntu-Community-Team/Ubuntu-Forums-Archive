---
title: "pidgin does not sleep (constant processor load)"
date: 2009-12-29
forum: General Help
---

### Post by dragilla on 2009-12-29
Hi, 

I'm running Ubuntu 9.10. I got rid of gnome-panels. I have one lxpanel and a cairo-dock. Except for the two all other is ubuntu-standard.

Hardware: Samsung Q210, Intel(R) Core(TM)2 Duo CPU     P7450  @ 2.13GHz
with 4GB of RAM.

My problem is that my pidgin never goes to sleep. It takes 2-5% of the prcessor all the time. He're the top of my top after not doing anything on my laptop for 10 minutes:

top - 17:50:33 up 5 days,  7:42,  5 users,  load average: 1.00, 1.28, 1.39
Tasks: 196 total,   1 running, 194 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.1%us,  1.6%sy,  0.0%ni, 97.1%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   4113828k total,  3079164k used,  1034664k free,   443668k buffers
Swap:  4192924k total,    26624k used,  4166300k free,  1314152k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
24194 luke      20   0  119m  29m  18m S    2  0.7   0:27.11 pidgin             
24495 root      20   0 88312  76m  16m S    1  1.9  70:03.61 Xorg               
25209 luke      20   0  587m 272m  36m S    1  6.8  89:23.35 firefox            
22970 luke      20   0  666m 220m  29m S    1  5.5   2:03.49 eclipse            
24139 luke      20   0  221m  63m  19m S    0  1.6   0:17.74 skype              
24838 luke      20   0  2468 1212  884 R    0  0.0   0:00.07 top                
25163 luke      20   0  104m  61m  17m S    0  1.5  25:55.26 compiz.real        
    1 root      20   0  3288 1008  656 S    0  0.0   0:02.03 init 

Is this normal? I don't think so... Any ideas?

edit: ok, I think I found the reason of all this: it's skype4pidgin!
When I deinstalled it pidgin no longer appears on the top of my top.
This doesn't solve my problem tho. I like this feature a lot. Is it suppose to load the processor so much?

cheers,

---

