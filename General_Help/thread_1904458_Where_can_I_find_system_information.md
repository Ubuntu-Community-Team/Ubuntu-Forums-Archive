---
title: "Where can I find system information?"
date: 2012-01-04
forum: General Help
---

### Post by pretty_whistle on 2012-01-04
I'm using Ubuntu 11.04 with Unity desktop.

Is there some place I can look to get system information like what kind of video card I have, version of Ubuntu, version of Gnome 11.04 has (if I were using it), etc.?

I recall seeing something some place but can't recall it at all.

:confused:

---

### Post by westie457 on 2012-01-04
Try clicking on the gear wheel top right of the screen and selecting 'System Settings'. AFAIK some things are there from what I remember when I was using 11.04.

---

### Post by grahammechanical on 2012-01-04
Look for System Monitor.

You are using Gnome if you are using 11.04 with Unity. Even in Ubuntu classic you are using Gnome. It is the Desktop Environment that Ubuntu is based upon since who knows when. It is Gnome 2 in 11.04 and backwards, and Gnome 3 in 11.10 onwards.

Unity is the User Interface that sits on top of the Desktop Environment. Different User Interfaces have different window managers but underneath with Ubuntu it is still Gnome 3.

Regards.

---

### Post by pretty_whistle on 2012-01-04
> **westie457 said:**
> Try clicking on the gear wheel top right of the screen and selecting 'System Settings'. AFAIK some things are there from what I remember when I was using 11.04.
Not there.  It had various things like disk utility, printing, mouse, sound, etc. to change settings on.

---

### Post by bluexrider on 2012-01-04
> **pretty_whistle said:**
> Not there.  It had various things like disk utility, printing, mouse, sound, etc.

```
sudo lshw
``` for system hardware
```

uname -a
``` for distro info

you could also ```
sudo apt-get install sysinfo 
``` and get a GUI for it

```
sudo lspci
``` will give PCI card info

---

### Post by pretty_whistle on 2012-01-04
> **grahammechanical said:**
> Look for System Monitor.

You are using Gnome if you are using 11.04 with Unity. Even in Ubuntu classic you are using Gnome. It is the Desktop Environment that Ubuntu is based upon since who knows when. It is Gnome 2 in 11.04 and backwards, and Gnome 3 in 11.10 onwards.

Unity is the User Interface that sits on top of the Desktop Environment. Different User Interfaces have different window managers but underneath with Ubuntu it is still Gnome 3.

Regards.
System Monitor?  That's where I saw it!!

Thanx!
:)

---

### Post by pretty_whistle on 2012-01-04
> **bluexrider said:**
> ```
sudo lshw
``` for system hardware
```

uname -a
``` for distro info

you could also ```
sudo apt-get install sysinfo 
``` and get a GUI for it

```
sudo lspci
``` will give PCI card info
Thanx!

---

### Post by pretty_whistle on 2012-01-04
Got what I needed.

Thanx everyone.

---

### Post by imachavel on 2012-01-04
> **bluexrider said:**
> ```
sudo lshw
``` for system hardware
```

uname -a
``` for distro info

you could also ```
sudo apt-get install sysinfo 
``` and get a GUI for it

```
sudo lspci
``` will give PCI card info


worked for me, boy did it work:

description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-5600-104A-8037-B1C04F4A3731
  *-core
       description: Motherboard
       product: 0M3918
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN7082153O03TD.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 01/10/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Microprocessor
          size: 2800MHz
          capacity: 4GHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 3328MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:dfd00000-dfefffff memory:c0000000-cfffffff
           *-display
                description: VGA compatible controller
                product: RV730XT [Radeon HD 4670]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:43 memory:c0000000-cfffffff memory:dfdf0000-dfdfffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff
           *-multimedia
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:42 memory:dfdec000-dfdeffff
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:dfc00000-dfcfffff ioport:d0000000(size=2097152)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:dfb00000-dfbfffff
           *-communication
                description: Modem
                product: FA82537EP 56K V.92 Data/Fax Modem PCI
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:17 memory:dfbfe000-dfbfefff ioport:cc00(size=256)
           *-network
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 03
                serial: 00:13:20:37:87:1b
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.102 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:dfbff000-dfbfffff ioport:c8c0(size=64)
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:23 ioport:ec00(size=256) ioport:e8c0(size=64) memory:dffffe00-dfffffff memory:dffffd00-dffffdff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD reader
                product: CDRW/DVD TSH492B
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/CoD1
                version: TB06
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/CoD1
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD5000AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCATR6988261
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ded99
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4b94c53e-8dc8-45b9-af1e-aa6f47568e1e
                   size: 268GiB
                   capacity: 268GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2011-09-15 12:50:33 filesystem=ext3 modified=2011-12-23 14:17:06 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2012-01-04 16:47:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 151GiB
                   capacity: 151GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 34GiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 56GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2551MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e8a0(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: 00:21:2f:39:be:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.103 multicast=yes wireless=IEEE 802.11bgn

---

### Post by stinkeye on 2012-01-04
If you want an easy to read html page use.
```
sudo lshw -html > hwinfo.html
``` 
Html file will be placed in your home folder.

---

### Post by bluexrider on 2012-01-05
[imachavel]("http://ubuntuforums.org/member.php?u=1454193") 

It was not intended to post the result, more for the OP

---

### Post by dak0 on 2012-01-05
> **pretty_whistle said:**
> I'm using Ubuntu 11.04 with Unity desktop.

Is there some place I can look to get system information like what kind of video card I have, version of Ubuntu, version of Gnome 11.04 has (if I were using it), etc.?

I recall seeing something some place but can't recall it at all.

:confused:

This is what you need buddy :) great application!

[IMG]http://pic.mk/images/o5Clg.png[/IMG]

---

