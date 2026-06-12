---
title: "Just getting problems with Ubuntu"
date: 2010-09-24
forum: General Help
---

### Post by Arunomi on 2010-09-24
I have installed Ubuntu on my laptop and I only get problems.
First I couldn't make a swap so I installed ubuntu with out one.
The disk is partiend with one small partition in the beginning and on at the end there there for me to recover Windows if I need to.
And then I got the Windows partition and the Linux partition.

When I got it installed the screen flickers from time to time its like strips a cross the screen that flickers around.
And some graphic software are slow.

Then the update manager didn't want to update Google Chrome.
It downloaded the package but sade it was corrupt.

And now the last one Thunderbird don't load as it should.
I took a screen shot.


And for last this is all the info I can get on my laptop.
LG R405-A.CPH5V:
* Windows Vista Home Premium
* Intel® Pentium Dual Core 1.86GHz
* 250Gb hårddisk
* 14,1" LCD skärm
* 3G/HSPDA/GPRS modem inbyggt
* Vikt endast 2,3 kilo
* Minne 3GB(2+1Gb) DDR II
* Minnesslot:5-in-1
* Webkamera:1.3M pixel

Ubuntu 10.04 LTS - Lucid Lynx
Kernel 2.6.32-25-generic

```
arunomilaptop             
    description: Computer
    product: R405-A.CPH5V
    vendor: LG Electronics
    version: 0100
    serial: 809KSNA003791
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=00E8D378-917A-0010-8242-6AA5960C3817
  *-core
       description: Motherboard
       product: Lhotse-II
       vendor: LG Electronics Inc.
       physical id: 0
       version: Rev0.4b
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: LHORSF12 (11/14/2008)
          size: 108KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect edd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U23
          size: 800MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 6MiB
             capabilities: burst internal write-back
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
          physical id: d
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous [empty]
             physical id: 0
             slot: J400
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: J401
             size: 2GiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: J501
        *-bank:3
             description: DIMM DRAM Synchronous
             physical id: 3
             slot: J500
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
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
          product: Radeon Xpress 7930 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS7932 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:9000(size=4096) memory:dfe00000-dfefffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Radeon Xpress 1250
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:28 memory:e0000000-efffffff(prefetchable) memory:dfef0000-dfefffff ioport:9000(size=256)
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:a000(size=4096) memory:f4400000-f44fffff
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 15
                serial: 00:e0:91:33:7b:65
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:27 memory:f4400000-f4403fff ioport:a000(size=256)
        *-pci:2
             description: PCI bridge
             product: RS7936 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:3
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f4300000-f43fffff
           *-network
                description: Wireless interface
                product: RT2860
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 00
                serial: 00:22:43:26:f5:2d
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2860 ip=192.168.1.66 latency=0 multicast=yes wireless=RT2860 Wireless
                resources: irq:19 memory:f4300000-f430ffff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8438(size=8) ioport:8444(size=4) ioport:8430(size=8) ioport:8440(size=4) ioport:8400(size=16) memory:f4209000-f42093ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHY2250B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 0000
                serial: K42RT8826RWW
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f13747a3
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a26c-c58d
                   size: 1534MiB
                   capacity: 1536MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2008-06-20 01:08:45 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 48589787-7139-4d4c-85c8-2db6e53782ae
                   size: 99GiB
                   capacity: 100GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-06-20 01:53:18 filesystem=ntfs state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 5b54a8d2-b693-4a10-a99d-112afaedff7b
                   size: 124GiB
                   capacity: 124GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-08-22 19:34:09 filesystem=ext4 lastmountpoint=/1&#1612;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;k &#65533;&#65533;i/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;mn modified=2010-09-15 13:19:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-24 22:38:41 state=mounted
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   version: 3.1
                   serial: 546f-a9a7
                   size: 7159MiB
                   capacity: 7169MiB
                   capabilities: primary boot ntfs initialized
                   configuration: clustersize=4096 created=2009-07-12 00:32:10 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f4004000-f4004fff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f4005000-f4005fff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f4006000-f4006fff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f4007000-f4007fff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f4008000-f4008fff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f4209400-f42094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T40N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: JH01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f4000000-f4003fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
  *-battery
       description: Lithium Ion Battery
       product: xxx
       vendor: xxx
       physical id: 1
       slot: Left Front
       capacity: 651200mWh
       configuration: voltage=14.8V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: inbound
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes

```

I hope some one can help me.

Best regards Sean

---

### Post by n1unqn on 2010-09-24
I installed 10.04 using the windows application and everything runs fine

Some 3D games were slow graphics at first but a pop-up came up with a driver for my nVidia graphics card and they run fast now. Look for an icon on your desktop bar that says a new driver is available.

---

### Post by Arunomi on 2010-09-25
There is no such icon. 
And if I go to the Hardware Divers in System it says that there
are no for any hardware on my system.

My grafic card is ATI Mobility Radeon X1200.

---

