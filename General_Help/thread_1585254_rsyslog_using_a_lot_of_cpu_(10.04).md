---
title: "rsyslog using a lot of cpu (10.04)"
date: 2010-09-30
forum: General Help
---

### Post by supremedalek on 2010-09-30
Checked this morning and found out my CPU fan was hard at work. Checking top,

```

Tasks: 282 total,   2 running, 280 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.8%us,  4.2%sy,  3.2%ni, 77.2%id,  0.9%wa,  0.1%hi,  0.6%si,  0.0%st
Mem:   8193388k total,  8142680k used,    50708k free,    15224k buffers
Swap: 11694072k total,    31416k used, 11662656k free,  5681060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1118 root      20   0  330m 8104 1016 S  181  0.1 975:53.55 rsyslogd           
23833 raub      20   0 1133m 411m  17m S   21  5.1 325:23.35 firefox-bin  
```      

I see that rsylog is using a lot of CPU.  Any clues for the reason?

---

### Post by friedl on 2010-10-01
Hi supremedalek.

Are you using tls in rsyslog?

Perhaps you should post this in the support forum of rsyslog. 

Florian

---

### Post by supremedalek on 2010-11-01
Thank you for the suggestion. Found what is wrong and now it works much better.

---

