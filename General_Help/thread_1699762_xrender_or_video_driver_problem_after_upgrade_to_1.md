---
title: "xrender or video driver problem after upgrade to 10.10"
date: 2011-03-04
forum: General Help
---

### Post by elempe on 2011-03-04
Hi,

after upgrading to 10.10 I ran into one problem. Upgraded some while ago (when released), then noticed problem but now it starts to really bother me. Unfortunately didn't find any solution yet. I'm 100% sure I didn't have such problem during upgrades starting from Karmic till Lucid.

The problem is with any version of wine (it's not wine issue, i think) and MetaTrader4 on it. Not typical VNC issue ;)

The problem is that it works almost normally, but don't show some lines on screen. Take a look at screenshot attached. I found in wine proposal to disable xrender:
[http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71](http://wiki.winehq.org/FAQ#head-3b18ce54edb7ea108c8f08945bc52812c4e3ef71)
it really helps with that issue, but then I ran in typical AplhaBlend problem and no visible icons in toolbars. So I have to choose to see normal icons in toolbars (see 2nd screenshot) or to see correct chart :D

Little bit about my laptop:
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Fujitsu Limited. Device 13f8
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe000000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Fujitsu Limited. Device 13f8
    Flags: bus master, fast devsel, latency 0
    Memory at fe100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3

and:
lsmod | egrep "video|agp"
uvcvideo               55847  0 
videodev               43098  1 uvcvideo
video                  18712  1 i915
intel_agp              26566  2 i915
v4l1_compat            13359  2 uvcvideo,videodev
agpgart                32011  2 drm,intel_agp
output                  1883  1 video

So maybe there is some ideas what to try to do? Maybe some workaround? 

Thanks ;)

---

### Post by elempe on 2011-03-13
Really nobody have any ideas? :rolleyes:

---

