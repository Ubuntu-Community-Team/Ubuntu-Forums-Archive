---
title: "Driver/Effects not working after reinstallation"
date: 2010-06-19
forum: General Help
---

### Post by Axilus on 2010-06-19
I recently had accidentally reformatted my laptop hardrive (don't ask how, I just did); so subsequently, today I spent the whole day doing a reinstall of all my programs and settings etc.

In order to do said task, I used a list of programs installed on my home pc:
```
sudo dpkg --get-selections > installed-software
```

And then installed in onto my fresh install of Ubuntu 10.04 x64 onto my laptop using:
```
sudo dpkg --set-selctions < installed-software
```
```
sudo dselect
```

It then took my slow internet connection a good 4 hours to install all of my previous programs. I then proceeded to download my fonts and themes that I previously had as well.

To my surprise I noticed extreme screen tearing all of a sudden, and Docky reported that composting wasn't turned on.

Next, I proceeded to go into Appearance -> Visual Effects, and I noticed that they were turned off. I then tried enabling Normal, Extra, and Custom to no success. A message box would pop up saying, "searching for drivers", and then displays another box that reads, "Desktop Effects could not be enabled."

When I try to open 'Ati Catalyst Control Center' I get this message:
```
There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
```

And when I try 'compiz --replace' I get this message:
```
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

And nothing happens after that.

The hardware specs of my laptop and desktop are the following, respectively:
```
emmanuel-laptop           
    description: Portable Computer
    product: M-1629
    vendor: Gateway
    version: 3409925R
    serial: T4C86A1003365
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=portable uuid=70E33D97-7831-003E-D247-8F8F7841EEA7
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 9D.05
       serial: QTFENH82501746
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 9D.05 (05/23/2008)
          size: 112KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          slot: Socket M2/S1G1
          size: 1800MHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
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
             slot: H0 L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             serial: 764E98A4
             slot: S1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             serial: 824D4D87
             slot: S2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:f8000000-f81fffff ioport:f0000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:30 memory:f0000000-f7ffffff(prefetchable) memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff
           *-multimedia
                description: Audio device
                product: Radeon X1200 Series Audio Controller
                vendor: ATI Technologies Inc
                physical id: 5.2
                bus info: pci@0000:01:05.2
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=64
                resources: irq:19 memory:f8110000-f8113fff
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24
        *-pci:2
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
             resources: irq:25 ioport:a000(size=4096) memory:f8200000-f82fffff
           *-network
                description: Wireless interface
                product: RTL8187SE Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 22
                serial: 00:16:44:d2:6f:e6
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=r8180 ip=192.168.1.102 latency=0 multicast=yes wireless=802.11b/g  link
                resources: irq:16 ioport:a000(size=256) memory:f8200000-f8203fff
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26
        *-pci:4
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:b000(size=4096) memory:f8300000-f83fffff memory:c0000000-c01fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 01
                serial: 00:e0:b8:fb:06:e7
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:b000(size=256) memory:f8300000-f8300fff memory:c0000000-c001ffff(prefetchable)
        *-pci:5
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8434(size=4) ioport:8438(size=8) ioport:8430(size=4) ioport:8400(size=16) memory:f8609000-f86093ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXE508HW1113
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000caa05
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9585f45c-b430-4ffd-b97e-8c7301079d45
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-06-19 10:27:18 filesystem=ext4 lastmountpoint=/(&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;&#65533;&#65533;-&#65533;&#65533;&#65533;&#65533;@X&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;.&#65533;&#65533; modified=2010-06-19 10:42:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-19 20:08:36 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 201GiB
                   capacity: 201GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5721MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 195GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
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
             resources: irq:16 memory:f8604000-f8604fff
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
             resources: irq:17 memory:f8605000-f8605fff
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
             resources: irq:18 memory:f8606000-f8606fff
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
             resources: irq:17 memory:f8607000-f8607fff
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
             resources: irq:18 memory:f8608000-f8608fff
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
             resources: irq:19 memory:f8609400-f86094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DX06
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
             resources: irq:16 memory:f8600000-f8603fff
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
        *-pci:6
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SMP-PANA
       physical id: 1
       version: 2008/05/27
       serial: 1192
       slot: In the Back side
       capacity: 4800mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

```
axilus                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=E091001E-8C00-01F9-F3F6-00261880EA2E
  *-core
       description: Motherboard
       product: M4A78-E
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 100888140000933
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1210 (06/26/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 945 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 945 Processor
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 38
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:c000(size=4096) memory:fbd00000-fbdfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV790 [Radeon HD 4800 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:d0000000-dfffffff(prefetchable) memory:fbde0000-fbdeffff ioport:c000(size=256) memory:fbdc0000-fbddffff(prefetchable)
           *-multimedia
                description: Audio device
                product: HD48x0 audio
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fbdfc000-fbdfffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:fbe00000-fbefffff
           *-network
                description: Ethernet interface
                product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 00:26:18:80:ea:2e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:28 memory:fbec0000-fbefffff ioport:dc00(size=128)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:19 memory:fbfff800-fbffffff ioport:e800(size=256)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fbcffc00-fbcfffff
           *-disk:0
                description: ATA Disk
                product: ST3500418AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: CC35
                serial: 9VM29Q7Q
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e02b6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 1fc0cd45-6f3b-4659-9119-a5da50b105c6
                   size: 454GiB
                   capacity: 454GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-01 11:42:26 filesystem=ext4 lastmountpoint=/&#65533;<&#65533;&#65533;&#65533;&#65533;&#65533;&#267;&#1608;<&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;yT&#65533;&#65533;&#65533;&#65533;&#65533;u+&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(i*&#65533; modified=2010-05-24 07:00:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-18 06:17:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD800JD-00MS
                vendor: Western Digital
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 10.0
                serial: WD-WMAM9V266585
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=11f911f8
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 1c48170a-3e3e-5b43-96ac-54fb098e60c0
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-08-05 08:03:02 filesystem=ntfs state=clean
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fbcfd000-fbcfdfff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fbcfe000-fbcfefff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fbcff800-fbcff8ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfb000-fbcfbfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfc000-fbcfcfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fbcff400-fbcff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVDRW SHW-160P6S
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: PS0A
                capabilities: removable audio cd-r cd-rw dvd dvd-r
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
             resources: irq:16 memory:fbcf4000-fbcf7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfa000-fbcfafff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

And here is the list of installed programs that I used with dselect:
```
acpi-support					install
acpid						install
adduser						install
adium-theme-ubuntu				install
agave						install
aisleriot					deinstall
akirad-keyring-and-mirrors			install
akonadi-server					install
alacarte					install
alarm-clock					deinstall
alsa-base					install
alsa-utils					install
anacron						install
anjuta						deinstall
anjuta-common					deinstall
ant						install
ant-gcj						install
ant-optional					install
ant-optional-gcj				install
apache2						install
apache2-mpm-prefork				install
apache2-utils					install
apache2.2-bin					install
apache2.2-common				install
app-install-data				install
app-install-data-partner			install
apparmor					install
apparmor-utils					install
apport						install
apport-gtk					install
apport-symptoms					install
apt						install
apt-transport-https				install
apt-utils					install
apt-xapian-index				install
aptdaemon					install
aptitude					install
apturl						install
apturl-common					install
ardour						install
aspell						install
aspell-en					install
at						install
at-spi						install
audacious					deinstall
audacious-plugins				install
audacity					install
audacity-data					install
autoconf					install
automake					install
automake1.9					install
autopano-sift					install
autotools-dev					install
avahi-autoipd					install
avahi-daemon					install
avahi-utils					install
avr-libc					install
avrdude						install
banshee						deinstall
base-files					install
base-passwd					install
bash						install
bash-completion					install
bc						install
bcmwl-modaliases				install
bind9-host					install
binfmt-support					install
binutils					install
binutils-avr					install
blender						install
bluez						install
bluez-alsa					install
bluez-cups					install
bluez-gstreamer					install
bogofilter					install
bogofilter-bdb					install
bogofilter-common				install
branding-ubuntu					install
brasero						install
brasero-common					install
breathe-icon-theme				install
brltty						install
brltty-x11					install
bsd-mailx					install
bsdmainutils					install
bsdutils					install
build-essential					install
burg						install
burg-common					install
burg-emu					install
burg-pc						install
burg-themes					install
burg-themes-common				install
busybox-initramfs				install
busybox-static					install
byobu						install
bzip2						install
bzr						install
bzr-builddeb					install
bzr-dbus					install
bzr-explorer					install
bzr-gtk						install
bzrtools					install
ca-certificates					install
ca-certificates-java				install
cabextract					install
capplets-data					install
caps						install
cdparanoia					install
checkbox					install
checkbox-gtk					install
cheese						install
cheese-common					install
chromium-browser				install
chromium-browser-inspector			install
chromium-codecs-ffmpeg				install
cinelerra					install
cli-common					install
comerr-dev					install
command-not-found				install
command-not-found-data				install
community-themes				install
compiz						install
compiz-core					install
compiz-fusion-plugins-extra			install
compiz-fusion-plugins-main			install
compiz-gnome					install
compiz-plugins					install
compizconfig-backend-gconf			install
compizconfig-settings-manager			install
computer-janitor				install
computer-janitor-gtk				install
conky						install
conky-all					install
console-setup					install
console-terminus				install
consolekit					install
coreutils					install
couchdb-bin					install
cpio						install
cpp						install
cpp-4.4						install
cpu-checker					install
cron						install
cups						install
cups-bsd					install
cups-client					install
cups-common					install
cups-driver-gutenprint				install
cvs						install
dash						install
dbus						install
dbus-x11					install
dc						install
dcraw						install
dctrl-tools					install
ddclient					install
debconf						install
debconf-i18n					install
debianutils					install
default-jdk					install
default-jdk-doc					install
default-jre					install
default-jre-headless				install
defoma						install
deja-dup					deinstall
desktop-file-utils				install
desktopcouch					install
devscripts					install
dhcp3-client					install
dhcp3-common					install
dictionaries-common				install
diffstat					install
diffutils					install
dkms						install
dmidecode					install
dmsetup						install
dmz-cursor-theme				install
dnsmasq-base					install
dnsutils					install
doc-base					install
docbook-xml					install
docky						install
dosfstools					install
dpkg						install
dpkg-dev					install
dput						install
dvd+rw-tools					install
dvdauthor					install
dvgrab						install
e2fslibs					install
e2fsprogs					install
eclipse						install
eclipse-jdt					install
eclipse-pde					install
eclipse-platform				install
eclipse-platform-data				install
eclipse-plugin-cvs				install
eclipse-rcp					install
ed						install
eject						install
empathy						install
empathy-common					install
eog						install
erlang-base					install
erlang-crypto					install
erlang-inets					install
erlang-mnesia					install
erlang-public-key				install
erlang-runtime-tools				install
erlang-ssl					install
erlang-syntax-tools				install
erlang-xmerl					install
esound-clients					install
esound-common					install
espeak						install
espeak-data					install
evince						install
evolution					install
evolution-common				install
evolution-couchdb				install
evolution-data-server				install
evolution-data-server-common			install
evolution-exchange				install
evolution-indicator				install
evolution-plugins				install
evolution-webcal				install
exaile						deinstall
example-content					install
exiv2						install
f-spot						deinstall
fakeroot					install
fancontrol					install
fastjar						install
ffmpeg						install
fglrx						install
fglrx-amdcccle					install
fglrx-modaliases				install
file						install
file-roller					install
findutils					install
finger						install
firefox						install
firefox-branding				install
firefox-gnome-support				install
flashplugin-installer				install
fontconfig					install
fontconfig-config				install
foo2zjs						install
foomatic-db					install
foomatic-db-engine				install
foomatic-filters				install
freeglut3					deinstall
freepats					install
frei0r-plugins					install
friendly-recovery				install
ftp						install
fuse-utils					install
g++						install
g++-4.4						install
gamin						install
gawk						install
gbrainy						deinstall
gcalctool					install
gcc						install
gcc-4.4						install
gcc-4.4-base					install
gcc-avr						install
gcj-4.4-base					install
gcj-4.4-jre-lib					install
gconf-defaults-service				install
gconf-editor					install
gconf2						install
gconf2-common					install
gdb						install
gdebi						install
gdebi-core					install
gdebi-kde					install
gdm						install
gdm-guest-session				install
geany						install
gedit						install
gedit-common					install
genisoimage					install
geoip-database					install
gespeaker					install
getdeb-repository				install
gettext						install
gettext-base					install
gettext-kde					install
ghostscript					install
ghostscript-cups				install
ghostscript-x					install
gimp						install
gimp-data					install
gksu						install
gnome-about					install
gnome-accessibility-themes			install
gnome-applets					install
gnome-applets-data				install
gnome-bluetooth					install
gnome-codec-install				install
gnome-control-center				install
gnome-desktop-data				install
gnome-disk-utility				install
gnome-do					install
gnome-do-docklets				install
gnome-do-plugins				install
gnome-doc-utils					install
gnome-games-common				install
gnome-icon-theme				install
gnome-keyring					install
gnome-mag					install
gnome-mahjongg					deinstall
gnome-media					install
gnome-media-common				install
gnome-menus					install
gnome-mime-data					install
gnome-nettool					install
gnome-orca					install
gnome-panel					install
gnome-panel-data				install
gnome-power-manager				install
gnome-screensaver				install
gnome-session					install
gnome-session-bin				install
gnome-session-canberra				install
gnome-settings-daemon				install
gnome-sudoku					deinstall
gnome-system-monitor				install
gnome-system-tools				install
gnome-terminal					install
gnome-terminal-data				install
gnome-themes-selected				install
gnome-themes-ubuntu				install
gnome-user-guide				install
gnome-user-guide-en				install
gnome-user-share				install
gnome-utils					install
gnomine						deinstall
gnupg						install
gnupg-curl					install
gparted						install
gpgv						install
gpodder						install
grep						install
groff-base					install
grub-common					install
grub-pc						install
gsfonts						install
gstreamer0.10-alsa				install
gstreamer0.10-ffmpeg				install
gstreamer0.10-gnonlin				install
gstreamer0.10-nice				install
gstreamer0.10-plugins-bad			install
gstreamer0.10-plugins-bad-multiverse		install
gstreamer0.10-plugins-base			install
gstreamer0.10-plugins-base-apps			install
gstreamer0.10-plugins-good			install
gstreamer0.10-plugins-ugly			install
gstreamer0.10-plugins-ugly-multiverse		install
gstreamer0.10-pulseaudio			install
gstreamer0.10-tools				install
gstreamer0.10-x					install
gtk-recordmydesktop				install
gtk2-engines					install
gtk2-engines-murrine				install
gtk2-engines-pixbuf				install
gucharmap					install
guile-1.8-libs					install
gvfs						install
gvfs-backends					install
gvfs-bin					install
gvfs-fuse					install
gwibber						install
gwibber-service					install
gzip						install
hal						install
hal-info					install
hdparm						install
hicolor-icon-theme				install
hostname					install
hpijs						install
hplip						install
hplip-data					install
hugin						deinstall
hugin-tools					deinstall
human-icon-theme				install
humanity-icon-theme				install
hunspell-en-ca					install
hunspell-en-us					install
hydrogen					deinstall
ia32-libs					install
ibus						install
ibus-gtk					install
ibus-m17n					install
ibus-table					install
icedtea-6-jre-cacao				install
icedtea6-plugin					install
icoutils					install
ifupdown					install
im-switch					install
imagemagick					install
indicator-applet				install
indicator-applet-session			install
indicator-application				install
indicator-me					install
indicator-messages				install
indicator-session				install
indicator-sound					install
info						install
initramfs-tools					install
initramfs-tools-bin				install
initscripts					install
inkscape					install
inputattach					install
insserv						install
install-info					install
install-package					install
intel-gpu-tools					install
intltool-debian					install
iproute						install
iptables					install
iputils-arping					install
iputils-ping					install
iputils-tracepath				install
irqbalance					install
iso-codes					install
istanbul					deinstall
jackd						install
jackd-firewire					install
jarwrapper					install
java-common					install
javahelp2					install
jetty						install
jockey-common					install
jockey-gtk					install
jruby1.1					install
jsvc						install
junit						install
junit4						install
kbd						install
kdebase-runtime					install
kdebase-runtime-data				install
kdebase-workspace-bin				install
kdebase-workspace-data				install
kdebase-workspace-kgreet-plugins		install
kdelibs-bin					install
kdelibs-data					install
kdelibs4-dev					install
kdelibs4c2a					install
kdelibs5					install
kdelibs5-data					install
kdenlive					install
kdenlive-data					install
kdepim-runtime					install
kdepimlibs-data					install
kdepimlibs5					install
kdesdk-scripts					install
kdesudo						install
kerneloops-daemon				install
klibc-utils					install
kpackagekit					install
krb5-multidev					install
ksysguardd					install
kubuntu-debug-installer				install
language-pack-en				install
language-pack-en-base				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
language-selector				install
language-selector-common			install
language-support-en				install
language-support-writing-en			install
laptop-detect					install
launchpad-integration				install
less						install
lftp						install
lib32asound2					install
lib32bz2-1.0					install
lib32gcc1					install
lib32ncurses5					install
lib32nss-mdns					install
lib32stdc++6					install
lib32v4l-0					install
lib32z1						install
liba52-0.7.4					install
libaa1						install
libaa1-dev					install
libaccess-bridge-java				install
libaccess-bridge-java-jni			install
libacl1						install
libacl1-dev					install
libakonadiprivate1				install
libalut0					install
libanthy0					install
libapache2-mod-php5				install
libapparmor-perl				install
libapparmor1					install
libappframework-java				install
libappindicator0				install
libapr1						install
libaprutil1					install
libaprutil1-dbd-sqlite3				install
libaprutil1-ldap				install
libapt-pkg-perl					install
libarchive1					install
libart-2.0-2					install
libart-2.0-dev					install
libart2.0-cil					install
libasm2-java					install
libasm3-java					install
libasound2					install
libasound2-dev					install
libasound2-plugins				install
libaspell-dev					install
libaspell15					install
libass4						install
libatasmart4					install
libatk1.0-0					install
libatk1.0-data					install
libatm1						install
libatspi1.0-0					install
libattica0					install
libattr1					install
libattr1-dev					install
libaubio2					install
libaudclient2					install
libaudcore1					install
libaudid3tag2					install
libaudio-dev					install
libaudio2					install
libaudiofile-dev				install
libaudiofile0					install
libauthen-sasl-perl				install
libavahi-client-dev				install
libavahi-client3				install
libavahi-common-data				install
libavahi-common-dev				install
libavahi-common3				install
libavahi-core6					install
libavahi-glib1					install
libavahi-gobject0				install
libavahi-qt3-1					install
libavahi-qt3-dev				install
libavahi-ui0					install
libavc1394-0					install
libavcodec-extra-52				install
libavcodec52					deinstall
libavdevice52					install
libavfilter0					install
libavformat52					install
libavutil-extra-49				install
libavutil49					deinstall
libbabl-0.0-0					install
libbeagle1					install
libbeansbinding-java				install
libbind9-60					install
libbinio1ldbl					install
libblas3gf					install
libblkid1					install
libbluetooth3					install
libbonobo2-0					install
libbonobo2-common				install
libbonoboui2-0					install
libbonoboui2-common				install
libboost-program-options1.40.0			install
libboost-thread1.40.0				deinstall
libbrasero-media0				install
libbrlapi0.5					install
libbsd0						install
libburn4					install
libbz2-1.0					install
libbz2-dev					install
libc-bin					install
libc-dev-bin					install
libc6						install
libc6-dev					install
libc6-i386					install
libcaca-dev					install
libcaca0					install
libcairo-perl					install
libcairo2					install
libcairomm-1.0-1				install
libcamel1.2-14					install
libcanberra-gtk-module				install
libcanberra-gtk0				install
libcanberra-pulse				install
libcanberra0					install
libcap-ng0					install
libcap2						install
libcdaudio1					install
libcddb2					install
libcdio-cdda0					install
libcdio-paranoia0				install
libcdio10					install
libcdparanoia0					install
libcelt0-0					install
libcheese-gtk18					install
libcinelerra					install
libck-connector0				install
libclass-accessor-perl				install
libclucene0ldbl					install
libclutter-1.0-0				install
libclutter-gtk-0.10-0				install
libcobertura-java				install
libcolamd2.7.1					install
libcomerr2					install
libcommons-beanutils-java			install
libcommons-codec-java				install
libcommons-collections3-java			install
libcommons-compress-java			install
libcommons-daemon-java				install
libcommons-digester-java			install
libcommons-el-java				install
libcommons-httpclient-java			install
libcommons-logging-java				install
libcommons-net-java				install
libcompizconfig0				install
libcouchdb-glib-1.0-2				install
libcroco3					install
libcryptui0					install
libcue1						install
libcups2					install
libcups2-dev					install
libcupscgi1					install
libcupsdriver1					install
libcupsimage2					install
libcupsmime1					install
libcupsppdc1					install
libcurl3					install
libcurl3-gnutls					install
libcv4						install
libcvaux4					install
libcwidget3					install
libdaemon0					install
libdatrie1					install
libdb-je-java					install
libdb4.7-java					install
libdb4.7-java-gcj				install
libdb4.8					install
libdbd-mysql-perl				install
libdbi-perl					install
libdbus-1-3					install
libdbus-1-dev					install
libdbus-glib-1-2				install
libdbusmenu-glib1				install
libdbusmenu-gtk1				install
libdbusmenu-qt2					install
libdc1394-22					install
libdca0						install
libdecoration0					install
libdesktopcouch-glib-1.0-2			install
libdevel-symdump-perl				install
libdevhelp-1-1					deinstall
libdevkit-power-gobject1			install
libdevmapper1.02.1				install
libdirac-encoder0				install
libdirectfb-1.2-0				install
libdirectfb-dev					install
libdirectfb-extra				install
libdjvulibre-text				install
libdjvulibre21					install
libdns64					install
libdotconf1.0					install
libdrm-dev					install
libdrm-intel1					install
libdrm-nouveau1					install
libdrm-radeon1					install
libdrm2						install
libdv4						install
libdvbpsi5					install
libdvdnav4					install
libdvdread4					install
libebackend1.2-0				install
libebml0					install
libebook1.2-9					install
libecal1.2-7					install
libecj-java					install
libedata-book1.2-2				install
libedata-cal1.2-6				install
libedataserver1.2-11				install
libedataserverui1.2-8				install
libedit2					install
libeggdbus-1-0					install
libegroupwise1.2-13				install
libelf1						install
libenca0					install
libenchant1c2a					install
libept0						install
libequinox-osgi-java				install
libesd0						install
libesd0-dev					install
libespeak1					install
libevdocument2					install
libevent-1.4-2					install
libevview2					install
libexchange-storage1.2-3			install
libexempi3					install
libexif12					install
libexiv2-6					install
libexpat1					install
libexpat1-dev					install
libfaac0					install
libfaad2					install
libffado2					install
libffi5						install
libfftw3-3					install
libfile-copy-recursive-perl			install
libflac++6					install
libflac8					install
libflickrnet2.2-cil				install
libflite1					install
libfluidsynth1					install
libfont-afm-perl				install
libfontconfig1					install
libfontconfig1-dev				install
libfontenc1					install
libfreemarker-java				install
libfreetype6					install
libfreetype6-dev				install
libfreezethaw-perl				install
libfribidi0					install
libfs6						install
libftgl2					install
libfuse2					install
libgadu3					install
libgail-common					install
libgail-gnome-module				install
libgail18					install
libgamin0					install
libgavl1					install
libgc1c2					install
libgcc1						install
libgcj-bc					install
libgcj-common					install
libgcj10					install
libgconf2-4					install
libgconf2.0-cil					install
libgconfmm-2.6-1c2				install
libgcr0						install
libgcrypt11					install
libgcrypt11-dev					install
libgd2-xpm					install
libgda-4.0-4					deinstall
libgda-4.0-common				deinstall
libgdata-common					install
libgdata-google1.2-1				install
libgdata1.2-1					install
libgdata1.4-cil					install
libgdata6					install
libgdbm3					install
libgdict-1.0-6					install
libgdiplus					install
libgdl-1-3					deinstall
libgdu-gtk0					install
libgdu0						install
libgee2						install
libgegl-0.0-0					install
libgeoip1					install
libgfortran3					install
libgif4						install
libgimp2.0					install
libgksu2-0					install
libgl1-mesa-dev					install
libgl1-mesa-dri					install
libgl1-mesa-glx					install
libglade2-0					install
libglade2.0-cil					install
libglademm-2.4-1c2a				install
libgladeui-1-9					deinstall
libglew1.5					deinstall
libglib-perl					install
libglib2.0-0					install
libglib2.0-cil					install
libglib2.0-data					install
libglib2.0-dev					install
libglibmm-2.4-1c2a				install
libglitz-glx1					install
libglitz1					install
libglu1-mesa					install
libglu1-mesa-dev				install
libgme0						install
libgmime-2.4-2					install
libgmime2.4-cil					install
libgmp3c2					install
libgnome-bluetooth7				install
libgnome-desktop-2-17				install
libgnome-keyring0				install
libgnome-keyring1.0-cil				install
libgnome-mag2					install
libgnome-media0					install
libgnome-menu2					install
libgnome-pilot2					install
libgnome-vfs2.0-cil				install
libgnome-window-settings1			install
libgnome2-0					install
libgnome2-canvas-perl				install
libgnome2-common				install
libgnome2-perl					install
libgnome2-vfs-perl				install
libgnome2.24-cil				install
libgnomecanvas2-0				install
libgnomecanvas2-common				install
libgnomecanvasmm-2.6-1c2a			install
libgnomecups1.0-1				install
libgnomedesktop2.20-cil				install
libgnomekbd-common				install
libgnomekbd4					install
libgnomepanel2.24-cil				install
libgnomeprint2.2-0				install
libgnomeprint2.2-data				install
libgnomeprintui2.2-0				install
libgnomeprintui2.2-common			install
libgnomeui-0					install
libgnomeui-common				install
libgnomevfs2-0					install
libgnomevfs2-common				install
libgnomevfs2-extra				install
libgnutls-dev					install
libgnutls26					install
libgomp1					install
libgoocanvas-common				install
libgoocanvas3					install
libgp11-0					install
libgpg-error-dev				install
libgpg-error0					install
libgpgme11					install
libgphoto2-2					install
libgphoto2-port0				install
libgpm2						install
libgpod-common					install
libgpod4					install
libgraphite3					install
libgraphviz4					install
libgs8						install
libgsf-1-114					install
libgsf-1-common					install
libgsl0ldbl					install
libgsm1						install
libgssapi-krb5-2				install
libgssdp-1.0-2					install
libgssrpc4					install
libgstfarsight0.10-0				install
libgstreamer-plugins-base0.10-0			install
libgstreamer0.10-0				install
libgtk-vnc-1.0-0				install
libgtk2-perl					install
libgtk2.0-0					install
libgtk2.0-bin					install
libgtk2.0-cil					install
libgtk2.0-common				install
libgtkhtml-editor-common			install
libgtkhtml-editor0				install
libgtkhtml3.14-19				install
libgtkmm-2.4-1c2a				install
libgtksourceview2.0-0				install
libgtksourceview2.0-common			install
libgtkspell0					install
libgtop2-7					install
libgtop2-common					install
libgucharmap7					install
libgudev-1.0-0					install
libgupnp-1.0-3					install
libgupnp-igd-1.0-2				install
libgutenprint2					install
libgvfscommon0					install
libgweather-common				install
libgweather1					install
libhal-storage1					install
libhal1						install
libhamcrest-java				install
libhighgui4					install
libhpmud0					install
libhtml-format-perl				install
libhtml-parser-perl				install
libhtml-tagset-perl				install
libhtml-template-perl				install
libhtml-tree-perl				install
libhunspell-1.2-0				install
libhyphen0					install
libibus1					install
libical0					install
libice-dev					install
libice6						install
libicu42					install
libicu4j-java					install
libid3tag0					install
libidl0						install
libidn11					install
libidn11-dev					install
libido-0.1-0					install
libiec61883-0					install
libieee1284-3					install
libijs-0.35					install
libilmbase-dev					install
libilmbase6					install
libimlib2					install
libimobiledevice0				install
libindicate-gtk2				install
libindicate4					install
libindicator0					install
libini4j-java					install
libio-pty-perl					install
libio-socket-ssl-perl				install
libio-string-perl				install
libio-stringy-perl				install
libiodbc2					install
libipc-run-perl					install
libiptcdata0					install
libisc60					install
libisccc60					install
libisccfg60					install
libiso9660-7					install
libisofs6					install
libiw30						install
libjack0					install
libjasper-dev					install
libjasper-java					install
libjasper1					install
libjaxp1.3-java					install
libjetty-java					install
libjetty-java-doc				install
libjline-java					install
libjna-java					install
libjpeg62					install
libjpeg62-dev					install
libjs-jquery					install
libjsch-java					install
libjson-glib-1.0-0				install
libjtidy-java					install
libjzlib-java					install
libk5crypto3					install
libkadm5clnt-mit7				install
libkadm5srv-mit7				install
libkate1					install
libkdb5-4					install
libkephal4					install
libkeyutils1					install
libkfontinst4					install
libklibc					install
libkpathsea5					install
libkrb5-3					install
libkrb5-dev					install
libkrb5support0					install
libkscreensaver5				install
libksgrd4					install
libkworkspace4					install
liblapack3gf					install
liblash2					install
liblaunchpad-integration1			install
liblaunchpad-integration1.0-cil			install
liblcms1					install
liblcms1-dev					install
libldap-2.4-2					install
liblircclient0					install
liblo7						install
liblocale-gettext-perl				install
liblockfile1					install
liblog4j1.2-java				install
libloudmouth1-0					install
liblouis-data					install
liblouis0					install
liblpint-bonobo0				install
liblrdf0					install
libltdl7					install
liblua5.1-0					install
liblua50					install
liblua50-dev					install
liblualib50					install
liblualib50-dev					install
liblucene2-java					install
liblwres60					install
liblzma1					install
libm17n-0					install
libmad0						install
libmagic1					install
libmagick++2					install
libmagickcore2					install
libmagickcore2-extra				install
libmagickwand2					install
libmailtools-perl				install
libmatroska0					install
libmcs1						install
libmeanwhile1					install
libmetacity-private0				install
libmikmod2					install
libmikmod2-dev					install
libmimic0					install
libmjpegtools-1.9				install
libmldbm-perl					install
libmlt++3					install
libmlt-data					install
libmlt2						install
libmms0						install
libmng-dev					install
libmng1						install
libmodplug0c2					install
libmono-addins-gui0.2-cil			install
libmono-addins0.2-cil				install
libmono-cairo2.0-cil				install
libmono-corlib2.0-cil				install
libmono-data-tds2.0-cil				install
libmono-getoptions2.0-cil			install
libmono-i18n-west2.0-cil			install
libmono-posix2.0-cil				install
libmono-security2.0-cil				install
libmono-sharpzip2.84-cil			install
libmono-sqlite2.0-cil				install
libmono-system-data2.0-cil			install
libmono-system-runtime2.0-cil			install
libmono-system-web2.0-cil			install
libmono-system2.0-cil				install
libmono2.0-cil					install
libmowgli1					install
libmp3lame0					install
libmp4v2-0					install
libmpcdec3					install
libmpeg2-4					install
libmpfr1ldbl					install
libmtp8						install
libmusicbrainz4c2a				install
libmysqlclient16				install
libnautilus-extension1				install
libnb-apisupport1-java				install
libnb-ide12-java				install
libnb-java3-java				install
libnb-javaparser-java				install
libnb-platform-devel-java			install
libnb-platform11-java				install
libnb-svnclientadapter-java			install
libncurses5					install
libncurses5-dev					install
libncursesw5					install
libndesk-dbus-glib1.0-cil			install
libndesk-dbus1.0-cil				install
libneon27-gnutls				install
libnet-daemon-perl				install
libnet-dbus-perl				install
libnet-libidn-perl				install
libnet-ssleay-perl				install
libnewt0.52					install
libnice0					install
libnih-dbus1					install
libnih1						install
libnl1						install
libnm-glib2					install
libnm-util1					install
libnotify0.4-cil				install
libnotify1					install
libnspr4-0d					install
libnss-mdns					install
libnss3-1d					install
libntfs-3g75					install
libntfs10					install
libnunit2.4-cil					install
libofa0						install
libogg-dev					install
libogg0						install
liboil0.3					install
liboobs-1-4					install
libopenal1					install
libopencore-amrnb0				install
libopencore-amrwb0				install
libopenexr-dev					install
libopenexr6					install
libopenjpeg2					install
libopenobex1					install
libopts25					deinstall
liborbit2					install
liborc-0.4-0					install
liboro-java					install
libotf0						install
libpackagekit-glib2-12				install
libpackagekit-qt-12				install
libpam-ck-connector				install
libpam-gnome-keyring				install
libpam-modules					install
libpam-runtime					install
libpam0g					install
libpanel-applet2-0				install
libpango-perl					install
libpango1.0-0					install
libpango1.0-common				install
libpangomm-1.4-1				install
libpano13-1					deinstall
libpaper-utils					install
libpaper1					install
libparse-debcontrol-perl			install
libparse-debianchangelog-perl			install
libparted0debian1				install
libpcap0.8					install
libpci3						install
libpciaccess0					install
libpcre3					install
libpcre3-dev					install
libpcrecpp0					install
libpcsclite1					install
libperl5.10					install
libphonon4					install
libpisock9					install
libpisync1					install
libpixman-1-0					install
libplasma-applet-system-monitor4		install
libplasma-geolocation-interface4		install
libplasma3					install
libplasmaclock4					install
libplasmagenericshell4				install
libplist1					install
libplot2c2					deinstall
libplrpc-perl					install
libplymouth2					install
libpng12-0					install
libpng12-dev					install
libpod-coverage-perl				install
libpolkit-agent-1-0				install
libpolkit-backend-1-0				install
libpolkit-gobject-1-0				install
libpolkit-gtk-1-0				install
libpolkit-qt-1-0				install
libpoppler-glib4				install
libpoppler5					install
libpopt0					install
libportaudio2					install
libportmidi0					deinstall
libpostproc51					install
libprocesscore4					install
libprocessui4					install
libprotobuf5					install
libprotoc5					install
libproxy0					install
libpst4						install
libpth20					install
libpthread-stubs0				install
libpthread-stubs0-dev				install
libpulse-browse0				install
libpulse-dev					install
libpulse-mainloop-glib0				install
libpulse0					install
libpurple-bin					install
libpurple0					install
libpython2.6					install
libqca2						install
libqimageblitz4					install
libqt3-compat-headers				install
libqt3-headers					install
libqt3-mt					install
libqt3-mt-dev					install
libqt4-assistant				install
libqt4-dbus					install
libqt4-designer					install
libqt4-dev					install
libqt4-help					install
libqt4-multimedia				install
libqt4-network					install
libqt4-opengl					install
libqt4-opengl-dev				install
libqt4-qt3support				install
libqt4-script					install
libqt4-scripttools				install
libqt4-sql					install
libqt4-sql-mysql				install
libqt4-svg					install
libqt4-test					install
libqt4-webkit					install
libqt4-xml					install
libqt4-xmlpatterns				install
libqtcore4					install
libqtgui4					install
libquicktime1					install
libraptor1					install
librarian0					install
librasqal2					install
libraw1394-11					install
librdf0						install
libreadline5					install
libreadline6					install
libregexp-java					install
libresid-builder0c2a				install
librpc-xml-perl					install
librsvg2-2					install
librsvg2-2.18-cil				install
librsvg2-common					install
librsync1					deinstall
libsamplerate0					install
libsane						install
libsasl2-2					install
libsasl2-dev					install
libsasl2-modules				install
libschroedinger-1.0-0				install
libsctp1					install
libsdl-image1.2					install
libsdl-image1.2-dev				install
libsdl-mixer1.2					install
libsdl-mixer1.2-dev				install
libsdl-net1.2					install
libsdl-net1.2-dev				install
libsdl1.2-dev					install
libsdl1.2debian					install
libsdl1.2debian-pulseaudio			install
libselinux1					install
libsensors4					install
libsepol1					install
libservlet2.3-java				install
libservlet2.4-java				install
libservlet2.5-java				install
libsexy2					install
libsgutils2-2					install
libshout3					install
libsidplay1					install
libsidplay2					install
libsigc++-2.0-0c2a				install
libsilc-1.1-2					install
libsilcclient-1.1-3				install
libslang2					install
libslang2-dev					install
libslf4j-java					install
libslp1						install
libslv2-9					install
libsm-dev					install
libsm6						install
libsmbclient					install
libsmpeg-dev					install
libsmpeg0					install
libsndfile1					install
libsnmp-base					install
libsnmp15					install
libsolidcontrol4				install
libsolidcontrolifaces4				install
libsoprano4					install
libsoundtouch1c2				install
libsoup-gnome2.4-1				install
libsoup2.4-1					install
libsox-fmt-alsa					install
libsox-fmt-base					install
libsox1a					install
libspectre1					install
libspeechd2					install
libspeex1					install
libspeexdsp1					install
libsqlite0					install
libsqlite3-0					install
libss2						install
libssh-4					install
libssl-dev					install
libssl0.9.8					install
libstartup-notification0			install
libstdc++6					install
libstdc++6-4.4-dev				install
libstk0c2a					install
libstreamanalyzer0				install
libstreams0					install
libsub-name-perl				install
libsvn-java					install
libsvn1						install
libswing-layout-java				install
libswingworker-java				install
libswingx-java					install
libswscale0					install
libsysfs-dev					install
libsysfs2					install
libtag1-vanilla					install
libtag1c2a					install
libtalloc2					install
libtar						install
libtaskmanager4					install
libtasn1-3					install
libtasn1-3-dev					install
libtdb1						install
libtelepathy-farsight0				install
libtelepathy-glib0				install
libterm-readkey-perl				install
libterm-size-perl				install
libtest-pod-perl				install
libtext-charwidth-perl				install
libtext-iconv-perl				install
libtext-wrapi18n-perl				install
libthai-data					install
libthai0					install
libtheora0					install
libtidy-0.99-0					install
libtie-ixhash-perl				install
libtiff4					install
libtiff4-dev					install
libtiffxx0c2					install
libtimedate-perl				install
libtotem-plparser17				install
libtracker-client-0.8-0				install
libts-0.0-0					install
libtwolame0					install
libubuntuone-1.0-1				install
libudev0					install
libunique-1.0-0					install
libupnp3					install
libupower-glib1					install
liburi-perl					install
libusb-0.1-4					install
libusb-1.0-0					install
libusbmuxd1					install
libuuid-perl					install
libuuid1					install
libv4l-0					install
libvala0					deinstall
libvamp-hostsdk3				install
libvamp-sdk2					install
libvcdinfo0					install
libvisual-0.4-0					install
libvisual-0.4-plugins				install
libvlc2						install
libvlccore2					install
libvncserver0					install
libvorbis-dev					install
libvorbis0a					install
libvorbisenc2					install
libvorbisfile3					install
libvte-common					install
libvte9						install
libwavpack1					install
libwbclient0					install
libweather-ion4					install
libwebkit-1.0-2					install
libwebkit-1.0-common				install
libwildmidi0					install
libwmf-bin					install
libwmf0.2-7					install
libwmf0.2-7-gtk					install
libwnck-common					install
libwnck2.20-cil					install
libwnck22					install
libwpd8c2a					install
libwpg-0.1-1					install
libwps-0.1-1					install
libwrap0					install
libwww-perl					install
libwxbase2.8-0					install
libwxgtk2.8-0					install
libx11-6					install
libx11-data					install
libx11-dev					install
libx264-85					install
libx86-1					install
libxapian15					install
libxau-dev					install
libxau6						install
libxaw7						install
libxcb-atom1					install
libxcb-aux0					install
libxcb-event1					install
libxcb-keysyms1					install
libxcb-render-util0				install
libxcb-render0					install
libxcb-shape0					install
libxcb-shm0					install
libxcb-xv0					install
libxcb1						install
libxcb1-dev					install
libxcomposite1					install
libxcursor-dev					install
libxcursor1					install
libxdamage1					install
libxdelta2					install
libxdmcp-dev					install
libxdmcp6					install
libxerces2-java					install
libxext-dev					install
libxext6					install
libxfixes-dev					install
libxfixes3					install
libxfont1					install
libxft-dev					install
libxft2						install
libxi-dev					install
libxi6						install
libxine1					install
libxine1-bin					install
libxine1-console				install
libxine1-misc-plugins				install
libxine1-x					install
libxinerama-dev					install
libxinerama1					install
libxkbfile1					install
libxklavier16					install
libxml++2.6-2					install
libxml-commons-resolver1.1-java			install
libxml-libxml-perl				install
libxml-namespacesupport-perl			install
libxml-parser-perl				install
libxml-sax-expat-perl				install
libxml-sax-perl					install
libxml-twig-perl				install
libxml-xpath-perl				install
libxml2						install
libxml2-dev					install
libxml2-utils					install
libxmu-dev					install
libxmu-headers					install
libxmu6						install
libxmuu1					install
libxp6						install
libxpm4						install
libxrandr-dev					install
libxrandr2					install
libxrender-dev					install
libxrender1					install
libxres1					install
libxslt1-dev					install
libxslt1.1					install
libxss1						install
libxt-dev					install
libxt6						install
libxtst6					install
libxv1						install
libxvidcore4					install
libxvmc1					install
libxxf86dga1					install
libxxf86misc1					install
libxxf86vm1					install
libzephyr4					install
light-themes					install
lintian						install
linux-firmware					install
linux-generic					install
linux-headers-2.6.32-21				install
linux-headers-2.6.32-21-generic			install
linux-headers-2.6.32-22				install
linux-headers-2.6.32-22-generic			install
linux-headers-generic				install
linux-image-2.6.32-21-generic			install
linux-image-2.6.32-22-generic			install
linux-image-generic				install
linux-libc-dev					install
linux-sound-base				install
lksctp-tools					install
lm-sensors					install
lmms						install
lmms-common					install
locales						install
lockfile-progs					install
login						install
logrotate					install
lp-solve					install
lsb-base					install
lsb-release					install
lshw						install
lshw-gtk					deinstall
lsof						install
ltrace						install
lua50						install
lzma						install
m17n-contrib					install
m17n-db						install
m4						install
make						install
makedev						install
man-db						install
manpages					install
manpages-dev					install
mawk						install
mbrola						install
mbrola-de6					install
mbrola-de7					install
mbrola-en1					install
mbrola-it3					install
mbrola-sw2					install
mbrola-us1					install
mbrola-us2					install
media-player-info				install
melt						install
memtest86+					install
mesa-common-dev					install
mesa-utils					install
metacity					install
metacity-common					install
mime-support					install
min12xxw					install
mjpegtools					install
mlocate						install
mobile-broadband-provider-info			install
modemmanager					install
module-init-tools				install
mono-2.0-gac					install
mono-gac					install
mono-runtime					install
mount						install
mountall					install
mousetweaks					install
mscompress					install
mtools						install
mtr-tiny					install
myspell-en-au					install
myspell-en-gb					install
myspell-en-za					install
mysql-client-5.1				install
mysql-client-core-5.1				install
mysql-common					install
mysql-server					install
mysql-server-5.1				install
mysql-server-core-5.1				install
nano						install
nautilus					install
nautilus-bzr					install
nautilus-data					install
nautilus-sendto					install
nautilus-sendto-empathy				install
nautilus-share					install
ncurses-base					install
ncurses-bin					install
net-tools					install
netbase						install
netbeans					install
netcat-openbsd					install
network-manager					install
network-manager-gnome				install
network-manager-pptp				install
network-manager-pptp-gnome			install
notify-osd					install
notify-osd-icons				install
nspluginwrapper					install
ntfs-3g						install
ntfsprogs					install
ntpdate						install
nvidia-173-modaliases				install
nvidia-96-modaliases				install
nvidia-common					install
nvidia-current-modaliases			install
obex-data-server				install
obexd-client					install
onboard						install
openjdk-6-doc					install
openjdk-6-jdk					install
openjdk-6-jre					install
openjdk-6-jre-headless				install
openjdk-6-jre-lib				install
openoffice.org-base-core			install
openoffice.org-calc				install
openoffice.org-common				install
openoffice.org-core				install
openoffice.org-draw				install
openoffice.org-emailmerge			install
openoffice.org-gnome				install
openoffice.org-gtk				install
openoffice.org-help-en-gb			install
openoffice.org-help-en-us			install
openoffice.org-hyphenation			install
openoffice.org-hyphenation-en-us		install
openoffice.org-impress				install
openoffice.org-l10n-common			install
openoffice.org-l10n-en-gb			install
openoffice.org-l10n-en-za			install
openoffice.org-math				install
openoffice.org-style-human			install
openoffice.org-thesaurus-en-au			install
openoffice.org-thesaurus-en-us			install
openoffice.org-writer				install
openprinting-ppds				install
openshot					deinstall
openssh-client					install
openssh-server					install
openssl						install
os-prober					install
oxygen-icon-theme				install
packagekit					install
packagekit-backend-apt				install
parted						install
passwd						install
patch						install
patchutils					install
pbzip2						install
pciutils					install
pcmciautils					install
perl						install
perl-base					install
perl-modules					install
perlmagick					install
phonon						install
phonon-backend-xine				install
php5-common					install
php5-mysql					install
pidgin						deinstall
pidgin-data					deinstall
pitivi						deinstall
pkg-config					install
plasma-dataengines-workspace			install
plasma-scriptengine-javascript			install
plasma-widgets-workspace			install
playonlinux					install
plymouth					install
plymouth-label					install
plymouth-theme-ubuntu-logo			install
plymouth-theme-ubuntu-text			install
plymouth-x11					install
pm-utils					install
pm-utils-powersave-policy			install
pnm2ppa						install
podsleuth					deinstall
policykit-1					install
policykit-1-gnome				install
policykit-desktop-privileges			install
polkit-kde-1					install
poppler-utils					install
popularity-contest				install
postfix						install
powermgmt-base					install
ppp						install
pppconfig					install
pppoeconf					install
pptp-linux					install
pristine-tar					install
procps						install
protobuf-compiler				install
psfontmgr					install
psmisc						install
pulseaudio					install
pulseaudio-esound-compat			install
pulseaudio-module-bluetooth			install
pulseaudio-module-gconf				install
pulseaudio-module-x11				install
pulseaudio-utils				install
pxljr						install
python						install
python-appindicator				install
python-apport					install
python-apt					install
python-aptdaemon				install
python-aptdaemon-gtk				install
python-avahi					install
python-brlapi					install
python-bugbuddy					install
python-cairo					install
python-central					install
python-chardet					install
python-compizconfig				install
python-configglue				install
python-configobj				install
python-couchdb					install
python-crypto					install
python-cups					install
python-cupshelpers				install
python-dbus					install
python-debian					install
python-desktopcouch				install
python-desktopcouch-records			install
python-docky					install
python-egenix-mxdatetime			install
python-egenix-mxtools				install
python-evince					install
python-evolution				install
python-farsight					install
python-feedparser				install
python-fstab					install
python-gconf					install
python-gdbm					install
python-glade2					install
python-gmenu					install
python-gnome2					install
python-gnome2-desktop				install
python-gnomeapplet				install
python-gnomecanvas				install
python-gnomedesktop				install
python-gnomekeyring				install
python-gnomeprint				install
python-gnupginterface				install
python-gobject					install
python-gpod					install
python-gst0.10					install
python-gtk2					install
python-gtksourceview2				install
python-gtkspell					install
python-gtop					install
python-httplib2					install
python-ibus					install
python-imaging					install
python-indicate					install
python-kde4					install
python-launchpad-integration			install
python-launchpadlib				install
python-lazr.restfulclient			install
python-lazr.uri					install
python-libxml2					install
python-louis					install
python-lxml					install
python-mako					install
python-mediaprofiles				install
python-metacity					install
python-minimal					install
python-mutagen					install
python-mygpoclient				install
python-nautilus					install
python-newt					install
python-notify					install
python-numpy					install
python-oauth					install
python-openssl					install
python-packagekit				install
python-pam					install
python-papyon					install
python-paramiko					install
python-pexpect					install
python-pkg-resources				install
python-problem-report				install
python-protobuf					install
python-pyasn1					install
python-pyatspi					install
python-pycurl					install
python-pygments					install
python-pygoocanvas				install
python-pyinotify				install
python-pymtp					install
python-pyorbit					install
python-qt4					install
python-rdflib					install
python-renderpm					install
python-reportlab				install
python-reportlab-accel				install
python-rsvg					install
python-serial					install
python-simplejson				install
python-sip					install
python-smbc					install
python-software-properties			install
python-speechd					install
python-support					install
python-telepathy				install
python-totem-plparser				install
python-twisted					install
python-twisted-bin				install
python-twisted-conch				install
python-twisted-core				install
python-twisted-lore				install
python-twisted-mail				install
python-twisted-names				install
python-twisted-news				install
python-twisted-runner				install
python-twisted-web				install
python-twisted-words				install
python-ubuntuone				install
python-ubuntuone-client				install
python-ubuntuone-storageprotocol		install
python-uniconvertor				install
python-uno					install
python-utidylib					install
python-virtkey					install
python-vte					install
python-wadllib					install
python-webkit					install
python-wnck					install
python-wxgtk2.8					install
python-wxversion				install
python-xapian					install
python-xdg					install
python-xkit					install
python-zope.interface				install
python2.6					install
python2.6-minimal				install
qbzr						install
qjackctl					install
qt3-dev-tools					install
qt4-qmake					install
quadrapassel					deinstall
radeontool					install
rarian-compat					install
rdesktop					install
readline-common					install
realpath					install
recordmydesktop					install
rhythmbox					install
rhythmbox-plugin-cdrecorder			install
rhythmbox-plugins				install
rhythmbox-ubuntuone-music-store			install
rsync						install
rsyslog						install
rtkit						install
samba-common					install
samba-common-bin				install
sane-utils					install
sat4j						install
screen						install
screen-resolution-extra				install
screensaver-default-images			install
seahorse					install
sed						install
sensible-utils					install
sgml-base					install
sgml-data					install
shared-desktop-ontologies			install
shared-mime-info				install
shotwell					install
simple-ccsm					install
simple-scan					install
skype						install
slv2-jack					install
smartdimmer					install
smbclient					install
software-center					install
software-properties-gtk				install
software-properties-kde				install
soprano-daemon					install
speech-dispatcher				install
spideroak					install
splix						install
ssh-askpass-gnome				install
ssl-cert					install
stk						install
strace						install
subversion					install
sudo						install
swh-plugins					install
synaptic					install
syslinux					install
system-config-printer-common			install
system-config-printer-gnome			install
system-config-printer-udev			install
system-tools-backends				install
sysv-rc						install
sysvinit-utils					install
tango-icon-theme				install
tap-plugins					install
tar						install
tasksel						install
tasksel-data					install
tcl						install
tcl8.4						install
tcpd						install
tcpdump						install
telepathy-butterfly				install
telepathy-gabble				install
telepathy-haze					install
telepathy-idle					install
telepathy-mission-control-5			install
telepathy-salut					install
telnet						install
time						install
tk						install
tk8.4						install
tomboy						install
toshset						install
totem						deinstall
totem-common					install
transmission-common				install
transmission-gtk				install
tsclient					install
tsconf						install
ttf-dejavu					install
ttf-dejavu-core					install
ttf-dejavu-extra				install
ttf-droid					install
ttf-freefont					install
ttf-indic-fonts-core				install
ttf-kacst-one					install
ttf-khmeros-core				install
ttf-lao						install
ttf-liberation					install
ttf-mscorefonts-installer			install
ttf-opensymbol					install
ttf-punjabi-fonts				install
ttf-symbol-replacement				install
ttf-takao-pgothic				install
ttf-thai-tlwg					install
ttf-unfonts-core				install
ttf-wqy-microhei				install
tzdata						install
tzdata-java					install
ubufox						install
ubuntu-artwork					install
ubuntu-docs					install
ubuntu-keyring					install
ubuntu-minimal					install
ubuntu-mono					install
ubuntu-restricted-extras			install
ubuntu-sounds					install
ubuntu-standard					install
ubuntu-system-service				install
ubuntu-tweak					install
ubuntu-wallpapers				install
ubuntuone-client				install
ubuntuone-client-gnome				install
ucf						install
udev						install
udisks						install
ufw						install
unattended-upgrades				install
unison						install
unison-gtk					install
uno-libs3					install
unrar						install
unzip						install
update-inetd					install
update-manager					install
update-manager-core				install
update-manager-kde				install
update-notifier					install
update-notifier-common				install
upower						install
upstart						install
ure						install
ureadahead					install
usb-creator-common				install
usb-creator-gtk					install
usbmuxd						install
usbutils					install
util-linux					install
uuid-runtime					install
v86d						install
vbetool						install
viewnior					install
vim-common					install
vim-tiny					install
vinagre						install
vino						install
virtualbox-ose					install
virtualbox-ose-dkms				install
virtualbox-ose-qt				install
virtuoso-nepomuk				install
vlc						install
vlc-data					install
vlc-nox						install
vlc-plugin-pulse				install
w3m						install
wamerican					install
wbritish					install
wdiff						install
wget						install
whiptail					install
whois						install
winbind						install
wine1.2						install
wine1.2-gecko					install
wireless-crda					install
wireless-tools					install
wodim						install
wpasupplicant					install
x-ttcidfont-conf				install
x11-apps					install
x11-common					install
x11-session-utils				install
x11-utils					install
x11-xfs-utils					install
x11-xkb-utils					install
x11-xserver-utils				install
x11proto-core-dev				install
x11proto-fixes-dev				install
x11proto-input-dev				install
x11proto-kb-dev					install
x11proto-randr-dev				install
x11proto-render-dev				install
x11proto-xext-dev				install
x11proto-xinerama-dev				install
x11vnc						install
xauth						install
xbitmaps					install
xchat-gnome					install
xchat-gnome-common				install
xcursor-themes					install
xdelta						install
xdg-user-dirs					install
xdg-user-dirs-gtk				install
xdg-utils					install
xfonts-100dpi					install
xfonts-75dpi					install
xfonts-base					install
xfonts-encodings				install
xfonts-mathml					install
xfonts-scalable					install
xfonts-utils					install
xinit						install
xinput						install
xkb-data					install
xml-core					install
xorg						install
xorg-docs-core					install
xscreensaver-data				install
xscreensaver-gl					install
xserver-common					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-mouse			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-vmmouse			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-apm				install
xserver-xorg-video-ark				install
xserver-xorg-video-ati				install
xserver-xorg-video-chips			install
xserver-xorg-video-cirrus			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-i128				install
xserver-xorg-video-intel			install
xserver-xorg-video-mach64			install
xserver-xorg-video-mga				install
xserver-xorg-video-neomagic			install
xserver-xorg-video-nouveau			install
xserver-xorg-video-nv				install
xserver-xorg-video-openchrome			install
xserver-xorg-video-r128				install
xserver-xorg-video-radeon			install
xserver-xorg-video-rendition			install
xserver-xorg-video-s3				install
xserver-xorg-video-s3virge			install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-trident			install
xserver-xorg-video-tseng			install
xserver-xorg-video-v4l				install
xserver-xorg-video-vesa				install
xserver-xorg-video-vmware			install
xserver-xorg-video-voodoo			install
xsltproc					install
xterm						install
xtrans-dev					install
xulrunner-1.9.2					install
xz-utils					install
yelp						install
zenity						install
zip						install
zlib1g						install
zlib1g-dev					install
```

---

