---
title: "Toshiba Satellite L875D, 12.04.1 total system freeze"
date: 2012-10-11
forum: General Help
---

### Post by Jakin on 2012-10-11
I recently purchased a Toshiba Satellite and running system 12.04.1 amd 64 (Kubuntu KDE 4.9.1 if that makes a difference) the system is smooth, i couldn't be more happier with it. Until however it has this habit of randomly (or that i can tell random) freezing, with the mouse and keyboard unresponsive. All i can do is hold down the power button to force a reboot.

I have been scratching my head, looking about the internet for insight, but i can't find anything; Or don't know how to search correctly- it's one of the two.

Has anyone run into this problem? Got a fix? 

Here are my specs:

```
joey@joey-HP:~$ sudo lshw
[sudo] password for joey: 
joey-hp                   
    description: Notebook
    product: Satellite L875D (PSKBQU-009004)
    vendor: TOSHIBA
    version: PSKBQU-009004
    serial: 6C281947R
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=Type1Family sku=PSKBQU-009004 uuid=002A9891-1C4C-E281-3DDD-4C72B939E5B5
  *-core
       description: Motherboard
       product: Pumori
       vendor: AMD
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 1.10
          date: 04/20/2012
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD A6-4400M APU with Radeon(tm) HD Graphics
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD A6-4400M APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FT1
          size: 2700MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 96KiB
             capacity: 96KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 533 MHz (1.9 ns)
             product: CM3X4GSD1066
             physical id: 0
             serial: 00000000
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: M471B5273DH0-CK0
             vendor: Samsung
             physical id: 1
             serial: C1F4D1E3
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Advanced Micro Devices [AMD] nee ATI
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:48 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff
        *-multimedia:0 UNCLAIMED
             description: Audio device
             product: Advanced Micro Devices [AMD] nee ATI
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi cap_list
             configuration: latency=0
             resources: memory:f0344000-f0347fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f0200000-f02fffff
           *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan1
                version: 00
                serial: 74:e5:43:24:8d:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723e driverversion=3.2.0-31-generic firmware=N/A ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 ioport:3000(size=256) memory:f0200000-f0203fff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f0100000-f01fffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth2
                version: 05
                serial: 4c:72:b9:39:e5:b5
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:46 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
        *-usb:0
             description: USB controller
             product: Hudson USB XHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0348000-f0349fff
        *-usb:1
             description: USB controller
             product: Hudson USB XHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:f034a000-f034bfff
        *-storage
             description: SATA controller
             product: Hudson SATA Controller [AHCI mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:19 ioport:4118(size=8) ioport:4124(size=4) ioport:4110(size=8) ioport:4120(size=4) ioport:4100(size=16) memory:f0351000-f03517ff
           *-disk
                description: ATA Disk
                product: ST95005620AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD28
                serial: 5YX1CNG4
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000eea31
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 34a6-ec88
                   size: 59GiB
                   capacity: 59GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-10-06 12:56:55 filesystem=ntfs state=clean
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   capacity: 60GiB
                   capabilities: primary bootable
                   configuration: mount.fstype=jfs mount.options=rw,relatime state=mounted
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /media/DATA
                   version: 3.1
                   serial: e81b9705-f56a-4404-91a8-aca90a663303
                   size: 345GiB
                   capacity: 345GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-06-27 16:16:10 filesystem=ntfs label=DATA mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SN-208AB
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: TO03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:2
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f0350000-f0350fff
        *-usb:3
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f034f000-f034f0ff
        *-usb:4
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f034e000-f034efff
        *-usb:5
             description: USB controller
             product: Hudson USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f034d000-f034d0ff
        *-serial UNCLAIMED
             description: SMBus
             product: Hudson SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: Hudson Azalia Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:47 memory:f0340000-f0343fff
        *-isa
             description: ISA bridge
             product: Hudson LPC Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: Hudson PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: Hudson USB OHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f034c000-f034cfff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
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
          product: Family 15h (Models 10h-1fh) Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz

```

```
joey@joey-HP:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9990
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```


KERNEL LOG
```

10/11/12 04:02:01 PM	pci 0000	0:14.2: PME# disabled
10/11/12 04:02:01 PM	pci 0000	0:14.3: [1022:780e] type 0 class 0x000601
10/11/12 04:02:01 PM	pci 0000	0:14.4: [1022:780f] type 1 class 0x000604
10/11/12 04:02:01 PM	pci 0000	0:14.5: [1022:7809] type 0 class 0x000c03
10/11/12 04:02:01 PM	pci 0000	0:14.5: reg 10: [mem 0xf034c000-0xf034cfff]
10/11/12 04:02:01 PM	pci 0000	0:18.0: [1022:1400] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	0:18.1: [1022:1401] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	0:18.2: [1022:1402] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	0:18.3: [1022:1403] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	0:18.4: [1022:1404] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	0:18.5: [1022:1405] type 0 class 0x000600
10/11/12 04:02:01 PM	pci 0000	1:00.0: [10ec:8723] type 0 class 0x000280
10/11/12 04:02:01 PM	pci 0000	1:00.0: reg 10: [io 0x3000-0x30ff]
10/11/12 04:02:01 PM	pci 0000	1:00.0: reg 18: [mem 0xf0200000-0xf0203fff 64bit]
10/11/12 04:02:01 PM	pci 0000	1:00.0: supports D1 D2
10/11/12 04:02:01 PM	pci 0000	1:00.0: PME# supported from D0 D1 D2 D3hot D3cold
10/11/12 04:02:01 PM	pci 0000	1:00.0: PME# disabled
10/11/12 04:02:01 PM	pci 0000	0:04.0: PCI bridge to [bus 01-01]
10/11/12 04:02:01 PM	pci 0000	0:04.0: bridge window [io 0x3000-0x3fff]
10/11/12 04:02:01 PM	pci 0000	0:04.0: bridge window [mem 0xf0200000-0xf02fffff]
10/11/12 04:02:01 PM	pci 0000	2:00.0: [10ec:8136] type 0 class 0x000200
10/11/12 04:02:01 PM	pci 0000	2:00.0: reg 10: [io 0x2000-0x20ff]
10/11/12 04:02:01 PM	pci 0000	2:00.0: reg 18: [mem 0xf0004000-0xf0004fff 64bit pref]
10/11/12 04:02:01 PM	pci 0000	2:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
10/11/12 04:02:01 PM	pci 0000	2:00.0: supports D1 D2
10/11/12 04:02:01 PM	pci 0000	2:00.0: PME# supported from D0 D1 D2 D3hot D3cold
10/11/12 04:02:01 PM	pci 0000	2:00.0: PME# disabled
10/11/12 04:02:01 PM	pci 0000	0:07.0: PCI bridge to [bus 02-05]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [io 0x2000-0x2fff]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [mem 0xf0100000-0xf01fffff]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
10/11/12 04:02:01 PM	pci 0000	0:14.4: PCI bridge to [bus 06-06] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [io 0x0000-0x0cf7] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [io 0x0d00-0xffff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
10/11/12 04:02:01 PM	pci 0000	0:14.4: bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
10/11/12 04:02:01 PM	 pci0000	0: Requesting ACPI _OSC control (0x1d)
10/11/12 04:02:01 PM	 pci0000	0: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
10/11/12 04:02:01 PM		ACPI _OSC control for PCIe not granted, disabling ASPM
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	ACPI	PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
10/11/12 04:02:01 PM	vgaarb	device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
10/11/12 04:02:01 PM	vgaarb	loaded
10/11/12 04:02:01 PM	vgaarb	bridge control possible 0000:00:01.0
10/11/12 04:02:01 PM	i2c-core	driver [aat2870] using legacy suspend method
10/11/12 04:02:01 PM	i2c-core	driver [aat2870] using legacy resume method
10/11/12 04:02:01 PM		SCSI subsystem initialized
10/11/12 04:02:01 PM		libata version 3.00 loaded.
10/11/12 04:02:01 PM	usbcore	registered new interface driver usbfs
10/11/12 04:02:01 PM	usbcore	registered new interface driver hub
10/11/12 04:02:01 PM	usbcore	registered new device driver usb
10/11/12 04:02:01 PM	PCI	Using ACPI for IRQ routing
10/11/12 04:02:01 PM	PCI	pci_cache_line_size set to 64 bytes
10/11/12 04:02:01 PM	reserve RAM buffer	000000000009f800 - 000000000009ffff
10/11/12 04:02:01 PM	reserve RAM buffer	00000000bf6bf000 - 00000000bfffffff
10/11/12 04:02:01 PM	reserve RAM buffer	00000000bfc00000 - 00000000bfffffff
10/11/12 04:02:01 PM	reserve RAM buffer	000000021f000000 - 000000021fffffff
10/11/12 04:02:01 PM	NetLabel	Initializing
10/11/12 04:02:01 PM	NetLabel	domain hash size = 128
10/11/12 04:02:01 PM	NetLabel	protocols = UNLABELED CIPSOv4
10/11/12 04:02:01 PM	NetLabel	unlabeled traffic allowed by default
10/11/12 04:02:01 PM	hpet0	at MMIO 0xfed00000, IRQs 2, 8, 0
10/11/12 04:02:01 PM	hpet0	3 comparators, 32-bit 14.318180 MHz counter
10/11/12 04:02:01 PM		Switching to clocksource hpet
10/11/12 04:02:01 PM	AppArmor	AppArmor Filesystem Enabled
10/11/12 04:02:01 PM	pnp	PnP ACPI init
10/11/12 04:02:01 PM	ACPI	bus type pnp registered
10/11/12 04:02:01 PM	pnp 00	0: [bus 00-ff]
10/11/12 04:02:01 PM	pnp 00	0: [io 0x0000-0x0cf7 window]
10/11/12 04:02:01 PM	pnp 00	0: [io 0x0d00-0xffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000a0000-0x000bffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000c0000-0x000c3fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000c4000-0x000c7fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000c8000-0x000cbfff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000cc000-0x000cffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000d0000-0x000d3fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000d4000-0x000d7fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000d8000-0x000dbfff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000dc000-0x000dffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000e0000-0x000e3fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000e4000-0x000e7fff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000e8000-0x000ebfff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0x000ec000-0x000effff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0xe0000000-0xf7ffffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0xfc000000-0xfed3ffff window]
10/11/12 04:02:01 PM	pnp 00	0: [mem 0xfed45000-0xffffffff window]
10/11/12 04:02:01 PM	pnp 00	0: [io 0x0cf8-0x0cff]
10/11/12 04:02:01 PM	pnp 00	0: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
10/11/12 04:02:01 PM	pnp 00	1: [mem 0xfec00000-0xfec00fff]
10/11/12 04:02:01 PM	pnp 00	1: [mem 0xfee00000-0xfee00fff]
10/11/12 04:02:01 PM	system 00	1: [mem 0xfec00000-0xfec00fff] could not be reserved
10/11/12 04:02:01 PM	system 00	1: [mem 0xfee00000-0xfee00fff] has been reserved
10/11/12 04:02:01 PM	system 00	1: Plug and Play ACPI device, IDs PNP0c02 (active)
10/11/12 04:02:01 PM	pnp 00	2: [irq 0 disabled]
10/11/12 04:02:01 PM	pnp 00	2: [irq 8]
10/11/12 04:02:01 PM	pnp 00	2: [mem 0xfed00000-0xfed003ff]
10/11/12 04:02:01 PM	pnp 00	2: Plug and Play ACPI device, IDs PNP0103 (active)
10/11/12 04:02:01 PM	pnp 00	3: [io 0x0000-0x000f]
10/11/12 04:02:01 PM	pnp 00	3: [io 0x0081-0x008f]
10/11/12 04:02:01 PM	pnp 00	3: [io 0x00c0-0x00df]
10/11/12 04:02:01 PM	pnp 00	3: [dma 4]
10/11/12 04:02:01 PM	pnp 00	3: Plug and Play ACPI device, IDs PNP0200 (active)
10/11/12 04:02:01 PM	pnp 00	4: [io 0x00f0-0x00fe]
10/11/12 04:02:01 PM	pnp 00	4: [irq 13]
10/11/12 04:02:01 PM	pnp 00	4: Plug and Play ACPI device, IDs PNP0c04 (active)
10/11/12 04:02:01 PM	pnp 00	5: [io 0x0070-0x0071]
10/11/12 04:02:01 PM	pnp 00	5: Plug and Play ACPI device, IDs PNP0b00 (active)
10/11/12 04:02:01 PM	pnp 00	6: [io 0x0061]
10/11/12 04:02:01 PM	pnp 00	6: Plug and Play ACPI device, IDs PNP0800 (active)
10/11/12 04:02:01 PM	pnp 00	7: [io 0x0060]
10/11/12 04:02:01 PM	pnp 00	7: [io 0x0064]
10/11/12 04:02:01 PM	pnp 00	7: [irq 1]
10/11/12 04:02:01 PM	pnp 00	7: Plug and Play ACPI device, IDs PNP0303 (active)
10/11/12 04:02:01 PM	pnp 00	8: [irq 12]
10/11/12 04:02:01 PM	pnp 00	8: Plug and Play ACPI device, IDs TOS0310 SYN1d00 SYN0002 PNP0f13 (active)
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0010-0x001f]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x002e-0x002f]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0072-0x0073]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0080]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x00b0-0x00b1]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0092]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x025c-0x025d]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0400-0x04cf]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x04d0-0x04d1]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x04d6]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0550-0x0551]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0680-0x06ff]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x077a]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0c00-0x0c01]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0c14]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0c50-0x0c52]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0c6c]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0c6f]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0cd0-0x0cdb]
10/11/12 04:02:01 PM	pnp 00	9: [io 0x0840-0x0847]
10/11/12 04:02:01 PM	system 00	9: [io 0x025c-0x025d] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0400-0x04cf] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x04d0-0x04d1] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x04d6] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0550-0x0551] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0680-0x06ff] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x077a] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0c00-0x0c01] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0c14] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0c50-0x0c52] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0c6c] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0c6f] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0cd0-0x0cdb] has been reserved
10/11/12 04:02:01 PM	system 00	9: [io 0x0840-0x0847] has been reserved
10/11/12 04:02:01 PM	system 00	9: Plug and Play ACPI device, IDs PNP0c02 (active)
10/11/12 04:02:01 PM	pnp 00	a: [mem 0x000e0000-0x000fffff]
10/11/12 04:02:01 PM	pnp 00	a: [mem 0xffe00000-0xffffffff]
10/11/12 04:02:01 PM	system 00	a: [mem 0x000e0000-0x000fffff] could not be reserved
10/11/12 04:02:01 PM	system 00	a: [mem 0xffe00000-0xffffffff] has been reserved
10/11/12 04:02:01 PM	system 00	a: Plug and Play ACPI device, IDs PNP0c01 (active)
10/11/12 04:02:01 PM	pnp	PnP ACPI: found 11 devices
10/11/12 04:02:01 PM	ACPI	ACPI bus type pnp unregistered
10/11/12 04:02:01 PM	PCI	max bus depth: 1 pci_try_num: 2
10/11/12 04:02:01 PM	pci 0000	0:04.0: PCI bridge to [bus 01-01]
10/11/12 04:02:01 PM	pci 0000	0:04.0: bridge window [io 0x3000-0x3fff]
10/11/12 04:02:01 PM	pci 0000	0:04.0: bridge window [mem 0xf0200000-0xf02fffff]
10/11/12 04:02:01 PM	pci 0000	0:07.0: PCI bridge to [bus 02-05]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [io 0x2000-0x2fff]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [mem 0xf0100000-0xf01fffff]
10/11/12 04:02:01 PM	pci 0000	0:07.0: bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
10/11/12 04:02:01 PM	pci 0000	0:14.4: PCI bridge to [bus 06-06]
10/11/12 04:02:01 PM	pci 0000	0:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
10/11/12 04:02:01 PM	pci 0000	0:04.0: setting latency timer to 64
10/11/12 04:02:01 PM	pci 0000	0:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
10/11/12 04:02:01 PM	pci 0000	0:07.0: setting latency timer to 64
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 4 [io 0x0000-0x0cf7]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 5 [io 0x0d00-0xffff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 6 [mem 0x000a0000-0x000bffff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 7 [mem 0x000c0000-0x000c3fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 8 [mem 0x000c4000-0x000c7fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 9 [mem 0x000c8000-0x000cbfff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 10 [mem 0x000d0000-0x000d3fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 11 [mem 0x000d4000-0x000d7fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 12 [mem 0x000d8000-0x000dbfff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 13 [mem 0x000dc000-0x000dffff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 14 [mem 0x000e0000-0x000e3fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 15 [mem 0x000e4000-0x000e7fff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 16 [mem 0x000e8000-0x000ebfff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 17 [mem 0x000ec000-0x000effff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 18 [mem 0xe0000000-0xf7ffffff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 19 [mem 0xfc000000-0xfed3ffff]
10/11/12 04:02:01 PM	pci_bus 0000	0: resource 20 [mem 0xfed45000-0xffffffff]
10/11/12 04:02:01 PM	pci_bus 0000	1: resource 0 [io 0x3000-0x3fff]
10/11/12 04:02:01 PM	pci_bus 0000	1: resource 1 [mem 0xf0200000-0xf02fffff]
10/11/12 04:02:01 PM	pci_bus 0000	2: resource 0 [io 0x2000-0x2fff]
10/11/12 04:02:01 PM	pci_bus 0000	2: resource 1 [mem 0xf0100000-0xf01fffff]
10/11/12 04:02:01 PM	pci_bus 0000	2: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 4 [io 0x0000-0x0cf7]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 5 [io 0x0d00-0xffff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 6 [mem 0x000a0000-0x000bffff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 7 [mem 0x000c0000-0x000c3fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 8 [mem 0x000c4000-0x000c7fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 9 [mem 0x000c8000-0x000cbfff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 10 [mem 0x000d0000-0x000d3fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 11 [mem 0x000d4000-0x000d7fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 12 [mem 0x000d8000-0x000dbfff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 13 [mem 0x000dc000-0x000dffff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 14 [mem 0x000e0000-0x000e3fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 15 [mem 0x000e4000-0x000e7fff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 16 [mem 0x000e8000-0x000ebfff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 17 [mem 0x000ec000-0x000effff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 18 [mem 0xe0000000-0xf7ffffff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 19 [mem 0xfc000000-0xfed3ffff]
10/11/12 04:02:01 PM	pci_bus 0000	6: resource 20 [mem 0xfed45000-0xffffffff]
10/11/12 04:02:01 PM	NET	Registered protocol family 2
10/11/12 04:02:01 PM		IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
10/11/12 04:02:01 PM		TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
10/11/12 04:02:01 PM		TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
10/11/12 04:02:01 PM	TCP	Hash tables configured (established 524288 bind 65536)
10/11/12 04:02:01 PM		TCP reno registered
10/11/12 04:02:01 PM		UDP hash table entries: 4096 (order: 5, 131072 bytes)
10/11/12 04:02:01 PM		UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
10/11/12 04:02:01 PM	NET	Registered protocol family 1
10/11/12 04:02:01 PM	pci 0000	0:01.0: Boot video device
10/11/12 04:02:01 PM	pci 0000	0:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:01 PM	pci 0000	0:10.0: PCI INT A disabled
10/11/12 04:02:01 PM	pci 0000	0:10.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:01 PM	pci 0000	0:10.1: PCI INT B disabled
10/11/12 04:02:01 PM	pci 0000	0:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:01 PM	pci 0000	0:12.0: PCI INT A disabled
10/11/12 04:02:01 PM	pci 0000	0:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:01 PM	pci 0000	0:12.2: PCI INT B disabled
10/11/12 04:02:01 PM	pci 0000	0:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:01 PM	pci 0000	0:13.0: PCI INT A disabled
10/11/12 04:02:01 PM	pci 0000	0:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:01 PM	pci 0000	0:13.2: PCI INT B disabled
10/11/12 04:02:01 PM	pci 0000	0:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:02 PM	pci 0000	0:14.5: PCI INT C disabled
10/11/12 04:02:02 PM	PCI	CLS 64 bytes, default 64
10/11/12 04:02:02 PM	PCI-DMA	Using software bounce buffering for IO (SWIOTLB)
10/11/12 04:02:02 PM		Placing 64MB software IO TLB between ffff8800bb6bd000 - ffff8800bf6bd000
10/11/12 04:02:02 PM		software IO TLB at phys 0xbb6bd000 - 0xbf6bd000
10/11/12 04:02:02 PM		Simple Boot Flag at 0x44 set to 0x1
10/11/12 04:02:02 PM	[Firmware Bug]	cpu 0, try to use APIC500 (LVT offset 0) for vector 0x10400, but the register is already in use for vector 0xf9 on another cpu
10/11/12 04:02:02 PM	[Firmware Bug]	cpu 0, IBS interrupt offset 0 not available (MSRC001103A=0x0000000000000100)
10/11/12 04:02:02 PM		Failed to setup IBS, -22
10/11/12 04:02:02 PM	audit	initializing netlink socket (disabled)
10/11/12 04:02:02 PM		type=2000 audit(1349971320.168:1): initialized
10/11/12 04:02:02 PM		HugeTLB registered 2 MB page size, pre-allocated 0 pages
10/11/12 04:02:02 PM	VFS	Disk quotas dquot_6.5.2
10/11/12 04:02:02 PM		Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
10/11/12 04:02:02 PM		fuse init (API version 7.17)
10/11/12 04:02:02 PM		msgmni has been set to 14907
10/11/12 04:02:02 PM		Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
10/11/12 04:02:02 PM		io scheduler noop registered
10/11/12 04:02:02 PM		io scheduler deadline registered
10/11/12 04:02:02 PM		io scheduler cfq registered (default)
10/11/12 04:02:02 PM	pci_hotplug	PCI Hot Plug PCI Core version: 0.5
10/11/12 04:02:02 PM	pciehp	PCI Express Hot Plug Controller Driver version: 0.4
10/11/12 04:02:02 PM	ACPI	Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
10/11/12 04:02:02 PM	ACPI	AC Adapter [AC0] (on-line)
10/11/12 04:02:02 PM	input	Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
10/11/12 04:02:02 PM	ACPI	Power Button [PWRB]
10/11/12 04:02:02 PM	input	Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
10/11/12 04:02:02 PM	ACPI	Lid Switch [LID]
10/11/12 04:02:02 PM	input	Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
10/11/12 04:02:02 PM	ACPI	Power Button [PWRF]
10/11/12 04:02:02 PM	ACPI	Fan [Z0F0] (off)
10/11/12 04:02:02 PM	ACPI	Fan [Z0F1] (off)
10/11/12 04:02:02 PM	ACPI	Fan [Z0F2] (off)
10/11/12 04:02:02 PM	ACPI	Fan [Z0F3] (off)
10/11/12 04:02:02 PM	ACPI	acpi_idle registered with cpuidle
10/11/12 04:02:02 PM	thermal LNXTHERM	0: registered as thermal_zone0
10/11/12 04:02:02 PM	ACPI	Thermal Zone [THZ0] (74 C)
10/11/12 04:02:02 PM	ACPI	Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
10/11/12 04:02:02 PM	ACPI	Battery Slot [BAT0] (battery present)
10/11/12 04:02:02 PM	ERST	Table is not found!
10/11/12 04:02:02 PM	GHES	HEST is not enabled!
10/11/12 04:02:02 PM	Serial	8250/16550 driver, 32 ports, IRQ sharing enabled
10/11/12 04:02:02 PM	ACPI	Battery Slot [BAT0] (battery present)
10/11/12 04:02:02 PM		Linux agpgart interface v0.103
10/11/12 04:02:02 PM	brd	module loaded
10/11/12 04:02:02 PM	loop	module loaded
10/11/12 04:02:02 PM	ahci 0000	0:11.0: version 3.0
10/11/12 04:02:02 PM	ahci 0000	0:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
10/11/12 04:02:02 PM	ahci 0000	0:11.0: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0xb impl SATA mode
10/11/12 04:02:02 PM	ahci 0000	0:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part sxs
10/11/12 04:02:02 PM	scsi0 	ahci
10/11/12 04:02:02 PM	scsi1 	ahci
10/11/12 04:02:02 PM	scsi2 	ahci
10/11/12 04:02:02 PM	scsi3 	ahci
10/11/12 04:02:02 PM	ata1	SATA max UDMA/133 abar m2048@0xf0351000 port 0xf0351100 irq 19
10/11/12 04:02:02 PM	ata2	SATA max UDMA/133 abar m2048@0xf0351000 port 0xf0351180 irq 19
10/11/12 04:02:02 PM	ata3	DUMMY
10/11/12 04:02:02 PM	ata4	SATA max UDMA/133 abar m2048@0xf0351000 port 0xf0351280 irq 19
10/11/12 04:02:02 PM	Fixed MDIO Bus	probed
10/11/12 04:02:02 PM	tun	Universal TUN/TAP device driver, 1.6
10/11/12 04:02:02 PM	tun	(C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
10/11/12 04:02:02 PM		PPP generic driver version 2.4.2
10/11/12 04:02:02 PM	ehci_hcd	USB 2.0 'Enhanced' Host Controller (EHCI) Driver
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: EHCI Host Controller
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: new USB bus registered, assigned bus number 1
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
10/11/12 04:02:02 PM	QUIRK	Enable AMD PLL fix
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: debug port 1
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: irq 17, io mem 0xf034f000
10/11/12 04:02:02 PM	ehci_hcd 0000	0:12.2: USB 2.0 started, EHCI 1.00
10/11/12 04:02:02 PM	hub 1-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 1-0	.0: 5 ports detected
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: EHCI Host Controller
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: new USB bus registered, assigned bus number 2
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: debug port 1
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: irq 17, io mem 0xf034d000
10/11/12 04:02:02 PM	ehci_hcd 0000	0:13.2: USB 2.0 started, EHCI 1.00
10/11/12 04:02:02 PM	hub 2-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 2-0	.0: 5 ports detected
10/11/12 04:02:02 PM	ohci_hcd	USB 1.1 'Open' Host Controller (OHCI) Driver
10/11/12 04:02:02 PM	ohci_hcd 0000	0:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:02 PM	ohci_hcd 0000	0:12.0: OHCI Host Controller
10/11/12 04:02:02 PM	ohci_hcd 0000	0:12.0: new USB bus registered, assigned bus number 3
10/11/12 04:02:02 PM	ohci_hcd 0000	0:12.0: irq 18, io mem 0xf0350000
10/11/12 04:02:02 PM	hub 3-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 3-0	.0: 5 ports detected
10/11/12 04:02:02 PM	ohci_hcd 0000	0:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:02 PM	ohci_hcd 0000	0:13.0: OHCI Host Controller
10/11/12 04:02:02 PM	ohci_hcd 0000	0:13.0: new USB bus registered, assigned bus number 4
10/11/12 04:02:02 PM	ohci_hcd 0000	0:13.0: irq 18, io mem 0xf034e000
10/11/12 04:02:02 PM	hub 4-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 4-0	.0: 5 ports detected
10/11/12 04:02:02 PM	ohci_hcd 0000	0:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:02 PM	ohci_hcd 0000	0:14.5: OHCI Host Controller
10/11/12 04:02:02 PM	ohci_hcd 0000	0:14.5: new USB bus registered, assigned bus number 5
10/11/12 04:02:02 PM	ohci_hcd 0000	0:14.5: irq 18, io mem 0xf034c000
10/11/12 04:02:02 PM	hub 5-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 5-0	.0: 2 ports detected
10/11/12 04:02:02 PM	uhci_hcd	USB Universal Host Controller Interface driver
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: setting latency timer to 64
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: xHCI Host Controller
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: new USB bus registered, assigned bus number 6
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: irq 18, io mem 0xf0348000
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: irq 40 for MSI/MSI-X
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: irq 41 for MSI/MSI-X
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: irq 42 for MSI/MSI-X
10/11/12 04:02:02 PM		xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:02 PM		xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:02 PM	hub 6-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 6-0	.0: 2 ports detected
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: xHCI Host Controller
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.0: new USB bus registered, assigned bus number 7
10/11/12 04:02:02 PM		xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:02 PM		xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:02 PM	hub 7-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 7-0	.0: 2 ports detected
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: setting latency timer to 64
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: xHCI Host Controller
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: new USB bus registered, assigned bus number 8
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: irq 17, io mem 0xf034a000
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: irq 43 for MSI/MSI-X
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: irq 44 for MSI/MSI-X
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: irq 45 for MSI/MSI-X
10/11/12 04:02:02 PM		xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:02 PM		xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:02 PM	hub 8-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 8-0	.0: 2 ports detected
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: xHCI Host Controller
10/11/12 04:02:02 PM	xhci_hcd 0000	0:10.1: new USB bus registered, assigned bus number 9
10/11/12 04:02:02 PM		xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:02 PM		xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:02 PM	hub 9-0	.0: USB hub found
10/11/12 04:02:02 PM	hub 9-0	.0: 2 ports detected
10/11/12 04:02:02 PM	usbcore	registered new interface driver libusual
10/11/12 04:02:02 PM	i8042	PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
10/11/12 04:02:02 PM	serio	i8042 KBD port at 0x60,0x64 irq 1
10/11/12 04:02:02 PM	serio	i8042 AUX port at 0x60,0x64 irq 12
10/11/12 04:02:02 PM	mousedev	PS/2 mouse device common for all mice
10/11/12 04:02:02 PM	rtc_cmos 00	5: RTC can wake from S4
10/11/12 04:02:02 PM	rtc_cmos 00	5: rtc core: registered rtc_cmos as rtc0
10/11/12 04:02:02 PM	rtc0	alarms up to one month, 114 bytes nvram, hpet irqs
10/11/12 04:02:02 PM	device-mapper	uevent: version 1.0.3
10/11/12 04:02:02 PM	device-mapper	ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
10/11/12 04:02:02 PM	cpuidle	using governor ladder
10/11/12 04:02:02 PM	cpuidle	using governor menu
10/11/12 04:02:02 PM		EFI Variables Facility v0.08 2004-May-17
10/11/12 04:02:02 PM		TCP cubic registered
10/11/12 04:02:02 PM	NET	Registered protocol family 10
10/11/12 04:02:02 PM	NET	Registered protocol family 17
10/11/12 04:02:02 PM		Registering the dns_resolver key type
10/11/12 04:02:02 PM	PM	Hibernation image not present or could not be loaded.
10/11/12 04:02:02 PM		registered taskstats version 1
10/11/12 04:02:02 PM	  Magic number	0:509:34
10/11/12 04:02:02 PM	rtc_cmos 00	5: setting system clock to 2012-10-11 16:02:01 UTC (1349971321)
10/11/12 04:02:02 PM	powernow-k8	Found 1 AMD A6-4400M APU with Radeon(tm) HD Graphics (2 cpu cores) (version 2.20.00)
10/11/12 04:02:02 PM	powernow-k8	Core Performance Boosting: on.
10/11/12 04:02:02 PM	powernow-k8	0 : pstate 0 (2700 MHz)
10/11/12 04:02:02 PM	powernow-k8	1 : pstate 1 (2400 MHz)
10/11/12 04:02:02 PM	powernow-k8	2 : pstate 2 (2000 MHz)
10/11/12 04:02:02 PM	powernow-k8	3 : pstate 3 (1700 MHz)
10/11/12 04:02:02 PM	powernow-k8	4 : pstate 4 (1400 MHz)
10/11/12 04:02:02 PM		BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
10/11/12 04:02:02 PM		EDD information not available.
10/11/12 04:02:02 PM	input	AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
10/11/12 04:02:02 PM	ata1	SATA link up 3.0 Gbps (SStatus 123 SControl 300)
10/11/12 04:02:02 PM	ata2	SATA link up 1.5 Gbps (SStatus 113 SControl 300)
10/11/12 04:02:02 PM	ata4	SATA link down (SStatus 0 SControl 300)
10/11/12 04:02:02 PM	ata1.00	ATA-8: ST95005620AS, SD28, max UDMA/133
10/11/12 04:02:02 PM	ata1.00	976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
10/11/12 04:02:02 PM	ata2.00	ATAPI: TSSTcorp CDDVDW SN-208AB, TO03, max UDMA/100
10/11/12 04:02:02 PM	ata2.00	configured for UDMA/100
10/11/12 04:02:02 PM	ata1.00	configured for UDMA/133
10/11/12 04:02:02 PM	scsi 0	:0:0: Direct-Access ATA ST95005620AS SD28 PQ: 0 ANSI: 5
10/11/12 04:02:02 PM	sd 0	:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
10/11/12 04:02:02 PM	sd 0	:0:0: Attached scsi generic sg0 type 0
10/11/12 04:02:02 PM	sd 0	:0:0: [sda] Write Protect is off
10/11/12 04:02:02 PM	sd 0	:0:0: [sda] Mode Sense: 00 3a 00 00
10/11/12 04:02:02 PM	sd 0	:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
10/11/12 04:02:02 PM	 sda	sda1 sda2 sda3
10/11/12 04:02:02 PM	sd 0	:0:0: [sda] Attached SCSI disk
10/11/12 04:02:02 PM	scsi 1	:0:0: CD-ROM TSSTcorp CDDVDW SN-208AB TO03 PQ: 0 ANSI: 5
10/11/12 04:02:02 PM	usb 2-3	new high-speed USB device number 2 using ehci_hcd
10/11/12 04:02:02 PM	sr0	scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
10/11/12 04:02:02 PM	cdrom	Uniform CD-ROM driver Revision: 3.20
10/11/12 04:02:02 PM	sr 1	:0:0: Attached scsi CD-ROM sr0
10/11/12 04:02:02 PM	sr 1	:0:0: Attached scsi generic sg1 type 5
10/11/12 04:02:02 PM		Freeing unused kernel memory: 920k freed
10/11/12 04:02:02 PM		Write protecting the kernel read-only data: 12288k
10/11/12 04:02:02 PM		Freeing unused kernel memory: 1616k freed
10/11/12 04:02:02 PM		Freeing unused kernel memory: 1200k freed
10/11/12 04:02:02 PM	udevd[95]	starting version 175
10/11/12 04:02:02 PM	wmi	Mapper loaded
10/11/12 04:02:02 PM		r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
10/11/12 04:02:02 PM	r8169 0000	2:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
10/11/12 04:02:02 PM	r8169 0000	2:00.0: setting latency timer to 64
10/11/12 04:02:02 PM	r8169 0000	2:00.0: irq 46 for MSI/MSI-X
10/11/12 04:02:02 PM	r8169 0000	2:00.0: eth0: RTL8105e at 0xffffc9000579a000, 4c:72:b9:39:e5:b5, XID 00c00000 IRQ 46
10/11/12 04:02:02 PM	acpi device	1: registered as cooling_device6
10/11/12 04:02:02 PM	input	Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
10/11/12 04:02:02 PM	ACPI	Video Device [VGA] (multi-head: yes rom: no post: no)
10/11/12 04:02:02 PM		Initializing USB Mass Storage driver...
10/11/12 04:02:02 PM	usbcore	registered new interface driver usb-storage
10/11/12 04:02:02 PM		USB Mass Storage support registered.
10/11/12 04:02:02 PM	usbcore	registered new interface driver uas
10/11/12 04:02:02 PM	scsi4 	usb-storage 2-3:1.0
10/11/12 04:02:02 PM	usbcore	registered new interface driver ums-realtek
10/11/12 04:02:03 PM		Refined TSC clocksource calibration: 2695.099 MHz.
10/11/12 04:02:03 PM		Switching to clocksource tsc
10/11/12 04:02:03 PM	usb 2-4	new high-speed USB device number 3 using ehci_hcd
10/11/12 04:02:03 PM	usb 4-5	new full-speed USB device number 2 using ohci_hcd
10/11/12 04:02:03 PM	usb 2-3	USB disconnect, device number 2
10/11/12 04:02:04 PM	vesafb	mode is 1600x900x32, linelength=6400, pages=0
10/11/12 04:02:04 PM	vesafb	scrolling: redraw
10/11/12 04:02:04 PM	vesafb	Truecolor: size=0:8:8:8, shift=0:16:8:0
10/11/12 04:02:04 PM	vesafb	framebuffer at 0xe0000000, mapped to 0xffffc90005800000, using 5632k, total 5632k
10/11/12 04:02:04 PM	Console	switching to colour frame buffer device 200x56
10/11/12 04:02:04 PM	fb0	VESA VGA frame buffer device
10/11/12 04:02:04 PM	JFS	nTxBlock = 8192, nTxLock = 65536
10/11/12 04:02:07 PM	ADDRCONF(NETDEV_UP)	eth0: link is not ready
10/11/12 04:02:07 PM	udevd[454]	starting version 175
10/11/12 04:02:07 PM	lp	driver loaded but no devices found
10/11/12 04:02:07 PM	toshiba_bluetooth	Detected Toshiba ACPI Bluetooth device - installing RFKill handler
10/11/12 04:02:07 PM	toshiba_bluetooth	Re-enabling Toshiba Bluetooth
10/11/12 04:02:07 PM	cfg80211	Calling CRDA to update world regulatory domain
10/11/12 04:02:07 PM	rtl8723e 0000	1:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
10/11/12 04:02:07 PM	rtl8723e 0000	1:00.0: setting latency timer to 64
10/11/12 04:02:07 PM	firemare	rtl8723fw_B.bin
10/11/12 04:02:07 PM	udevd[554]	renamed network interface eth0 to eth2
10/11/12 04:02:07 PM	fglrx	module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
10/11/12 04:02:07 PM		Disabling lock debugging due to kernel taint
10/11/12 04:02:08 PM	ACPI	resource piix4_smbus [io 0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
10/11/12 04:02:08 PM	ACPI	If an ACPI driver is available for this device, you should use it instead of the native driver
10/11/12 04:02:08 PM		[fglrx] Maximum main memory to use for locked dma buffers: 7233 MBytes.
10/11/12 04:02:08 PM	[fglrx]   vendor	1002 device: 9990 count: 1
10/11/12 04:02:08 PM	[fglrx] ioport	bar 1, base 0x4000, size: 0x100
10/11/12 04:02:08 PM	pci 0000	0:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:08 PM	pci 0000	0:01.0: setting latency timer to 64
10/11/12 04:02:08 PM		[fglrx] Kernel PAT support is enabled
10/11/12 04:02:08 PM		[fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
10/11/12 04:02:08 PM	Bluetooth	Core ver 2.16
10/11/12 04:02:08 PM	NET	Registered protocol family 31
10/11/12 04:02:08 PM	Bluetooth	HCI device and connection manager initialized
10/11/12 04:02:08 PM	Bluetooth	HCI socket layer initialized
10/11/12 04:02:08 PM	Bluetooth	L2CAP socket layer initialized
10/11/12 04:02:08 PM	Bluetooth	SCO socket layer initialized
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
10/11/12 04:02:08 PM	cfg80211	Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 04:02:08 PM		Linux video capture interface: v2.00
10/11/12 04:02:08 PM	Bluetooth	Generic Bluetooth USB driver ver 0.6
10/11/12 04:02:08 PM	usbcore	registered new interface driver btusb
10/11/12 04:02:08 PM	uvcvideo	Found UVC 1.00 device TOSHIBA Web Camera (04ca:7008)
10/11/12 04:02:08 PM	input	TOSHIBA Web Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0/input/input5
10/11/12 04:02:08 PM	usbcore	registered new interface driver uvcvideo
10/11/12 04:02:08 PM		USB Video Class driver (1.1.1)
10/11/12 04:02:08 PM	cfg80211	Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 04:02:08 PM	cfg80211	World regulatory domain updated:
10/11/12 04:02:08 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:08 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:08 PM	ieee80211 phy0	Selected rate control algorithm 'rtl_rc'
10/11/12 04:02:08 PM	rtlwifi	wireless switch is on
10/11/12 04:02:08 PM	cfg80211	Calling CRDA for country: EC
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:08 PM	cfg80211	2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	Disabling freq 2484 MHz
10/11/12 04:02:08 PM	cfg80211	Regulatory domain changed to country: EC
10/11/12 04:02:08 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:08 PM	cfg80211	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
10/11/12 04:02:08 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
10/11/12 04:02:08 PM	cfg80211	(5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
10/11/12 04:02:08 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
10/11/12 04:02:08 PM	snd_hda_intel 0000	0:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:08 PM	snd_hda_intel 0000	0:01.1: irq 47 for MSI/MSI-X
10/11/12 04:02:08 PM	snd_hda_intel 0000	0:01.1: setting latency timer to 64
10/11/12 04:02:08 PM	udevd[539]	renamed network interface wlan0 to wlan1
10/11/12 04:02:08 PM	psmouse serio1	synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
10/11/12 04:02:08 PM	psmouse serio1	synaptics: Toshiba Satellite L875D detected, limiting rate to 40pps.
10/11/12 04:02:08 PM	input	SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM		Too many HDMI devices
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:707:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:708:85
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:318:707:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:318:708:8a
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:f00:c
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:709:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:f09:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:318:f00:c
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:318:709:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:318:f09:0
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:e0:f0d:0
10/11/12 04:02:09 PM	HDMI status	Codec=0 Pin=2 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:09 PM	HDMI status	Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:09 PM	HDMI status	Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:09 PM	HDMI status	Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:09 PM	HDMI status	Codec=0 Pin=36752 Presence_Detect=1 ELD_Valid=1
10/11/12 04:02:09 PM	hda-codec	out of range cmd 0:0:8f90:f2e:8
10/11/12 04:02:09 PM	hda_codec	cannot build controls for #0 (error -16)
10/11/12 04:02:09 PM	hda_codec	cannot revert codec
10/11/12 04:02:09 PM	snd_hda_intel 0000	0:01.1: PCI INT B disabled
10/11/12 04:02:09 PM	snd_hda_intel	probe of 0000:00:01.1 failed with error -16
10/11/12 04:02:09 PM	snd_hda_intel 0000	0:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
10/11/12 04:02:09 PM	snd_hda_intel 0000	0:14.2: irq 47 for MSI/MSI-X
10/11/12 04:02:11 PM	input	HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
10/11/12 04:02:11 PM	input	HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=961 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=961 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=961 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=946 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.550:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=946 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.554:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=945 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.554:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=945 comm="apparmor_parser"
10/11/12 04:02:11 PM		type=1400 audit(1349985730.554:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=945 comm="apparmor_parser"
10/11/12 04:02:12 PM	init	failsafe main process (1068) killed by TERM signal
10/11/12 04:02:13 PM	Bluetooth	BNEP (Ethernet Emulation) ver 1.3
10/11/12 04:02:13 PM	Bluetooth	BNEP filters: protocol multicast
10/11/12 04:02:13 PM	ppdev	user-space parallel port driver
10/11/12 04:02:13 PM	Bluetooth	RFCOMM TTY layer initialized
10/11/12 04:02:13 PM	Bluetooth	RFCOMM socket layer initialized
10/11/12 04:02:13 PM	Bluetooth	RFCOMM ver 1.11
10/11/12 04:02:13 PM		type=1400 audit(1349985732.306:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1145 comm="apparmor_parser"
10/11/12 04:02:14 PM	ADDRCONF(NETDEV_UP)	wlan1: link is not ready
10/11/12 04:02:14 PM	ADDRCONF(NETDEV_UP)	wlan1: link is not ready
10/11/12 04:02:14 PM	r8169 0000	2:00.0: eth2: link down
10/11/12 04:02:14 PM	ADDRCONF(NETDEV_UP)	eth2: link is not ready
10/11/12 04:02:14 PM	ADDRCONF(NETDEV_UP)	eth2: link is not ready
10/11/12 04:02:14 PM	kvm	disabled by bios
10/11/12 04:02:14 PM	init	qemu-kvm pre-start process (1240) terminated with status 1
10/11/12 04:02:14 PM	/dev/vmmon[1314]	Module vmmon: registered with major=10 minor=165
10/11/12 04:02:14 PM	/dev/vmmon[1314]	Module vmmon: initialized
10/11/12 04:02:15 PM		[fglrx] ATIF platform detected with notification ID: 0x81
10/11/12 04:02:15 PM	[1322]	VMCI: shared components initialized.
10/11/12 04:02:15 PM	[1322]	VMCI: host components initialized.
10/11/12 04:02:15 PM	[1322]	VMCI: Module registered (name=vmci,major=10,minor=57).
10/11/12 04:02:15 PM	[1322]	VMCI: Using host personality
10/11/12 04:02:15 PM	[1322]	VMCI: Module (name=vmci) is initialized
10/11/12 04:02:16 PM	fglrx_pci 0000	0:01.0: irq 48 for MSI/MSI-X
10/11/12 04:02:16 PM		[fglrx] Firegl kernel thread PID: 1405
10/11/12 04:02:16 PM		[fglrx] Firegl kernel thread PID: 1406
10/11/12 04:02:16 PM		[fglrx] Firegl kernel thread PID: 1407
10/11/12 04:02:16 PM		[fglrx] IRQ 48 Enabled
10/11/12 04:02:16 PM	/dev/vmnet	open called by PID 1408 (vmnet-netifup)
10/11/12 04:02:16 PM	/dev/vmnet	hub 1 does not exist, allocating memory.
10/11/12 04:02:16 PM	/dev/vmnet	port on hub 1 successfully opened
10/11/12 04:02:16 PM	/dev/vmnet	open called by PID 1415 (vmnet-dhcpd)
10/11/12 04:02:16 PM	/dev/vmnet	port on hub 1 successfully opened
10/11/12 04:02:16 PM	/dev/vmnet	open called by PID 1424 (vmnet-natd)
10/11/12 04:02:16 PM	/dev/vmnet	hub 8 does not exist, allocating memory.
10/11/12 04:02:16 PM	/dev/vmnet	port on hub 8 successfully opened
10/11/12 04:02:16 PM	/dev/vmnet	open called by PID 1425 (vmnet-netifup)
10/11/12 04:02:16 PM	/dev/vmnet	port on hub 8 successfully opened
10/11/12 04:02:16 PM		[fglrx] Gart USWC size:1280 M.
10/11/12 04:02:16 PM		[fglrx] Gart cacheable size:508 M.
10/11/12 04:02:16 PM		[fglrx] Reserved FB block: Shared offset:0, size:1000000
10/11/12 04:02:16 PM		[fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000
10/11/12 04:02:16 PM		[fglrx] Reserved FB block: Unshared offset:1ffee000, size:12000
10/11/12 04:02:16 PM	/dev/vmnet	open called by PID 1433 (vmnet-dhcpd)
10/11/12 04:02:16 PM	/dev/vmnet	port on hub 8 successfully opened
10/11/12 04:02:16 PM	vboxdrv	Found 2 processor cores.
10/11/12 04:02:16 PM	vboxdrv	fAsync=0 offMin=0x2bf offMax=0xc7d
10/11/12 04:02:16 PM	vboxdrv	TSC mode is 'synchronous', kernel timer mode is 'normal'.
10/11/12 04:02:16 PM	vboxdrv	Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
10/11/12 04:02:16 PM	vboxpci	IOMMU not found (not registered)
10/11/12 04:02:19 PM	ACPI Error	Method parse/execution failed [\_SB_.PCI0.VGA_.AF03] (Node ffff880211c52f28), AE_AML_INFINITE_LOOP (20110623/psparse-536)
10/11/12 04:02:19 PM	ACPI Error	Method parse/execution failed [\_SB_.PCI0.VGA_.ATIF] (Node ffff880211c52cd0), AE_AML_INFINITE_LOOP (20110623/psparse-536)
10/11/12 04:02:26 PM	vmnet1	no IPv6 routers present
10/11/12 04:02:27 PM	vmnet8	no IPv6 routers present
10/11/12 04:02:37 PM		------------[ cut here ]------------
10/11/12 04:02:37 PM	WARNING	at /build/buildd/linux-3.2.0/fs/inode.c:885 unlock_new_inode+0x76/0x80()
10/11/12 04:02:37 PM	Hardware name	Satellite L875D
10/11/12 04:02:37 PM	Modules linked in	pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vmnet(O) vsock(O) vmci(O) vmmon(O) rfcomm parport_pc ppdev bnep binfmt_misc snd_hda_codec_realtek snd_hda_codec_hdmi joydev snd_hda_intel snd_hda_codec arc4 snd_hwdep uvcvideo btusb videodev bluetooth v4l2_compat_ioctl32 snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) psmouse i2c_piix4 snd soundcore snd_page_alloc serio_raw k10temp rtl8723e(O) rtlwifi(O) mac80211 cfg80211 mac_hid toshiba_bluetooth sparse_keymap lp parport jfs vesafb ums_realtek usb_storage uas r8169 video wmi [last unloaded: kvm]
10/11/12 04:02:37 PM	Pid	1838, comm: kdm Tainted: P O 3.2.0-31-generic #50-Ubuntu
10/11/12 04:02:37 PM	Call Trace	
10/11/12 04:02:37 PM		[<ffffffff81066d7f>] warn_slowpath_common+0x7f/0xc0
10/11/12 04:02:37 PM		[<ffffffff81066dda>] warn_slowpath_null+0x1a/0x20
10/11/12 04:02:37 PM		[<ffffffff81191866>] unlock_new_inode+0x76/0x80
10/11/12 04:02:37 PM		[<ffffffffa005bfee>] ialloc+0x22e/0x280 [jfs]
10/11/12 04:02:37 PM		[<ffffffffa0046b5c>] jfs_create+0x6c/0x380 [jfs]
10/11/12 04:02:37 PM		[<ffffffff8116449d>] ? kmem_cache_alloc+0x11d/0x140
10/11/12 04:02:37 PM		[<ffffffff8118fa04>] ? __d_alloc+0x34/0x180
10/11/12 04:02:37 PM		[<ffffffff8118fb00>] ? __d_alloc+0x130/0x180
10/11/12 04:02:37 PM		[<ffffffff8118fe88>] ? d_alloc+0x78/0x90
10/11/12 04:02:37 PM		[<ffffffff8129cdbc>] ? security_inode_permission+0x1c/0x30
10/11/12 04:02:37 PM		[<ffffffff811846d4>] vfs_create+0xb4/0x120
10/11/12 04:02:37 PM		[<ffffffff811862a9>] do_last+0x5c9/0x730
10/11/12 04:02:37 PM		[<ffffffff811877b1>] path_openat+0xd1/0x3f0
10/11/12 04:02:37 PM		[<ffffffff8118366f>] ? __lookup_hash.part.28+0xbf/0xe0
10/11/12 04:02:37 PM		[<ffffffff81187bf2>] do_filp_open+0x42/0xa0
10/11/12 04:02:37 PM		[<ffffffff81319321>] ? strncpy_from_user+0x31/0x40
10/11/12 04:02:37 PM		[<ffffffff81182f3a>] ? do_getname+0x10a/0x180
10/11/12 04:02:37 PM		[<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM		[<ffffffff81194eb7>] ? alloc_fd+0xf7/0x150
10/11/12 04:02:37 PM		[<ffffffff8117722d>] do_sys_open+0xed/0x220
10/11/12 04:02:37 PM		[<ffffffff81177380>] sys_open+0x20/0x30
10/11/12 04:02:37 PM		[<ffffffff811773c5>] sys_creat+0x15/0x20
10/11/12 04:02:37 PM		[<ffffffff81662b02>] system_call_fastpath+0x16/0x1b
10/11/12 04:02:37 PM		---[ end trace 3259395a6d4fc07c ]---
10/11/12 04:02:37 PM		------------[ cut here ]------------
10/11/12 04:02:37 PM	WARNING	at /build/buildd/linux-3.2.0/fs/inode.c:885 unlock_new_inode+0x76/0x80()
10/11/12 04:02:37 PM	Hardware name	Satellite L875D
10/11/12 04:02:37 PM	Modules linked in	pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vmnet(O) vsock(O) vmci(O) vmmon(O) rfcomm parport_pc ppdev bnep binfmt_misc snd_hda_codec_realtek snd_hda_codec_hdmi joydev snd_hda_intel snd_hda_codec arc4 snd_hwdep uvcvideo btusb videodev bluetooth v4l2_compat_ioctl32 snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) psmouse i2c_piix4 snd soundcore snd_page_alloc serio_raw k10temp rtl8723e(O) rtlwifi(O) mac80211 cfg80211 mac_hid toshiba_bluetooth sparse_keymap lp parport jfs vesafb ums_realtek usb_storage uas r8169 video wmi [last unloaded: kvm]
10/11/12 04:02:37 PM	Pid	1838, comm: kdm Tainted: P W O 3.2.0-31-generic #50-Ubuntu
10/11/12 04:02:37 PM	Call Trace	
10/11/12 04:02:37 PM		[<ffffffff81066d7f>] warn_slowpath_common+0x7f/0xc0
10/11/12 04:02:37 PM		[<ffffffff81066dda>] warn_slowpath_null+0x1a/0x20
10/11/12 04:02:37 PM		[<ffffffff81191866>] unlock_new_inode+0x76/0x80
10/11/12 04:02:37 PM		[<ffffffffa005bfee>] ialloc+0x22e/0x280 [jfs]
10/11/12 04:02:37 PM		[<ffffffffa0046b5c>] jfs_create+0x6c/0x380 [jfs]
10/11/12 04:02:37 PM		[<ffffffffa005ed54>] ? lmWriteRecord+0x214/0x3b0 [jfs]
10/11/12 04:02:37 PM		[<ffffffff8165a7e5>] ? _raw_spin_lock_irq+0x15/0x20
10/11/12 04:02:37 PM		[<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM		[<ffffffff811901b5>] ? __d_lookup+0x125/0x170
10/11/12 04:02:37 PM		[<ffffffffa0060031>] ? lmLog+0x91/0x1e0 [jfs]
10/11/12 04:02:37 PM		[<ffffffff8129cdbc>] ? security_inode_permission+0x1c/0x30
10/11/12 04:02:37 PM		[<ffffffff811846d4>] vfs_create+0xb4/0x120
10/11/12 04:02:37 PM		[<ffffffff811862a9>] do_last+0x5c9/0x730
10/11/12 04:02:37 PM		[<ffffffff811877b1>] path_openat+0xd1/0x3f0
10/11/12 04:02:37 PM		[<ffffffff81192aa2>] ? iput+0x32/0x50
10/11/12 04:02:37 PM		[<ffffffff81187bf2>] do_filp_open+0x42/0xa0
10/11/12 04:02:37 PM		[<ffffffff81319321>] ? strncpy_from_user+0x31/0x40
10/11/12 04:02:37 PM		[<ffffffff81182f3a>] ? do_getname+0x10a/0x180
10/11/12 04:02:37 PM		[<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM		[<ffffffff81194eb7>] ? alloc_fd+0xf7/0x150
10/11/12 04:02:37 PM		[<ffffffff8117722d>] do_sys_open+0xed/0x220
10/11/12 04:02:37 PM		[<ffffffff81177380>] sys_open+0x20/0x30
10/11/12 04:02:37 PM		[<ffffffff81662b02>] system_call_fastpath+0x16/0x1b
10/11/12 04:02:37 PM		---[ end trace 3259395a6d4fc07d ]---
10/11/12 04:02:47 PM	ACPI Error	[SSZE] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
10/11/12 04:02:47 PM	ACPI Error	Method parse/execution failed [\_SB_.PCI0.AC0_._PSR] (Node ffff880211c94078), AE_ALREADY_EXISTS (20110623/psparse-536)
10/11/12 04:02:47 PM	ACPI Exception	AE_ALREADY_EXISTS, Error reading AC Adapter state (20110623/ac-118)
10/11/12 04:02:47 PM	ACPI	Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
10/11/12 04:02:48 PM	wlan1	authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 04:02:48 PM	wlan1	authenticated
10/11/12 04:02:48 PM	wlan1	associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 04:02:48 PM	wlan1	RX AssocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=1)
10/11/12 04:02:48 PM	wlan1	associated
10/11/12 04:02:48 PM		ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
10/11/12 04:02:48 PM	cfg80211	Calling CRDA for country: US
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	Disabling freq 2467 MHz
10/11/12 04:02:48 PM	cfg80211	Disabling freq 2472 MHz
10/11/12 04:02:48 PM	cfg80211	Disabling freq 2484 MHz
10/11/12 04:02:48 PM	cfg80211	Regulatory domain changed to country: US
10/11/12 04:02:48 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:48 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 04:02:48 PM	cfg80211	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	cfg80211	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	cfg80211	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 04:02:49 PM	/dev/vmnet	open called by PID 1397 (vmnet-bridge)
10/11/12 04:02:49 PM	/dev/vmnet	hub 0 does not exist, allocating memory.
10/11/12 04:02:49 PM	/dev/vmnet	port on hub 0 successfully opened
10/11/12 04:02:49 PM	bridge-wlan1	device is wireless, enabling SMAC
10/11/12 04:02:49 PM	bridge-wlan1	up
10/11/12 04:02:49 PM	bridge-wlan1	attached
10/11/12 04:02:49 PM	userif-2	sent link down event.
10/11/12 04:02:49 PM	userif-2	sent link up event.
10/11/12 04:02:49 PM	userif-2	sent link down event.
10/11/12 04:02:49 PM	userif-2	sent link up event.
10/11/12 04:02:51 PM	userif-2	sent link down event.
10/11/12 04:02:51 PM	userif-2	sent link up event.
10/11/12 04:02:59 PM	wlan1	no IPv6 routers present
10/11/12 04:20:24 PM	show_signal_msg	33 callbacks suppressed
10/11/12 04:20:24 PM	fogger[3424]	segfault at 8 ip 00000000004d338d sp 00007fffa4b429e0 error 4 in python2.7[400000+271000]
10/11/12 04:57:46 PM	fogger[5305]	segfault at 8 ip 00000000004d338d sp 00007fff442b5c70 error 4 in python2.7[400000+271000]
10/11/12 05:22:27 PM	rtlwifi-0	tl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:22:27 PM	wlan1	Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:22:27 PM	bridge-wlan1	disabling the bridge on dev down
10/11/12 05:22:27 PM	bridge-wlan1	down
10/11/12 05:22:27 PM	bridge-wlan1	detached
10/11/12 05:22:27 PM	cfg80211	All devices are disconnected, going to restore regulatory settings
10/11/12 05:22:27 PM	cfg80211	Restoring regulatory settings
10/11/12 05:22:27 PM	cfg80211	Calling CRDA to update world regulatory domain
10/11/12 05:22:27 PM	cfg80211	Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:22:27 PM	cfg80211	World regulatory domain updated:
10/11/12 05:22:27 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:22:27 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:27 PM	cfg80211	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:27 PM	cfg80211	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:27 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:27 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:27 PM	userif-2	sent link down event.
10/11/12 05:22:27 PM	userif-2	sent link up event.
10/11/12 05:22:34 PM	wlan1	authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:22:34 PM	wlan1	authenticated
10/11/12 05:22:34 PM	wlan1	associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:22:34 PM	wlan1	RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:22:34 PM	wlan1	associated
10/11/12 05:22:34 PM	cfg80211	Calling CRDA for country: US
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:34 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	Disabling freq 2467 MHz
10/11/12 05:22:34 PM	cfg80211	Disabling freq 2472 MHz
10/11/12 05:22:34 PM	cfg80211	Disabling freq 2484 MHz
10/11/12 05:22:34 PM	cfg80211	Regulatory domain changed to country: US
10/11/12 05:22:34 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:22:34 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:34 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:22:34 PM	cfg80211	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:34 PM	cfg80211	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:34 PM	cfg80211	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:34 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:22:34 PM	/dev/vmnet	open called by PID 1397 (vmnet-bridge)
10/11/12 05:22:34 PM	/dev/vmnet	hub 0 does not exist, allocating memory.
10/11/12 05:22:34 PM	/dev/vmnet	port on hub 0 successfully opened
10/11/12 05:22:34 PM	bridge-wlan1	device is wireless, enabling SMAC
10/11/12 05:22:34 PM	bridge-wlan1	up
10/11/12 05:22:34 PM	bridge-wlan1	attached
10/11/12 05:22:34 PM	userif-2	sent link down event.
10/11/12 05:22:34 PM	userif-2	sent link up event.
10/11/12 05:24:29 PM	rtlwifi-0	tl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:24:29 PM	wlan1	Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:24:29 PM	bridge-wlan1	disabling the bridge on dev down
10/11/12 05:24:29 PM	bridge-wlan1	down
10/11/12 05:24:29 PM	bridge-wlan1	detached
10/11/12 05:24:30 PM	cfg80211	All devices are disconnected, going to restore regulatory settings
10/11/12 05:24:30 PM	cfg80211	Restoring regulatory settings
10/11/12 05:24:30 PM	cfg80211	Calling CRDA to update world regulatory domain
10/11/12 05:24:30 PM	cfg80211	Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:24:30 PM	cfg80211	World regulatory domain updated:
10/11/12 05:24:30 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:24:30 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:30 PM	cfg80211	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:30 PM	cfg80211	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:30 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:30 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:30 PM	userif-2	sent link down event.
10/11/12 05:24:30 PM	userif-2	sent link up event.
10/11/12 05:24:36 PM	wlan1	authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:24:36 PM	wlan1	authenticated
10/11/12 05:24:36 PM	wlan1	associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:24:36 PM	wlan1	RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:24:36 PM	wlan1	associated
10/11/12 05:24:36 PM	cfg80211	Calling CRDA for country: US
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:36 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	Disabling freq 2467 MHz
10/11/12 05:24:36 PM	cfg80211	Disabling freq 2472 MHz
10/11/12 05:24:36 PM	cfg80211	Disabling freq 2484 MHz
10/11/12 05:24:36 PM	cfg80211	Regulatory domain changed to country: US
10/11/12 05:24:36 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:24:36 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:36 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:24:36 PM	cfg80211	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:36 PM	cfg80211	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:36 PM	cfg80211	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:36 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:24:36 PM	/dev/vmnet	open called by PID 1397 (vmnet-bridge)
10/11/12 05:24:36 PM	/dev/vmnet	hub 0 does not exist, allocating memory.
10/11/12 05:24:36 PM	/dev/vmnet	port on hub 0 successfully opened
10/11/12 05:24:36 PM	bridge-wlan1	device is wireless, enabling SMAC
10/11/12 05:24:36 PM	bridge-wlan1	up
10/11/12 05:24:36 PM	bridge-wlan1	attached
10/11/12 05:24:37 PM	userif-2	sent link down event.
10/11/12 05:24:37 PM	userif-2	sent link up event.
10/11/12 05:29:24 PM	rtlwifi-0	tl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:29:24 PM	wlan1	Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:29:24 PM	bridge-wlan1	disabling the bridge on dev down
10/11/12 05:29:24 PM	bridge-wlan1	down
10/11/12 05:29:24 PM	bridge-wlan1	detached
10/11/12 05:29:24 PM	cfg80211	All devices are disconnected, going to restore regulatory settings
10/11/12 05:29:24 PM	cfg80211	Restoring regulatory settings
10/11/12 05:29:24 PM	cfg80211	Calling CRDA to update world regulatory domain
10/11/12 05:29:24 PM	cfg80211	Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:29:24 PM	cfg80211	World regulatory domain updated:
10/11/12 05:29:24 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:29:24 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:24 PM	cfg80211	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:24 PM	cfg80211	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:24 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:24 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:24 PM	userif-2	sent link down event.
10/11/12 05:29:24 PM	userif-2	sent link up event.
10/11/12 05:29:31 PM	wlan1	authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:29:31 PM	wlan1	authenticated
10/11/12 05:29:31 PM	wlan1	associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:29:31 PM	wlan1	RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:29:31 PM	wlan1	associated
10/11/12 05:29:31 PM	cfg80211	Calling CRDA for country: US
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:31 PM	cfg80211	2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	Disabling freq 2467 MHz
10/11/12 05:29:31 PM	cfg80211	Disabling freq 2472 MHz
10/11/12 05:29:31 PM	cfg80211	Disabling freq 2484 MHz
10/11/12 05:29:31 PM	cfg80211	Regulatory domain changed to country: US
10/11/12 05:29:31 PM	cfg80211	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:29:31 PM	cfg80211	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:31 PM	cfg80211	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:29:31 PM	cfg80211	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:31 PM	cfg80211	(5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:31 PM	cfg80211	(5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:31 PM	cfg80211	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:29:31 PM	/dev/vmnet	open called by PID 1397 (vmnet-bridge)
10/11/12 05:29:31 PM	/dev/vmnet	hub 0 does not exist, allocating memory.
10/11/12 05:29:31 PM	/dev/vmnet	port on hub 0 successfully opened
10/11/12 05:29:31 PM	bridge-wlan1	device is wireless, enabling SMAC
10/11/12 05:29:31 PM	bridge-wlan1	up
10/11/12 05:29:31 PM	bridge-wlan1	attached
10/11/12 05:29:31 PM	userif-2	sent link down event.
10/11/12 05:29:31 PM	userif-2	sent link up event.

```

SYSTEM LOG
```

 
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.348618] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.348625] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.348644] ehci_hcd 0000:00:13.2: debug port 1
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.348657] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf034d000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360159] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360392] hub 2-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360396] hub 2-0:1.0: 5 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360521] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360587] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360613] ohci_hcd 0000:00:12.0: OHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360662] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.360687] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf0350000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420307] hub 3-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420361] hub 3-0:1.0: 5 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420441] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420469] ohci_hcd 0000:00:13.0: OHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420514] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.420530] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf034e000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480298] hub 4-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480352] hub 4-0:1.0: 5 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480433] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480459] ohci_hcd 0000:00:14.5: OHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480507] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.480524] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf034c000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540302] hub 5-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540356] hub 5-0:1.0: 2 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540429] uhci_hcd: USB Universal Host Controller Interface driver
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540513] xhci_hcd 0000:00:10.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540541] xhci_hcd 0000:00:10.0: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540544] xhci_hcd 0000:00:10.0: xHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540594] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540786] xhci_hcd 0000:00:10.0: irq 18, io mem 0xf0348000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540842] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540848] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540852] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540981] xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.540984] xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.541006] hub 6-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.541059] hub 6-0:1.0: 2 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.541108] xhci_hcd 0000:00:10.0: xHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.541177] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.544258] xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.544260] xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.544280] hub 7-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.544302] hub 7-0:1.0: 2 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560191] xhci_hcd 0000:00:10.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560225] xhci_hcd 0000:00:10.1: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560230] xhci_hcd 0000:00:10.1: xHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560334] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560566] xhci_hcd 0000:00:10.1: irq 17, io mem 0xf034a000
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560641] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560650] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560656] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560857] xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560861] xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560903] hub 8-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.560913] hub 8-0:1.0: 2 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.561005] xhci_hcd 0000:00:10.1: xHCI Host Controller
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.561063] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.564044] xHCI xhci_add_endpoint called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.564046] xHCI xhci_check_bandwidth called for root hub
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.564069] hub 9-0:1.0: USB hub found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.564106] hub 9-0:1.0: 2 ports detected
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.588252] usbcore: registered new interface driver libusual
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.588289] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.590505] serio: i8042 KBD port at 0x60,0x64 irq 1
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.590512] serio: i8042 AUX port at 0x60,0x64 irq 12
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.590717] mousedev: PS/2 mouse device common for all mice
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.590896] rtc_cmos 00:05: RTC can wake from S4
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591001] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591024] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591096] device-mapper: uevent: version 1.0.3
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591170] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591214] cpuidle: using governor ladder
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591327] cpuidle: using governor menu
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591329] EFI Variables Facility v0.08 2004-May-17
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591529] TCP cubic registered
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.591620] NET: Registered protocol family 10
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.592130] NET: Registered protocol family 17
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.592134] Registering the dns_resolver key type
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.592282] PM: Hibernation image not present or could not be loaded.
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.592292] registered taskstats version 1
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599195]   Magic number: 0:509:34
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599326] rtc_cmos 00:05: setting system clock to 2012-10-11 16:02:01 UTC (1349971321)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599338] powernow-k8: Found 1 AMD A6-4400M APU with Radeon(tm) HD Graphics    (2 cpu cores) (version 2.20.00)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599353] powernow-k8: Core Performance Boosting: on.
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599410] powernow-k8:    0 : pstate 0 (2700 MHz)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599412] powernow-k8:    1 : pstate 1 (2400 MHz)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599414] powernow-k8:    2 : pstate 2 (2000 MHz)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599415] powernow-k8:    3 : pstate 3 (1700 MHz)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599417] powernow-k8:    4 : pstate 4 (1400 MHz)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599587] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.599589] EDD information not available.
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.606060] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.656179] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.656208] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.656232] ata4: SATA link down (SStatus 0 SControl 300)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.659712] ata1.00: ATA-8: ST95005620AS, SD28, max UDMA/133
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.659716] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.660069] ata2.00: ATAPI: TSSTcorp CDDVDW SN-208AB, TO03, max UDMA/100
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.663017] ata2.00: configured for UDMA/100
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665473] ata1.00: configured for UDMA/133
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665663] scsi 0:0:0:0: Direct-Access     ATA      ST95005620AS     SD28 PQ: 0 ANSI: 5
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665839] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665868] sd 0:0:0:0: Attached scsi generic sg0 type 0
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665888] sd 0:0:0:0: [sda] Write Protect is off
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665891] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.665912] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.666609]  sda: sda1 sda2 sda3
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.667053] sd 0:0:0:0: [sda] Attached SCSI disk
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.668716] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-208AB  TO03 PQ: 0 ANSI: 5
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.672166] usb 2-3: new high-speed USB device number 2 using ehci_hcd
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.676930] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.676934] cdrom: Uniform CD-ROM driver Revision: 3.20
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.677122] sr 1:0:0:0: Attached scsi CD-ROM sr0
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.677198] sr 1:0:0:0: Attached scsi generic sg1 type 5
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.679777] Freeing unused kernel memory: 920k freed
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.680060] Write protecting the kernel read-only data: 12288k
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.687468] Freeing unused kernel memory: 1616k freed
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.693351] Freeing unused kernel memory: 1200k freed
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.804132] wmi: Mapper loaded
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.905023] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.912316] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.912341] r8169 0000:02:00.0: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.912392] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    1.913222] r8169 0000:02:00.0: eth0: RTL8105e at 0xffffc9000579a000, 4c:72:b9:39:e5:b5, XID 00c00000 IRQ 46
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.042499] acpi device:01: registered as cooling_device6
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.042563] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.042741] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.068525] Initializing USB Mass Storage driver...
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.068625] usbcore: registered new interface driver usb-storage
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.068627] USB Mass Storage support registered.
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.068899] usbcore: registered new interface driver uas
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.092780] scsi4 : usb-storage 2-3:1.0
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.092877] usbcore: registered new interface driver ums-realtek
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.168157] Refined TSC clocksource calibration: 2695.099 MHz.
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.168163] Switching to clocksource tsc
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.176156] usb 2-4: new high-speed USB device number 3 using ehci_hcd
10/11/12 04:02:12 PM	joey-HP	kernel	[    2.820157] usb 4-5: new full-speed USB device number 2 using ohci_hcd
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.001417] usb 2-3: USB disconnect, device number 2
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.187062] vesafb: mode is 1600x900x32, linelength=6400, pages=0
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.187066] vesafb: scrolling: redraw
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.187069] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.188251] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005800000, using 5632k, total 5632k
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.188424] Console: switching to colour frame buffer device 200x56
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.188456] fb0: VESA VGA frame buffer device
10/11/12 04:02:12 PM	joey-HP	kernel	[    3.588646] JFS: nTxBlock = 8192, nTxLock = 65536
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.210650] ADDRCONF(NETDEV_UP): eth0: link is not ready
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.423623] lp: driver loaded but no devices found
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.768171] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.768227] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.868915] cfg80211: Calling CRDA to update world regulatory domain
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.936119] rtl8723e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.936128] rtl8723e 0000:01:00.0: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    6.950469] firemare: rtl8723fw_B.bin
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.113923] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.113928] Disabling lock debugging due to kernel taint
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.191927] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.191932] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.243754] [fglrx] Maximum main memory to use for locked dma buffers: 7233 MBytes.
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.243829] [fglrx]   vendor: 1002 device: 9990 count: 1
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.246885] [fglrx] ioport: bar 1, base 0x4000, size: 0x100
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.246901] pci 0000:00:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.246907] pci 0000:00:01.0: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.249980] [fglrx] Kernel PAT support is enabled
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.250012] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479809] Bluetooth: Core ver 2.16
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479836] NET: Registered protocol family 31
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479838] Bluetooth: HCI device and connection manager initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479842] Bluetooth: HCI socket layer initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479844] Bluetooth: L2CAP socket layer initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.479850] Bluetooth: SCO socket layer initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484212] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484219] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484222] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484225] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484228] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484231] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484233] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484236] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484239] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484242] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484244] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484248] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484250] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484253] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484256] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484259] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484262] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484264] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484267] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484270] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484272] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484276] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484278] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484281] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484284] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484287] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.484289] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.485000] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.502784] Linux video capture interface: v2.00
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.508351] Bluetooth: Generic Bluetooth USB driver ver 0.6
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.508575] usbcore: registered new interface driver btusb
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.515731] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera (04ca:7008)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.526993] input: TOSHIBA Web Camera as /devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0/input/input5
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.527294] usbcore: registered new interface driver uvcvideo
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.527297] USB Video Class driver (1.1.1)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538478] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538483] cfg80211: World regulatory domain updated:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538485] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538489] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538492] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538495] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538498] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.538501] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.621211] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.621831] rtlwifi: wireless switch is on
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.622016] cfg80211: Calling CRDA for country: EC
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642110] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642115] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642118] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642122] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642124] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642128] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642130] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642134] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642136] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642139] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642142] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642145] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642148] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642151] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642153] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642156] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642159] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642162] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642164] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642168] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642170] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642173] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642176] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642179] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642181] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642184] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642187] cfg80211: Disabling freq 2484 MHz
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642191] cfg80211: Regulatory domain changed to country: EC
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642193] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642208] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642211] cfg80211:     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642213] cfg80211:     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.642216] cfg80211:     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.649237] snd_hda_intel 0000:00:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.649309] snd_hda_intel 0000:00:01.1: irq 47 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.649338] snd_hda_intel 0000:00:01.1: setting latency timer to 64
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.879786] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.879794] psmouse serio1: synaptics: Toshiba Satellite L875D detected, limiting rate to 40pps.
10/11/12 04:02:12 PM	joey-HP	kernel	[    7.912363] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665187] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665190] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665191] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665193] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665194] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665195] Too many HDMI devices
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665286] hda-codec: out of range cmd 0:0:8f90:707:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665289] hda-codec: out of range cmd 0:0:8f90:708:85
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665377] hda-codec: out of range cmd 0:0:318:707:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665379] hda-codec: out of range cmd 0:0:318:708:8a
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665403] hda-codec: out of range cmd 0:0:8f90:f00:c
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665405] hda-codec: out of range cmd 0:0:8f90:709:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665407] hda-codec: out of range cmd 0:0:8f90:f09:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665409] hda-codec: out of range cmd 0:0:318:f00:c
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665410] hda-codec: out of range cmd 0:0:318:709:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665412] hda-codec: out of range cmd 0:0:318:f09:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665424] hda-codec: out of range cmd 0:0:e0:f0d:0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665427] HDMI status: Codec=0 Pin=2 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665478] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665519] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665563] HDMI status: Codec=0 Pin=0 Presence_Detect=0 ELD_Valid=0
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665588] HDMI status: Codec=0 Pin=36752 Presence_Detect=1 ELD_Valid=1
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665590] hda-codec: out of range cmd 0:0:8f90:f2e:8
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665593] hda_codec: cannot build controls for #0 (error -16)
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665595] hda_codec: cannot revert codec
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665980] snd_hda_intel 0000:00:01.1: PCI INT B disabled
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.665991] snd_hda_intel: probe of 0000:00:01.1 failed with error -16
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.666022] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
10/11/12 04:02:12 PM	joey-HP	kernel	[    8.666097] snd_hda_intel 0000:00:14.2: irq 47 for MSI/MSI-X
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.452568] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.452691] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.653408] type=1400 audit(1349985730.550:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=961 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.653745] type=1400 audit(1349985730.550:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=961 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.653929] type=1400 audit(1349985730.550:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=961 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.655229] type=1400 audit(1349985730.550:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=946 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.655558] type=1400 audit(1349985730.550:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=946 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.655751] type=1400 audit(1349985730.550:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=946 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.656134] type=1400 audit(1349985730.554:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=945 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.656450] type=1400 audit(1349985730.554:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=945 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   10.656621] type=1400 audit(1349985730.554:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=945 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	kernel	[   11.629233] init: failsafe main process (1068) killed by TERM signal
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.339858] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.339862] Bluetooth: BNEP filters: protocol multicast
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.352502] ppdev: user-space parallel port driver
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.372270] Bluetooth: RFCOMM TTY layer initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.372278] Bluetooth: RFCOMM socket layer initialized
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.372281] Bluetooth: RFCOMM ver 1.11
10/11/12 04:02:12 PM	joey-HP	kernel	[   12.409758] type=1400 audit(1349985732.306:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1145 comm="apparmor_parser"
10/11/12 04:02:12 PM	joey-HP	modem-manager[1110]	<info>  Loaded plugin X22X
10/11/12 04:02:12 PM	joey-HP	modem-manager[1110]	<info>  Loaded plugin ZTE
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> NetworkManager (version 0.9.4.0) is starting...
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> Read config file /etc/NetworkManager/NetworkManager.conf
10/11/12 04:02:12 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> VPN: loaded org.freedesktop.NetworkManager.pptp
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> DNS: loaded plugin dnsmasq
10/11/12 04:02:12 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
10/11/12 04:02:12 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.ColorManager'
10/11/12 04:02:12 PM	joey-HP	polkitd[1189]	started daemon version 0.104 using authority implementation `local' version `0.104'
10/11/12 04:02:12 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.PolicyKit1'
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: init!
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: update_system_hostname
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPluginIfupdown: management mode: unmanaged
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/wlan1, iface: wlan1)
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth2, iface: eth2)
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth2, iface: eth2): no ifupdown configuration found.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: end _init.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   Ifupdown: get unmanaged devices count: 0
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: (7748400) ... get_connections.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: (7748400) ... get_connections (managed=false): return empty list.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   keyfile: parsing Belkin.3A25 ... 
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   keyfile:     read connection 'Belkin.3A25'
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	   Ifupdown: get unmanaged devices count: 0
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> modem-manager is now available
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> monitoring kernel firmware directory '/lib/firmware'.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> WiFi enabled by radio killswitch; enabled by state file
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> WWAN enabled by radio killswitch; enabled by state file
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> WiMAX enabled by radio killswitch; enabled by state file
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> Networking is enabled by state file
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<error> [1349985732.844902] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): using nl80211 for WiFi device control
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<warn> (wlan1): driver supports Access Point (AP) mode
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): new 802.11 WiFi device (driver: 'rtl8723e' ifindex: 3)
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/0
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): now managed
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
10/11/12 04:02:12 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): bringing up device.
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): preparing device.
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): deactivating device (reason 'managed') [2]
10/11/12 04:02:13 PM	joey-HP	dbus[1097]	[system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.322620] ADDRCONF(NETDEV_UP): wlan1: link is not ready
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.323024] ADDRCONF(NETDEV_UP): wlan1: link is not ready
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<warn> failed to allocate link cache: (-10) Operation not supported
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): carrier is OFF
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): new Ethernet device (driver: 'r8169' ifindex: 2)
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): exported as /org/freedesktop/NetworkManager/Devices/1
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): now managed
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): bringing up device.
10/11/12 04:02:13 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'fi.w1.wpa_supplicant1'
10/11/12 04:02:13 PM	joey-HP	cron[1252]	(CRON) INFO (pidfile fd = 3)
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.558765] r8169 0000:02:00.0: eth2: link down
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.559798] ADDRCONF(NETDEV_UP): eth2: link is not ready
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): preparing device.
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (eth2): deactivating device (reason 'managed') [2]
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0/net/eth2
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.560276] ADDRCONF(NETDEV_UP): eth2: link is not ready
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> wpa_supplicant started
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: starting -> ready
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: ready -> inactive
10/11/12 04:02:13 PM	joey-HP	NetworkManager[1177]	<warn> Trying to remove a non-existant call id.
10/11/12 04:02:13 PM	joey-HP	cron[1266]	(CRON) STARTUP (fork ok)
10/11/12 04:02:13 PM	joey-HP	acpid	starting up with proc fs
10/11/12 04:02:13 PM	joey-HP	anacron[1264]	Anacron 2.3 started on 2012-10-11
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.642568] kvm: disabled by bios
10/11/12 04:02:13 PM	joey-HP	anacron[1264]	Normal exit (0 jobs run)
10/11/12 04:02:13 PM	joey-HP	acpid	37 rules loaded
10/11/12 04:02:13 PM	joey-HP	acpid	waiting for events: event logging is off
10/11/12 04:02:13 PM	joey-HP	kernel	[   13.715500] init: qemu-kvm pre-start process (1240) terminated with status 1
10/11/12 04:02:13 PM	joey-HP	cron[1266]	(CRON) INFO (Running @reboot jobs)
10/11/12 04:02:13 PM	joey-HP	acpid	client connected from 1300[0:0]
10/11/12 04:02:13 PM	joey-HP	acpid	1 client rule loaded
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.150545] /dev/vmmon[1314]: Module vmmon: registered with major=10 minor=165
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.150552] /dev/vmmon[1314]: Module vmmon: initialized
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.213422] [fglrx] ATIF platform detected with notification ID: 0x81
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.227455] [1322]: VMCI: shared components initialized.
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.227500] [1322]: VMCI: host components initialized.
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.227550] [1322]: VMCI: Module registered (name=vmci,major=10,minor=57).
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.227553] [1322]: VMCI: Using host personality
10/11/12 04:02:14 PM	joey-HP	kernel	[   14.227555] [1322]: VMCI: Module (name=vmci) is initialized
10/11/12 04:02:14 PM	joey-HP	vmnetBridge	Bridge process created.
10/11/12 04:02:14 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:eth2 index:2 flags:0x00001003
10/11/12 04:02:14 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.215141] fglrx_pci 0000:00:01.0: irq 48 for MSI/MSI-X
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.215804] [fglrx] Firegl kernel thread PID: 1405
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.215880] [fglrx] Firegl kernel thread PID: 1406
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.215952] [fglrx] Firegl kernel thread PID: 1407
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.216065] [fglrx] IRQ 48 Enabled
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.305155] /dev/vmnet: open called by PID 1408 (vmnet-netifup)
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.305164] /dev/vmnet: hub 1 does not exist, allocating memory.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.305183] /dev/vmnet: port on hub 1 successfully opened
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	<warn> /sys/devices/virtual/net/vmnet1: couldn't determine device driver; ignoring...
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1)
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1): no ifupdown configuration found.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Internet Software Consortium DHCP Server 2.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	All rights reserved.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Please contribute if you find this software useful.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	For info, please visit http://www.isc.org/dhcp-contrib.html
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Configured subnet: 172.16.247.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Setting vmnet-dhcp IP address: 172.16.247.254
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Recving on     VNet/vmnet1/172.16.247.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Sending on     VNet/vmnet1/172.16.247.0
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.361419] /dev/vmnet: open called by PID 1415 (vmnet-dhcpd)
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.361432] /dev/vmnet: port on hub 1 successfully opened
10/11/12 04:02:15 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:eth2 index:2 flags:0x00001003
10/11/12 04:02:15 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.387488] /dev/vmnet: open called by PID 1424 (vmnet-natd)
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.387498] /dev/vmnet: hub 8 does not exist, allocating memory.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.387514] /dev/vmnet: port on hub 8 successfully opened
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.391036] /dev/vmnet: open called by PID 1425 (vmnet-netifup)
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.391051] /dev/vmnet: port on hub 8 successfully opened
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8)
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	   SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8): no ifupdown configuration found.
10/11/12 04:02:15 PM	joey-HP	NetworkManager[1177]	<warn> /sys/devices/virtual/net/vmnet8: couldn't determine device driver; ignoring...
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Internet Software Consortium DHCP Server 2.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	All rights reserved.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Please contribute if you find this software useful.
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	For info, please visit http://www.isc.org/dhcp-contrib.html
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.439229] [fglrx] Gart USWC size:1280 M.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.439232] [fglrx] Gart cacheable size:508 M.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.439237] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.439240] [fglrx] Reserved FB block: Unshared offset:fbfd000, size:403000 
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.439242] [fglrx] Reserved FB block: Unshared offset:1ffee000, size:12000 
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Configured subnet: 172.16.80.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Setting vmnet-dhcp IP address: 172.16.80.254
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Recving on     VNet/vmnet8/172.16.80.0
10/11/12 04:02:15 PM	joey-HP	vmnet-dhcpd	Sending on     VNet/vmnet8/172.16.80.0
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.459502] /dev/vmnet: open called by PID 1433 (vmnet-dhcpd)
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.459520] /dev/vmnet: port on hub 8 successfully opened
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.678166] vboxdrv: Found 2 processor cores.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.678940] vboxdrv: fAsync=0 offMin=0x2bf offMax=0xc7d
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.679012] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.679015] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
10/11/12 04:02:15 PM	joey-HP	kernel	[   15.742642] vboxpci: IOMMU not found (not registered)
10/11/12 04:02:16 PM	joey-HP	anacron[1582]	Anacron 2.3 started on 2012-10-11
10/11/12 04:02:16 PM	joey-HP	anacron[1582]	Normal exit (0 jobs run)
10/11/12 04:02:18 PM	joey-HP	kernel	[   18.438245] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.AF03] (Node ffff880211c52f28), AE_AML_INFINITE_LOOP (20110623/psparse-536)
10/11/12 04:02:18 PM	joey-HP	kernel	[   18.438262] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.ATIF] (Node ffff880211c52cd0), AE_AML_INFINITE_LOOP (20110623/psparse-536)
10/11/12 04:02:20 PM	joey-HP	kdm_greet[1713]	Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
10/11/12 04:02:25 PM	joey-HP	kernel	[   25.840108] vmnet1: no IPv6 routers present
10/11/12 04:02:26 PM	joey-HP	kernel	[   26.280098] vmnet8: no IPv6 routers present
10/11/12 04:02:36 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
10/11/12 04:02:36 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.ConsoleKit'
10/11/12 04:02:37 PM	joey-HP	kdm	:0 '[1838]: Cannot update authorization file in home dir /home/joey
10/11/12 04:02:37 PM	joey-HP	kdm	:0 '[1838]: Session log file according to .xsession-errors cannot be created: Invalid argument
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130571] ------------[ cut here ]------------
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130580] WARNING: at /build/buildd/linux-3.2.0/fs/inode.c:885 unlock_new_inode+0x76/0x80()
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130582] Hardware name: Satellite L875D
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130584] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vmnet(O) vsock(O) vmci(O) vmmon(O) rfcomm parport_pc ppdev bnep binfmt_misc snd_hda_codec_realtek snd_hda_codec_hdmi joydev snd_hda_intel snd_hda_codec arc4 snd_hwdep uvcvideo btusb videodev bluetooth v4l2_compat_ioctl32 snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) psmouse i2c_piix4 snd soundcore snd_page_alloc serio_raw k10temp rtl8723e(O) rtlwifi(O) mac80211 cfg80211 mac_hid toshiba_bluetooth sparse_keymap lp parport jfs vesafb ums_realtek usb_storage uas r8169 video wmi [last unloaded: kvm]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130628] Pid: 1838, comm: kdm Tainted: P           O 3.2.0-31-generic #50-Ubuntu
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130630] Call Trace:
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130636]  [<ffffffff81066d7f>] warn_slowpath_common+0x7f/0xc0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130639]  [<ffffffff81066dda>] warn_slowpath_null+0x1a/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130642]  [<ffffffff81191866>] unlock_new_inode+0x76/0x80
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130650]  [<ffffffffa005bfee>] ialloc+0x22e/0x280 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130656]  [<ffffffffa0046b5c>] jfs_create+0x6c/0x380 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130661]  [<ffffffff8116449d>] ? kmem_cache_alloc+0x11d/0x140
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130665]  [<ffffffff8118fa04>] ? __d_alloc+0x34/0x180
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130668]  [<ffffffff8118fb00>] ? __d_alloc+0x130/0x180
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130671]  [<ffffffff8118fe88>] ? d_alloc+0x78/0x90
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130675]  [<ffffffff8129cdbc>] ? security_inode_permission+0x1c/0x30
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130678]  [<ffffffff811846d4>] vfs_create+0xb4/0x120
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130681]  [<ffffffff811862a9>] do_last+0x5c9/0x730
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130683]  [<ffffffff811877b1>] path_openat+0xd1/0x3f0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130686]  [<ffffffff8118366f>] ? __lookup_hash.part.28+0xbf/0xe0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130689]  [<ffffffff81187bf2>] do_filp_open+0x42/0xa0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130694]  [<ffffffff81319321>] ? strncpy_from_user+0x31/0x40
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130696]  [<ffffffff81182f3a>] ? do_getname+0x10a/0x180
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130700]  [<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130703]  [<ffffffff81194eb7>] ? alloc_fd+0xf7/0x150
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130706]  [<ffffffff8117722d>] do_sys_open+0xed/0x220
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130709]  [<ffffffff81177380>] sys_open+0x20/0x30
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130711]  [<ffffffff811773c5>] sys_creat+0x15/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130714]  [<ffffffff81662b02>] system_call_fastpath+0x16/0x1b
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.130717] ---[ end trace 3259395a6d4fc07c ]---
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131147] ------------[ cut here ]------------
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131153] WARNING: at /build/buildd/linux-3.2.0/fs/inode.c:885 unlock_new_inode+0x76/0x80()
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131155] Hardware name: Satellite L875D
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131156] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vmnet(O) vsock(O) vmci(O) vmmon(O) rfcomm parport_pc ppdev bnep binfmt_misc snd_hda_codec_realtek snd_hda_codec_hdmi joydev snd_hda_intel snd_hda_codec arc4 snd_hwdep uvcvideo btusb videodev bluetooth v4l2_compat_ioctl32 snd_seq_midi snd_pcm snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) psmouse i2c_piix4 snd soundcore snd_page_alloc serio_raw k10temp rtl8723e(O) rtlwifi(O) mac80211 cfg80211 mac_hid toshiba_bluetooth sparse_keymap lp parport jfs vesafb ums_realtek usb_storage uas r8169 video wmi [last unloaded: kvm]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131192] Pid: 1838, comm: kdm Tainted: P        W  O 3.2.0-31-generic #50-Ubuntu
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131194] Call Trace:
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131197]  [<ffffffff81066d7f>] warn_slowpath_common+0x7f/0xc0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131200]  [<ffffffff81066dda>] warn_slowpath_null+0x1a/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131203]  [<ffffffff81191866>] unlock_new_inode+0x76/0x80
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131210]  [<ffffffffa005bfee>] ialloc+0x22e/0x280 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131216]  [<ffffffffa0046b5c>] jfs_create+0x6c/0x380 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131223]  [<ffffffffa005ed54>] ? lmWriteRecord+0x214/0x3b0 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131226]  [<ffffffff8165a7e5>] ? _raw_spin_lock_irq+0x15/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131229]  [<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131232]  [<ffffffff811901b5>] ? __d_lookup+0x125/0x170
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131239]  [<ffffffffa0060031>] ? lmLog+0x91/0x1e0 [jfs]
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131242]  [<ffffffff8129cdbc>] ? security_inode_permission+0x1c/0x30
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131245]  [<ffffffff811846d4>] vfs_create+0xb4/0x120
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131248]  [<ffffffff811862a9>] do_last+0x5c9/0x730
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131251]  [<ffffffff811877b1>] path_openat+0xd1/0x3f0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131253]  [<ffffffff81192aa2>] ? iput+0x32/0x50
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131256]  [<ffffffff81187bf2>] do_filp_open+0x42/0xa0
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131260]  [<ffffffff81319321>] ? strncpy_from_user+0x31/0x40
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131263]  [<ffffffff81182f3a>] ? do_getname+0x10a/0x180
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131265]  [<ffffffff8165a4fe>] ? _raw_spin_lock+0xe/0x20
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131268]  [<ffffffff81194eb7>] ? alloc_fd+0xf7/0x150
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131271]  [<ffffffff8117722d>] do_sys_open+0xed/0x220
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131274]  [<ffffffff81177380>] sys_open+0x20/0x30
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131276]  [<ffffffff81662b02>] system_call_fastpath+0x16/0x1b
10/11/12 04:02:37 PM	joey-HP	kernel	[   37.131279] ---[ end trace 3259395a6d4fc07d ]---
10/11/12 04:02:38 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
10/11/12 04:02:38 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.UDisks'
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Auto-activating connection 'Belkin.3A25'.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) starting connection 'Belkin.3A25'
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1/wireless): access point 'Belkin.3A25' has security, but secrets are required.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<warn> No agents were available for this request.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<warn> Activation (wlan1) failed for access point (Belkin.3A25)
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> Marking connection 'Belkin.3A25' invalid.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<warn> Activation (wlan1) failed.
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: failed -> disconnected (reason 'none') [120 30 0]
10/11/12 04:02:40 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): deactivating device (reason 'none') [0]
10/11/12 04:02:41 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.UPower' (using servicehelper)
10/11/12 04:02:41 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.UPower'
10/11/12 04:02:41 PM	joey-HP	anacron[2043]	Anacron 2.3 started on 2012-10-11
10/11/12 04:02:41 PM	joey-HP	anacron[2043]	Normal exit (0 jobs run)
10/11/12 04:02:41 PM	joey-HP	ntfs-3g[2150]	Version 2012.1.15AR.1 external FUSE 28
10/11/12 04:02:41 PM	joey-HP	ntfs-3g[2150]	Mounted /dev/sda3 (Read-Write, label "DATA", NTFS 3.1)
10/11/12 04:02:41 PM	joey-HP	ntfs-3g[2150]	Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
10/11/12 04:02:41 PM	joey-HP	ntfs-3g[2150]	Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sda3,blkdev,blksize=4096
10/11/12 04:02:41 PM	joey-HP	ntfs-3g[2150]	Global ownership and permissions enforced, configuration type 7
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Auto-activating connection 'Belkin.3A25'.
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) starting connection 'Belkin.3A25'
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1/wireless): access point 'Belkin.3A25' has security, but secrets are required.
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
10/11/12 04:02:46 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
10/11/12 04:02:46 PM	joey-HP	kernel	[   46.840342] ACPI Error: [SSZE] Namespace lookup failure, AE_ALREADY_EXISTS (20110623/dsfield-143)
10/11/12 04:02:46 PM	joey-HP	kernel	[   46.840350] ACPI Error: Method parse/execution failed [\_SB_.PCI0.AC0_._PSR] (Node ffff880211c94078), AE_ALREADY_EXISTS (20110623/psparse-536)
10/11/12 04:02:46 PM	joey-HP	kernel	[   46.840362] ACPI Exception: AE_ALREADY_EXISTS, Error reading AC Adapter state (20110623/ac-118)
10/11/12 04:02:46 PM	joey-HP	kernel	[   46.872090] ACPI: Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1/wireless): connection 'Belkin.3A25' has security, and secrets exist.  No new secrets needed.
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Config: added 'ssid' value 'Belkin.3A25'
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Config: added 'scan_ssid' value '1'
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Config: added 'key_mgmt' value 'WPA-PSK'
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Config: added 'psk' value '<omitted>'
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> Config: set interface ap_scan to 1
10/11/12 04:02:47 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: inactive -> scanning
10/11/12 04:02:48 PM	joey-HP	wpa_supplicant[1246]	Trying to authenticate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: scanning -> authenticating
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.123941] wlan1: authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 04:02:48 PM	joey-HP	wpa_supplicant[1246]	Trying to associate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.127836] wlan1: authenticated
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.128164] wlan1: associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.131832] wlan1: RX AssocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=1)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.131836] wlan1: associated
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: authenticating -> associating
10/11/12 04:02:48 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 04:02:48 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 04:02:48 PM	joey-HP	wpa_supplicant[1246]	Associated with 94:44:52:6d:ba:25
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.149402] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.150262] cfg80211: Calling CRDA for country: US
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associating -> associated
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associated -> 4-way handshake
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161270] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161276] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161280] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161285] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161288] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161302] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161306] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161310] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161313] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161317] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161320] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161324] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161328] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161335] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161339] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161342] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161346] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161349] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161353] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161356] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161359] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161362] cfg80211: Disabling freq 2467 MHz
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161364] cfg80211: Disabling freq 2472 MHz
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161366] cfg80211: Disabling freq 2484 MHz
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161373] cfg80211: Regulatory domain changed to country: US
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161375] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161379] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161383] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161386] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161389] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161393] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.161395] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 04:02:48 PM	joey-HP	wpa_supplicant[1246]	WPA: Key negotiation completed with 94:44:52:6d:ba:25 [PTK=CCMP GTK=CCMP]
10/11/12 04:02:48 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-CONNECTED - Connection to 94:44:52:6d:ba:25 completed (auth) [id=0 id_str=]
10/11/12 04:02:48 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 04:02:48 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 04:02:48 PM	joey-HP	vmnetBridge	Adding interface wlan1 index:3
10/11/12 04:02:48 PM	joey-HP	vmnetBridge	Started bridge wlan1 to virtual network 0.
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: 4-way handshake -> completed
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Belkin.3A25'.
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: config -> ip-config (reason 'none') [50 70 0]
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176155] /dev/vmnet: open called by PID 1397 (vmnet-bridge)
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176173] /dev/vmnet: hub 0 does not exist, allocating memory.
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176191] /dev/vmnet: port on hub 0 successfully opened
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176207] bridge-wlan1: device is wireless, enabling SMAC
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176211] bridge-wlan1: up
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.176261] bridge-wlan1: attached
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> dhclient started with pid 2177
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
10/11/12 04:02:48 PM	joey-HP	dhclient	Internet Systems Consortium DHCP Client 4.1-ESV-R4
10/11/12 04:02:48 PM	joey-HP	dhclient	Copyright 2004-2011 Internet Systems Consortium.
10/11/12 04:02:48 PM	joey-HP	dhclient	All rights reserved.
10/11/12 04:02:48 PM	joey-HP	dhclient	For info, please visit https://www.isc.org/software/dhcp/
10/11/12 04:02:48 PM	joey-HP	dhclient	
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): DHCPv4 state changed nbi -> preinit
10/11/12 04:02:48 PM	joey-HP	dhclient	Listening on LPF/wlan1/74:e5:43:24:8d:d9
10/11/12 04:02:48 PM	joey-HP	dhclient	Sending on   LPF/wlan1/74:e5:43:24:8d:d9
10/11/12 04:02:48 PM	joey-HP	dhclient	Sending on   Socket/fallback
10/11/12 04:02:48 PM	joey-HP	dhclient	DHCPREQUEST of 192.168.2.6 on wlan1 to 255.255.255.255 port 67
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.375224] userif-2: sent link down event.
10/11/12 04:02:48 PM	joey-HP	dhclient	DHCPACK of 192.168.2.6 from 192.168.2.1
10/11/12 04:02:48 PM	joey-HP	dhclient	bound to 192.168.2.6 -- renewal in 2147483648 seconds.
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): DHCPv4 state changed preinit -> reboot
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info>   address 192.168.2.6
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info>   prefix 24 (255.255.255.0)
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info>   gateway 192.168.2.1
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info>   nameserver '192.168.2.1'
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info>   domain name 'Belkin'
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
10/11/12 04:02:48 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
10/11/12 04:02:48 PM	joey-HP	vmnet-natd	RTM_NEWADDR: index:3, addr:192.168.2.6
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.375229] userif-2: sent link up event.
10/11/12 04:02:48 PM	joey-HP	kernel	[   48.665740] userif-2: sent link down event.
10/11/12 04:02:49 PM	joey-HP	NetworkManager[1177]	<info> DNS: starting dnsmasq...
10/11/12 04:02:49 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): writing resolv.conf to /sbin/resolvconf
10/11/12 04:02:49 PM	joey-HP	dnsmasq[2183]	started, version 2.59 cache disabled
10/11/12 04:02:49 PM	joey-HP	dnsmasq[2183]	compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
10/11/12 04:02:49 PM	joey-HP	dnsmasq[2183]	using nameserver 192.168.2.1#53
10/11/12 04:02:49 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): device state change: ip-config -> activated (reason 'none') [70 100 0]
10/11/12 04:02:50 PM	joey-HP	vmnet-natd	RTM_NEWROUTE: index:3
10/11/12 04:02:50 PM	joey-HP	NetworkManager[1177]	<info> Policy set 'Belkin.3A25' (wlan1) as default for IPv4 routing and DNS.
10/11/12 04:02:50 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) successful, device activated.
10/11/12 04:02:50 PM	joey-HP	NetworkManager[1177]	<info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
10/11/12 04:02:50 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
10/11/12 04:02:50 PM	joey-HP	vmnetBridge	RTM_NEWROUTE: index:3
10/11/12 04:02:50 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.nm_dispatcher'
10/11/12 04:02:50 PM	joey-HP	kernel	[   48.665744] userif-2: sent link up event.
10/11/12 04:02:50 PM	joey-HP	kernel	[   50.328536] userif-2: sent link down event.
10/11/12 04:02:51 PM	joey-HP	dbus[1097]	[system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
10/11/12 04:02:51 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.freedesktop.RealtimeKit1'
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Successfully called chroot.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Successfully dropped privileges.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Successfully limited resources.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Running.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Watchdog thread running.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Successfully made thread 2315 of process 2315 (n/a) owned by '1000' high priority at nice level -11.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Supervising 1 threads of 1 processes of 1 users.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Canary thread running.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Successfully made thread 2320 of process 2315 (n/a) owned by '1000' RT at priority 5.
10/11/12 04:02:51 PM	joey-HP	rtkit-daemon[2317]	Supervising 2 threads of 1 processes of 1 users.
10/11/12 04:02:52 PM	joey-HP	rtkit-daemon[2317]	Successfully made thread 2321 of process 2315 (n/a) owned by '1000' RT at priority 5.
10/11/12 04:02:52 PM	joey-HP	rtkit-daemon[2317]	Supervising 3 threads of 1 processes of 1 users.
10/11/12 04:02:58 PM	joey-HP	kernel	[   50.328539] userif-2: sent link up event.
10/11/12 04:02:58 PM	joey-HP	kernel	[   58.496015] wlan1: no IPv6 routers present
10/11/12 04:02:59 PM	joey-HP	ntpdate[2250]	adjust time server 91.189.94.4 offset -0.140371 sec
10/11/12 04:03:02 PM	joey-HP	hp-systray	hp-systray[2361]: error: option -s not recognized
10/11/12 04:09:01 PM	joey-HP	CRON[2991]	(root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
10/11/12 04:17:01 PM	joey-HP	CRON[3397]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
10/11/12 04:20:23 PM	joey-HP	kernel	[ 1104.008318] show_signal_msg: 33 callbacks suppressed
10/11/12 04:20:23 PM	joey-HP	kernel	[ 1104.008323] fogger[3424]: segfault at 8 ip 00000000004d338d sp 00007fffa4b429e0 error 4 in python2.7[400000+271000]
10/11/12 04:39:01 PM	joey-HP	CRON[4091]	(root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
10/11/12 04:57:45 PM	joey-HP	kernel	[ 3345.673744] fogger[5305]: segfault at 8 ip 00000000004d338d sp 00007fff442b5c70 error 4 in python2.7[400000+271000]
10/11/12 05:09:01 PM	joey-HP	CRON[5671]	(root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
10/11/12 05:13:12 PM	joey-HP	dbus[1097]	[system] Activating service name='org.debian.apt' (using servicehelper)
10/11/12 05:13:12 PM	joey-HP	AptDaemon	INFO: Initializing daemon
10/11/12 05:13:12 PM	joey-HP	dbus[1097]	[system] Successfully activated service 'org.debian.apt'
10/11/12 05:13:12 PM	joey-HP	AptDaemon.PackageKit	INFO: Initializing PackageKit compat layer
10/11/12 05:13:12 PM	joey-HP	AptDaemon	INFO: UpdateCache() was called
10/11/12 05:13:12 PM	joey-HP	AptDaemon.Trans	INFO: Queuing transaction /org/debian/apt/transaction/33121b68b7ce48109d02ef8f9766461d
10/11/12 05:13:12 PM	joey-HP	AptDaemon.Worker	INFO: Simulating trans: /org/debian/apt/transaction/33121b68b7ce48109d02ef8f9766461d
10/11/12 05:13:12 PM	joey-HP	AptDaemon.Worker	INFO: Processing transaction /org/debian/apt/transaction/33121b68b7ce48109d02ef8f9766461d
10/11/12 05:13:13 PM	joey-HP	AptDaemon.Worker	INFO: Updating cache
10/11/12 05:13:35 PM	joey-HP	AptDaemon.Worker	INFO: Finished transaction /org/debian/apt/transaction/33121b68b7ce48109d02ef8f9766461d
10/11/12 05:13:47 PM	joey-HP	AptDaemon	INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'boot-repair'), dbus.String(u'boot-sav'), dbus.String(u'boot-sav-extra')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
10/11/12 05:13:47 PM	joey-HP	AptDaemon.Trans	INFO: Queuing transaction /org/debian/apt/transaction/6a9c678d3ae94299b77defe8dc7b4e7d
10/11/12 05:13:47 PM	joey-HP	AptDaemon.Worker	INFO: Simulating trans: /org/debian/apt/transaction/6a9c678d3ae94299b77defe8dc7b4e7d
10/11/12 05:13:48 PM	joey-HP	AptDaemon.Worker	INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'boot-repair'), dbus.String(u'boot-sav'), dbus.String(u'boot-sav-extra')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
10/11/12 05:13:49 PM	joey-HP	AptDaemon.Worker	INFO: Processing transaction /org/debian/apt/transaction/6a9c678d3ae94299b77defe8dc7b4e7d
10/11/12 05:14:08 PM	joey-HP	AptDaemon.Worker	INFO: Finished transaction /org/debian/apt/transaction/6a9c678d3ae94299b77defe8dc7b4e7d
10/11/12 05:17:01 PM	joey-HP	CRON[6584]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
10/11/12 05:19:13 PM	joey-HP	AptDaemon	INFO: Quitting due to inactivity
10/11/12 05:19:13 PM	joey-HP	AptDaemon	INFO: Quitting was requested
10/11/12 05:22:26 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:22:26 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:22:26 PM	joey-HP	vmnetBridge	Removing interface wlan1 index:3
10/11/12 05:22:26 PM	joey-HP	vmnetBridge	Stopped bridge wlan1 to virtual network 0.
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.908224] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.908255] wlan1: Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.910039] bridge-wlan1: disabling the bridge on dev down
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.910209] bridge-wlan1: down
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.910223] bridge-wlan1: detached
10/11/12 05:22:26 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-DISCONNECTED bssid=94:44:52:6d:ba:25 reason=4
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.972390] cfg80211: All devices are disconnected, going to restore regulatory settings
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.972401] cfg80211: Restoring regulatory settings
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.972409] cfg80211: Calling CRDA to update world regulatory domain
10/11/12 05:22:26 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: completed -> disconnected
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980669] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980677] cfg80211: World regulatory domain updated:
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980681] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980687] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980693] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980698] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980703] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:26 PM	joey-HP	kernel	[ 4826.980708] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:26 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: disconnected -> scanning
10/11/12 05:22:27 PM	joey-HP	kernel	[ 4827.110059] userif-2: sent link down event.
10/11/12 05:22:33 PM	joey-HP	wpa_supplicant[1246]	Trying to authenticate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:22:33 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: scanning -> authenticating
10/11/12 05:22:33 PM	joey-HP	wpa_supplicant[1246]	Trying to associate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4827.110065] userif-2: sent link up event.
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.704621] wlan1: authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.707538] wlan1: authenticated
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.708067] wlan1: associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:22:33 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: authenticating -> associating
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.713335] wlan1: RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.713345] wlan1: associated
10/11/12 05:22:33 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:22:33 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:22:33 PM	joey-HP	wpa_supplicant[1246]	Associated with 94:44:52:6d:ba:25
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.732715] cfg80211: Calling CRDA for country: US
10/11/12 05:22:33 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associating -> 4-way handshake
10/11/12 05:22:33 PM	joey-HP	wpa_supplicant[1246]	WPA: Key negotiation completed with 94:44:52:6d:ba:25 [PTK=CCMP GTK=CCMP]
10/11/12 05:22:33 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-CONNECTED - Connection to 94:44:52:6d:ba:25 completed (reauth) [id=0 id_str=]
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740342] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740349] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740354] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740356] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740359] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740361] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740363] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740366] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740368] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740370] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740372] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740375] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740377] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740379] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740381] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740384] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740386] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740388] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740390] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740395] cfg80211: Disabling freq 2467 MHz
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740396] cfg80211: Disabling freq 2472 MHz
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740398] cfg80211: Disabling freq 2484 MHz
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740403] cfg80211: Regulatory domain changed to country: US
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740404] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740407] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740409] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740411] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740413] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740415] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.740417] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:22:33 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:22:33 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:22:33 PM	joey-HP	vmnetBridge	Adding interface wlan1 index:3
10/11/12 05:22:33 PM	joey-HP	vmnetBridge	Started bridge wlan1 to virtual network 0.
10/11/12 05:22:33 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: 4-way handshake -> completed
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744416] /dev/vmnet: open called by PID 1397 (vmnet-bridge)
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744428] /dev/vmnet: hub 0 does not exist, allocating memory.
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744447] /dev/vmnet: port on hub 0 successfully opened
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744458] bridge-wlan1: device is wireless, enabling SMAC
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744463] bridge-wlan1: up
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.744605] bridge-wlan1: attached
10/11/12 05:22:33 PM	joey-HP	kernel	[ 4833.944680] userif-2: sent link down event.
10/11/12 05:24:29 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:24:29 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:24:29 PM	joey-HP	vmnetBridge	Removing interface wlan1 index:3
10/11/12 05:24:29 PM	joey-HP	vmnetBridge	Stopped bridge wlan1 to virtual network 0.
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4833.944687] userif-2: sent link up event.
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.152238] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.152268] wlan1: Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.154143] bridge-wlan1: disabling the bridge on dev down
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.154220] bridge-wlan1: down
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.154234] bridge-wlan1: detached
10/11/12 05:24:29 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-DISCONNECTED bssid=94:44:52:6d:ba:25 reason=4
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.208760] cfg80211: All devices are disconnected, going to restore regulatory settings
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.208771] cfg80211: Restoring regulatory settings
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.208779] cfg80211: Calling CRDA to update world regulatory domain
10/11/12 05:24:29 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: completed -> disconnected
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216618] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216627] cfg80211: World regulatory domain updated:
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216630] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216637] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216642] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216648] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216653] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.216658] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:29 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: disconnected -> scanning
10/11/12 05:24:29 PM	joey-HP	kernel	[ 4949.354085] userif-2: sent link down event.
10/11/12 05:24:35 PM	joey-HP	wpa_supplicant[1246]	Trying to authenticate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:24:35 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: scanning -> authenticating
10/11/12 05:24:35 PM	joey-HP	wpa_supplicant[1246]	Trying to associate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4949.354091] userif-2: sent link up event.
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.940912] wlan1: authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.942525] wlan1: authenticated
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.942952] wlan1: associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:24:35 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: authenticating -> associating
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.946644] wlan1: RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.946652] wlan1: associated
10/11/12 05:24:35 PM	joey-HP	wpa_supplicant[1246]	Associated with 94:44:52:6d:ba:25
10/11/12 05:24:35 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:24:35 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.966554] cfg80211: Calling CRDA for country: US
10/11/12 05:24:35 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associating -> associated
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974138] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974147] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974153] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974164] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974174] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974180] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974185] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974195] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974201] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974206] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974211] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974216] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974221] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974226] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974232] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974236] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974242] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974247] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974257] cfg80211: Disabling freq 2467 MHz
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974260] cfg80211: Disabling freq 2472 MHz
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974263] cfg80211: Disabling freq 2484 MHz
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974273] cfg80211: Regulatory domain changed to country: US
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974277] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974282] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974287] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974292] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974297] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974302] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.974307] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:24:35 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associated -> 4-way handshake
10/11/12 05:24:35 PM	joey-HP	wpa_supplicant[1246]	WPA: Key negotiation completed with 94:44:52:6d:ba:25 [PTK=CCMP GTK=CCMP]
10/11/12 05:24:35 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-CONNECTED - Connection to 94:44:52:6d:ba:25 completed (reauth) [id=0 id_str=]
10/11/12 05:24:35 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:24:35 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:24:35 PM	joey-HP	vmnetBridge	Adding interface wlan1 index:3
10/11/12 05:24:35 PM	joey-HP	vmnetBridge	Started bridge wlan1 to virtual network 0.
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.981885] /dev/vmnet: open called by PID 1397 (vmnet-bridge)
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.981906] /dev/vmnet: hub 0 does not exist, allocating memory.
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.981950] /dev/vmnet: port on hub 0 successfully opened
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.981971] bridge-wlan1: device is wireless, enabling SMAC
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.981979] bridge-wlan1: up
10/11/12 05:24:35 PM	joey-HP	kernel	[ 4955.982223] bridge-wlan1: attached
10/11/12 05:24:35 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: 4-way handshake -> completed
10/11/12 05:24:36 PM	joey-HP	kernel	[ 4956.182025] userif-2: sent link down event.
10/11/12 05:29:23 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:29:23 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00001003
10/11/12 05:29:23 PM	joey-HP	vmnetBridge	Removing interface wlan1 index:3
10/11/12 05:29:23 PM	joey-HP	vmnetBridge	Stopped bridge wlan1 to virtual network 0.
10/11/12 05:29:23 PM	joey-HP	kernel	[ 4956.182032] userif-2: sent link up event.
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.740229] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.740262] wlan1: Connection to AP 94:44:52:6d:ba:25 lost.
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.742245] bridge-wlan1: disabling the bridge on dev down
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.742413] bridge-wlan1: down
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.742427] bridge-wlan1: detached
10/11/12 05:29:23 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-DISCONNECTED bssid=94:44:52:6d:ba:25 reason=4
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.800766] cfg80211: All devices are disconnected, going to restore regulatory settings
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.800776] cfg80211: Restoring regulatory settings
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.800783] cfg80211: Calling CRDA to update world regulatory domain
10/11/12 05:29:23 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: completed -> disconnected
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808261] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808270] cfg80211: World regulatory domain updated:
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808274] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808280] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808285] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808291] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808296] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.808301] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:23 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: disconnected -> scanning
10/11/12 05:29:23 PM	joey-HP	kernel	[ 5243.942184] userif-2: sent link down event.
10/11/12 05:29:30 PM	joey-HP	wpa_supplicant[1246]	Trying to authenticate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:29:30 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: scanning -> authenticating
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5243.942190] userif-2: sent link up event.
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.530336] wlan1: authenticate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.532085] wlan1: authenticated
10/11/12 05:29:30 PM	joey-HP	wpa_supplicant[1246]	Trying to associate with 94:44:52:6d:ba:25 (SSID='Belkin.3A25' freq=2417 MHz)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.532374] wlan1: associate with 94:44:52:6d:ba:25 (try 1)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.536037] wlan1: RX ReassocResp from 94:44:52:6d:ba:25 (capab=0x411 status=0 aid=3)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.536047] wlan1: associated
10/11/12 05:29:30 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: authenticating -> associating
10/11/12 05:29:30 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:29:30 PM	joey-HP	wpa_supplicant[1246]	Associated with 94:44:52:6d:ba:25
10/11/12 05:29:30 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011003
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.555558] cfg80211: Calling CRDA for country: US
10/11/12 05:29:30 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associating -> associated
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563122] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563137] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563143] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563148] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563153] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563158] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563164] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563169] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563179] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563185] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563189] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563195] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563200] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563205] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563210] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563215] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563220] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563226] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563230] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563236] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563240] cfg80211: Disabling freq 2467 MHz
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563243] cfg80211: Disabling freq 2472 MHz
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563247] cfg80211: Disabling freq 2484 MHz
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563256] cfg80211: Regulatory domain changed to country: US
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563260] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563265] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563270] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563275] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563280] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563285] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.563290] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
10/11/12 05:29:30 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: associated -> 4-way handshake
10/11/12 05:29:30 PM	joey-HP	wpa_supplicant[1246]	WPA: Key negotiation completed with 94:44:52:6d:ba:25 [PTK=CCMP GTK=CCMP]
10/11/12 05:29:30 PM	joey-HP	wpa_supplicant[1246]	CTRL-EVENT-CONNECTED - Connection to 94:44:52:6d:ba:25 completed (reauth) [id=0 id_str=]
10/11/12 05:29:30 PM	joey-HP	vmnet-natd	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:29:30 PM	joey-HP	vmnetBridge	RTM_NEWLINK: name:wlan1 index:3 flags:0x00011043
10/11/12 05:29:30 PM	joey-HP	vmnetBridge	Adding interface wlan1 index:3
10/11/12 05:29:30 PM	joey-HP	vmnetBridge	Started bridge wlan1 to virtual network 0.
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.570925] /dev/vmnet: open called by PID 1397 (vmnet-bridge)
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.570945] /dev/vmnet: hub 0 does not exist, allocating memory.
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.570986] /dev/vmnet: port on hub 0 successfully opened
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.571004] bridge-wlan1: device is wireless, enabling SMAC
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.571013] bridge-wlan1: up
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.571019] bridge-wlan1: attached
10/11/12 05:29:30 PM	joey-HP	NetworkManager[1177]	<info> (wlan1): supplicant interface state: 4-way handshake -> completed
10/11/12 05:29:30 PM	joey-HP	kernel	[ 5250.770493] userif-2: sent link down event.
10/11/12 05:39:01 PM	joey-HP	CRON[7046]	(root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)

```

let me know if i'm missing something.. zip kernel/system log below.

Thanks very much in advance :)

---

### Post by Jakin on 2012-10-12
I had a kernel update to 3.2.0-32generic, yesterday; however nothing improved. 
I tried kernels 3.4 and 3.5, which were suggested [elsewhere](http://ubuntuforums.org/showthread.php?t=2054699&highlight=Toshiba+Satellite+freeze) on this forum (which wasn't the same hardware, but who knows i gave it a shot)- resulted in my machine not booting at all, so i had to fallback to my original kernel.

Also elsewhere on this forum, it was suggested to use " i8042.reset i8042.nomux " kernel parameter, to fix issues of unresponsive touchpad and keyboard, unfortunately this didn't work either.

---

### Post by Jakin on 2012-10-15
As it turns out, was a simple fix. Days of searching made me try other combinations. and finally adding =1 to the end of the Kernel string, has stopped the system from ever freezing up.

" i8042.reset i8042.nomux=1 " .

I'll marked as solved.

---

