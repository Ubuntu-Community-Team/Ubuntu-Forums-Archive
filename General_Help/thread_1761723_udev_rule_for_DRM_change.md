---
title: "udev rule for DRM change"
date: 2011-05-18
forum: General Help
---

### Post by djkadu on 2011-05-18
Hi, I'm trying to create a udev rule that will run a script when DRM changes, I want to use this so my desktop detects the correct number of monitors when I dock/undock my laptop

I'm aware gnome probably does this as default, but I'm not using gnome. I'm using e16 instead.

The rule should be simple but nothing is happening.

```

cat 20-dock.rules 
SUBSYSTEM=="drm",ACTION=="change",RUN+="/etc/X11/Xsession.d/45custom_xrandr-settings"

```As we can see from the output of udevadm monitor the drm sees a change event
```

$ udevadm monitor 
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1305733978.495595] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [1305733978.498275] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)

```Any help much appreciated.

---

