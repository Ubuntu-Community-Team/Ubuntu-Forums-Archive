---
title: "gdm restart error"
date: 2009-10-24
forum: General Help
---

### Post by nimonika on 2009-10-24
I get the following error;
/etc/init.d$ gdm restart
gdm[12457]: WARNING: GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2042 (): Cannot run seteuid to 0: Operation not permitted

please can someone help.

Thanks

---

### Post by markitoxs on 2009-10-24
Is this command run with super user privileges?

---

### Post by SPr on 2009-10-24
> **markitoxs said:**
> Is this command run with super user privileges?
> **nimonika said:**
> 
/etc/init.d***$*** gdm restart


Root permission is required.

---

