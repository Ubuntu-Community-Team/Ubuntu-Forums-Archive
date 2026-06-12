---
title: "Xorg Crash when playing videos"
date: 2010-09-30
forum: General Help
---

### Post by BlueMendicant on 2010-09-30
Hi,

This morning I tried to open a movie with VLC and it crashed X, so I tried it in movie player, and then ran the Ubuntu system test. Everything kept crashing X. I was able to watch movies before today :(

The only thing funny in my Xorg.log.old is:

> drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "i915"
(EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
(EE) intel(0): Failed to become DRM master.

Full logs can be found [http://paste.ubuntu.com/503256/](http://paste.ubuntu.com/503256/), any ideas?

-----

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Lenovo Device 20e0
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Lenovo Device 20e4
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f4400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Lenovo Device 20e4
	Flags: bus master, fast devsel, latency 0
	Memory at f4200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
	Subsystem: Lenovo Device 20e6
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fc226800 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

---

### Post by BlueMendicant on 2010-09-30
Hi,

The issue was that I was passing an invalid kernel parameter (which is only available in new kernels) in my grub.conf which caused the module not to load.

---

