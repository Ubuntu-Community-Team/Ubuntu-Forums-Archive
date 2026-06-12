---
title: "Slow desktop gfx performance in all areas, fail-safe boot works fine"
date: 2012-05-28
forum: General Help
---

### Post by Sere on 2012-05-28
Hello everyone and thanks in advance. Have been looking on the forums and elsewhere, the issue/symtpoms seem relatively unique so a new thread it is.

Symptoms:
The gui and desktop seems sluggish in general, and any gfx-heavy action makes it much worse and pegs both cores at 100%.  E.G. Lower res videos played from the hdd play ok-ish, but resizing to larger gets about 1-2 fps. Unity 2d no noticeable difference. 3d Games are totally unplayable. Things remarkably work fine if I reboot into the 'fail-safe'? mode.


Background:
Minimal/zero Linux experience. 12.04 desktop installed from LiveCD, proprietary drivers checkbox enabled, no other changes. Both with full updates, and after a flatten/reinstall w/o updates.

Hardware:
Heavily modified Dell dimension 4600.
CPU: Intel® Pentium(R) 4 CPU 3.00GHz × 2 
Mem: 1.5 GiB
Gfx card: Geforce2 MX 400
SB Audigy sound card

output of sudo lspci -v:
```
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA controller])
    Subsystem: CardExpert Technology Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Expansion ROM at fea00000 [disabled] [size=64K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 2.0
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb
```That's just gfx card as I'd imagine it's the most relevant, can post rest if wanted. Other linux distros (puppy linux et al) working just fine with nouveau., but I'd rather have Precise working.
ANY help wildly appreciated, and thanks again in advance.

---

### Post by Rodney9 on 2012-05-28
Xubuntu 12.04 would run much faster.

[http://www.dedoimedo.com/computers/xubuntu-pangolin.html](http://www.dedoimedo.com/computers/xubuntu-pangolin.html)

Rodney

---

