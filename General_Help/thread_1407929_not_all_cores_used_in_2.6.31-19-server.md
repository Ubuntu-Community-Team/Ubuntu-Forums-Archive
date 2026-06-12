---
title: "not all cores used in 2.6.31-19-server"
date: 2010-02-15
forum: General Help
---

### Post by jmcarval on 2010-02-15
Hello.
Machine with two quad core Xeons W5580 (8 physical cores total) and with hyperthreading disabled, Ubuntu 9.10, kernel 2.6.31-19-server #56-Ubuntu SMP.
Threads are not correctly distributed by the available hardware. In previous releases of Ubuntu/kernel they were.
Is there a fix/workaround?

Example:
[PHP]top - 00:38:43 up 7 days, 11:11,  2 users,  load average: 1.86, 0.69, 1.78
Tasks: 270 total,  12 running, 258 sleeping,   0 stopped,   0 zombie
Cpu0  : 99.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  1.0%si,  0.0%st
Cpu1  :100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :100.0%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  49559188k total,  6809032k used, 42750156k free,   931476k buffers
Swap: 51478520k total,        0k used, 51478520k free,  3356664k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
30500 jmcarval  20   0  424m 321m  932 R 99.7  0.7   0:12.38 a.out              
30502 jmcarval  20   0  424m 321m  932 R 99.7  0.7   0:12.35 a.out              
30503 jmcarval  20   0  424m 321m  932 R 99.7  0.7   0:12.38 a.out              
30504 jmcarval  20   0  424m 321m  932 R 99.7  0.7   0:12.33 a.out              
30506 jmcarval  20   0  424m 321m  932 R 99.7  0.7   0:12.33 a.out              
30507 jmcarval  20   0  424m 321m  932 R 33.3  0.7   0:04.12 a.out              
30505 jmcarval  20   0  424m 321m  932 R 33.0  0.7   0:04.11 a.out              
30508 jmcarval  20   0  424m 321m  932 R 33.0  0.7   0:04.11 a.out              
    1 root      20   0 19456 1860 1196 S  0.0  0.0   0:03.03 init
[/PHP]

---

### Post by colinhercus on 2010-12-09
Hi JM,
Did you solve this? I have the same problem and I'd like that extra 12.5% performance I'd get if all cores were working.

Colin

---

