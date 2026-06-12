---
title: "At power cut, how to avoid linux to ask for root password?"
date: 2009-11-24
forum: General Help
---

### Post by frenchn00b on 2009-11-24
FSCK COnfiguration and problem
 
At power cut, how to avoid linux to ask for root password after putting power on again to the pc?
Cannot it fixes itself with -a automatic options ?

---

### Post by dcstar on 2009-11-24
> **frenchn00b said:**
> FSCK COnfiguration and problem
 
At power cut, how to avoid linux to ask for root password after putting power on again to the pc?
Cannot it fixes itself with -a automatic options ?

```
gksudo gedit /etc/default/rcS
```

Make FSCKFIX=yes

---

