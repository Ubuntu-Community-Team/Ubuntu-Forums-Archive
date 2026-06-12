---
title: "Ubuntu 9.10 and 10.10 Legacy Hardware"
date: 2011-04-21
forum: General Help
---

### Post by markhc on 2011-04-21
**Legacy Hardware**             
                                                                I have a chunk of hardware I bought in 2005 that came with Windoze verzhun Whatever. Very soon after buying it I decided to discard the trash that came with it, and installed Mandrake. I lived with Mandrake for a while until I decided to install Debian. Debian lasted me very well, until Lenny became Squeeze.

All of a sudden, my hardware was slow. I couldn't keep up. Lenny had seen my applications crash more and more often, but Squeeze just couldn't keep me in the race. I chose to go to Ubuntu.

With my hardware, Ubuntu 10.10 just would not see my disks. Ubuntu 9.10 could not install grub. I tried everything - take a look at a google forum that I didn't look at, if you can.

Ubuntu 8.04 loads and runs without any special work.  

I suggest that Ubuntu 9.10 and 10.10 have special hardware requirements.

root@gizmo:~# lshw
gizmo                     
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=404549A5-74FE-D511-8FF9-1F7BEF2DCD82
  *-core
       description: Motherboard
       product: P4S800-MX SE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1004.002 (06/21/2005)
          size: 64KiB
          capacity: 448KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: Socket 478
          size: 2800MHz
          capacity: 3800MHz
          width: 32 bits
          clock: 200MHz
capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
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
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 1GiB
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
             description: DIMM SDRAM Synchronous [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             width: 64 bits
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_sis latency=128 module=pata_sis
           *-cdrom:0
                description: DVD writer
                product: DVD RW DRU-510A
                vendor: SONY
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0c
                serial: [SONY    DVD RW DRU-510A 1.0c Aug06 ,2003
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: DVD reader
                product: 16X
                vendor: DVD-ROM
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 5.CV
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:13:d4:15:83:af
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.103 latency=64 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
        *-ide:1
             description: IDE interface
             product: SATA
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_sis latency=64 module=sata_sis
           *-disk:0
                description: ATA Disk
                product: Maxtor 6Y080M0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YAR5
                serial: Y3K8XD5E
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00088c01
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 561b7efd-18f2-49f3-ab95-8ac13dadaaac
                   size: 73GiB
                   capacity: 73GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration: created=2011-04-21 23:12:07 filesystem=ext3 modified=2011-04-21 23:28:01 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-04-21 23:12:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2957MiB
                   capacity: 2957MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2957MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 6Y080M0
                vendor: Maxtor
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: YAR5
                serial: Y2Q73JEE
                size: 76GiB (81GB)
                configuration: ansiversion=5
        *-communication UNCLAIMED
             description: Communication controller
             product: V.92 56K WinModem
             vendor: Agere Systems
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64 maxlatency=14 mingnt=252
     *-scsi
          physical id: 1
          bus info: usb@4:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 3200AAJ External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             version: 1.06
             serial: E
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=41ffc810
           *-volume
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/disk
                version: 3.6
                serial: a174a6e6-06e4-439c-ac6e-0c77f2aa8785
                size: 298GiB
                capacity: 298GiB
                capabilities: primary journaled reiserfs initialized
configuration: filesystem=reiserfs hash=r5 mount.fstype=reiserfs mount.options=rw,nosuid,nodev,relatime state=mounted

---

### Post by dino99 on 2011-04-21
hope your hdd is not tatooed, if so use western digital software to remove the hidden partition. For old hardware config, Lubuntu is faster

---

