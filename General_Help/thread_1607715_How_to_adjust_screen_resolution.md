---
title: "How to adjust screen resolution"
date: 2010-10-28
forum: General Help
---

### Post by asifnaz on 2010-10-28
On last boot it was fine but now it is showing 800X600 which is too low . How to adjust it

---

### Post by TeoBigusGeekus on 2010-10-28
What are your pc specs? Did you do anything before the last boot? Have you installed any restricted drivers?

---

### Post by asifnaz on 2010-10-28
Please answer me . I have no other choice to format and new install

---

### Post by asifnaz on 2010-10-28
> **TeoBigusGeekus said:**
> What are your pc specs? Did you do anything before the last boot? Have you installed any restricted drivers?

PIII . 256 ram . My brother was using last time he just surf some time and power off the computer from the plug instead of shutting down using the log out menu .
I did not install any thing

---

### Post by TeoBigusGeekus on 2010-10-28
Graphics card?

---

### Post by asifnaz on 2010-10-28
asif-desktop              
    description: Tower Computer
    product: System Name
    vendor: System Manufacturer
    version: System Version
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: CUSI-MN
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: ASUS CUSI-M ACPI BIOS Revision 1009 (06/07/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.10
          slot: PGA 370
          size: 1GHz
          capacity: 1600MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 128MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 128MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 630 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@0000:00:00.1
             logical name: scsi0
             logical name: scsi1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d800(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 2B020H1
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: WAH2
                serial: B15L638E
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a9f5a9f5
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 2c4d-bd37
                   size: 2070MiB
                   capacity: 2070MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3913MiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4886MiB
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 4871MiB
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /
                      capacity: 3564MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:4
                      description: Linux swap / Solaris partition
                      physical id: 9
                      logical name: /dev/sda9
                      capacity: 221MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=sis630_smbus latency=0
             resources: irq:0
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:6 memory:e7800000-e7800fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:6 memory:e7000000-e7000fff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:e6000000-e67fffff memory:f0000000-febfffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: 630/730 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 21
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 cap_list rom
                configuration: driver=sisfb latency=0
                resources: irq:11 memory:f0000000-f7ffffff(prefetchable) memory:e6000000-e601ffff ioport:a800(size=128)
        *-multimedia:0
             description: Multimedia audio controller
             product: CM8738
             vendor: C-Media Electronics Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2
             resources: irq:11 ioport:9800(size=256)
        *-network
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: eth0
             version: 24
             serial: 00:a0:24:4f:f5:ac
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
             resources: irq:11 ioport:9400(size=128) memory:e5800000-e580007f memory:10000000-1001ffff(prefetchable)
        *-multimedia:1
             description: Multimedia audio controller
             product: ES1969 Solo-1 Audiodrive
             vendor: ESS Technology
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ESS ES1938 (Solo-1) latency=32 maxlatency=24 mingnt=2
             resources: irq:9 ioport:9000(size=64) ioport:8800(size=16) ioport:8400(size=16) ioport:8000(size=4) ioport:7800(size=4)
asif@asif-desktop:~$

---

### Post by TeoBigusGeekus on 2010-10-28
Have you enabled the extra effects (right click on desktop>appearance settings>last tab)? If not, try to. Ubuntu might resolve the issue by itself when you do so.

---

### Post by realzippy on 2010-10-28
> **TeoBigusGeekus said:**
> Have you enabled the extra effects (right click on desktop>appearance settings>last tab)? If not, try to. Ubuntu might resolve the issue by itself when you do so.

you mean,ubuntu will install a driver when enabling desktop effects?
doubt that this works since OP has a:

product: 630/730 PCI/AGP VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]

have you (OP) been at System/Preferences/Monitors?

---

### Post by TeoBigusGeekus on 2010-10-28
> **realzippy said:**
> you mean,ubuntu will install a driver when enabling desktop effects?
doubt that this works since OP has a:

product: 630/730 PCI/AGP VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]

have you (OP) been at System/Preferences/Monitors?

Can't say anymore cause I just noticed that op uses Lubuntu.
I'd just delete xorg.conf, reboot and cross my fingers.

Or, else, (to op) punch your brother on the nose and reinstall.

---

### Post by realzippy on 2010-10-28
*Or, else, (to op) punch your brother on the nose and reinstall.*

**+1**

---

### Post by asifnaz on 2010-10-28
Well I prayed and reboot system .
And now it is working fine .
see uploaded file .
Thank you for your time and will to help.:)

---

### Post by realzippy on 2010-11-07
...so you can set thread as "solved" (threadtools).

---

### Post by friTTe81 on 2010-11-09
I had that happen aswell, and i have been using Lubuntu for a while.
But a restart sorted it out :)

---

