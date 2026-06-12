---
title: "sound problem"
date: 2011-02-07
forum: General Help
---

### Post by piymon on 2011-02-07
Here are some details about my laptop:

When running lspci -v:
> 
piyush@piyush-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Device 0044 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Device 0046 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4050 [size=8]
    Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Ibex Peak HECI Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 94406100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 94405c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Ibex Peak High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 93400000-943fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000913fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 92400000-933fffff
    Prefetchable memory behind bridge: 0000000091400000-00000000923fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at 94405800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation Ibex Peak 4 port SATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
    I/O ports at 4048 [size=8]
    I/O ports at 405c [size=4]
    I/O ports at 4040 [size=8]
    I/O ports at 4058 [size=4]
    I/O ports at 4020 [size=32]
    Memory at 94405000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: medium devsel, IRQ 10
    Memory at 94406000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation Ibex Peak Thermal Subsystem (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 94404000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1483
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at 93400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 2295
    I/O ports at 2000 [size=256]
    Memory at 91410000 (64-bit, prefetchable) [size=4K]
    Memory at 91400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 91420000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Device 2c62 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Device 2d01 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Device 2d10 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Device 2d11 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

piyush@piyush-laptop:~$ 



all external devices r working fine but the inbuilt sound speaker is not working

---

### Post by piymon on 2011-02-07
my model no. is g42-460tu

---

### Post by bilkay on 2011-02-07
Check this:

[http://ubuntuforums.org/showthread.php?t=1570060](http://ubuntuforums.org/showthread.php?t=1570060)

---

### Post by piymon on 2011-02-08
> **bilkay said:**
> Check this:

[http://ubuntuforums.org/showthread.php?t=1570060](http://ubuntuforums.org/showthread.php?t=1570060)

i read the whole thread but nothing worked
should i install ubuntu 10.10 netbook on my laptop or not.
i mean to say does netbook versions  have any problems

---

### Post by piymon on 2011-02-08
i hav installed 10.10 desktop 64 bit and working very cool. thanks for help

---

