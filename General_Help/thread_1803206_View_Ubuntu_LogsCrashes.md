---
title: "View Ubuntu Logs/Crashes"
date: 2011-07-12
forum: General Help
---

### Post by phosphide on 2011-07-12
I am currently using 11.04 (Upgraded from 10.10) and my system is freezing/crashing and requires me to hold down the power button to use it again.

I was wondering if it is possible to review a log file that could detail why my system is freezing and crashing? I'm not doing anything that should yield an incredible amount of processing power. Mainly just browsing the internet and running an application or so. It works almost all the time, though usually about once a session I have to restart.

Here are my specs:

```
description: Notebook
    product: HP Compaq 8510w (RM297UT#ABA)
    vendor: Hewlett-Packard
    version: F.0B
    serial: CNU805038Q
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=RM297UT#ABA uuid=19076695-4B15-E011-0394-6D9910046129
  *-core
       description: Motherboard
       product: 30C5
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 71.36
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MVD Ver. F.0B
          date: 12/07/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          slot: U10
          size: 2201MHz
          capacity: 2201MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst external write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-667E1
             vendor: Micron Technology
             physical id: 0
             serial: EA01EF6D
             slot: DIMM #1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: DIMM #2
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:e5000000-e7ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84M [Quadro FX 570M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e5000000-e5ffffff memory:d0000000-dfffffff memory:e6000000-e7ffffff ioport:4000(size=128)
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: Mobile PM965/GM965 MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-e800000f
        *-ide:0
             description: IDE interface
             product: Mobile PM965/GM965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=ata_generic latency=0
             resources: irq:18 ioport:5000(size=8) ioport:5008(size=4) ioport:5010(size=8) ioport:5018(size=4) ioport:5020(size=16)
        *-communication:1
             description: Serial controller
             product: Mobile PM965/GM965 KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:5030(size=8) memory:e8001000-e8001fff
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1a:4b:7c:0a:98
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:44 memory:e8020000-e803ffff memory:e8040000-e8040fff ioport:5040(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:5060(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:5080(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:e8041000-e80413ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:e8044000-e8047fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:6000(size=4096) memory:e4000000-e40fffff ioport:88000000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wlan0
                version: 61
                serial: 00:1d:e0:a4:c3:e3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:e4000000-e4001fff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:2000(size=8192) memory:e0000000-e3ffffff ioport:88200000(size=2097152)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:50a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:50c0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:50e0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e8048000-e80483ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:e4100000-e43fffff ioport:80000000(size=134217728)
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:02:06.0
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00303020-b0030301f irq:16 memory:e4100000-e4100fff ioport:7000(size=256) ioport:7400(size=256) memory:80000000-83ffffff memory:8c000000-8fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:02:06.1
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00704020-b0070401f irq:17 memory:e4101000-e4101fff ioport:7800(size=256) ioport:7c00(size=256) memory:84000000-87ffffff memory:90000000-93ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:e4102000-e41027ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:19 memory:e4103000-e41030ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5100(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: BD-MLT UJ-210S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:5140(size=32) memory:e8049000-e80497ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHW2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sda
                version: 891B
                serial: K30XT8125UEY
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=95aa95aa
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7ef52e46-5202-4a92-9d1a-6e8be12da637
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2011-02-17 15:17:00 filesystem=ext3 modified=2011-05-05 12:05:12 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-07-12 22:08:45 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sda2
                   size: 4690MiB
                   capacity: 4690MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4690MiB
                      capabilities: nofs
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 11/25/2010
       serial: 00877
       slot: Primary
       capacity: 52000mWh
       configuration: voltage=14.8V

```

---

### Post by wildmanne39 on 2011-07-13
Hi, yes you can open log file viewer and look at the dmesg logs.Here is a link on freezing issues.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

From what you posted I see nothing wrong with your hardware.

---

### Post by phosphide on 2011-07-13
Thanks for the link. Might come in handy. Though, how would I run a terminal command if I'm frozen?

```
[    0.832636] loop: module loaded
[    0.832731] i2c-core: driver [adp5520] using legacy suspend method
[    0.832733] i2c-core: driver [adp5520] using legacy resume method
[    0.832825] ata_piix 0000:00:1f.1: version 2.13
[    0.832834] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.832875] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.833212] scsi0 : ata_piix
[    0.833303] scsi1 : ata_piix
[    0.833612] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5100 irq 14
[    0.833615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5108 irq 15
[    0.833660] ata2: port disabled. ignoring.
[    0.833666] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.833692] pata_acpi 0000:00:03.2: setting latency timer to 64
[    0.833703] pata_acpi 0000:00:03.2: PCI INT C disabled
[    0.833735] ata_generic 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.833751] ata_generic 0000:00:03.2: setting latency timer to 64
[    0.834135] scsi2 : ata_generic
[    0.834203] scsi3 : ata_generic
[    0.834246] ata3: PATA max UDMA/100 cmd 0x5000 ctl 0x5008 bmdma 0x5020 irq 18
[    0.834249] ata4: PATA max UDMA/100 cmd 0x5010 ctl 0x5018 bmdma 0x5028 irq 18
[    0.834544] Fixed MDIO Bus: probed
[    0.834573] PPP generic driver version 2.4.2
[    0.834614] tun: Universal TUN/TAP device driver, 1.6
[    0.834616] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.834701] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.834717] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.834730] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.834734] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.834775] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.834896] ehci_hcd 0000:00:1a.7: debug port 1
[    0.838788] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.838793] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe8041000
[    0.860018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.860149] hub 1-0:1.0: USB hub found
[    0.860155] hub 1-0:1.0: 4 ports detected
[    0.860233] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.860244] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.860248] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.860283] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.860343] ehci_hcd 0000:00:1d.7: debug port 1
[    0.864237] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.864252] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe8048000
[    0.880017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.880130] hub 2-0:1.0: USB hub found
[    0.880134] hub 2-0:1.0: 6 ports detected
[    0.880211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.880229] uhci_hcd: USB Universal Host Controller Interface driver
[    0.880276] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.880283] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.880287] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.880324] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.880380] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00005060
[    0.880498] hub 3-0:1.0: USB hub found
[    0.880503] hub 3-0:1.0: 2 ports detected
[    0.880572] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.880579] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.880583] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.880618] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.880674] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00005080
[    0.880793] hub 4-0:1.0: USB hub found
[    0.880797] hub 4-0:1.0: 2 ports detected
[    0.880869] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.880876] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.880879] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.880917] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.880964] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000050a0
[    0.881082] hub 5-0:1.0: USB hub found
[    0.881088] hub 5-0:1.0: 2 ports detected
[    0.881161] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.881168] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.881172] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.881211] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.881266] uhci_hcd 0000:00:1d.1: irq 22, io base 0x000050c0
[    0.881382] hub 6-0:1.0: USB hub found
[    0.881386] hub 6-0:1.0: 2 ports detected
[    0.881456] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.881463] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.881466] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.881509] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.881556] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000050e0
[    0.881673] hub 7-0:1.0: USB hub found
[    0.881677] hub 7-0:1.0: 2 ports detected
[    0.881807] i8042: PNP: PS/2 Controller [PNP0303:C251,PNP0f13:C252] at 0x60,0x64 irq 1,12
[    0.883441] i8042: Detected active multiplexing controller, rev 1.1
[    0.884157] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.884163] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.884194] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.884218] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.884244] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.884350] mousedev: PS/2 mouse device common for all mice
[    0.884508] rtc_cmos 00:07: RTC can wake from S4
[    0.884572] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.884604] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.884709] device-mapper: uevent: version 1.0.3
[    0.884780] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.884843] device-mapper: multipath: version 1.2.0 loaded
[    0.884846] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.885007] cpuidle: using governor ladder
[    0.885076] cpuidle: using governor menu
[    0.885301] TCP cubic registered
[    0.885419] NET: Registered protocol family 10
[    0.885874] NET: Registered protocol family 17
[    0.885887] Registering the dns_resolver key type
[    0.891626] PM: Hibernation image not present or could not be loaded.
[    0.891638] registered taskstats version 1
[    0.892025]   Magic number: 3:362:108
[    0.892031] usbmon usbmon4: hash matches
[    0.892036] ata_device dev3.1: hash matches
[    0.892038]  dev3.1: hash matches
[    0.892174] rtc_cmos 00:07: setting system clock to 2011-07-13 03:08:15 UTC (1310526495)
[    0.892177] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.892179] EDD information not available.
[    0.905787] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.010475] ata1.00: ATAPI: MATSHITABD-MLT UJ-210S, 1.24, max MWDMA2
[    1.050376] ata1.00: configured for MWDMA2
[    1.052911] scsi 0:0:0:0: CD-ROM            MATSHITA BD-MLT UJ-210S   1.24 PQ: 0 ANSI: 5
[    1.056035] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.056038] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.056137] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.056191] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.222397] Freeing unused kernel memory: 956k freed
[    1.222774] Write protecting the kernel read-only data: 10240k
[    1.223622] Freeing unused kernel memory: 184k freed
[    1.228849] Freeing unused kernel memory: 1444k freed
[    1.247205] <30>udev[74]: starting version 167
[    1.357883] sdhci: Secure Digital Host Controller Interface driver
[    1.357886] sdhci: Copyright(c) Pierre Ossman
[    1.359381] sdhci-pci 0000:02:06.3: SDHCI controller found [1180:0822] (rev 20)
[    1.359409] sdhci-pci 0000:02:06.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.360459] sdhci-pci 0000:02:06.3: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.366714] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    1.366717] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.366753] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.366765] e1000e 0000:00:19.0: setting latency timer to 64
[    1.366909] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[    1.383266] mmc0: no vmmc regulator found
[    1.384310] Registered led device: mmc0::
[    1.386807] mmc0: SDHCI controller on PCI [0000:02:06.3] using DMA
[    1.386847] firewire_ohci 0000:02:06.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.460117] firewire_ohci: Added fw-ohci device 0000:02:06.2, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.590036] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.902344] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1a:4b:7c:0a:98
[    1.902347] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.902375] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: FFFFFF-0FF
[    1.902419] ahci 0000:00:1f.2: version 3.0
[    1.902441] ahci 0000:00:1f.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.902501] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.902538] ahci: SSS flag set, parallel bus scan disabled
[    1.902563] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    1.902567] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc 
[    1.902573] ahci 0000:00:1f.2: setting latency timer to 64
[    1.903153] scsi4 : ahci
[    1.903290] scsi5 : ahci
[    1.903396] scsi6 : ahci
[    1.903480] ata5: SATA max UDMA/133 abar m2048@0xe8049000 port 0xe8049100 irq 45
[    1.903488] ata6: DUMMY
[    1.903489] ata7: DUMMY
[    1.960154] firewire_core: created device fw0: GUID 00023f9929610410, S400
[    2.060055] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.250086] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.251508] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.251511] ata5.00: ACPI cmd b1/c1:00:00:00:00:a0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.251641] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[    2.251645] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.252034] ata5.00: ATA-8: FUJITSU MHW2120BJ G1, 891B, max UDMA/100
[    2.252036] ata5.00: 234441648 sectors, multi 16: LBA48 
[    2.253541] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    2.253544] ata5.00: ACPI cmd b1/c1:00:00:00:00:a0 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.253669] ata5.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
[    2.253673] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.254061] ata5.00: configured for UDMA/100
[    2.254229] scsi 4:0:0:0: Direct-Access     ATA      FUJITSU MHW2120B 891B PQ: 0 ANSI: 5
[    2.254372] sd 4:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.254393] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.254426] sd 4:0:0:0: [sda] Write Protect is off
[    2.254429] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.254459] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.312138]  sda: sda1 sda2 < sda5 >
[    2.312496] sd 4:0:0:0: [sda] Attached SCSI disk
[    2.491392] EXT3-fs (sda1): recovery required on readonly filesystem
[    2.491396] EXT3-fs (sda1): write access will be enabled during recovery
[    2.495162] EXT3-fs: barriers not enabled
[    4.188334] kjournald starting.  Commit interval 5 seconds
[    4.188393] EXT3-fs (sda1): orphan cleanup on readonly fs
[    4.515926] ext3_orphan_cleanup: deleting unreferenced inode 467151
[    4.525983] ext3_orphan_cleanup: deleting unreferenced inode 469324
[    4.532600] ext3_orphan_cleanup: deleting unreferenced inode 417874
[    4.532799] ext3_orphan_cleanup: deleting unreferenced inode 417840
[    4.550431] ext3_orphan_cleanup: deleting unreferenced inode 1655601
[    4.550638] ext3_orphan_cleanup: deleting unreferenced inode 1655568
[    4.550834] ext3_orphan_cleanup: deleting unreferenced inode 1655519
[    4.551006] ext3_orphan_cleanup: deleting unreferenced inode 1655321
[    4.568096] ext3_orphan_cleanup: deleting unreferenced inode 3801128
[    4.574477] ext3_orphan_cleanup: deleting unreferenced inode 417803
[    4.574488] ext3_orphan_cleanup: deleting unreferenced inode 417800
[    4.594077] ext3_orphan_cleanup: deleting unreferenced inode 467521
[    4.595065] ext3_orphan_cleanup: deleting unreferenced inode 467786
[    4.595078] ext3_orphan_cleanup: deleting unreferenced inode 1818806
[    4.608724] ext3_orphan_cleanup: deleting unreferenced inode 1818654
[    4.608736] ext3_orphan_cleanup: deleting unreferenced inode 467140
[    4.608933] ext3_orphan_cleanup: deleting unreferenced inode 469334
[    4.608948] ext3_orphan_cleanup: deleting unreferenced inode 1818649
[    4.608956] EXT3-fs (sda1): 18 orphan inodes deleted
[    4.608958] EXT3-fs (sda1): recovery complete
[    4.638870] EXT3-fs (sda1): mounted filesystem with ordered data mode
[   30.621138] <30>udev[388]: starting version 167
[   30.636247] lp: driver loaded but no devices found
[   30.681150] Adding 4803396k swap on /dev/sda5.  Priority:-1 extents:1 across:4803396k 
[   30.707706] hp_accel: hardware type NC8510 found
[   30.708337] lis3lv02d: 12 bits sensor found
[   30.794387] tpm_tis 00:03: 1.2 TPM (device-id 0xB, rev-id 16)
[   30.888617] EXT3-fs (sda1): using internal journal
[   30.981071] type=1400 audit(1310526525.587:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=691 comm="apparmor_parser"
[   30.981940] type=1400 audit(1310526525.587:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=691 comm="apparmor_parser"
[   30.982500] type=1400 audit(1310526525.587:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=691 comm="apparmor_parser"
[   31.059820] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:30c5]
[   31.059883] acpi device:02: registered as cooling_device13
[   31.060297] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   31.060393] ACPI: Video Device [C14B] (multi-head: yes  rom: no  post: no)
[   31.070130] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   31.070336] Registered led device: hp::hddprotect
[   31.070387] hp_accel: driver loaded
[   31.144232] cfg80211: Calling CRDA to update world regulatory domain
[   31.190980] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   31.190983] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   31.190991] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   31.190994] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0xe4100000-0xe43fffff]
[   31.190998] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe4100000-0xe43fffff: excluding 0xe4100000-0xe412ffff
[   31.191013] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x87ffffff pref]
[   31.191016] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x87ffffff: excluding 0x80000000-0x87ffffff
[   31.198744] ppdev: user-space parallel port driver
[   31.219015] type=1400 audit(1310526525.817:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=915 comm="apparmor_parser"
[   31.222641] type=1400 audit(1310526525.827:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=914 comm="apparmor_parser"
[   31.224426] type=1400 audit(1310526525.827:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=915 comm="apparmor_parser"
[   31.224988] type=1400 audit(1310526525.827:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=915 comm="apparmor_parser"
[   31.237041] type=1400 audit(1310526525.837:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=918 comm="apparmor_parser"
[   31.239329] yenta_cardbus 0000:02:06.1: CardBus bridge found [103c:30c5]
[   31.259260] type=1400 audit(1310526525.857:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox-5.0/firefox{,*[^s][^h]}" pid=920 comm="apparmor_parser"
[   31.265947] cfg80211: World regulatory domain updated:
[   31.265950] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   31.265953] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.265955] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   31.265958] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   31.265961] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.265963] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   31.268433] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.278841] type=1400 audit(1310526525.877:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox-5.0/firefox{,*[^s][^h]}//browser_java" pid=920 comm="apparmor_parser"
[   31.323889] nvidia: module license 'NVIDIA' taints kernel.
[   31.323894] Disabling lock debugging due to kernel taint
[   31.383125] yenta_cardbus 0000:02:06.1: ISA IRQ mask 0x0000, PCI irq 17
[   31.383130] yenta_cardbus 0000:02:06.1: Socket status: 30000810
[   31.383134] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   31.383144] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   31.383147] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [mem 0xe4100000-0xe43fffff]
[   31.383151] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe4100000-0xe43fffff: excluding 0xe4100000-0xe412ffff
[   31.383165] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge window: [mem 0x80000000-0x87ffffff pref]
[   31.383168] pcmcia_socket pcmcia_socket1: cs: memory probe 0x80000000-0x87ffffff: excluding 0x80000000-0x87ffffff
[   31.482598] Bluetooth: Core ver 2.15
[   31.482652] NET: Registered protocol family 31
[   31.482654] Bluetooth: HCI device and connection manager initialized
[   31.482656] Bluetooth: HCI socket layer initialized
[   31.485481] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   31.498800] usbcore: registered new interface driver btusb
[   31.500748] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   31.500751] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   31.500832] iwlagn 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.500841] iwlagn 0000:10:00.0: setting latency timer to 64
[   31.500873] iwlagn 0000:10:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   31.539660] iwlagn 0000:10:00.0: device EEPROM VER=0x36, CALIB=0x5
[   31.539663] iwlagn 0000:10:00.0: Device SKU: 0Xb
[   31.547784] iwlagn 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   31.547870] iwlagn 0000:10:00.0: irq 46 for MSI/MSI-X
[   31.621643] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   31.774948] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa44793/0x300000/0x0
[   31.774954] serio: Synaptics pass-through port at isa0060/serio4/input0
[   31.780349] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   31.815601] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   31.850105] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   31.850407] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.950113] parport_pc 00:02: reported by Plug and Play ACPI
[   31.950191] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   31.983473] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xcc000-0xd3fff 0xe0000-0xfffff
[   31.983530] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   31.983584] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   32.041286] lp0: using parport0 (interrupt-driven).
[   32.148536] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.148546] nvidia 0000:01:00.0: setting latency timer to 64
[   32.148551] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   32.148729] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
[   32.171233] Bluetooth: L2CAP ver 2.15
[   32.171236] Bluetooth: L2CAP socket layer initialized
[   32.179486] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.179489] Bluetooth: BNEP filters: protocol multicast
[   32.186320] Bluetooth: SCO (Voice Link) ver 0.6
[   32.186323] Bluetooth: SCO socket layer initialized
[   32.212011] iwlagn 0000:10:00.0: loaded firmware version 228.61.2.24
[   32.212253] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   32.222829] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   32.278633] Bluetooth: RFCOMM TTY layer initialized
[   32.278638] Bluetooth: RFCOMM socket layer initialized
[   32.278640] Bluetooth: RFCOMM ver 1.11
[   32.299579] input: HP WMI hotkeys as /devices/virtual/input/input7
[   32.320149] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[   32.320162] pcmcia_socket pcmcia_socket1: cs: memory probe 0xe4130000-0xe43fffff:
[   32.320496] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xcc000-0xd3fff 0xe0000-0xfffff
[   32.320558] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   32.320630] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   32.324815]  excluding 0xe43f0000-0xe441bfff
[   32.324963] pcmcia 1.0: pcmcia: registering new device pcmcia1.0 (IRQ: 17)
[   32.370601] scsi7 : pata_pcmcia
[   32.370660] ata8: PATA max PIO0 cmd 0x7100 ctl 0x710e irq 17
[   32.477264] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.541813] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   32.541823] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   32.541833] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.541899] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   32.541933] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   32.623372] vboxdrv: Found 2 processor cores.
[   32.623995] vboxdrv: fAsync=0 offMin=0x1c3 offMax=0x953
[   32.624098] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   32.624100] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[   39.137578] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input8
[  200.717844] wlan0: authenticate with 3c:ea:4f:be:87:21 (try 1)
[  200.719363] wlan0: authenticated
[  200.719383] wlan0: associate with 3c:ea:4f:be:87:21 (try 1)
[  200.721186] wlan0: RX AssocResp from 3c:ea:4f:be:87:21 (capab=0x31 status=0 aid=4)
[  200.721190] wlan0: associated
[  200.747239] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  200.749202] cfg80211: Calling CRDA for country: US
[  200.752619] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  200.752623] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752625] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  200.752628] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752630] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  200.752633] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752635] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  200.752637] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752639] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  200.752642] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752644] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  200.752647] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752649] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  200.752651] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752653] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  200.752656] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752658] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  200.752661] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752663] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  200.752666] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752668] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  200.752671] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  200.752673] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  200.752676] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  200.752678] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  200.752681] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  200.752683] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  200.752685] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  200.752687] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  200.752690] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  200.752692] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  200.752695] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  200.752697] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  200.752700] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  200.752702] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  200.752704] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  200.752707] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  200.752709] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  200.752711] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  200.752714] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  200.752716] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  200.752719] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  200.752721] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  200.752724] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  200.752726] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  200.752728] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  200.752731] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  200.752733] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  200.752736] cfg80211: Regulatory domain changed to country: US
[  200.752738] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  200.752740] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  200.752743] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  200.752746] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.752748] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.752751] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  200.752753] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  211.650090] wlan0: no IPv6 routers present
```

Here is everything from the dmesg output.

---

### Post by wildmanne39 on 2011-07-13
Hi, the next time your system freezes, as soon as you get into it get the contents of this log again and post here.

---

