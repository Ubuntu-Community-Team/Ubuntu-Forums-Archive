---
title: "why isn't there a nvidia-180 package in 10.04?"
date: 2010-05-13
forum: General Help
---

### Post by calmasy on 2010-05-13
the choices in Ubuntu 10.04 for Nvidia drivers seem to be the following three packages:

1. nvidia-current (driver version 195.36.15)
2. nvidia-173 (driver version 173.14.22)
3. nvidia-96 (driver version 96.43.17)

why isn't there a package that provides a version 185.* driver any longer? nvidia-current breaks the 3D apps on my system (causes random freezing). nvidia-173 fixes the freezing problems but is really old, and casts a blue tint on video playback. 

i'm not understanding why there's not something more recent between the 173 and current packages. i'm in a real pickle here without a working Nvidia driver. Ubuntu 9.10 worked flawlessly on this system, but i made a mistake by upgrading to 10.04 it seems.

---

### Post by Woody1987 on 2010-05-13
Just run
```
sudo apt-get install nvidia-glx-185
```

Alternatively, download the latest from the nvidia website and install manually.

---

### Post by calmasy on 2010-05-13
> **Woody1987 said:**
> Just run
```
sudo apt-get install nvidia-glx-185
```

No. the -185 package provides Nvidia version 195.36.15 drivers. Seems odd, I know, but it's the case.

---

### Post by Woody1987 on 2010-05-20
According to synaptic, the 180 package contains the 185 version.

---

### Post by Nythain on 2010-05-20
i can only assume that there's no 180 package (if thats actually the case) because 173 is the current stable legacy release, and 195 is the current release, it doesnt make much sense to have the 180 driver

---

