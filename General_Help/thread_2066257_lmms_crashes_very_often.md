---
title: "lmms crashes very often"
date: 2012-10-04
forum: General Help
---

### Post by ContextualFabric on 2012-10-04
I installed lmms with apt-get in Ubuntu 11.10
and starting in terminal as sudo does give no hints as to why crashes. other programs do not crash.

Kernel: 3.0.0-26-generic
```

##### lshw #####

mkroeks-desktop
    description: Desktop Computer
    version: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4C800
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1010.004
          date: 07/21/2003
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.5
          slot: CPU 1
          size: 2800MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 37
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82875P/E7210 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82875P Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fa900000-fe9fffff memory:bff00000-dfefffff
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:fc000000-fcffffff memory:fe9e0000-fe9fffff
        *-generic UNCLAIMED
             description: System peripheral
             product: 82875P/E7210 Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:eec0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ef00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ef20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febff800-febffbff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-storage
                description: RAID bus controller
                product: PDC20378 (FastTrak 378/SATA 378)
                vendor: Promise Technology, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: scsi2
                logical name: scsi3
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list emulated
                configuration: driver=sata_promise latency=240 maxlatency=18 mingnt=4
                resources: irq:23 ioport:df00(size=64) ioport:dfa0(size=16) ioport:dc00(size=128) memory:feaff000-feafffff memory:feac0000-feadffff
              *-disk:0
                   description: ATA Disk
                   product: WDC WD10EARS-00Y
                   vendor: Western Digital
                   physical id: 0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sda
                   version: 80.0
                   serial: WD-WMAV52254526
                   size: 931GiB (1TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=f7d267f9
                 *-volume:0 UNCLAIMED
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      version: 3.1
                      serial: 328d33e8-957b-9d4b-a79c-210eb5ee7d6a
                      size: 5122MiB
                      capacity: 5122MiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=65536 created=2011-02-06 16:53:27 filesystem=ntfs label=SWAP state=clean
                 *-volume:1 UNCLAIMED
                      description: Linux swap volume
                      physical id: 2
                      bus info: scsi@2:0.0.0,2
                      version: 1
                      serial: 412c6e93-286c-464f-b2b9-9446a68bd519
                      size: 6000MiB
                      capacity: 6000MiB
                      capabilities: primary nofs swap initialized
                      configuration: filesystem=swap pagesize=4096
                 *-volume:2 UNCLAIMED
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@2:0.0.0,3
                      version: 1.0
                      serial: e65c8785-97bb-4aa7-a2df-4098f1e33d89
                      size: 123GiB
                      capacity: 123GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2012-10-01 16:43:32 filesystem=ext4 lastmountpoint=/ modified=2012-10-01 17:06:49 mounted=2012-10-04 08:47:37 state=clean
                 *-volume:3 UNCLAIMED
                      description: Windows NTFS volume
                      physical id: 4
                      bus info: scsi@2:0.0.0,4
                      version: 3.1
                      serial: 246ce00a-4826-48c6-9b0a-eafcc15a0c0a
                      size: 797GiB
                      capacity: 797GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2010-08-29 17:12:07 filesystem=ntfs label=DATA state=clean
              *-disk:1
                   description: ATA Disk
                   product: Hitachi HDT72101
                   vendor: Hitachi
                   physical id: 1
                   bus info: scsi@3:0.0.0
                   logical name: /dev/sdb
                   version: ST6O
                   serial: STF607MH2UVG6K
                   size: 931GiB (1TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=f7d267f9
                 *-volume:0 UNCLAIMED
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@3:0.0.0,1
                      version: 3.1
                      serial: 328d33e8-957b-9d4b-a79c-210eb5ee7d6a
                      size: 5122MiB
                      capacity: 5122MiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=65536 created=2011-02-06 16:53:27 filesystem=ntfs label=SWAP state=clean
                 *-volume:1 UNCLAIMED
                      description: Linux swap volume
                      physical id: 2
                      bus info: scsi@3:0.0.0,2
                      version: 1
                      serial: 412c6e93-286c-464f-b2b9-9446a68bd519
                      size: 6000MiB
                      capacity: 6000MiB
                      capabilities: primary nofs swap initialized
                      configuration: filesystem=swap pagesize=4096
                 *-volume:2 UNCLAIMED
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@3:0.0.0,3
                      version: 1.0
                      serial: e65c8785-97bb-4aa7-a2df-4098f1e33d89
                      size: 123GiB
                      capacity: 123GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2012-10-01 16:43:32 filesystem=ext4 lastmountpoint=/ modified=2012-10-01 17:06:49 mounted=2012-10-04 08:47:37 state=clean
                 *-volume:3 UNCLAIMED
                      description: Windows NTFS volume
                      physical id: 4
                      bus info: scsi@3:0.0.0,4
                      version: 3.1
                      serial: 246ce00a-4826-48c6-9b0a-eafcc15a0c0a
                      size: 797GiB
                      capacity: 797GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2010-08-29 17:12:07 filesystem=ntfs label=DATA state=clean
           *-network
                description: Ethernet interface
                product: 3c940 10/100/1000Base-T [Marvell]
                vendor: 3Com Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 12
                serial: 00:0c:6e:a0:df:73
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.178.33 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:22 memory:feaf8000-feafbfff ioport:d800(size=256)
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: c
                bus info: pci@0000:02:0c.0
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:20 ioport:df80(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: c.1
                bus info: pci@0000:02:0c.1
                version: 08
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64
                resources: irq:0 ioport:dfe0(size=8)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:efe0(size=8) ioport:efac(size=4) ioport:efa0(size=8) ioport:efa8(size=4) ioport:ef90(size=16) memory:dff00000-dff003ff
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3520AW
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 3.07
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
```

---

