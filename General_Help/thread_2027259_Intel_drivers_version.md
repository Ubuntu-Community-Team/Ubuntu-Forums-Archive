---
title: "Intel drivers version"
date: 2012-07-16
forum: General Help
---

### Post by Lupajz on 2012-07-16
How can I obtain what version of Intel Linux Graphics am I running atm ?

---

### Post by dino99 on 2012-07-16
use synaptic to check xserver-xorg-video-intel package

---

### Post by Cheesemill on 2012-07-16
Or from the command line:
```
apt-cache show xserver-xorg-video-intel | grep Version
```

---

