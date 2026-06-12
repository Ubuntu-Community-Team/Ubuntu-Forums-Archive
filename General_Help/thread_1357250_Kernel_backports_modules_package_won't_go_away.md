---
title: "Kernel backports modules package won't go away"
date: 2009-12-17
forum: General Help
---

### Post by humphreybc on 2009-12-17
I'm running kernel 2.6.32 on my laptop, and I want to get rid of the 2.6.31-15 stuff - so I removed the packages in Synaptic, which was all good - but now the "residual config" for the linux-backports-modules-2.6.31-15-generic package won't go away. 

When I choose to completely remove it under Synaptic I get this error:

```

E: linux-backports-modules-2.6.31-15-generic: subprocess installed post-removal script returned error exit status 1

```

---

### Post by Leppie on 2009-12-17
have you tried re-installing the 2.6.31-15 kernel, then remove the backports module and remove the kernel again?

---

### Post by ankle on 2010-05-03
Try making an empty directory in /lib/modules:
```
sudo mkdir /lib/modules/2.6.31-15-generic
```

---

