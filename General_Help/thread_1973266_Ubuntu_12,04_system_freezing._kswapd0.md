---
title: "Ubuntu 12,04 system freezing. kswapd0"
date: 2012-05-04
forum: General Help
---

### Post by Alan01252 on 2012-05-04
Hi all,

I recently migrated from wubi to a full install of ubuntu. But now I'm having teething problems. The process kswapd0 seems to be causing 100% cpu usage which eventually hangs the system

```

top - 18:55:05 up  1:36,  2 users,  load average: 65.25, 20.51, 8.25
Tasks: 190 total,   2 running, 184 sleeping,   0 stopped,   4 zombie
Cpu(s):  0.2%us,  0.3%sy,  0.0%ni,  0.0%id, 99.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2050060k total,  1977992k used,    72068k free,      108k buffers
Swap:  4779300k total,   361344k used,  4417956k free,    58100k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   27 root      20   0     0    0    0 D    2  0.0   0:06.90 kswapd0            
 3546 alan      20   0  635m  69m  656 D    0  3.4   2:15.31 chrome             
 3834 alan      20   0  606m 2436   88 D    0  0.1   0:54.69 psensor            
 1099 mysql     20   0  921m 8456    0 S    0  0.4   0:03.55 mysqld  

```

Top displays the above. Is there any work around for this?
Ironically I moved from wubi to a new partition to prevent mount.nfs causing lock ups!.

Thanks in advance

Alan

edit:

Could this be something to do with google chrome? When I SSH in and kill chrome the problem seems to go away at the same time?

---

### Post by gordintoronto on 2012-05-04
You're running out of memory. Chrome is using 3.4% of your memory, and that's the straw that broke the camel's back.

Can you run less stuff? Add memory? (Current memory has become incredibly cheap, but old memory is still expensive.)

Interesting that you have two users, I've never seen that.

---

