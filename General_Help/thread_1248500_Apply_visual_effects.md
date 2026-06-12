---
title: "Apply visual effects"
date: 2009-08-24
forum: General Help
---

### Post by ramakantkul on 2009-08-24
i am new user of ubuntu. when i applly visual effects i get popups that " visual effects could not apply". when i try to troubleshoot it i get solution that " some graphic drivers are restricted" so please tell me, is there any graphic drivers which i can install and enjoy visual effects. my motherboard is of gigabite 486. please tell me and send me that drivers list which i can download and install it.

---

### Post by P4man on 2009-08-24
you need accelerated drivers to enable those effects. Which ones you need (or if its even possible) depends what videocard you have. To determine that, open a terminal and type:

```
lspci
```

copy/paste the output here.


(edit: not sure what Gigabyte 486 stands for, but if that is a i486 era computer, you can forget about enabling desktop effects, and Im shocked ubuntu runs on it at all)

---

### Post by BackwardsDown on 2009-08-24
Have you tried System->Administration->Hardware Drivers yet?

---

