---
title: "How to find graphic card, and if latest driver is installed"
date: 2011-10-01
forum: General Help
---

### Post by SeaHawk22 on 2011-10-01
Is there a terminal command that will tell me what Graphics Card my computer has, and also is there a terminal command that will tell me if I have the latest driver installed, or at the very least what driver I have installed?

Running Ubuntu 11.04

Thank you in advance =)

:D

---

### Post by oldos2er on 2011-10-01
```
lspci | grep VGA
```

---

### Post by SeaHawk22 on 2011-10-01
The computer was given to me by a family since it did not work, I fixed it obviously lol. Runs fine, but integrated graphics card means basically a parasitic graphics card that steals CPU resources correct? By the way does it seem to have the latest driver?

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```


Thank you ):P

---

