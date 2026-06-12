---
title: "Command to see drivers in 11.04?"
date: 2011-06-15
forum: General Help
---

### Post by Doctorly on 2011-06-15
Is there a command to see which drivers I have installed? More specifically my GPU driver. Thanks in advance:)

---

### Post by idoitprone on 2011-06-15
```
lspci -v

```?

---

### Post by Doctorly on 2011-06-15
Hm, my results were interesting:

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0292
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
    Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon


Does the fact that it says radeon mean that I have no driver? Does the fact that "Capabillites" says "access denied" a bad thing? I really hope my problem is the driver!! It could fix some problems for me:)!

---

### Post by plucky on 2011-06-15
> Does the fact that it says radeon mean that I have no driver?

You are using the radeon driver as opposed to the vesa driver built into the kernel.


> Does the fact that "Capabillites" says "access denied" a bad thing?

It just means you don't have the permission to access that information.

Try ```
sudo lspci -v
```

Also ```
sudo lshw -C display
```

> I really hope my problem is the driver!! It could fix some problems for me! 

Have you tried **System > Administration > Hardware Drivers** to see what drivers are available for your video card? 

You will need internet access for this to work.

Good Luck

---

