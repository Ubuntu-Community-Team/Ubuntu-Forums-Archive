---
title: "System sometimes is completely busy for several minutes"
date: 2010-02-18
forum: General Help
---

### Post by tuxolero on 2010-02-18
Hi,
Every few days, my PC is so busy that it is completely unusable for up to about 10 minutes.
During this time, the harddisk works constantly.
Even switching to a terminal or opening a konsole (for runing top) takes so long that the problem is over before I am there.

Once the problem occured, it comes back again and again until I reboot.
After reboot, everything is OK for 1 to 5 days.

But this time, I could check top.
It showed no process with more than a few percent CPU usage, but between 50% and 80%, sometimes nerly 90% waiting.
I recognized one of the processes with about 1% CPU usage. I hat problems with this one a few years ago:
kswapd0

Does anyone know if thre is a problem with this daemon again ?
Or can anybody give me a hint for a tool to identify which process is creating such a huge I/O load ?

Thanks and Regards,
Markus

---

### Post by SecretCode on 2010-02-20
Possibly swapping?

How much RAM do you have?

```
free -mt
```

---

