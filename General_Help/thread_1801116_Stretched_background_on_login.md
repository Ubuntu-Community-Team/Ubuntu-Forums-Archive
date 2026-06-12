---
title: "Stretched background on login"
date: 2011-07-09
forum: General Help
---

### Post by charlesg99 on 2011-07-09
Hi guys and thanks for reading. 

I'm a new linux user and I tried many versions before I settled with ubuntu 11.04. I really like unity so far and, in my opinion, it is the best of the "futuristic" desktop. 

I have this problem though (have a look at the screenshot). The background gets stretched when I login in ubuntu. The weird thing is that it comes back to normal when I press a key or click somewhere... Anyone seen this? I installed the nvidia-current drivers and I'm running twin view. My main monitor (screenshot) is 1920x1200 and I have a small one as a second which is 1024x768. Everything works great except for that. I tried having the background spanning on both screen, centered, etc.

Any thoughts?

Thanks

---

### Post by wildmanne39 on 2011-07-10
> **charlesg99 said:**
> Hi guys and thanks for reading. 

I'm a new linux user and I tried many versions before I settled with ubuntu 11.04. I really like unity so far and, in my opinion, it is the best of the "futuristic" desktop. 

I have this problem though (have a look at the screenshot). The background gets stretched when I login in ubuntu. The weird thing is that it comes back to normal when I press a key or click somewhere... Anyone seen this? I installed the nvidia-current drivers and I'm running twin view. My main monitor (screenshot) is 1920x1200 and I have a small one as a second which is 1024x768. Everything works great except for that. I tried having the background spanning on both screen, centered, etc.

Any thoughts?

ThanksHi, there are a few things but we need more information run these commands in a terminal
```
sudo lshw
```
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

1. Have you changed any settings in compiz?
2. Use this link to resolve some issues with nvidia cards and a few others.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
I will wait to see the information you post before going on.

---

### Post by charlesg99 on 2011-07-10
Hi and thanks for your answer.

I tried the steps from the link you posted but it didn't do much. I noticed that it is choppy (like when I drag a window around) but since I'm a first time linux user I thought it was normal... 

I didn't change stuff in compiz and I'm not using any crazy animations.

here is the output of the 2 commands you pointed out:

```

charles@CharlesG-PC:~$ sudo lshw


DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       
ABI

   

charlesg-pc
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=60A0001F-C600-0007-DC3D-BCAEC524D512
  *-core
       description: Motherboard
       product: SABERTOOTH X58
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 107945980003297
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0702
          date: 11/16/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU 950 @ 3.07GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1366
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 3f
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 4GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             width: 64 bits
        *-bank:2
             description: DIMM
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 4GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             width: 64 bits
        *-bank:4
             description: DIMM
             product: ModulePartNumber04
             vendor: Manufacturer04
             physical id: 4
             serial: SerNum04
             slot: DIMM4
             size: 4GiB
             width: 64 bits
        *-bank:5
             description: DIMM [empty]
             product: ModulePartNumber05
             vendor: Manufacturer05
             physical id: 5
             serial: SerNum05
             slot: DIMM5
             width: 64 bits
     *-pci
          description: Host bridge
          product: 5520/5500/X58 I/O Hub to ESI Port
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 13
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:b000(size=4096) memory:f9e00000-f9efffff
           *-storage
                description: SATA controller
                product: 88SE9123 PCIe SATA 6.0 Gb/s controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: scsi6
                logical name: scsi7
                logical name: scsi13
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom emulated
                configuration: driver=ahci latency=0
                resources: irq:75 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16) memory:f9eff800-f9efffff memory:f9ee0000-f9eeffff
              *-disk:0
                   description: ATA Disk
                   product: INTEL SSDSA2M080
                   physical id: 0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sde
                   version: 2CV1
                   serial: CVPO9373007H080BGN
                   size: 74GiB (80GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=9fa83887
                 *-volume:0
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@6:0.0.0,1
                      logical name: /dev/sde1
                      version: 3.1
                      serial: 8ae4-5ff2
                      size: 98MiB
                      capacity: 100MiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2011-01-20 05:22:08 filesystem=ntfs label=Réservé au système state=clean
                 *-volume:1
                      description: Windows NTFS volume
                      physical id: 2
                      bus info: scsi@6:0.0.0,2
                      logical name: /dev/sde2
                      version: 3.1
                      serial: 96a6f313-35a8-e948-8e63-c5f7950547b8
                      size: 74GiB
                      capacity: 74GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2011-01-20 05:22:30 filesystem=ntfs state=clean
              *-disk:1
                   description: ATA Disk
                   product: OCZ-VERTEX2
                   physical id: 1
                   bus info: scsi@7:0.0.0
                   logical name: /dev/sdf
                   version: 1.24
                   serial: OCZ-IL7O1329WD55GP00
                   size: 111GiB (120GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=c5f338c1
                 *-volume
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@7:0.0.0,1
                      logical name: /dev/sdf1
                      version: 3.1
                      serial: 1c0840aa-7758-fd48-b716-51363a2ac88b
                      size: 111GiB
                      capacity: 111GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2011-01-19 22:51:40 filesystem=ntfs label=Programmes state=clean
              *-processor UNCLAIMED
                   description: SCSI Processor
                   physical id: 0.0.0
                   bus info: scsi@13:0.0.0
        *-pci:1
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 memory:f9f00000-f9ffffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:29 memory:f9ffe000-f9ffffff
        *-pci:2
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:c000(size=4096) memory:fa000000-fbcfffff ioport:d6000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF110 [Geforce GTX 570]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff
           *-multimedia
                description: Audio device
                product: GF110 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:34 memory:fbcfc000-fbcfffff
        *-pci:3
             description: PCI bridge
             product: 5520/5500/X58 I/O Hub PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-generic:0
             description: PIC
             product: 5520/5500/X58 I/O Hub System Management Registers
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: driver=i7core_edac latency=0
             resources: irq:0
        *-generic:1 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers
             vendor: Intel Corporation
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Control Status and RAS Registers
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress 8259 cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: PIC
             product: 5520/5500/X58 I/O Hub Throttle Registers
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 13
             width: 32 bits
             clock: 33MHz
             capabilities: 8259
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:a800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:a880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ac00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f9dff000-f9dff3ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:76 memory:f9df8000-f9dfbfff
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:2000(size=4096) memory:c0000000-c03fffff ioport:f8f00000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:65 ioport:d000(size=4096) memory:fbd00000-fbdfffff ioport:c0400000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB362 AHCI Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:16 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:fbdffc00-fbdffdff memory:c0400000-c040ffff
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a080(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:a480(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f9dfe000-f9dfe3ff
        *-pci:6
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fbe00000-fbefffff
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:07:01.0
                logical name: eth0
                version: 10
                serial: bc:ae:c5:24:d5:12
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.11 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:19 ioport:e800(size=256) memory:fbeffc00-fbeffcff memory:fbec0000-fbedffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 2
                bus info: pci@0000:07:02.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:18 memory:fbefe000-fbefe7ff ioport:ec00(size=128)
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:66 ioport:9c00(size=8) ioport:9880(size=4) ioport:9800(size=8) ioport:9480(size=4) ioport:9400(size=32) memory:f9dfc000-f9dfc7ff
           *-disk:0
                description: ATA Disk
                product: WDC WD740ADFD-00
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 21.0
                serial: WD-WMANS1889097
                size: 69GiB (74GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=89d39c96
              *-volume UNCLAIMED
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   version: 3.1
                   serial: e204390b-fa3a-8243-8871-f41da720baba
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-24 17:47:36 filesystem=ntfs label=Backup state=clean
           *-disk:1
                description: ATA Disk
                product: WDC WD740ADFD-00
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 21.0
                serial: WD-WMANS1893414
                size: 69GiB (74GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=89d39c96
              *-volume UNCLAIMED
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   version: 3.1
                   serial: e204390b-fa3a-8243-8871-f41da720baba
                   size: 69GiB
                   capacity: 69GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-24 17:47:36 filesystem=ntfs label=Backup state=clean
           *-disk:2
                description: ATA Disk
                product: WDC WD5000AAKS-0
                vendor: Western Digital
                physical id: 2
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: 01.0
                serial: WD-WCASY8185187
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e9b2924a
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: c06c38bd-219a-fb4e-be83-6d0004532bdd
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-19 22:50:59 filesystem=ntfs label=Data state=clean
           *-disk:3
                description: ATA Disk
                product: OCZ-VERTEX2
                physical id: 3
                bus info: scsi@3:0.0.0
                logical name: /dev/sdd
                version: 1.33
                serial: OCZ-G7853Y0T7957XGHN
                size: 107GiB (115GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002859f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdd1
                   logical name: /
                   version: 1.0
                   serial: fe062822-1817-4659-9401-a18d0da4dcb9
                   size: 102GiB
                   capacity: 102GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-07-08 22:44:41 filesystem=ext4 lastmountpoint=/ modified=2011-07-08 22:46:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-07-10 00:16:11 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdd2
                   size: 4799MiB
                   capacity: 4799MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdd5
                      capacity: 4799MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW SH-S183L
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9dfd000-f9dfd0ff ioport:1000(size=32)
charles@CharlesG-PC:~$ lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation GF110 [Geforce GTX 570] (rev a1)

```

Thanks for your time.

---

### Post by wildmanne39 on 2011-07-10
Hi, no the lagging is not normal, with your system it should be very smooth and quick. Did you do what the link mentioned?
Also you may want to look in additional drivers and see if there is another driver for your video card there and try it. I have to use the older driver for my nvidia card because the new driver does not like unity and my card, but mine is a older card. If there is not one there you might want to check nvidias website for a different driver. Also you should log out and click on your user name then go to the bottom of the screen and click on ubuuntu classic no effects and see if that helps. I am not going to be on here much today because I am writing a guide for the cube and effects. One more thing to check open synaptic and type in nvidia and make sure there is only one driver installed.

---

### Post by charlesg99 on 2011-07-10
Right, thanks for the tips, I'll try this tomorrow when I'll get back to my computer. Yes I did try the steps from the link in your last post but the result was the same.

I'm used to just double click on an installable driver and then it works... I downloaded a linux driver from the nvidia website but it is a .run file and I just don't know what to do with it :).  Haa, the joys of learning new softwares.

I'll report back tomorrow if I can get this fixed or if I can figure out what to do with the .run file.

---

### Post by charlesg99 on 2011-07-11
Well I can't figure it out...

I successfully installed the proprietary driver from nvidia and I still have the same problem. I tried a lot of solution I found googling but I still have a choppy ubuntu and my initial stretched background problem is still there. I tried the same driver with fedora 15 and it was nice and smooth with gnome 3/gnome shell. Pity that I really prefer the unity interface.

This is something that should be worked on... I'm a programmer myself and I have more than enough problem coding my applications. I don't really like loosing that much time fiddling with an os. I have a php contract at the moment and that is why I wanted to learn linux. I didn't mind learning shell commands but the drivers should work right after the installation I believe.

I choose ubuntu for it's accessibility but I've lost 3 days now just to set it up. It still doesn't work... I can't imagine trying to set up eclipse/apache/php/mysql based on that. Like I said, I really want it to work so I don't have to go with fedora.

Any more clues?

Cheers

---

### Post by wildmanne39 on 2011-07-12
Hi, you can open your nvidia manager and see if vblank is being used and rendering. VBlank is good if it is only being used in one place and not also in compiz.

---

### Post by charlesg99 on 2011-07-12
Hi,

 yeah I tried different things with the vsync in compiz and the nvidia settings but to no avail. Moving windows around is still very choppy. I'm including some screenshots if it can give some clues to what my problem might be.

First, the driver is reported as activated but not in use... How can I "use" it if it isn't already?

Second, the refresh rate is off in the monitor's panel even though it is set correctly in the nvidia settings and in compiz. I only have one option in there and it is 50hz.

Also, I don't know if it is normal but if I toggle "full screen" browsing a 1080p flash movie on youtube, the progress bar will have the width of my monitor ( 1920 ) but the movie itself seems to have the resolution of my small monitor ( 1024x768 ) and is centered above the progress bar... very odd.

This is frustrating, I feel so close to having the desktop environment that I want. 

Thanks for your time.

---

### Post by wildmanne39 on 2011-07-12
> **charlesg99 said:**
> Hi,

 yeah I tried different things with the vsync in compiz and the nvidia settings but to no avail. Moving windows around is still very choppy. I'm including some screenshots if it can give some clues to what my problem might be.

First, the driver is reported as activated but not in use... How can I "use" it if it isn't already?

Second, the refresh rate is off in the monitor's panel even though it is set correctly in the nvidia settings and in compiz. I only have one option in there and it is 50hz.

Also, I don't know if it is normal but if I toggle "full screen" browsing a 1080p flash movie on youtube, the progress bar will have the width of my monitor ( 1920 ) but the movie itself seems to have the resolution of my small monitor ( 1024x768 ) and is centered above the progress bar... very odd.

This is frustrating, I feel so close to having the desktop environment that I want. 

Thanks for your time.Hi,

1. That is just a bug it is really in use, mine and many other people says the same thing.

2. You can try to manually set the refresh rate but I do not think that is your problem, I have the same problem but it does not effect my system.

3. The youtube issue does not sound normal.

4. Since you have installed more the one driver for your video card open synaptic and type nvidia in the search window and make sure you have only one nvidia driver installed, this happened to me I had to manually remove the other one then my problem was solved. 

It will only show one in additional drivers so do not let that fool you, there may still be more then one installed in synaptic.

---

### Post by charlesg99 on 2011-07-13
Hi, I'm happy to say that half my problem is solved. 

Turns out that the lagging wasn't from the nvidia drivers... I came by chance across this article: [http://osdir.com/ml/ubuntu-bugs/2011-07/msg05029.html](http://osdir.com/ml/ubuntu-bugs/2011-07/msg05029.html) and that was my problem! I'm using a logitech g9 mouse that was polling 1000 time seconds. I turned it down to 500 and now there is no more lag when I drag a window around.

Now I only have the flash fullscreen problem and the stretched backround when I login but it looks like a known bug: [https://bugs.launchpad.net/unity/+bug/769458](https://bugs.launchpad.net/unity/+bug/769458)

Thanks for your support, I'm confident now!

---

### Post by charlesg99 on 2011-07-19
Hi, ok I found a workaround for the stretched background when I login: [http://www.shareconnector.com/ubuntu-11-04-dual-screen-tearing-fix-workaround](http://www.shareconnector.com/ubuntu-11-04-dual-screen-tearing-fix-workaround).

This solution fixes the tearing when I drag a window around but the settings in the nvidia x server settings won't save. How can I save so when I restart the changes will take effect?

Just to be clear, the only way I can fix the tearing problem is by unchecking "force full gpu scaling" and checking "aspect ratio" in the nvidia x server settings. The problem is that it won't save and after a reboot, the "force full gpu scaling" is checked again.

I tried running the nvidia x server settings as root but it still won't save. 

I also tried to modify my xorg.conf file with Option "FlatPanelProperties" "Scaling = aspect-scaled" but it still has the gpu scaling on. If I set the scaling as "Native" the gpu scaling will be disabled but I still get some tearing. 

Basically I just need to be able to save the nvidia settings so "force full gpu scaling" is disabled and the scaling mode is "aspect ratio".

Any clues?

---

