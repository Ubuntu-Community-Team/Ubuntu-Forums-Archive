---
title: "Ubuntu 10.04 + Nvidia(6600GT) =&gt; Segmentation fault at address 0x24"
date: 2010-05-05
forum: General Help
---

### Post by tgyet on 2010-05-05
Hello!

Somedays ago I installed Ubuntu 10.04. Everything worked perfectly until I installed the Nvidia drivers. The system started but when the desktop was loaded the OS freezed. It was black with colored artifacts. (So not totally black) If the system ran previously the last desktop state was shown with the same artifacts. (So that's why I think this is not the same black screen problem like others have.)

I can not use the desktop but I can switch to the console mode (CTRL+ALT+F1), I tried to search the root of the problem and what I found from Xorg.0.log: The system recognized the video card (6600GT), the monitor (LG W2252S) and it can found the optimal resolution (1680x1050) too. However when it wanted to change the resolution to the optimal one, there was an error message:

```
(II) May 04 19:07:13 NVIDIA(0): Setting mode "nvidia-auto-select"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x675410]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting
```

I tried more than one driver (185,195,173), but I had the same problem with every version.

I used Windows 7 until now and I had no problem with the computer, so I think it is not hardware related. Maybe important: I have an AsRock p4i65g main-board with an integrated Intel video card. (When I use a real GPU, the integrated one is disabled by the BIOS) I already installed the Linux more than once, I thought maybe the installation went wrong, but it did not helped.

Has somebody this problem too? Thank you for your helps.

TGYET

---

### Post by abolo on 2010-10-13
Same issue, the machine often goes for days without any problem.

uname -a = 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

version = Ubuntu 10.04.1 LTS

graphics = 8600GT

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e938b]
1: /usr/bin/X (0x8048000+0x61c8d) [0x80a9c8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xf34410]
Segmentation fault at address 0x24

Caught signal 11 (Segmentation fault). Server aborting

---

### Post by zaidaus on 2011-01-06
I'm having the same issue on 10.04 using nvidia 7600gs.


(II) Jan 07 09:26:50 NVIDIA(0): Assigned Display Device: CRT-0
(==) Jan 07 09:26:50 NVIDIA(0): 
(==) Jan 07 09:26:50 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jan 07 09:26:50 NVIDIA(0):     will be used as the requested mode.
(==) Jan 07 09:26:50 NVIDIA(0): 
(II) Jan 07 09:26:50 NVIDIA(0): Validated modes:
(II) Jan 07 09:26:50 NVIDIA(0):     "nvidia-auto-select"
(II) Jan 07 09:26:50 NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) Jan 07 09:26:50 NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) Jan 07 09:26:50 NVIDIA(0):     option
(==) Jan 07 09:26:50 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jan 07 09:26:50 NVIDIA(0): Initialized GPU GART.
(II) Jan 07 09:26:50 NVIDIA(0): Setting mode "nvidia-auto-select"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eaadb]
1: /usr/bin/X (0x8048000+0x610fd) [0x80a90fd]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb781e410]
Segmentation fault at address 0x24

---

### Post by thegve on 2011-01-25
Same issue:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Dell Latitude E5500 notebook

# modinfo i915
filename:       /lib/modules/2.6.35-24-generic/kernel/drivers/gpu/drm/i915/i915.ko

# cat /etc/issue.net 
Ubuntu 10.10

In my updates, I see there is a fix addressing a crash issue when using gestures. These 'gestures' seem to have something to do with multitouch stuff Apple and other vendors use, I don't use gestures however, see [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/670016](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/670016) .

I'll search for and probably make a new bug report.

xorg.0.log.old
```
[  5708.998] (II) intel(0): Modeline "1280x800"x0.0   49.84  1280 1296 1344 1494  800 801 804 834 +hsync -vsync (33.4 kHz)
[  6514.602] 
Backtrace:
[  6514.613] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[  6514.614] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[  6514.614] 2: /lib/libpthread.so.0 (0x7fdf65abe000+0xfb40) [0x7fdf65acdb40]
[  6514.614] 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fdf62c41000+0x1eed4) [0x7fdf62c5fed4]
[  6514.614] 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7fdf62c41000+0x37b34) [0x7fdf62c78b34]
[  6514.614] 5: /usr/bin/X (0x400000+0xd3b8a) [0x4d3b8a]
[  6514.614] 6: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[  6514.614] 7: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[  6514.614] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fdf64a29d8e]
[  6514.614] 9: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[  6514.614] Segmentation fault at address 0x3b
[  6514.614] 
Caught signal 11 (Segmentation fault). Server aborting
[  6514.614] 
```

---

