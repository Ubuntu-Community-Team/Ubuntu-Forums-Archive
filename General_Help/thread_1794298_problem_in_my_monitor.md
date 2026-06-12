---
title: "problem in my monitor"
date: 2011-06-30
forum: General Help
---

### Post by mtmwwf on 2011-06-30
hello

my monitor
LG  LCD Flatron Wide Screen w1934s 
 has problem

1-resolution is fixed and not change
there on possible only 1440*900 is very bad

2-refresh rate 0
and not changed and the picture is not fine 
there are Similar to Waves on screen and it effect my eye
[IMG]http://www8.0zz0.com/2011/06/30/23/381689164.jpg[/IMG]
ia m new in Linux

---

### Post by wolfen69 on 2011-06-30
Did you install graphics drivers?

---

### Post by wildmanne39 on 2011-07-01
Hi, if you installed video card drivers, then go to this link to set resolution manually.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by mtmwwf on 2011-07-01
i dont know how the video driver is installed or not ??

iam new to linux

[IMG]http://www9.0zz0.com/2011/07/01/07/139630221.jpg[/IMG]

---

### Post by mtmwwf on 2011-07-01
plz any help

---

### Post by wildmanne39 on 2011-07-01
Hi, type this command in a terminal
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by mtmwwf on 2011-07-01
Thanks wildmanne39 for interactive

this is the output

```
elsabagh@elsabagh:~$ sudo lshw
[sudo] password for elsabagh: 
elsabagh                  
    description: Desktop Computer
    product: P4GE-MX
    vendor: ASUSTeK Computer INC.
    version: 2.xx
    serial: 123456789000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: P4GE-MX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 2.xx
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS P4GE-MX ACPI BIOS Revision 1006 (04/20/2005)
          size: 128KiB
          capacity: 320KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: PGA 478
          size: 2400MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM 40961 MHz (0.0 ns) [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             clock: 2306MHz (0.4ns)
        *-bank:1
             description: DIMM DDR Synchronous 66 MHz (15.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 66MHz (15.2ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:ec100000-ec17ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ec180000-ec1803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:ec000000-ec0fffff
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:01:0d.0
                logical name: eth0
                version: 10
                serial: 00:11:d8:b4:f6:0d
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.12 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:17 ioport:c000(size=256) memory:ec000000-ec0000ff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
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
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:20000000-200003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600AABB-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00.0
                serial: WD-WMAP9C766241
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2b232b22
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/8CE8A891E8A87B5A
                   version: 3.1
                   serial: 7e5f4084-3611-2f48-ba3f-f0d72e89af2a
                   size: 22GiB
                   capacity: 22GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-11-14 16:38:46 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: e7de3561-cd8a-4b33-a954-89b4f8719b09
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-10-23 20:38:59 filesystem=ext3 modified=2011-05-31 02:16:32 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-07-01 15:04:33 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: ad08cf31-00ab-4e41-8e16-3c6d11d968f0
                   size: 1239MiB
                   capacity: 1239MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/B2E44F1CE44EE1E9
                      capacity: 15GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 39GiB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 64GiB
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:ec181000-ec1811ff memory:ec182000-ec1820ff
elsabagh@elsabagh:~$ 

```

---

### Post by wildmanne39 on 2011-07-01
Hi, one more command so I can make sure your video driver is working properly.
```
sudo lspci -k
```
post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by mtmwwf on 2011-07-02
Thanks man for help

this is the output

```
elsabagh@elsabagh:~$ sudo lspci -k
[sudo] password for elsabagh: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8093
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8093
    Kernel driver in use: i915
    Kernel modules: i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8089
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 810f
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
elsabagh@elsabagh:~$ 

```

---

### Post by wildmanne39 on 2011-07-02
> **mtmwwf said:**
> Thanks man for help

this is the output

```
elsabagh@elsabagh:~$ sudo lspci -k
[sudo] password for elsabagh: 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8093
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 8093
    Kernel driver in use: i915
    Kernel modules: i915
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
    Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. P4B533
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8089
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 810f
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
elsabagh@elsabagh:~$ 

```
Hi, ok your driver module is loaded, everything looks good, what you need to do is set your resolution manually, I had to do this also. Here is a link with the best instructions I have find to do this.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

