---
title: "Flash Player crashes very frequently..."
date: 2012-06-14
forum: General Help
---

### Post by watgrad on 2012-06-14
I'm experiencing many crashes with Flash Player in both Chrome and Firefox. I'm running 12.04 upgraded from 11.10.  Usually (always?) this happens with streaming videos.

Flash version: 11.2.202.236
Linux 3.2.0-25-generic (64-bit)
3 gig ram
Nvidia 295.49 (Ge-Force 8400 GS)

I've removed and reinstalled flash - but no change.
This is the error I get:
plugin-container: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


Any ideas??

---

### Post by pqwoerituytrueiwoq on 2012-06-14
try making/editing this file to look like this (suggestion is based on gpu stated in the op)
```
~$ cat /etc/adobe/mms.cfg 
OverrideGPUValidation=false
EnableLinuxHWVideoDecode=0
```

---

### Post by watgrad on 2012-06-21
Thanks!
This fixed the frequent crashes.

---

