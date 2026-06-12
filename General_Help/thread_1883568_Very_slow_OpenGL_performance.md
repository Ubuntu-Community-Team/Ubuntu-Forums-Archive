---
title: "Very slow OpenGL performance"
date: 2011-11-19
forum: General Help
---

### Post by keithclark on 2011-11-19
I'm getting extremely poor OpenGL performance.  glxgears reports around 180 fps and Flightgear runs about 4 fps.

System:

Pentium Dual-Core E5800 @ 3.2 GHz
8 GB RAM
64 bit Ubuntu 11.10
GeForce 6200/PCI/SSE2

Software information:

grep -i memory /var/log/Xorg.0.log 
[    19.440] (--) NVIDIA(0): Memory: 524288 kBytes
[    19.692] (==) NVIDIA(0): Disabling shared memory pixmaps

lspci -v -s 03:00.0
03:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Device b402
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
	Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (32-bit, prefetchable) [size=512M]
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at de000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

glxinfo | grep ^Open
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 280.13
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

Flightgear version is 2.0.0-4ubuntu1

Any ideas on how to improve on this?  My old AMD 64 3500+ with 4 GB RAM and an ATI xpress200m outperformed this system!

Thanks,

Keith

---

