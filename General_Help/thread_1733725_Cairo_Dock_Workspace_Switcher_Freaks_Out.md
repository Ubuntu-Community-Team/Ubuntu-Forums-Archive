---
title: "Cairo Dock Workspace Switcher Freaks Out"
date: 2011-04-19
forum: General Help
---

### Post by fleamour on 2011-04-19
Not finding any helpful posts on Google.  

Whenever I enable the workspace switcher, upon clicking on it, it'll fly out of the desktop altogether.  I can reset X/Y position, but every time I click on it it displays this buggy behaviour.

---

### Post by fleamour on 2011-04-21
[bump]

---

### Post by josephmills on 2011-04-21
could we please see your hardware ```
lshw
``` thanks

---

### Post by fleamour on 2011-04-21
Tried disabling edge bindings.


          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: L1.82 (01/21/2009)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPUSocket
          size: 3003MHz
          capacity: 3003MHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2003MHz
          capacity: 2003MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fd000000-feafffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 220]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:dc00(size=128) memory:fea00000-fea7ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:feafc000-feafffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:44 memory:fc6fc000-fc6fffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:fc800000-fcffffff ioport:cc000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:b000(size=4096) memory:fc700000-fc7fffff ioport:c8000000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 01
                serial: 00:19:66:70:d7:fe
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:43 ioport:b800(size=256) memory:fc7ff000-fc7fffff memory:fc7c0000-fc7dffff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a480(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a800(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:a880(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ac00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc6fbc00-fc6fbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-usb:0
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:05:01.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=32
                resources: irq:22 ioport:e880(size=32)
           *-usb:1
                description: USB Controller
                product: VT82xxxxx UHCI USB 1.1 Controller
                vendor: VIA Technologies, Inc.
                physical id: 1.1
                bus info: pci@0000:05:01.1
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: pm uhci bus_master cap_list
                configuration: driver=uhci_hcd latency=32
                resources: irq:23 ioport:ec00(size=32)
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: VIA Technologies, Inc.
                physical id: 1.2
                bus info: pci@0000:05:01.2
                version: 63
                width: 32 bits
                clock: 33MHz
                capabilities: pm ehci bus_master cap_list
                configuration: driver=ehci_hcd latency=32
                resources: irq:20 memory:febf7c00-febf7cff
           *-network
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: RaLink
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: wlan0
                version: 00
                serial: 00:1f:1f:4b:74:88
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.3 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:23 memory:febf8000-febfffff
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-115D
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.06
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:a400(size=8) ioport:a080(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9880(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD5000AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAYUD143261
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a10bd000
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 844d72c5-9aec-9742-a248-523088e77260
                   size: 298MiB
                   capacity: 298MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-05-04 04:24:57 filesystem=ntfs label=System Reserve state=clean
              *-volume:1
                   description: Windows FAT volume
                   vendor: -FVE-FS-
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: FAT32
                   serial: 0000-0000
                   size: 15EiB
                   capabilities: primary fat initialized
                   configuration: FATs=0 filesystem=fat
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 08bd9287-6301-6c42-be31-bbe79fa7300f
                   size: 316GiB
                   capacity: 316GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-28 14:44:02 filesystem=ntfs label=Store state=clean
           *-disk:1
                description: ATA Disk
                product: ST3500418AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: CC37
                serial: 6VM82EJF
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7ffd62f1
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 7c6f7176-45f9-4df0-897b-00f4075661b4
                   size: 9536MiB
                   capacity: 9536MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-24 00:05:24 filesystem=ext4 lastmountpoint=/}&#1234;&#65533;&#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;P>&#65533;Tv!&#65533;H&#65533;&#65533;&#65533;@>&#65533;pw&#65533;&#65533;pw&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h>&#65533;&#65533;x!&#65533;&#65533;o modified=2011-04-04 15:22:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-04-21 17:52:37 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdb2
                   size: 3814MiB
                   capacity: 3814MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 3814MiB
                      capabilities: nofs
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@3:0.0.0,3
                   logical name: /dev/sdb3
                   version: 3.1
                   serial: 32ac3f04-a0c7-7943-85ca-51f199102c2d
                   size: 415GiB
                   capacity: 415GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-10-23 22:53:20 filesystem=ntfs label=Restore state=clean
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@3:0.0.0,4
                   logical name: /dev/sdb4
                   logical name: /home
                   version: 1.0
                   serial: 9e598d1e-ce06-4c5a-b634-9814f7a01a18
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-24 00:05:27 filesystem=ext4 lastmountpoint=/home&#65533;k&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;V&#65533;&#65533;i&#65533;P&#65533;&#65533;&#65533;Tv!&#65533;z30&#65533;&#65533;&#65533;&#65533;&#756966;&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;x modified=2011-04-21 17:52:38 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-04-21 17:52:38 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)

---

