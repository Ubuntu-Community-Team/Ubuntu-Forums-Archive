---
title: "I was able to burn CD's in Karmic RC, but not in KK final"
date: 2009-10-29
forum: General Help
---

### Post by ankspo71 on 2009-10-29
Hi All,

I did a fresh install of Karmic today, just after burning the Karmic image to cd while using Karmic RC. When I rebooted (after installing Karmic), I found out I am no longer able to burn cds in Karmic (final). I tested Karmic Beta and RC and I was burning CD's just fine, but now I can't burn anymore. Both Brasero and XFburn (my favorite alt burner) both said I had successful burns, but those cd's were actually unreadable and unmountable. I tried DVD+RW and CD-R's, about 5 or 6 of them total. How can I diagnose/fix this problem (considering they are said to be successful burns)? I was running Ubuntu Karmic final, but now I am using the command-line install from the alt cd with an xfce4 desktop. I thought maybe I had a bad install, but apparently not... I'm still making coasters.
Thanks in advance, I'll be back first thing in the morning,
James. 


```
james@mini:~$ sudo lshw
mini                      
    description: Desktop Computer
    product: P4M90-M4
    vendor: BIOSTAR Group
    version: Ver:1.0
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-3412-000078563412
  *-core
       description: Motherboard
       product: P4M90-M4
       vendor: BIOSTAR Group
       physical id: 0
       version: Ver:1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/12/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
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
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2
             physical id: 0
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: A1
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d8000000-dfffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:c000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:fa000000-faffffff memory:c0000000-cfffffff(prefetchable) memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fb000000-fb01ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:31 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-75CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8H3081423
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008032c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: c80b9022-4d91-4988-b9a5-574d62f771ad
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-29 22:05:25 filesystem=ext4 lastmountpoint=/4&#65533;2&#1152;&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;^&#65533;&#65533;iW&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^&#65533;&#65533;&#65533;^&#65533;&#65533;&#65533;Y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2009-10-29 22:22:04 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-10-29 22:36:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3120213A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 2AAA
                serial: 5LS24VQ3
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002c9d7
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/6aa796b8-5caf-4f4b-9cd6-a0a7d6703c1a
                   version: 1.0
                   serial: 6aa796b8-5caf-4f4b-9cd6-a0a7d6703c1a
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-28 01:39:25 filesystem=ext4 lastmountpoint=/media/sdb1&#65533;&#1312;&#65533;&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;j&#65533;&#65533;&#65533;^V&#65533;iW&#65533;p9&#65533;p9&#65533;&#65533;&#65533;T&#65533;&#65533;^V&#65533;&#65533;^V&#65533;&#65533;Y&#65533; modified=2009-10-29 22:40:33 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2009-10-29 22:40:33 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S202J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:e0:4d:bd:db:9f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.5 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:d000(size=256) memory:fdffe000-fdffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:bfffc000-bfffffff

```

---

### Post by ankspo71 on 2009-10-30
Hi Everyone,
here's a recap....

I was able to burn cds in Jaunty, Karmic beta and Karmic Release Candidate. When I did a clean upgrade to the final Karmic, I was no longer able to burn cd's (even though it was said to be successful burns). I tried reinstalling Ubuntu, but instead using the cli option with a xfce4 desktop, still unable to burn. I tried Brasero and Xfburn at this point.

Since I posted, I installed windows, and my cd burner worked. I reinstalled Jaunty and it worked again. Then I went back to a full install of the final Karmic Ubuntu, it went back to not working again. Also, I just got done swapping CD burners with my wife's computer, and I still can't burn cds, but she still can. I also tried K3b since then too. I already have gone though about 10 cds since yesterday, and none of the cds are usable anymore. The ones I burned in windows and jaunty turned out great.

It is clearly a problem between my computer and the final release of Karmic. I don't know what to do from here, but I think I am going to try to find a windows burning application that will work under wine, or instal a second linux OS (probably Jaunty or crunchbang 9.04).... until a fix becomes available. I tried burning cds by launching my burner apps by command line, but I am not getting any errors reported.

New hardware is listed here:
```
james@Karmic:~$ sudo lshw
[sudo] password for james: 
karmic                    
    description: Desktop Computer
    product: P4M90-M4
    vendor: BIOSTAR Group
    version: Ver:1.0
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-3412-000078563412
  *-core
       description: Motherboard
       product: P4M90-M4
       vendor: BIOSTAR Group
       physical id: 0
       version: Ver:1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/12/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
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
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2
             physical id: 0
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: A1
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d8000000-dfffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:c000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:fa000000-faffffff memory:c0000000-cfffffff(prefetchable) memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fb000000-fb01ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:31 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD400BB-75CA
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8H3081423
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008032c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: a2c7a5f2-c35f-4b8b-a7b8-9c797539b0f0
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-30 05:12:46 filesystem=ext4 lastmountpoint=/gg=\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;iW&#65533;&#65533;E&#65533;&#65533;&#65533;E&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;\&#65533;&#65533;&#65533;&#65533;%&#65533; modified=2009-10-30 05:43:29 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2009-10-30 14:11:36 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3120213A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 2AAA
                serial: 5LS24VQ3
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002c9d7
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/sdb1
                   version: 1.0
                   serial: c7b86883-b9e5-461e-b18b-39830583d5af
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-30 13:07:32 filesystem=ext4 lastmountpoint=/media/sdb1N&#65533;&#65533;&#65533;j&#65533;&#65533;k&#65533;&#65533;'k&#65533;&#65533;iW&#65533;(+$&#65533;(+$&#65533;&#65533;&#65533;j&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533; modified=2009-10-30 14:11:36 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2009-10-30 14:11:36 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: iHAP122   8
                vendor: ATAPI
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: UL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:e0:4d:bd:db:9f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.5 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:d000(size=256) memory:fdffe000-fdffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:bfffc000-bfffffff

```Thanks for listening,
James.

---

### Post by elegant55 on 2009-10-30
If you installed Karmic RC and keep updated that would be virtually same as final release. Dose your burner work at this circumstance?

Have you md5sum checked your downloaded iso and installer CD?

---

### Post by ankspo71 on 2009-10-30
Hi Elegant55

Brasero has the checksum plugin enabled but it passed. This is what I am confused about. I did not check my CD for defects when starting it up though, I will go do that now. Thanks for that thought.

No, neither one of the cd burners is are working in Karmic. I just installed wine and DeepBurner 1.9  (which got a platinum rating at [http://appdb.winehq.org/](http://appdb.winehq.org/)) and it gives me the same trouble.

Oh, the reason why I did a fresh install to Karmic (from RC) is because my computer was full of unnecessary apps that I tested. I wanted to eliminate any possibility of errors from that.

Thanks for the help, I will report back whether or not my install cd passes the check.
James

---

### Post by ankspo71 on 2009-10-30
Hi Again,

I md5'ed my ISO and it checked out fine.

```
james@Karmic:~$ cd Desktop
james@Karmic:~/Desktop$ ls
DeepBurner 1.9.exe  ubuntu-9.10-desktop-i386.iso
james@Karmic:~/Desktop$ md5sum ubuntu-9.10-desktop-i386.iso
8790491bfa9d00f283ed9dd2d77b3906  ubuntu-9.10-desktop-i386.iso

```8790491bfa9d00f283ed9dd2d77b3906 ( Checksum from Ubuntu site )

I also did a Ubuntu cd check and memory check, I passed both of those too.

Hmm, maybe the Ubuntu install cd failed to detect that my drive is a burner and didn't install the necessary drivers? I'm almost tempted to try out Kubuntu or Xubuntu Karmic to see what happens. Although, the alternate Ubuntu install didn't help either so I think Kubuntu or Xubuntu wouldn't help my situation.

Thanks,
James.

---

### Post by aaronchall on 2009-10-30
I'd look for the drivers on your manufacturer's site (for linux) and install them, if I were you.

---

### Post by ankspo71 on 2009-10-31
Thanks Aaronchall,

I looked around the Internet, including the drives manufacturer's websites, but I was unable to locate any Linux drivers.

I do have some good news though. I just now managed to successfully burn a cd using Gnomebaker. :D  Now I have to swap the drives back again and see if it still works.

So I changed OS'es 4 times since installing Karmic (final), swapped drives once so far, and I burned 11-ish cds... all before burning one good cd. I must have more patience than I thought. ;)

---

### Post by ankspo71 on 2009-10-31
Hi Again,

Does anybody know if I can report a bug with the little information I have here? I can report Ubuntu version information, burning application information, and hardware information. Other than that, I have no error or crash information to report. [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Thanks again,
James

---

### Post by adrn on 2009-11-03
I just burned and successfully read from a cheap CDR with a MadDog DVD/CD burner.  
from lshw:

 description: DVD writer
                product: MD-16XDVD9A4
                vendor: MAD DOG
....
logical name: /media/cdrom0
                version: 1.F0
                serial: [MAD DOG MD-16XDVD9A4    1.F005032500
                capabilities: removable audio cd-r cd-rw dvd dvd-r



> **ankspo71 said:**
> Hi Elegant55

Brasero has the checksum plugin enabled but it passed. This is what I am confused about. I did not check my CD for defects when starting it up though, I will go do that now. Thanks for that thought.

No, neither one of the cd burners is are working in Karmic. I just installed wine and DeepBurner 1.9  (which got a platinum rating at [http://appdb.winehq.org/](http://appdb.winehq.org/)) and it gives me the same trouble.


---

### Post by FredMcD on 2009-11-06
I was having similar issues to those posted here.  Mine were resolved by booting with the -generic kernel as opposed to the -i386 one.

---

### Post by ankspo71 on 2009-11-06
Thanks FredMcD,

But I already went back to Jaunty so I can burn cds. I had a look at my boot menu and all I see are generic kernels, no i386 in the list. I have my recovery options too. I could swear (sware?) my Karmic installation had the same choices. I went back to jaunty because Gnomebaker quit burning. I'm willing to wager that it's a problem with my hardware setup because it uses VIA (chipsets etc). I have been hearing that this brand is not the best for linux.

Thanks,
James

---

### Post by tai133 on 2009-11-14
I don't think it is your chipset because I am having the same problem on a Shuttle SNGv3 with Nvidia chipset. Everything worked fine in Jaunty. Now the disk burns and K3b reports success, but the disk is not readable or bootable. Just a coaster. I've attached my output from lshw.

---

### Post by gilou on 2009-11-17
Hello

I think burning in karmic is broken. I tried with k3b and in command line.

I have Ati chipset SB700/SB800, others guys have nvidia chipset.

Burning operations was ok in jaunty. 

I've verified rights, purged k3b and cdrdao/wodim, reinstall, it's the same. Burning fails while simulating or writing in k3b and in all the other softwares.

We have to wait for updates or downgrade to jaunty. As for me I have a dual boot karmic/debian lenny and all is fine in lenny. This is no hardware fault.

gilou

---

### Post by Shpongle on 2009-11-26
yea im having the same problem too , guess well just have to wait

---

### Post by johnnie69 on 2010-02-26
Hello!

More of this strange burning story... My case seems identical. In Jaunty burning cds/dvds was just a breeze, at some point in Karmic everything went to hell... It seems to me that it is a kernel or/and wodim issue. 

I've burned many many, more than 10 cds/dvds with various methods and programs. And I always get successful writes BUT unreadable/unmountable media.

This is undoubtfully the worst problem I have ever faced with Ubuntu (at some point I've tried Debian 5 and it produces similar results). 

An hdparm produces some interesting results similar to those posted in other threads concerning burning problems in Karmic, some IO failures.

---

### Post by tiggsy on 2010-02-26
Just seems to be proving that Karmic is not fit for purpose - which is a shame, as I much prefer koalas to jackals.

---

### Post by tai133 on 2010-02-27
FWIW, all my problems went away with a clean install of Karmic. My old system had been updated several times, starting with 7.10 I think. I also had non-supported sources in my /etc/apt/sources.list, so this may have contributed to the problem.

---

