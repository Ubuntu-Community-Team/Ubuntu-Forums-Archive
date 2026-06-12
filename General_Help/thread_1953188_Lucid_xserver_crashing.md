---
title: "Lucid xserver crashing"
date: 2012-04-05
forum: General Help
---

### Post by wgw on 2012-04-05
I'm getting random xserver crashes (cursor moves, but requires a hard reset to continue), usually (always?) when I am in Firefox or Chrome. It looks exactly like this ibm chipset problem ([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)) but I have an ati card, and not an ibm chipset: a thinkpad T60 with a ati X1300 Radeon card. I'm using the ubuntu driver without a problem for at least a year.  

I don't seem to have a problem with Opera, though it is hard to tell. I should probably file a bug report, but I thought I would check here first to see whether this is something already known. I'm not sure how I would ever fix it on my own. 

Thanks for any suggestions; error from /var/log/Xorg.0.log.old below. 

```
II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 90.0 MHz   Image Size:  285 x 214 mm
(II) RADEON(0): h_active: 1400  h_sync: 1448  h_sync_end 1560 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1051  v_sync_end 1054 v_blanking: 1066 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  HT14P12-100
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0030ae224000000000
(II) RADEON(0): 	000f0103801c1578eaaf4095564a8f25
(II) RADEON(0): 	20505421080081800101010101010101
(II) RADEON(0): 	010101010101302a7820511a10403070
(II) RADEON(0): 	13001dd61000001925237820511a1040
(II) RADEON(0): 	307013001dd6100000190000000f0090
(II) RADEON(0): 	43329043280f010009e50000000000fe
(II) RADEON(0): 	00485431345031322d3130300a20003f
(II) RADEON(0): EDID vendor "LEN", prod id 16418
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) Power Button: Device reopened after 1 attempts.
(II) Video Bus: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) TPPS/2 IBM TrackPoint: Device reopened after 1 attempts.
(II) ThinkPad Extra Buttons: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) XKB: reuse xkmfile /var/lib/xkb/server-5EAA9CFE77070260D8C18F7AFC4790090B1B9103.xkm
[mi] EQ overflowing. The server is probably stuck in an infinite loop.

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e954b]
1: /usr/bin/X (mieqEnqueue+0x1ab) [0x80e8d3b]
2: /usr/bin/X (xf86PostMotionEventP+0xd2) [0x80c2ed2]
3: /usr/bin/X (xf86PostMotionEvent+0x68) [0x80c3058]
4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x31b000+0x3603) [0x31e603]
5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x31b000+0x5e3d) [0x320e3d]
6: /usr/bin/X (0x8048000+0x6d75f) [0x80b575f]
7: /usr/bin/X (0x8048000+0x122914) [0x816a914]
8: (vdso) (__kernel_sigreturn+0x0) [0x5c1400]
9: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x5c2000+0xe525) [0x5d0525]
10: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x5c2000+0xe949) [0x5d0949]
11: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x5c2000+0x9f862) [0x661862]
12: /usr/lib/xorg/modules/libexa.so (0x308000+0x88e8) [0x3108e8]
13: /usr/lib/xorg/modules/libexa.so (0x308000+0x950b) [0x31150b]
14: /usr/bin/X (0x8048000+0xd9315) [0x8121315]
15: /usr/lib/xorg/modules/libexa.so (0x308000+0xa769) [0x312769]
16: /usr/bin/X (0x8048000+0xd8d88) [0x8120d88]
17: /usr/bin/X (CompositeGlyphs+0xa5) [0x81b9bf5]
18: /usr/bin/X (0x8048000+0xd2eaf) [0x811aeaf]
19: /usr/bin/X (0x8048000+0xcebc3) [0x8116bc3]
20: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
21: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
22: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x355bd6]
23: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
```

---

### Post by viniciushrs on 2013-04-12
I'm having the same problem (same backtrace, same desktop symptoms - only the cursor moves - system restart is required).

From Xorg.log:

[mi] EQ overflowing. The server is probably stuck in an infinite loop.


Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e955b]
1: /usr/bin/X (mieqEnqueue+0x1ab) [0x80e8d4b]
2: /usr/bin/X (xf86PostMotionEventP+0xd2) [0x80c2ee2]
3: /usr/lib/xorg/modules/input/evdev_drv.so (0x24e000+0x48a1) [0x2528a1]
4: /usr/lib/xorg/modules/input/evdev_drv.so (0x24e000+0x4b96) [0x252b96]
5: /usr/bin/X (0x8048000+0x6d76f) [0x80b576f]
6: /usr/bin/X (0x8048000+0x122944) [0x816a944]
7: (vdso) (__kernel_sigreturn+0x0) [0xca8400]
8: /lib/libdrm.so.2 (drmCommandWrite+0x3b) [0x1bd0ab]
9: /lib/libdrm_nouveau.so.1 (0x1ef000+0x2d7a) [0x1f1d7a]
10: /lib/libdrm_nouveau.so.1 (nouveau_bo_map_range+0xf1) [0x1f1ff1]
11: /lib/libdrm_nouveau.so.1 (nouveau_bo_map+0x33) [0x1f20c3]
12: /lib/libdrm_nouveau.so.1 (0x1ef000+0x1e38) [0x1f0e38]
13: /lib/libdrm_nouveau.so.1 (nouveau_pushbuf_flush+0x2f3) [0x1f1223]
14: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x1c5000+0x1c377) [0x1e1377]
15: /usr/lib/xorg/modules/libexa.so (0xe35000+0x894b) [0xe3d94b]
16: /usr/lib/xorg/modules/libexa.so (0xe35000+0x950b) [0xe3e50b]
17: /usr/bin/X (0x8048000+0xd9345) [0x8121345]
18: /usr/lib/xorg/modules/libexa.so (0xe35000+0xa769) [0xe3f769]
19: /usr/bin/X (0x8048000+0xd8db8) [0x8120db8]
20: /usr/bin/X (CompositeGlyphs+0xa5) [0x81b9c25]
21: /usr/bin/X (0x8048000+0xd2ebf) [0x811aebf]
22: /usr/bin/X (0x8048000+0xcebd3) [0x8116bd3]
23: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
24: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
25: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x361bd6]
26: /usr/bin/X (0x8048000+0x1e961) [0x8066961]



It only occurs after some time having Eclipse or Aptana Studio opened. The problem started to occur after I have installed an extra monitor to the PC.

---

