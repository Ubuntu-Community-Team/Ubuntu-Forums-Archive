---
title: "video driver"
date: 2012-10-01
forum: General Help
---

### Post by haaho on 2012-10-01
PLease help,


The problem is that after fresh instalation I can use Unity 3D with no problems.
But if the system is shutdown inproperly (no electricity or hardware reset)  I can not use it any nore. It always starts Unity 2D. How can I fix this?

I am using ATI 9550 with free driver.

I forgot to mention I am using Ubuntu 12.04, but the same thing happened with 10.04 also.
Thank you.



Now after several hard restarts I managed to fix it, somehow, and I can see the difference with the previous stage:

first It was:

```
ivo@ivo-server:~$ dmesg | grep drm
[   18.570423] [drm] Initialized drm 1.1.0 20060810
[   18.816574] [drm] radeon defaulting to kernel modesetting.
[   18.816580] [drm] radeon kernel modesetting enabled.

```now it is

```
ivo@ivo-server:~$ dmesg | grep drm
[   18.570423] [drm] Initialized drm 1.1.0 20060810
[   18.816574] [drm] radeon defaulting to kernel modesetting.
[   18.816580] [drm] radeon kernel modesetting enabled.
[   18.823865] [drm] initializing kernel modesetting (RV350 0x1002:0x4153 0x1458:0x4050).
[   18.823895] [drm] register mmio base: 0xFF4F0000
[   18.823897] [drm] register mmio size: 65536
[   18.825431] [drm] Generation 2 PCI interface, using max accessible memory
[   18.825452] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.825454] [drm] Driver supports precise vblank timestamp query.
[   18.825479] [drm] radeon: irq initialized.
[   18.828889] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.828893] [drm] RAM width 128bits DDR
[   18.833493] [drm] radeon: 128M of VRAM memory ready
[   18.833495] [drm] radeon: 256M of GTT memory ready.
[   18.833553] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   18.841171] [drm] Loading R300 Microcode
[   19.023192] [drm] radeon: ring at 0x00000000E0001000
[   19.023220] [drm] ring test succeeded in 0 usecs
[   19.023466] [drm] radeon: ib pool ready.
[   19.023528] [drm] ib test succeeded in 0 usecs
[   19.042704] [drm] Radeon Display Connectors
[   19.042708] [drm] Connector 0:
[   19.042710] [drm]   VGA
[   19.042712] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   19.042714] [drm]   Encoders:
[   19.042716] [drm]     CRT1: INTERNAL_DAC1
[   19.042717] [drm] Connector 1:
[   19.042719] [drm]   DVI-I
[   19.042720] [drm]   HPD1
[   19.042722] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   19.042724] [drm]   Encoders:
[   19.042725] [drm]     CRT2: INTERNAL_DAC2
[   19.042727] [drm]     DFP1: INTERNAL_TMDS1
[   19.042729] [drm] Connector 2:
[   19.042730] [drm]   S-video
[   19.042731] [drm]   Encoders:
[   19.042826] [drm]     TV1: INTERNAL_DAC2
[   19.423585] [drm] fb mappable at 0xD0040000
[   19.423589] [drm] vram apper at 0xD0000000
[   19.423591] [drm] size 5242880
[   19.423593] [drm] fb depth is 24
[   19.423594] [drm]    pitch is 5120
[   19.423779] fbcon: radeondrmfb (fb0) is primary device
[   19.424579] fb0: radeondrmfb frame buffer device
[   19.424581] drm: registered panic notifier
[   19.424591] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0

```
and one more:

it was ```
ivo@ivo-server:~$ glxinfo | egrep "direct|vendor"
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VMware.... something...... 

```now it is:

```
ivo@ivo-server:~$ glxinfo | egrep "direct|vendor"
direct rendering: Yes
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: X.Org R300 Project

```
What is the reason for these changes and how can I prevent them on every electrical failure?

Thanks again

---

### Post by haaho on 2012-11-05
Anybody on this?

Why does my system change from R300 project to VMware a then back to R300?

---

### Post by apochry on 2012-11-05
Isn't the proprietary driver from AMD not working for you, or you just don't want to touch closed software?

---

### Post by haaho on 2012-11-05
No, It's not working with new kernels. The last Ubuntu proprietary driver worked with is 8.04 I think, anyway it is out of question.

When I have 3d efect with the free driver it is OK, for some reason I just loose them from time to time.

---

### Post by Mark Phelps on 2012-11-05
> **apochry said:**
> Isn't the proprietary driver from AMD not working for you, or you just don't want to touch closed software?

There is NO proprietary AMD driver for that video chipset -- and there has not been for YEARS. If the OP downloads anything from AMD and forces the install, they will LOSE video.

---

### Post by haaho on 2012-11-06
Could it be some mother board/bios thing/settings?

---

