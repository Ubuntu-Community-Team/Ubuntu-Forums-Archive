---
title: "VLC Error - DVD"
date: 2011-02-18
forum: General Help
---

### Post by phosphide on 2011-02-18
Hi all,

So I have downloaded and looked at just about every tutorial in the world for trying to get dvd's to play on Ubuntu, but I am still running into problems.

I have downloaded the w64codecs, the libdvd's, etc. However, when I open up VLC, it starts to run the dvd but then immediately closes.

This is the output from the terminal:

```
VLC media player 1.0.6 Goldeneye
[0x200b4b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: AVATAR
libdvdnav: DVD Serial Number: 3C63A5C7
libdvdnav: DVD Title (Alternative): AVATAR
libdvdnav: Unable to find map file '/home/tristan/.dvdnav/AVATAR.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000144
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000030f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004d3
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000004d3)!!
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00001f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00002122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000313e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00003302
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00005e74
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00006038
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00006246
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0002cc2f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x0002cc2f)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003d7455
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 5
[0x7fc868001828] main input error: ES_OUT_RESET_PCR called
[0x7fc868001828] main input error: ES_OUT_RESET_PCR called
[0x7fc868001828] main input error: ES_OUT_RESET_PCR called
[0x7fc868001828] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
```

Does anyone have any suggestions?

I am using 10.04.

---

### Post by jerrrys on 2011-02-20
i didnt look at the printout, but thought i would add that our version of vlc has known bugs and is no longer supported by vlc.  so i went here 

[http://www.ubuntugeek.com/how-to-install-vlc-1-1-4-in-ubuntu-10-04-new-ppa.html](http://www.ubuntugeek.com/how-to-install-vlc-1-1-4-in-ubuntu-10-04-new-ppa.html)

---

### Post by phosphide on 2011-02-20
Well, still running into problems as I can't get any dvd's to work with any programs at all. Not even xine.

---

### Post by emarkay on 2011-02-21
What is your graphic display type, and VRAM, and system RAM and processor;   other hardware details?
Next, give more info - did you ever have DVD playback, is this an upgrade or a new install of Ubuntu?
Do you have Medibuntu, and the DVD decrypt codec (they are separately listed on that site's webpage) and Ubuntu Restricted Packages installed?
Can you read the contents on the DVD in Nautilus? 
Do all DVD's fail?
If you dual boot, can you play the DVD's in another OS? 

It sounds like either a hardware or a codec issue.

---

### Post by thefasterblueone on 2011-02-21
Try reinstalling libdvdnav and rebooting.

---

### Post by phosphide on 2011-02-22
> **emarkay said:**
> What is your graphic display type, and VRAM, and system RAM and processor;   other hardware details?
Next, give more info - did you ever have DVD playback, is this an upgrade or a new install of Ubuntu?
Do you have Medibuntu, and the DVD decrypt codec (they are separately listed on that site's webpage) and Ubuntu Restricted Packages installed?
Can you read the contents on the DVD in Nautilus? 
Do all DVD's fail?
If you dual boot, can you play the DVD's in another OS? 

It sounds like either a hardware or a codec issue.

I am posting the results from lshw below.

```
description: Notebook
    product: HP Compaq 8510w
    vendor: Hewlett-Packard
    version: F.0B
    serial: CNU805038Q
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=19076695-4B15-E011-0394-6D9910046129
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
          version: 68MVD Ver. F.0B (12/07/2007)
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
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
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
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:4000(size=4096) memory:e5000000-e7ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Quadro FX 570M
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e5000000-e5ffffff memory:d0000000-dfffffff(prefetchable) memory:e6000000-e7ffffff ioport:4000(size=128)
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
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: Mobile PM965/GM965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi cap_list
             configuration: latency=0
             resources: ioport:5000(size=8) ioport:5008(size=4) ioport:5010(size=8) ioport:5018(size=4) ioport:5020(size=16)
        *-communication:1
             description: Serial controller
             product: Mobile PM965/GM965 KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
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
             capacity: 1GB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:28 memory:e8020000-e803ffff memory:e8040000-e8040fff ioport:5040(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
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
             capabilities: bus_master
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
             capabilities: pm debug bus_master cap_list
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
             resources: irq:17 memory:e8044000-e8047fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:6000(size=4096) memory:e4000000-e40fffff memory:88000000-881fffff(prefetchable)
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
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.71 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:30 memory:e4000000-e4001fff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:2000(size=8192) memory:e0000000-e3ffffff memory:88200000-883fffff(prefetchable)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
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
             capabilities: bus_master
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
             capabilities: bus_master
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
             capabilities: pm debug bus_master cap_list
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
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=4096) memory:e4100000-e43fffff memory:80000000-87ffffff(prefetchable)
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
                resources: iomemory:b00303020-b0030301f irq:16 memory:e4100000-e4100fff ioport:7000(size=256) ioport:7400(size=256) memory:80000000-83ffffff(prefetchable) memory:8c000000-8fffffff
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
                resources: iomemory:b00704020-b0070401f irq:17 memory:e4101000-e4101fff ioport:7800(size=256) ioport:7c00(size=256) memory:84000000-87ffffff(prefetchable) memory:90000000-93ffffff
              *-pccard UNCLAIMED
                   description: RICOH
                   physical id: 0
                   version: Bay8Controller
                   slot: Socket 1
                   resources: irq:17
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:e4102000-e41027ff
           *-generic:0
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
           *-generic:1
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255
                resources: irq:5 memory:e4104000-e41040ff
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
                logical name: /media/cdrom0
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:5140(size=32) memory:e8049000-e80497ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHW2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
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
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7ef52e46-5202-4a92-9d1a-6e8be12da637
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2011-02-17 15:17:00 filesystem=ext3 modified=2011-02-18 10:52:42 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-02-21 22:00:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
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

```

Yes, I have medibuntu, the restricted packages, and I followed the tutorial from here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I have upgraded from Ubuntu 9.04 and I don't know what Nautilus is. Lastly, no I am not dual booting and all dvd's are failing.

---

### Post by phosphide on 2011-02-22
> **thefasterblueone said:**
> Try reinstalling libdvdnav and rebooting.
When I tried running sudo apt-get install libdvdnav it says couldn't find package. Though I do have libdvdnav4 installed.

EDIT: This is the output from when I tried running vlc again.

```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
```

---

### Post by phosphide on 2011-02-23
Sorry to bump, but I am still running into problems.

---

### Post by emarkay on 2011-03-04
Sorry for delay!

I presume you are fully updated and also have any Restricted Drivers installed.

Try updating VLC: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Follow the instructions there.

---

### Post by coldraven on 2011-03-04
Try cleaning the lens, I had this a few weeks ago and it took three goes at cleaning before VLC would play. Too much nicotine in this house :confused:

---

