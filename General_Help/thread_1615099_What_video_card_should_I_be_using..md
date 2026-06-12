---
title: "What video card should I be using."
date: 2010-11-06
forum: General Help
---

### Post by tbrminsanity on 2010-11-06
I'm having problems with my video card (Radeon X1600) ever since I upgraded to 10.04 (video is fine until I stress the video card (eg using 3D acceleration)).  This appears to be a problem with the drivers for the video card.  I've had problems in the past with video cards (many because I didn't check that the card I'm buying is "Linux friendly" or not.  Now I'm doing my do diligence and asking the community what video card I should buy to replace my current one?  Keep in mind I'm on a very tight budget (I can't spend more then $150).

I have the following Motherboard:
[http://www.gigabyte.lv/products/mb/specs/ga-n650sli-ds4_10.html](http://www.gigabyte.lv/products/mb/specs/ga-n650sli-ds4_10.html)

---

### Post by arpanaut on 2010-11-06
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121390](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121390)

[http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx460&num=11](http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx460&num=11)

I prefer nVidia  but there are some suggestions for AMD/ATI in the review,

---

### Post by I'mGeorge on 2010-11-06
I've always been an ATI fan, but I guess it's a mater of tastes.

---

### Post by fragos on 2010-11-06
Every Nvidia card or on board video chip set I've ever owned worked well with very little if any fuss. My next video card will probably be a 220. My current mobo has a 7050 chip set and it does full 1080p HD very well. I'm not a gamer.

---

### Post by CharlesA on 2010-11-06
> **arpanaut said:**
> [http://www.newegg.com/Product/Product.aspx?Item=N82E16814121390](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121390)

[http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx460&num=11](http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx460&num=11)

I prefer nVidia  but there are some suggestions for AMD/ATI in the review,

You really don't need a fermi unless you are a gamer. a 9000 series or GT series would work perfectly fine (and cheaper too).

---

### Post by arpanaut on 2010-11-06
> You really don't need a fermi unless you are a gamer. a 9000 series or GT series would work perfectly fine (and cheaper too).

Good point!  I was just suggesting a good spec card within said price point...
Also I'm not sure his board supports PCIe 2 spec card?

Post had sat unanswered for a while so it was a polite bump.

---

### Post by CharlesA on 2010-11-06
> **arpanaut said:**
> Good point!  I was just suggesting a good spec card within said price point...
Also I'm not sure his board supports PCIe 2 spec card?

Post had sat unanswered for a while so it was a polite bump.

Not sure if it can support 2.0 either, since I don't see anything mentioned in the manual.

I've run 2.0 cards in a 1.0 slot before without any problems, since they are backwards compatible.

The PCIe slot will run at x16 in non SLI mode and x8 in SLI mode.

---

### Post by fragos on 2010-11-06
Runs "sudo lshw", up toward the beginning of the output it will identify your mobo. You can Google the vendor and product to get details about your mobo.

---

### Post by JaradT on 2010-11-06
Anything will do as long as your motherboard supports it.
I have an Intel GMA video card in my computer that has been repaired. (DANG YOU WINDOWS VISTAAAA!) and Compiz seems to work. I can play OpenGL games and Windows games, too. (Blockland, for example)

---

### Post by tbrminsanity on 2010-11-07
> **fragos said:**
> Runs "sudo lshw", up toward the beginning of the output it will identify your mobo. You can Google the vendor and product to get details about your mobo.


```
cymru
    description: Desktop Computer
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: GA-N650SLI-DS4
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: Wed Apr 11 03:17:37 2007
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F4 (04/09/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU 670
          slot: Socket 775
          size: 1600MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 4MiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: Intel
          physical id: 5
          bus info: cpu@1
          version: Intel(R) Core(TM)2 CPU 670
          slot: Socket 775
          size: 1600MHz
          capacity: 3200MHz
          clock: 266MHz
          capabilities: cpufreq
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
             width: 9472 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 9472 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 9472 bits
     *-pci
          description: Host bridge
          product: C55 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.6
             bus info: pci@0000:00:00.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.7
             bus info: pci@0000:00:00.7
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:11 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:12 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:13 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:14 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:15 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:16 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: C55 PCI Express bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi ht pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:e2000000-e3ffffff ioport:d0000000(size=268435456)
           *-display:0
                description: VGA compatible controller
                product: RV530 [Radeon X1600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:25 memory:d0000000-dfffffff(prefetchable) memory:e3000000-e300ffff ioport:d000(size=256) memory:e2000000-e201ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV530 [Radeon X1600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:e3010000-e301ffff
        *-memory:17 UNCLAIMED
             description: RAM memory
             product: MCP51 Host Bridge
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: ht bus_master cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP51 LPC Bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP51 SMBus
             vendor: nVidia Corporation
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:5 ioport:1c00(size=64) ioport:1c80(size=64)
        *-memory:18 UNCLAIMED
             description: RAM memory
             product: MCP51 Memory Controller 0
             vendor: nVidia Corporation
             physical id: a.2
             bus info: pci@0000:00:0a.2
             version: a3
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: MCP51 USB Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:e4106000-e4106fff
        *-usb:1
             description: USB Controller
             product: MCP51 USB Controller
             vendor: nVidia Corporation
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:e4107000-e41070ff
        *-ide:0
             description: IDE interface
             product: MCP51 IDE
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: scsi0
             logical name: scsi1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk:0
                description: ATA Disk
                product: ST3300831A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.03
                serial: 3NF17Y1A
                size: 279GiB (300GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=69205244
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /windows
                   version: 3.1
                   serial: e4eb5c47-ab16-b348-829f-a96fd8cab825
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-01-30 06:48:27 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: e9cc8cd9-a6dd-4f0d-b6b5-477bfd3bb745
                   size: 1953MiB
                   capacity: 1953MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 3d0f689a-e729-4019-a22d-54cf9e8874ae
                   size: 228GiB
                   capacity: 228GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-02 11:21:49 filesystem=ext4 lastmountpoint=/8}&#65533;n&#65533;&#65533;&#65533;&#65533;<C&#65533;(}&#65533;n&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;@kSr&#65533;&#65533;&#65533;Y}&#65533;&#65533;&#65533;ps&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;2y&#65533; modified=2010-08-06 22:21:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-05 14:13:28 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC AC22100H
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 10.0
                serial: WD-WT3611485005
                size: 2014MiB (2111MB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=01110110
              *-volume
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /share
                   version: FAT32
                   serial: 0b18-07e9
                   size: 2011MiB
                   capacity: 2012MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,gid=46,fmask=0007,dmask=0007,allow_utime=0020,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,errors=remount-ro state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22NP20
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                serial: [HL-DT-STDVD-RAM GH22NP201.0108/06/10 7U01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: MCP51 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi ht bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e600(size=16) memory:e4104000-e4104fff
        *-ide:2
             description: IDE interface
             product: MCP51 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi ht bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:eb00(size=16) memory:e4105000-e4105fff
        *-pci:1
             description: PCI bridge
             product: MCP51 PCI Bridge
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: memory:e4000000-e40fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:02:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:19 memory:e4004000-e40047ff memory:e4000000-e4003fff
        *-multimedia
             description: Audio device
             product: MCP51 High Definition Audio
             vendor: nVidia Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ht bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
             resources: irq:22 memory:e4100000-e4103fff
        *-bridge
             description: Ethernet interface
             product: MCP51 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             logical name: eth0
             version: a3
             serial: 00:1a:4d:41:d3:1d
             size: 100000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=71.17.149.204 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:23 memory:e4108000-e4108fff ioport:ec00(size=8)
     *-scsi:0
          physical id: 1
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sdf
     *-scsi:1
          physical id: 2
          bus info: usb@1:8
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart C4180
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdg
             version: 1.00
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by fragos on 2010-11-07
Your mobo is a Gigabyte GA-N650SLI-DS4 and here's the spec's. It has two PCI Express x16 slots so you can use any of the current generation video cards.

---

### Post by tbrminsanity on 2010-11-07
Would this be a good card?
[http://www.newegg.com/Product/Product.aspx?Item=14-125-305&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=14-125-305&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo)

---

### Post by CharlesA on 2010-11-07
It's decent, yes.

---

### Post by fragos on 2010-11-07
> **tbrminsanity said:**
> Would this be a good card?
[http://www.newegg.com/Product/Product.aspx?Item=14-125-305&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=14-125-305&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo)

Looks like a good choice to me but one caution, this card takes two slots so make sure you have an empty slot to the right of the PCI express slot you will be using.

---

### Post by tbrminsanity on 2010-11-07
> **fragos said:**
> Looks like a good choice to me but one caution, this card takes two slots so make sure you have an empty slot to the right of the PCI express slot you will be using.

I would be removing my current card for this one so I will have the extra slot available.

---

