---
title: "PowerMizer causes crash on power source change"
date: 2010-03-15
forum: General Help
---

### Post by Lockheed on 2010-03-15
I edited xorg.conf and changed
```
Option         "RegistryDwords" "PowerMizerLevel=0x3"
```
to
```
Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
```
which, according to [_this guide_]("http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/"), should give me max powersaving on battery and adaptive clocking on AC. 
However, now if I unplug the AC, plug it in again, and then unplug for the second time, system freezes. 
Why?

---

### Post by Lockheed on 2010-03-17
bump

---

