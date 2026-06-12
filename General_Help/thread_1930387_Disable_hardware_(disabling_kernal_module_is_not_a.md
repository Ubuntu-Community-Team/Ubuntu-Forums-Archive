---
title: "Disable hardware (disabling kernal module is not a option)"
date: 2012-02-23
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-02-23
Technically not solved but irrelevant
seems it is the nvidia driver not the presence of a loaded kernel model that has this result

Orignal post:
Enabling HDMI sound is a real pita so it would be easer to disable it and use the secondary audio input on the tv that would be active when using DVI-HDMI adapter i figured out that if there is no kernel model loaded on the hdmi sound card it will use the 1/8" audio jack but both pieces of hardware use the same kernel module [FONT=Courier New]snd-hda-intel[/FONT]

so if i disable this:
```
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 83be
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```while not disabling this:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. Device 836c
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f7ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```i can get sound on the tv via the 1/8" audio cable that would normally be used with DVI or VGA

---

