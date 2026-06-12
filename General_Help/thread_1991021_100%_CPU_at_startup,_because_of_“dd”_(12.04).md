---
title: "100% CPU at startup, because of “dd” (12.04)"
date: 2012-05-30
forum: General Help
---

### Post by Nesbitt on 2012-05-30
My 12.04 Ubuntu often has 100% CPU usage at startup. The top command give me this: 
   ```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND    
1510 root      20   0  2312  332  256 R  100  0.0   2:08.33 dd                   
1522 root      20   0  2312  328  256 R  100  0.0   2:08.08 dd                   
1514 root      20   0  2312  328  256 R  100  0.0   2:07.73 dd                   
1526 root      20   0  2312  328  256 R  100  0.0   2:08.91 dd                   
1524 root      20   0  2312  328  256 R   99  0.0   2:07.92 dd                   
1516 root      20   0  2312  332  256 R   97  0.0   2:08.33 dd                   
1520 root      20   0  2312  332  256 R   96  0.0   2:08.43 dd                   
1518 root      20   0  2312  328  256 R   96  0.0   2:04.87 dd 
```Google says that the dd process is for copying data output by the kernel from virtual file [FONT=Courier New]/proc/kmsg to /var/run/syslog/kmsg[/FONT], presumably so it can be kept (anything in /proc is temporary state). But why does this process cosume so much resource? And how to fix this? 
  Hope someone can help. Thank you very much.

---

### Post by ajgreeny on 2012-05-30
WOW!  That's a new one.

Is this a new installation, or has this just started to happen on an OS that previously ran well?

---

### Post by Nesbitt on 2012-05-31
Hi ajgreeny,

The problem happened only after I upgraded from 11.10 to 12.04.

Regards.

---

### Post by ajgreeny on 2012-05-31
> **Nesbitt said:**
> Hi ajgreeny,

The problem happened only after I upgraded from 11.10 to 12.04.

Regards.
Upgrade or clean install of 12.04?

---

### Post by Nesbitt on 2012-05-31
Hi ajgreeny, I think I was clear, it was an upgrade.

---

