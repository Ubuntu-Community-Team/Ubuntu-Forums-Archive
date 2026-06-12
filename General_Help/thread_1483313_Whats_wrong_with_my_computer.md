---
title: "Whats wrong with my computer???"
date: 2010-05-14
forum: General Help
---

### Post by demonic_crow on 2010-05-14
Anyone see what wrong with my computer.  I'm running Ubuntu 9.10. My wireless internal internet card doesn't work for some reason and I do get some pci error message when I boot my computer up on and off again for some reason.  Any way of fixing these problems.

```
demonic@Hellraiser:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: fast devsel
    Memory at 20100000 (32-bit, non-prefetchable) [disabled] [size=512K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b4000000-b7ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at b0040000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=216
    Memory behind bridge: 20000000-200fffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at b0040800 (32-bit, non-prefetchable) [size=512]
    Memory at b0040400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: medium devsel, IRQ 20
    I/O ports at 2400 [size=256]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    Subsystem: Gateway 2000 Device 0365
    Flags: medium devsel, IRQ 11
    I/O ports at 20a0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Memory at b4000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 3000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

06:09.0 Non-VGA unclassified device: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
    !!! Invalid class 0000 for header type 02
    Subsystem: Gateway 2000 Device 0365
    Flags: bus master, medium devsel, latency 64
    Bus: primary=00, secondary=00, subordinate=00, sec-latency=0
    16-bit legacy interface ports at 03e1
    Kernel modules: yenta_socket

06:09.2 PIC: Texas Instruments OHCI Compliant IEEE 1394 Host Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

06:09.4 Non-VGA unclassified device: Catalina Research Inc Device 8031 (prog-if 04)
    !!! Invalid class 0000 for header type 02
    Subsystem: Device 0420:0000
    Flags: bus master, medium devsel, latency 68
    Memory at <ignored> (32-bit, non-prefetchable) [disabled]
    Bus: primary=00, secondary=04, subordinate=00, sec-latency=0
    16-bit legacy interface ports at 07e1

06:09.6 PIC: Catalina Research Inc Device 8032 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

06:09.7 Mass storage controller: Catalina Research Inc Device 8033 (rev ff) (prog-if ff)
    !!! Unknown header type 7f

```

---

### Post by demonic_crow on 2010-05-15
anyone can help me out???

---

