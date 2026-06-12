---
title: "Problems after installing drivers"
date: 2011-03-09
forum: General Help
---

### Post by Enk on 2011-03-09
Hi

I'm running 64-bit Ubuntu 10.10, and got a ATI Radeon HD 5700 Series graphics card.

I've used the system for a while without problems (played some WoW with no problems).

But I wanted to try out SC2 in Ubuntu, and since it didn't seem to work, I decided to try to update the drivers.

I downloaded the drivers from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and ran it, but after the install X wouldn't start.

I tried aticonfi --inital, but got an error msg about display wasn't found.

So I deleted the /etc/X11/xorg.conf-file, and ran startx, and got back intro X11 (guess with default settings?).

I tried to run a "glxinfo" but that gave me an segmentation fault :/

Now I tried enabling the drivers from the "Additional Drivers"-window in Ubuntu, but it just gives me this error:

```
2011-03-09 14:40:56,735 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-09 14:40:56,736 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
```

I tried to remove/install fglrx, but now it just gives me a error message.

So what I want now is EITHER to be able to use the drivers I downloaded from ATI, or the proprietary ones. Don't know what's going on now :P

---

### Post by Enk on 2011-03-09
Error message when trying to re-install fglrx:

```
[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

```

I've tried what the error message suggest, but get the same error message when doing that :S

---

