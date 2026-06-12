---
title: "NVidia drivers fail to load"
date: 2011-05-12
forum: General Help
---

### Post by HughJarse on 2011-05-12
```
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
```

If I hit the option Restart X it boots and displays normally but I always get this while booting

---

### Post by khelben1979 on 2011-05-12
I think it's good news since the nVidia driver from the Linux kernel is the open source video driver, and you want it disabled to be able to use the faster non-free driver which I guess you presently do?

In the nVidia control panel, can you see what driver version you got? Other than that, making sure that noveau is disabled might remove that error you're getting.

More information about the nVidia graphics driver:
[Nouveau : Accelerated Open Source driver for nVidia cards]("http://nouveau.freedesktop.org/wiki/").

---

