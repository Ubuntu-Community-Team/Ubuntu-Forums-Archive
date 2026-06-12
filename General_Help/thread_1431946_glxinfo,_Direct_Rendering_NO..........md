---
title: "glxinfo, Direct Rendering: NO.........?"
date: 2010-03-17
forum: General Help
---

### Post by Sceiron on 2010-03-17
By running glxinfo i find out that i have no Direct Rendering.

What does this mean? 
I want to install WC3 in VirtualBox, and that presuppose OpenGL support is available.
(Accorgin to this site: [http://forums.virtualbox.org/viewtopic.php?f=2&t=15436](http://forums.virtualbox.org/viewtopic.php?f=2&t=15436))

How do i know that OpenGL is working?

```
$ glxinfo
name of display: :1046.0
Xlib:  extension "Generic Event Extension" missing on display ":1046.0".
display: :1046  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
...............

```

Do i need to have Driver "OpenGL" instead of Nvidia?

```

~$ hwinfo --gfxcard
24: PCI 400.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_92
  Unique ID: YmUS.+FyNonh2c48
  Parent ID: vSkL.aEVL1N5Zl53
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:04:00.0
  SysFS BusID: 0000:04:00.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 7800 GT"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0092 "GeForce 7800 GT"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81db 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"

```


Running glxgears gives a low fps accoring to other posts I have seen, but its maybe my graphics card... .?
```

~$ glxgears
Xlib:  extension "Generic Event Extension" missing on display ":1046.0".
2923 frames in 5.0 seconds
3240 frames in 5.0 seconds
3280 frames in 5.0 seconds
3360 frames in 5.0 seconds
3260 frames in 5.0 seconds
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":1046.0"
      after 36040 requests (35901 known processed) with 0 events remai

```


EDIT:
By turning off Visual Effects in the System ->Preferences-> Apperance ->visual effects
Direct Rendering is now enabled. So this solves it.

---

