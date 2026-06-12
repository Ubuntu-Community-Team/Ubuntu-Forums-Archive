---
title: "2 touchsrcreen monitores"
date: 2011-01-20
forum: General Help
---

### Post by ideacoratex on 2011-01-20
Hello i am trying to put ubuntu working with 2 usbtouchscreens but i am having a problem with my 2º touchscreen can someone help me .
here part of my Xorg.0.log i think the problem is that ubuntu is loading evdev module before the second monitor.


(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
(II) Loading /usr/lib/xorg/modules/input/evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
        compiled for 1.7.6, module version = 0.8.8
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

Thanks in advance

---

