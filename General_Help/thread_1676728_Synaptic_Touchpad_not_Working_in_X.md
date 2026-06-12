---
title: "Synaptic Touchpad not Working in X"
date: 2011-01-27
forum: General Help
---

### Post by mbusha on 2011-01-27
I have a Lenovo T510 whose touchpad seems to have suddenly stopped working.  It operates fine if I boot into Windows, but in Ubuntu, neither the touchpad nor its associated buttons have any effect (the eraser mouse still works, though).  I'm guessing I inadvertently made a stupid change to my settings somehow.  

If I try booting into Recover Mode, the trackpad works while selecting modes to boot into, but the stops working as soon as X starts.  I've checked the touchpad settings under Preferences->Mouse and Preferences->Pointing Devices, and nothing seems to be obviously disabled, but I might be missing something.  When I check my Xorg.0.log file, it looks like the touchpad is being loading correctly:

```
$ grep -i synaptics Xorg.0.log
[    21.922] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    21.923] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.923] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.923] (II) LoadModule: "synaptics"
[    21.923] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.183] (II) Module synaptics: vendor="X.Org Foundation"
[    22.183] (II) Synaptics touchpad driver version 1.2.2
[    22.481] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    22.481] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4820
[    22.481] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.481] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    22.481] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    22.711] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.711] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.780] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    22.780] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.780] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    22.780] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.780] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.880] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.880] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
```I'm running the 64-bit version of Ubuntu 10.10.  Any thoughts would be appreciated.

---

