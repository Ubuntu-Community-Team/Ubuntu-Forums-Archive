---
title: "KDE Plasma Workspace is CONSTANTLY crashing!"
date: 2011-10-24
forum: General Help
---

### Post by linuxuser12345 on 2011-10-24
I have been trying to use the KDE Plasma Workspace (minimal) on Ubuntu 11.10 x64 and it CONSTANTLY crashes! :(
Every time I log in using Plasma, I start getting constant error messages AND it won't let me do any administrative work: By that, I mean I can't install programs, etc. because it won't show the password dialogue! 

Can someone help me out, here?

---

### Post by 2F4U on 2011-10-24
What error messages do you get? Also, what are your hardware specs and what graphics driver do you use?
Did you try to reduce the graphical effects?

---

### Post by linuxuser12345 on 2011-10-24
Is there a way I can use the terminal to look up this information?

---

### Post by searchfgold6789 on 2011-10-24
Yes, just press Ctrl + Alt + F1 and you'll get a terminal, hopefully.

---

### Post by linuxuser12345 on 2011-10-24
I mean, how do I look up this information in the terminal? I know there is a way, I just forgot.

---

### Post by searchfgold6789 on 2011-10-24
Sure:```
lspci

```Then we can help you get your drivers sorted out.

---

### Post by linuxuser12345 on 2011-10-24
```
jeb@Kitchen-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
jeb@Kitchen-PC:~$ 

```

---

### Post by searchfgold6789 on 2011-10-24
Sorry, I gave you the wrong command ... :( Can you post the output of this instead? It gives more info than the previous one.
```
sudo lshw
```

---

### Post by linuxuser12345 on 2011-10-25
```
jeb@Kitchen-PC:~$ sudo lshw
[sudo] password for jeb: 
kitchen-pc                
    description: Desktop Computer
    product: A880G+ (To Be Filled By O.E.M.)
    vendor: BIOSTAR Group
    serial: None
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: A880G+
       vendor: BIOSTAR Group
       physical id: 0
       serial: None
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080016
          date: 08/30/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II X3 435 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) II X3 435 Processor
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=3 enabledcores=3
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: CL7-7-7 DDR3-10660
             vendor: Manufacturer01
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (int gfx)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe900000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS880 [Radeon HD 4250]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fea00000-feafffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fe9e8000-fe9ebfff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 00:30:67:9e:89:87
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:e800(size=256) memory:fdffb000-fdffbfff memory:fdffc000-fdffffff memory:febe0000-febfffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:fe8ffc00-fe8fffff
           *-disk
                description: ATA Disk
                product: ST3500418AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: CC38
                serial: 9VMNV621
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000171b8
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: dc048b87-f94d-4c08-aed4-a5390667355f
                   size: 462GiB
                   capacity: 462GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-14 16:22:53 filesystem=ext4 lastmountpoint=/ modified=2011-10-14 16:48:13 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-10-23 20:35:02 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3837MiB
                   capacity: 3837MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3837MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DRW-24B1ST
                vendor: ASUS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fe000-fe8fefff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe8fd000-fe8fdfff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe8ff800-fe8ff8ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fc000-fe8fcfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fb000-fe8fbfff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe8ff400-fe8ff4ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
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
             resources: irq:16 memory:fe8f4000-fe8f7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe8fa000-fe8fafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
jeb@Kitchen-PC:~$ 

```

---

### Post by mastablasta on 2011-10-25
*-display
description: VGA compatible controller
product: RS880 [Radeon HD 4250]
 
 
do you have the proprietary drivers installed?
 
> KDE Plasma Workspace ***(minimal)***
What does minimal mean? did you install it from minimal iso? or do you mean low-fat package?

---

### Post by linuxuser12345 on 2011-10-25
No. I find the open source drivers to be much more stable. And by minimal, I mean kde-plasma-desktop with minimal set of applications.

---

### Post by mastablasta on 2011-10-25
So it's not Kubuntu desktop? If so then this is not really a Kubuntu issue. 
 
Ok even if you think it is, you are not using the product as it was made huh?
 
KDE forums reply quite fast. if this is only some basic KDE plasma desktop, they will be able to help you better maybe. Or they will just bounce you back here like they did me. :-) Still i would give it a try. Especially since as i understand it's the KDE that is crashing.

---

### Post by searchfgold6789 on 2011-10-25
> **linuxuser12345 said:**
> No. I find the open source drivers to be much more stable.
OK, did you mean to say that you did install drivers, and they were the open source ones, or did you mean to say that you didn't install drivers, period?

---

### Post by linuxuser12345 on 2011-10-25
I am having to re-format my whole hard drive. I installed the proprietary driver, and it caused my system to seriously lag. I uninstalled it, and now my computer has crashed! :(

OMG Why can't Canonical allow beta testing on Ubuntu releases to last a few more months? Every time a new release comes out, it is so bogged down with bugs it's unbearable!

---

### Post by searchfgold6789 on 2011-10-25
I would refer you to a specific quote from a certain person's forum signature I saw quite recently. :popcorn:
Start from scratch.

Does you computer have the guts to handle KDE? If you have the GPU for desktop effects, but not the RAM or processor speed, your computer will certainly lag once you install GPU drivers because it will turn all sorts of fancy things on once it detects that your driver supports it. You CPU is only 800 Mhz; red flag.

Exactly how it was lagging and how much it was lagging can tell you alot about what is wrong with a computer. If it was lagging but with short spurts of high performance you just need to press Alt+Shift+F12, which turns desktop effects off. If it was just plain out cruddy performance, try to see if it still happens from a Live CD and even a different OS or distro.

There could be some process hogging your system. Next time you're having the problem, get to a command line and type:```
top
```to find out if there's any malicious programs running. (I consider a program to be "Malicious" in Linux if it's hogging system resources or affecting other programs in a bad way, as opposed to being synonymous with "virus" in the Windows world.)
Good luck,
 - search

---

### Post by linuxuser12345 on 2011-10-25
I definitely have the guts to run KDE. My computer has an ATI Radeon HD GPU, an AMD Athlon II x3 processor, and 4GB DDR3 RAM. I will try re-installing KDE and seeing if I have the same problem, since I have re-formatted my HDD.

---

### Post by searchfgold6789 on 2011-10-26
Yeah, and let us know if my other suggestions work as well.

---

### Post by linuxuser12345 on 2011-10-26
The exact same problem after formatting my HDD multiple times. :(

---

### Post by searchfgold6789 on 2011-10-27
OK, but does it happen from a Live CD? does it happen without desktop effects as I described? you need to read my previous post and then post back. Especially with the "top" command.
With 11.10, I've been getting KWin crashes and major lagging every time I activate a taskbar thumbnail or Side-by-side desktops. So try 11.04 too.
 - search

---

