---
title: "diagnose hdd issue"
date: 2009-12-12
forum: General Help
---

### Post by mike909 on 2009-12-12
I keep seeing the below messages in dmesg/syslog every couple seconds. I can only guess it's a failing hdd, but I'm not sure which of the 2 in the system it is. I have run SMART tests on both and they pass, nothing in smartctl that looks bad. 

Anyone have an idea as to what these messages mean?
> 
Dec 12 16:02:36 htpc kernel: [  353.138642] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Dec 12 16:02:36 htpc kernel: [  353.138649] ata3.00: irq_stat 0x40000001
Dec 12 16:02:36 htpc kernel: [  353.138659] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 12 16:02:36 htpc kernel: [  353.138661]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec 12 16:02:36 htpc kernel: [  353.138663]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
Dec 12 16:02:36 htpc kernel: [  353.138667] ata3.00: status: { DRDY ERR }
Dec 12 16:02:36 htpc kernel: [  353.138673] ata3: hard resetting link
Dec 12 16:02:36 htpc kernel: [  353.456022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 12 16:02:36 htpc kernel: [  353.456679] ata3.00: both IDENTIFYs aborted, assuming NODEV
Dec 12 16:02:36 htpc kernel: [  353.456683] ata3.00: revalidation failed (errno=-2)
Dec 12 16:02:41 htpc kernel: [  358.456022] ata3: hard resetting link
Dec 12 16:02:41 htpc kernel: [  358.776030] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 12 16:02:41 htpc kernel: [  358.802440] ata3.00: configured for PIO3
Dec 12 16:02:41 htpc kernel: [  358.803101] ata3.00: limiting speed to PIO0
Dec 12 16:02:41 htpc kernel: [  358.803107] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x7 t4
Dec 12 16:02:41 htpc kernel: [  358.803111] ata3: irq_stat 0x40000001
Dec 12 16:02:41 htpc kernel: [  358.803117] ata3: hard resetting link
Dec 12 16:02:41 htpc kernel: [  359.120022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 12 16:02:42 htpc kernel: [  359.146413] ata3.00: configured for PIO0
Dec 12 16:02:42 htpc kernel: [  359.147077] ata3: EH complete
Dec 12 16:02:44 htpc kernel: [  361.136088] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
Dec 12 16:02:44 htpc kernel: [  361.136094] ata3.00: irq_stat 0x08000000, interface fatal error
Dec 12 16:02:44 htpc kernel: [  361.136098] ata3: SError: { UnrecovData Handshk }
Dec 12 16:02:44 htpc kernel: [  361.136108] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Dec 12 16:02:44 htpc kernel: [  361.136110]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Dec 12 16:02:44 htpc kernel: [  361.136111]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)

ubuntu 9.10
both drives are seagate
> 
mike@htpc:~$ sudo smartctl -i /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3160827AS
Serial Number:    3MT0BHFF
Firmware Version: 3.42
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sat Dec 12 16:20:27 2009 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

mike@htpc:~$ sudo smartctl -i /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST31500341AS
Serial Number:    9VS0X5D0
Firmware Version: CC1H
User Capacity:    1,500,301,910,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat Dec 12 16:20:39 2009 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

output from lshw:
> 
sudo lshw
htpc                      
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00E841B3-8DFE-D511-BF51-0015F2093EEE
  *-core
       description: Motherboard
       product: P5WD2-Premium
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0606 (10/30/2005)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          slot: Socket 775
          size: 3200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
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
          physical id: 40
          slot: System board or motherboard
          size: 2GiB
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
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
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
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.4
          serial: 0000-0F44-0000-0000-0000-0000
          size: 3200MHz
          capabilities: ht
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
          product: 82955X Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82955X PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096) memory:e2f00000-e7ffffff ioport:e8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e4000000-e7ffffff memory:e8000000-efffffff(prefetchable) memory:e3000000-e3ffffff memory:e2fe0000-e2ffffff(prefetchable)
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:e2bf4000-e2bf7fff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096)
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:c000(size=4096) memory:e2e00000-e2efffff
           *-network
                description: Ethernet interface
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 00
                serial: 00:15:f2:4c:f7:b7
                size: 1GB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-7 ip=10.0.0.83 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
                resources: irq:29 memory:e2ee0000-e2efffff ioport:c800(size=32)
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:b000(size=4096) memory:e2d00000-e2dfffff
           *-storage
                description: Mass storage controller
                product: SiI 3132 Serial ATA Raid II Controller
                vendor: Silicon Image, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list rom
                configuration: driver=sata_sil24 latency=0
                resources: irq:17 memory:e2dffc00-e2dffc7f memory:e2df8000-e2dfbfff ioport:b800(size=128) memory:e2d00000-e2d7ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:6400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:7000(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:e2bff800-e2bffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:9000(size=8192) memory:e2c00000-e2cfffff memory:80000000-800fffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:21 memory:e2cfb800-e2cfbfff memory:e2cf4000-e2cf7fff
           *-storage
                description: Mass storage controller
                product: ITE 8211F Single Channel UDMA 133
                vendor: Integrated Technology Express, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 11
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom
                configuration: driver=pata_it821x latency=64 maxlatency=8 mingnt=8
                resources: irq:19 ioport:a400(size=8) ioport:a000(size=4) ioport:9800(size=8) ioport:9400(size=4) ioport:9000(size=16) memory:80000000-8001ffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 5
                bus info: pci@0000:01:05.0
                logical name: eth0
                version: 13
                serial: 00:15:f2:4c:fe:bf
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
                resources: irq:21 memory:e2cfc000-e2cfffff ioport:a800(size=256) memory:80020000-8003ffff(prefetchable)
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
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:8800(size=8) ioport:8400(size=4) ioport:8000(size=8) ioport:7800(size=4) ioport:7400(size=16) memory:e2bffc00-e2bfffff
           *-disk:0
                description: ATA Disk
                product: ST3160827AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 3.42
                serial: 3MT0BHFF
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a39ca39c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 285570f1-c899-464e-bf8a-5b2d7ea20c9a
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-17 22:28:16 filesystem=ext4 lastmountpoint=/&#65533;&#65533;£&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;x>&#65533;&#65533;X.4&#65533;X.4&#65533;&#65533;&#65533;&#65533;>&#65533;>&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;-&&#65533; modified=2009-11-17 22:50:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-12-12 15:57:06 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 5898MiB
                   capacity: 5898MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5898MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: ST31500341AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: CC1H
                serial: 9VS0X5D0
                size: 1397GiB (1500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00099a66
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/storage
                   version: 1.0
                   serial: 113b98cd-a95e-411a-85a6-016228ff73e4
                   size: 1397GiB
                   capacity: 1397GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-02-06 20:16:42 filesystem=ext3 modified=2009-12-12 15:57:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2009-12-12 15:57:07 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)

more dmesg output, but basically the same as my syslog output:
> 
[ 1532.883717] ata3.00: status: { DRDY ERR }
[ 1532.883723] ata3: hard resetting link
[ 1533.200023] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1533.200677] ata3.00: both IDENTIFYs aborted, assuming NODEV
[ 1533.200682] ata3.00: revalidation failed (errno=-2)
[ 1538.200029] ata3: hard resetting link
[ 1538.520022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1538.546434] ata3.00: configured for PIO0
[ 1538.547096] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[ 1538.547101] ata3: irq_stat 0x40000001
[ 1538.573538] ata3.00: configured for PIO0
[ 1538.573550] ata3: EH complete
[ 1538.576240] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1538.576244] ata3.00: irq_stat 0x40000001
[ 1538.576253] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1538.576254]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1538.576255]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 1538.576259] ata3.00: status: { DRDY ERR }
[ 1538.576265] ata3: hard resetting link
[ 1538.896022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1538.922435] ata3.00: configured for PIO0
[ 1538.923096] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[ 1538.923100] ata3: irq_stat 0x40000001
[ 1538.949548] ata3.00: configured for PIO0
[ 1538.949559] ata3: EH complete
[ 1615.133852] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[ 1615.133858] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1615.133863] ata3: SError: { UnrecovData Handshk }
[ 1615.133873] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1615.133875]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1615.133877]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1615.133881] ata3.00: status: { DRDY }
[ 1615.133887] ata3: hard resetting link
[ 1615.452022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1615.477926] ata3.00: failed to enable ATAPI AN (err_mask=0x100)
[ 1615.477961] ata3.00: configured for PIO0
[ 1615.477965] ata3.00: TEST_UNIT_READY failed (err_mask=0x40)
[ 1620.452031] ata3: hard resetting link
[ 1620.772022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1620.798441] ata3.00: configured for PIO0
[ 1620.799103] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[ 1620.799107] ata3: irq_stat 0x40000001
[ 1620.825549] ata3.00: configured for PIO0
[ 1620.825558] ata3: EH complete
[ 1620.838810] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[ 1620.838814] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1620.838819] ata3: SError: { UnrecovData Handshk }
[ 1620.838829] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1620.838830]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1620.838832]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1620.838836] ata3.00: status: { DRDY }
[ 1620.838842] ata3: hard resetting link
[ 1621.156022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1621.182413] ata3.00: configured for PIO0
[ 1621.183089] ata3: EH complete
[ 1621.184371] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x800100 action 0x6 frozen
[ 1621.184376] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1621.184380] ata3: SError: { UnrecovData LinkSeq }
[ 1621.184390] ata3.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 1621.184392]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
[ 1621.184394]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1621.184398] ata3.00: status: { DRDY }
[ 1621.184403] ata3: hard resetting link
[ 1621.504021] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1621.530419] ata3.00: configured for PIO0
[ 1621.531096] ata3: EH complete
[ 1639.134212] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1639.134217] ata3.00: irq_stat 0x40000001
[ 1639.134227] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1639.134229]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1639.134230]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 1639.134235] ata3.00: status: { DRDY ERR }
[ 1639.134241] ata3: hard resetting link
[ 1639.452022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1639.478433] ata3.00: configured for PIO0
[ 1639.479094] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[ 1639.479099] ata3: irq_stat 0x40000001
[ 1639.505545] ata3.00: configured for PIO0
[ 1639.505555] ata3: EH complete
[ 1655.136815] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1655.136820] ata3.00: irq_stat 0x40000001
[ 1655.136830] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1655.136832]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1655.136834]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 1655.136838] ata3.00: status: { DRDY ERR }
[ 1655.136844] ata3: hard resetting link
[ 1655.456021] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1655.482430] ata3.00: configured for PIO0
[ 1655.483087] ata3: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1 t4
[ 1655.483091] ata3: irq_stat 0x40000001
[ 1655.509532] ata3.00: configured for PIO0
[ 1655.509542] ata3: EH complete
[ 1671.133305] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x800100 action 0x6 frozen
[ 1671.133310] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1671.133314] ata3: SError: { UnrecovData LinkSeq }
[ 1671.133324] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1671.133325]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1671.133327]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1671.133331] ata3.00: status: { DRDY }
[ 1671.133337] ata3: hard resetting link
[ 1671.452022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1671.478430] ata3.00: configured for PIO0
[ 1671.479088] ata3: EH complete
[ 1711.132046] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[ 1711.132051] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1711.132056] ata3: SError: { UnrecovData Handshk }
[ 1711.132066] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1711.132068]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1711.132073]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1711.132077] ata3.00: status: { DRDY }
[ 1711.132082] ata3: hard resetting link
[ 1711.452022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1711.478436] ata3.00: configured for PIO0
[ 1711.479096] ata3: EH complete
[ 1725.135834] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x800100 action 0x6 frozen
[ 1725.135840] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1725.135844] ata3: SError: { UnrecovData LinkSeq }
[ 1725.135854] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1725.135855]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1725.135857]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1725.135861] ata3.00: status: { DRDY }
[ 1725.135867] ata3: hard resetting link
[ 1725.452021] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1725.478431] ata3.00: configured for PIO0
[ 1725.479091] ata3: EH complete
[ 1747.130623] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[ 1747.130629] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1747.130634] ata3: SError: { UnrecovData Handshk }
[ 1747.130643] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1747.130645]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1747.130647]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1747.130651] ata3.00: status: { DRDY }
[ 1747.130657] ata3: hard resetting link
[ 1747.448022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1747.474418] ata3.00: configured for PIO0
[ 1747.475097] ata3: EH complete
[ 1749.139589] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6 frozen
[ 1749.139594] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1749.139598] ata3: SError: { UnrecovData Handshk }
[ 1749.139608] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1749.139610]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1749.139611]          res 50/00:03:00:08:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[ 1749.139616] ata3.00: status: { DRDY }
[ 1749.139621] ata3: hard resetting link
[ 1749.456022] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 1749.482418] ata3.00: configured for PIO0
[ 1749.483094] ata3: EH complete


---

### Post by jessel on 2009-12-17
The dmesg output does look unusual to me. I wouldn't ignore it. I am not an expert by any means, I came across your post trying to set up smartmontools and looking for info. One reference I'm looking at is [www.linuxjournal.com/article/6983](www.linuxjournal.com/article/6983)

Your output of "smartctl -i" is only going to show that your drive is smart capable or not. It looks like your drive is smart capable, but the more interesting command would be "smartctl -A"

You may not have a smartd process running. To see if thats the case "ps -e" or better yet "ps -e | grep sm"

Also, do you need both drives to run? If not temporarily disconnect one.

---

### Post by mike909 on 2009-12-26
jessel,
I dont have the smartd daemon running, but I have run both short and long tests...both showing no errors. To figure out which drive it is, I will disconnect the storage (non-boot) drive and see if errors persist. 
The more interesting question is, once I find out which drive it is, what do those messages actually mean?

---

### Post by jessel on 2009-12-26
> **mike909 said:**
> jessel,
I dont have the smartd daemon running, but I have run both short and long tests...both showing no errors. To figure out which drive it is, I will disconnect the storage (non-boot) drive and see if errors persist. 
The more interesting question is, once I find out which drive it is, what do those messages actually mean?

> 
Dec 12 16:02:44 htpc kernel: [ 361.136094] ata3.00: irq_stat 0x08000000, interface fatal error


I'm sure you'd like something more definitive but when I look at the above I'm thinking that the your problem could be either with the hard drive, the motherboard and maybe even with BIOS settings. 

When I look at my BIOS settings there is an option to enable SMART support which I have not enabled. I'm not convinced this is the problem but I always double check BIOS settings when I have a hardware issue. Have you made any changes recently?

As far as the issue being with the motherboard, well, thats what the drive is connected to. I'm interested in seeing what happens when one drive is removed.

The thing that I took from my reading about smartmontools is that this utility can tell if the drive is bad a lot of the time, not all the time. In other words it might give you advanced warning, but might not.

---

### Post by mike909 on 2009-12-28
I do have smart enabled in BIOS but im not entirely sure what that actually does.
When I get back home I will try removing the nonboot drive and at least figure out which drive it is.
the mobo being the problem is entirely possible as it uses 2 onboard fake-raid controllers, and one hdd is connected to each. possibly one of them is going bad. its the nforce 4 chipset.

---

### Post by Zeniff on 2010-02-02
I'm having the exact same errors, but I have only one HDD and no RAID.

I've had these constant errors probably even before I had upgraded from Jaunty.

I think the errors are more common than before...because in the past, I think I was able to use (at least some of) the CTRL+ALT+Fn terminals... But now, they are so frequent on every tty that they are unusable.

From dmesg:
```

[11752.144071] ata3.00: qc timeout (cmd 0xa0)
[11752.144112] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[11752.144122] ata3.00: irq_stat 0x40000001
[11752.144147] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[11752.144151]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[11752.144154]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[11752.144163] ata3.00: status: { DRDY ERR }
[11752.144178] ata3: hard resetting link
[11752.628060] ata3: softreset failed (device not ready)
[11752.628073] ata3: applying SB600 PMP SRST workaround and retrying
[11752.792065] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[11752.806957] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[11752.822474] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[11752.822487] ata3.00: configured for PIO0
[11752.824540] ata3: EH complete

```

I hope this isn't serious are damaging to my hard disk. O_O

---

### Post by mike909 on 2010-02-03
Another interesting thing is "SATA link up 1.5 Gbps" when my drives & controllers are 3 Gbps.

---

### Post by jessel on 2010-02-17
> I hope this isn't serious are damaging to my hard disk. O_OWell, how important is the stuff on your hard disk? Its not a question of whether its being damaged, so much as whether its going to stop working and leave you in a lurch. There must be a problem somewhere, and it seems likely its the hard drives's controller.

One thing that you could do is to boot off of the installation media with the hard disk physically disconnected. See what errors you get...

In my experience with hardware problems, they can be difficult to pinpoint as they tend to produce unpredictable results. It can be a component you would not have guessed. Basically what I've done in the past, is remove everything I can and see what happens running the stripped down system. Then add everything back one piece at a time, checking for unusual behavior.

---

