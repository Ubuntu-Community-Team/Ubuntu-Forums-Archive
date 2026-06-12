---
title: "It takes a long time to open a browser!"
date: 2011-05-11
forum: General Help
---

### Post by Richiegs on 2011-05-11
After upgrading to a 64-bit Ubuntu 11.04, I have found that it takes a lot longer to open any browsers such as Firefox, Google Chrome or Opera. Does anyone know why? I thought 64 bit Ubuntu should be faster than the 32 bit version. Nevertheless, I see no difference besides the browser problem mentioned above. Thank you very much in advance.

---

### Post by Grenage on 2011-05-11
> **Richiegs said:**
> After upgrading to a 64-bit Ubuntu 11.04, I have found that it takes a lot longer to open any browsers such as Firefox, Google Chrome or Opera. Does anyone know why? I thought 64 bit Ubuntu should be faster than the 32 bit version. Nevertheless, I see no difference besides the browser problem mentioned above. Thank you very much in advance.

x64 is marginally quicker for some things, a fair bit in others (video stuff, etc), and no faster for most.  If you can post you system specs and other pertinent information, we can offer further advice.

---

### Post by sweetleaf on 2011-05-11
> **Richiegs said:**
> After upgrading... I have found that it takes a lot longer to open any browsers such as Firefox, Google Chrome or Opera.

Perhaps you had installed preload before, and now you no longer have it?

---

### Post by Richiegs on 2011-06-15
> **Grenage said:**
> x64 is marginally quicker for some things, a fair bit in others (video stuff, etc), and no faster for most.  If you can post you system specs and other pertinent information, we can offer further advice.

My PC is a Dell Pentium D with 3 gigabyte of Ram.
I wonder if the delay is due to Ubuntu 11.04. It never happened with Ubuntu 10.04.

---

### Post by Richiegs on 2011-06-15
> **Grenage said:**
> x64 is marginally quicker for some things, a fair bit in others (video stuff, etc), and no faster for most.  If you can post you system specs and other pertinent information, we can offer further advice.
If 64-bit Ubuntu is marginally quicker than 32-bit's, then what is the reason of installing 64-bit Ubuntu? Security?

---

### Post by WorMzy on 2011-06-15
I'm using an Intel Wolfdale myself, and it takes me 2.4 seconds to open Firefox. So what sort of time are we talking about here? "Significantly longer" leaves an awful lot to the imagination.

If you've experienced a significant start-up time reduction with a 32-bit OS, and there's no pressing reason for you to use a 64-bit OS, then reverting to the 32-bit OS is by no means a bad choice. How often do you use >3GB of RAM while using Linux anyway?

---

### Post by Richiegs on 2011-06-15
> **WorMzy said:**
> I'm using an Intel Wolfdale myself, and it takes me 2.4 seconds to open Firefox. So what sort of time are we talking about here? "Significantly longer" leaves an awful lot to the imagination.

If you've experienced a significant start-up time reduction with a 32-bit OS, and there's no pressing reason for you to use a 64-bit OS, then reverting to the 32-bit OS is by no means a bad choice. How often do you use >3GB of RAM while using Linux anyway?

2.4 seconds is pretty fast! It takes me about 10 seconds to open any browser such as Firefox.

I usually use about 1.4 GB of RAM even thoush my PC has 3 GB.

---

### Post by WorMzy on 2011-06-15
I missed your previous post. I assumed you already knew the "benefits" of 64-bit OSs.

As Grenage mentioned, the 64-bit architecture boasts a slight improvement in performance when dealing with RAM-heavy tasks, like video encoding; but for every days things, like web browsing, checking your mail, etc., there's no real benefit. It still allows you to utilise upto ~16 exabytes of RAM, but since you're using 3 gigabytes, you don't need to worry about the 32-bit limitation any way. 

I'm not sure where the problem you're having is being caused. I neglected to mention earlier that I'm also using a 64-bit OS (also Linux, just not Ubuntu). So I'm not sure where your problem is originating from. I can only recommend that you switch back to the 32-bit version of Ubuntu. You won't be missing out on anything by doing so.

However, if you want to try the 10.04 64-bit version, and see if that works better than the 11.04 64-bit version, feel free. 11.04 has a few significant changes which *may* be responsible for degradation in performance.

---

### Post by wildmanne39 on 2011-06-15
> **Richiegs said:**
> 2.4 seconds is pretty fast! It takes me about 10 seconds to open any browser such as Firefox.

I usually use about 1.4 GB of RAM even thoush my PC has 3 GB.Hi, also are you using any desktop effects? How many addons do you have installed in firefox?. Also if there is a problem because of resources or conflicts with compiz try logging into ubuntu with no effects and see if that helps. I know how much ram you have but penthium d I know nothing about like is it for processor or one and how fast are they. If you do not know and you want to run this from the terminal.
```
sudo lshw
```

---

### Post by Richiegs on 2011-06-15
However, if you want to try the 10.04 64-bit version, and see if that works better than the 11.04 64-bit version, feel free. 11.04 has a few significant changes which *may* be responsible for degradation in performance.[/QUOTE]


If I want to change from 64-bit to a 32-bit Ubuntu, do I need to do a clean install?

---

### Post by Richiegs on 2011-06-15
ubuntu                    
    description: Tower Computer
    product: Dimension 9100
    vendor: Winbond Electronics
    serial: 
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=tower power-on_password=enabled uuid=44454C4C-4C00-105A-8038-B7C04F523158
  *-core
       description: Motherboard
       product: 0X8582
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN7082155EH02W.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A03
          date: 07/07/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl cid cx16 xtpr
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: NT512T64U88A0BY-37
             vendor: Nanya Technology
             physical id: 0
             serial: DB232E43
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: Kingston
             physical id: 1
             serial: 69CC8420
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: NT512T64U88A0BY-37
             vendor: Nanya Technology
             physical id: 2
             serial: A7282E42
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: Kingston
             physical id: 3
             serial: 67CC7820
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fe900000-feafffff ioport:fc000000(size=33554432)
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:45 memory:fc000000-fdffffff memory:fe9e0000-fe9effff ioport:dc00(size=256) memory:fea00000-fea1ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:fe9f0000-fe9fffff
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
             resources: irq:46 memory:febfc000-febfffff
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
             resources: irq:41 ioport:1000(size=4096) memory:fe800000-fe8fffff ioport:c0000000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:c0200000-c03fffff ioport:c0400000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:c0600000-c07fffff ioport:c0800000(size=2097152)
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
             resources: irq:21 ioport:ff80(size=32)
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
             resources: irq:22 ioport:ff60(size=32)
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
             resources: irq:18 ioport:ff40(size=32)
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
             resources: irq:23 ioport:ff20(size=32)
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
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:fe700000-fe7fffff
           *-network
                description: Ethernet interface
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 01
                serial: 00:12:3f:70:1b:27
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.67.94.29 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:fe7ff000-fe7fffff ioport:ccc0(size=64)
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVR-118L
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/BenQ_LCD
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/BenQ_LCD
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:febfbc00-febfbfff
           *-disk
                description: ATA Disk
                product: Maxtor 6Y160M0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YAR5
                serial: 
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: Windows FAT volume
                   vendor: Winbond Electronics
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT16
                   serial: 07d5-0709
                   size: 47MiB
                   capacity: 47MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=DellUtility
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 08379d5b-da5f-bc45-a242-10a36e7201d3
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-03 13:42:22 filesystem=ntfs state=clean
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 34d28fc5-336d-4412-b9d3-7db77491c5ae
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-27 11:44:50 filesystem=ext4 lastmountpoint=/ modified=2011-06-12 08:36:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-16 08:41:16 state=mounted
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
             resources: ioport:ece0(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde

---

### Post by Richiegs on 2011-06-15
The delay happens in every internet browser I use such as Firefox, Opera and Chrome. I use very few add-ons.

---

### Post by wildmanne39 on 2011-06-15
> **Richiegs said:**
> The delay happens in every internet browser I use such as Firefox, Opera and Chrome. I use very few add-ons.
Hi, looking at your system and knowing that there are some issues sometimes with video card drivers and compiz I still think you should log in with ubuntu classic no effects and see if that helps. Unity is heavier on resources and you have one cpu. I have four and with compiz and effects running in unity it eats up my cpu usage, I have sensors installed to watch my cpu, memory usage that is how I know.

---

### Post by WorMzy on 2011-06-16
> **Richiegs said:**
> If I want to change from 64-bit to a 32-bit Ubuntu, do I need to do a clean install?

I'm afraid so.

---

