---
title: "New PC won't recognize storage devices"
date: 2010-09-30
forum: General Help
---

### Post by Serpher on 2010-09-30
My friend bought a new PC, and he's duel booting Ubuntu 10.04LTS and Windows 7 Ultimate. At first I tried partitioning the hardrive using fdisk in Ubuntu, but it couldn't find hda. After looking in /dev/, there wasn't hda, or any sd* devices. I looked in gparted and used the installer afterwards and both came up with nil. I installed Windows, updated the BIOS using the utility that came with the mobo, and tried seeing if Ubuntu could detect my hardrive and it couldn't. I even turned ACPI off when booting and that didn't work either. 
[[IMG]http://img837.imageshack.us/img837/9265/postp.png[/IMG]](http://img837.imageshack.us/i/postp.png/)

The motherboard is a new Gigabit with 3 PCIe slots and a USB3.0. It's pretty new so I'm wondering if that would be the problem.


Thanks!

---

### Post by Serpher on 2010-09-30
Output of lspci:

```
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
04:00.0 Power PC: Freescale Semiconductor Inc Device 00b6 (rev 12)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
07:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
07:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
09:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
09:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```

Output of lshw:

```
ubuntu
    description: Desktop Computer
    product: X58A-UD3R
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=4 uuid=00000000-0000-0000-0000-6CF0495836BE
  *-core
       description: Motherboard
       product: X58A-UD3R
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6 (08/24/2010)
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.10.5
          serial: 0001-06A5-0000-0000-0000-0000
          slot: Socket 1366
          size: 1596MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=7
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 8MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 7.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 7.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 7.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 7.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 7.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 7.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 7.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 7.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 7.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 7.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 7.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 7.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 7.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 7.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 7.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 7.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 2244 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             physical id: 2
             slot: A2
             size: 2GiB
             width: 2244 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
        *-bank:4
             description: DIMM 400 MHz (2.5 ns)
             physical id: 4
             slot: A4
             size: 2GiB
             width: 2244 bits
             clock: 400MHz (2.5ns)
        *-bank:5
             description: DIMM [empty]
             physical id: 5
             slot: A5
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.10.5
          serial: 0001-06A5-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          capabilities: vmx ht cpufreq
          configuration: id=7
        *-logicalcpu:0
             description: Logical CPU
             physical id: 7.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 7.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 7.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 7.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 7.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 7.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 7.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 7.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 7.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 7.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 7.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 7.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 7.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 7.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 7.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 7.10
             capabilities: logical
     *-cpu:2
          physical id: 2
          bus info: cpu@2
          version: 6.10.5
          serial: 0001-06A5-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          capabilities: vmx ht cpufreq
          configuration: id=7
        *-logicalcpu:0
             description: Logical CPU
             physical id: 7.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 7.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 7.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 7.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 7.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 7.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 7.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 7.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 7.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 7.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 7.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 7.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 7.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 7.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 7.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 7.10
             capabilities: logical
     *-cpu:3
          physical id: 3
          bus info: cpu@3
          version: 6.10.5
          serial: 0001-06A5-0000-0000-0000-0000
          size: 1596MHz
          capacity: 1596MHz
          capabilities: vmx ht cpufreq
          configuration: id=7
        *-logicalcpu:0
             description: Logical CPU
             physical id: 7.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 7.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 7.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 7.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 7.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 7.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 7.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 7.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 7.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 7.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 7.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 7.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 7.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 7.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 7.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 7.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: 5520/5500/X58 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:a000(size=4096) memory:fb800000-fb8fffff memory:f4000000-f40fffff(prefetchable)
           *-ide UNCLAIMED
                description: IDE interface
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress cap_list
                configuration: latency=0
                resources: ioport:af00(size=8) ioport:ae00(size=4) ioport:ad00(size=8) ioport:ac00(size=4) ioport:ab00(size=16) memory:fb8ff000-fb8ff7ff memory:f4000000-f400ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:fb600000-fb6fffff
           *-usb
                description: USB Controller
                product: NEC Corporation
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:16 memory:fb6fe000-fb6fffff
        *-pci:2
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:b000(size=4096) memory:f6000000-f9ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9800 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f8000000-f8ffffff memory:e0000000-efffffff(prefetchable) memory:f6000000-f7ffffff ioport:bf00(size=128) memory:f9000000-f901ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:fbd00000-fbefffff ioport:fa000000(size=16777216)
           *-processor UNCLAIMED
                description: Power PC
                product: Freescale Semiconductor Inc
                vendor: Freescale Semiconductor Inc
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 12
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:fbd00000-fbdfffff memory:fbeff000-fbefffff memory:fa000000-faffffff(prefetchable) memory:fbef8000-fbefbfff
        *-generic:0 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Physical and Link Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Routing and Protocol Layer Registers Port 0
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 13
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: PIC
             product: 5520/5500 Physical and Link Layer Registers Port 1
             vendor: Intel Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: 5520/5500 Routing & Protocol Layer Register Port 1
             vendor: Intel Corporation
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 13
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fbfff000-fbffffff
        *-generic:5 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:6 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:7 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:8 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 Trusted Execution Technology Registers
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 13
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:fe00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:fbff8000-fbffbfff
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:1000(size=4096) memory:f4100000-f42fffff memory:f4300000-f44fffff(prefetchable)
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:e000(size=4096) memory:fbc00000-fbcfffff memory:f4500000-f46fffff(prefetchable)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:17 memory:fbcfe000-fbcfffff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:06:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:18 ioport:ef00(size=8) ioport:ee00(size=4) ioport:ed00(size=8) ioport:ec00(size=4) ioport:eb00(size=16)
        *-pci:6
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:d000(size=4096) memory:fbb00000-fbbfffff memory:f4700000-f48fffff(prefetchable)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:19 memory:fbbfe000-fbbfffff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:07:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:df00(size=8) ioport:de00(size=4) ioport:dd00(size=8) ioport:dc00(size=4) ioport:db00(size=16)
        *-pci:7
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:c000(size=4096) memory:fba00000-fbafffff ioport:fb900000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 03
                serial: 6c:f0:49:58:36:be
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:32 ioport:ce00(size=256) memory:fb9ff000-fb9fffff(prefetchable) memory:fb9f8000-fb9fbfff(prefetchable) memory:fb900000-fb91ffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:fc00(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fb00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fa00(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-pci:8
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:fb700000-fb7fffff
           *-network
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 00:1e:2a:cc:7c:9a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.0.101 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:fb7e0000-fb7effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:09:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:18 memory:fb7ff000-fb7ff7ff memory:fb7f8000-fb7fbfff
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16) ioport:f800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffc000-fbffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=8) ioport:f300(size=4) ioport:f200(size=16) ioport:f100(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7260S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
```

---

### Post by Serpher on 2010-10-01
I booted with the kernel argument "pci=nomsi", and tonight I'm going to try running Fedora on it due to it's newer kernel. If anybody could give me any help it would be appreciated.

---

