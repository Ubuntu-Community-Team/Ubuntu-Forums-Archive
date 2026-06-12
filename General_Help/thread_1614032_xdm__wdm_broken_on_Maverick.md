---
title: "xdm / wdm broken on Maverick"
date: 2010-11-05
forum: General Help
---

### Post by ZYV on 2010-11-05
Hi!

I have installed a Maverick machine and was utterly annoyed by the removal of XDCMP chooser in GDM (why in the world one would do this?!). The common wisdom seemed to install xdm or wdm instead.

I did try both of them (dpkg-reconfigure gdm and select xdm or wdm), BUT none is working. The only relevant point I found in xdm log: it fails to start X correctly, where spawned X instance claims that no usable screens can be found.

At the same time, gdm starts just fine.

Was anyone successful in getting any of these running?

Z.

---

### Post by ZYV on 2010-11-05
I posted the X log that I get when I set the login manager to xdm here: [http://paste.ubuntu.com/526303/](http://paste.ubuntu.com/526303/) . The relevant part is:

> [    15.626] (--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
[    15.627] (II) RADEON(0): AGP card detected
[    15.627] (II) RADEON(0): KMS Color Tiling: disabled
[    15.627] drmOpenDevice: node name is /dev/dri/card0
[    15.627] drmOpenDevice: open result is 9, (OK)
[    15.627] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    15.627] drmOpenDevice: node name is /dev/dri/card0
[    15.627] drmOpenDevice: open result is 9, (OK)
[    15.627] drmOpenByBusid: drmOpenMinor returns 9
[    15.627] drmOpenByBusid: drmGetBusid reports 
...
[    15.685] drmOpenDevice: node name is /dev/dri/card0
[    15.685] drmOpenDevice: open result is 9, (OK)
[    15.685] drmOpenDevice: node name is /dev/dri/card0
[    15.685] drmOpenDevice: open result is 9, (OK)
[    15.685] drmGetBusid returned ''
[    15.685] (EE) RADEON(0): [drm] failed to set drm interface version.
[    15.685] (EE) RADEON(0): Kernel modesetting setup failed
[    15.685] (II) UnloadModule: "radeon"
[    15.685] (EE) Screen(s) found, but none have a usable configuration.
[    15.685] 
Fatal server error:
[    15.685] no screens found


which is completely brilliant. So it looks for dri devices everywhere, finds one and just bails out instead of using it. How great!

Anyway, gdm somehow manages to start it, so I suspect, that there is a problem with the way wdm / xdm invoke X. Maybe AppArmor, capabilities, permissions or something along these lines?

Ideas?

Z.

---

### Post by ZYV on 2010-11-05
[https://bugs.launchpad.net/ubuntu/+source/xdm/+bug/585853](https://bugs.launchpad.net/ubuntu/+source/xdm/+bug/585853)

---

### Post by StygianAgenda on 2011-03-01
> **ZYV said:**
> I posted the X log that I get when I set the login manager to xdm here: [http://paste.ubuntu.com/526303/](http://paste.ubuntu.com/526303/) . The relevant part is:



which is completely brilliant. So it looks for dri devices everywhere, finds one and just bails out instead of using it. How great!

Anyway, gdm somehow manages to start it, so I suspect, that there is a problem with the way wdm / xdm invoke X. Maybe AppArmor, capabilities, permissions or something along these lines?

Ideas?

Z.

I might be wrong, but I think the problem is with the 'radeon' driver module.  If memory serves, the Radeon module doesn't support card of the 9xxx series anymore.  Try the vesa driver instead.  I had this exact same problem with both Ubuntu 10.04 and OpenSuSE 11.2-3.  ATI has now moved support for older cards to their legacy driver, which ended production around a year ago.  ATI's answer for this is to either (a) upgrade, or (b) use the generic VESA driver instead.

---

### Post by ZYV on 2011-03-01
StygianAgenda, thanks for the helpful reply. I posted the link to the bug already. It is in fact related to faulty graphics drivers but it not only affects radeon, but also other drivers.

I solved the problem by using kdm for now.

---

