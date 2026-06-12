---
title: "Can't install NVidia driver ( 173 )."
date: 2009-10-18
forum: General Help
---

### Post by OpenGuard on 2009-10-18
Installed minimal Gnome ( 9.04, Minimal CD + gnome-core ) and can't seem to find a way to enable video card driver. As you see, I've installed all the packages, but nvidia module fails to load. What I'm missing here ?

```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
``````
ii  nvidia-173-kernel-source                   173.14.16-0ubuntu1                        NVIDIA binary kernel module source
ii  nvidia-glx-173                             173.14.16-0ubuntu1                        NVIDIA binary Xorg driver
ii  nvidia-settings                            180.25-0ubuntu1                           Tool of configuring the NVIDIA graphics driv

``````
FATAL: Module nvidia not found.
```

---

