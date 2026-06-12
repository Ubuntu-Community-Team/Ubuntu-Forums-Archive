---
title: "High CPU usage when Matlab is idle on Ubuntu"
date: 2012-07-19
forum: General Help
---

### Post by liviogasp on 2012-07-19
Hi all, I installed Matlab 7.14.0.739 (R2012a) on a core i5 machine with 4 GiB  of RAM. The OS is Ubuntu 11.04 64 bit. Matlab works fine, (apart from some Unix version related issues), but  when idle it takes more than 100% CPU. The top command reports:
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  17162 newcesir 20   0 1137m 382m  70m S  107  4.8   2:35.14 MATLAB   9 root     20   0     0    0    0 S   21  0.0 898:12.00 ksoftirqd/1   3 root     20   0     0    0    0 S   19  0.0 923:00.86 ksoftirqd/0  13 root     20   0     0    0    0 S   10  0.0 779:41.32 ksoftirqd/2  16 root     20   0     0    0    0 S    0  0.0 640:55.65 ksoftirqd/3 The 4 ksoftirqd processes have something to do with interrupt  handling for the 4 processors, and are assciated with the matlab  running. The machine is multi user, and having one cpu occupied for every matlab  instance started is not good at all. 

I tried to start matlab without graphical interface and jvm, and the problem wasn't there any more, so maybe it has something to do with java. So I tried a different jre, but nothing changed...

Does anyone know why this is happening? 

Thank you

---

### Post by Gusss on 2012-07-19
Not sure but someone mentioned something similar to this and it was to do with programs trying to do absurdly complex floating point calculations (the closer to zero the more decimal places) so even though the calculations should be winding down the cpu explodes.....

---

### Post by liviogasp on 2012-07-23
> **liviogasp said:**
> Hi all, I installed Matlab 7.14.0.739 (R2012a) on a core i5 machine with 4 GiB  of RAM. The OS is Ubuntu 11.04 64 bit. Matlab works fine, (apart from some Unix version related issues), but  when idle it takes more than 100% CPU. The top command reports:
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  17162 newcesir 20   0 1137m 382m  70m S  107  4.8   2:35.14 MATLAB   9 root     20   0     0    0    0 S   21  0.0 898:12.00 ksoftirqd/1   3 root     20   0     0    0    0 S   19  0.0 923:00.86 ksoftirqd/0  13 root     20   0     0    0    0 S   10  0.0 779:41.32 ksoftirqd/2  16 root     20   0     0    0    0 S    0  0.0 640:55.65 ksoftirqd/3 The 4 ksoftirqd processes have something to do with interrupt  handling for the 4 processors, and are assciated with the matlab  running. The machine is multi user, and having one cpu occupied for every matlab  instance started is not good at all. 

I tried to start matlab without graphical interface and jvm, and the problem wasn't there any more, so maybe it has something to do with java. So I tried a different jre, but nothing changed...

Does anyone know why this is happening? 

Thank you

Solved. It was because of the leap second.
[http://www.wired.com/wiredenterprise/2012/07/leap-second-bug-wreaks-havoc-with-java-linux/](http://www.wired.com/wiredenterprise/2012/07/leap-second-bug-wreaks-havoc-with-java-linux/)
Simply rebooting the machine did the job.

---

