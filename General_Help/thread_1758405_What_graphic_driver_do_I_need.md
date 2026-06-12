---
title: "What graphic driver do I need?"
date: 2011-05-14
forum: General Help
---

### Post by winchendonsprings on 2011-05-14
Here is my lspci -v ```


00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4050 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

```It's a brand new hp G62x laptop. I originally posted a longer description( and possibly more confusing) in the hardware section [here]("http://ubuntuforums.org/showthread.php?t=1755830"). No one answered and I know someone must have had the same issue and figured it out. 

No proprietary drivers show up in the up in the Additional Drivers section. Is there a repository I should get?

---

### Post by lithopsian on 2011-05-14
Try xserver-xorg-video-intel and everything it wants to bring with it.  Probably also libgl1-mesa-glx.  These are the open source drivers.  If they don't work for you.  Intel chips don't have proprietary drivers in Linux.

---

### Post by winchendonsprings on 2011-05-15
Both of those were already installed. Damn

---

