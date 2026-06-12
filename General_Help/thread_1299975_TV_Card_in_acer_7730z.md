---
title: "TV Card in acer 7730z"
date: 2009-10-24
forum: General Help
---

### Post by Michaelsheldon on 2009-10-24
Hi y'all

Recently purchased an acer 7730 laptob and installed it with ubuntu 9.04. The laptop has a tv tuner built in but i cant seem to get it to work. Have tried some programmes mentioned by people for veiwing tv but they dont seem to work. Could this be a problem with drivers for the tv card? Will i need to down load them? Or could it be more to do with tuning signals
or reception in my area?

Any help greatly appreciated

---

### Post by sisco311 on 2009-10-24
Open a terminal and post the output of:
```
lspci
```
```
lsmod
```
and
```
ls -l /dev/video*
```

---

