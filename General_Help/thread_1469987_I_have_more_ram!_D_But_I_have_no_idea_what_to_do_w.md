---
title: "I have more ram! :D But I have no idea what to do with it now."
date: 2010-05-02
forum: General Help
---

### Post by TheNerdAL on 2010-05-02
So my friend gave me her old computer and I took the ram out and put it on my main computer, it wasn't that much, it was about 256 MB I think. Now I have no idea if it is defective or not, how can I check? Because it was sort of dusty and I forgot to ground myself while taking it off for the first time. 

Anyways, now that I have more ram, what can I do with it? :D 

I can see the difference though, but again I'm not sure if it's defective or not.

---

### Post by EarthMind on 2010-05-02
Don't you have a memtest86 option in grub? If so you can test your RAM for defects with it.

---

### Post by overdrank on 2010-05-02
Moved to General Help. :)

---

### Post by Macchi on 2010-05-02
> **TheNerdAL said:**
>  ...I took the ram out and put it on my main computer ... Now I have no idea if it is defective or not...

Most systems have a fast and simple memory test on boot that can be turned on or off in the BIOS settings. Additionally you may boot your system with the Ubuntu Desktop Live CD or with Knoppix and choose the Memory Test on the boot menu. The later memory tests are more comprehensive and normally take quite a long time. But can be a good insurance in case of doubt!



PS: Beware that there are many parameters to match when extending the system memory, such as latency times, bus speeds, BIOS settings, memory types, etc. Eventual failure can depend on many factors such as temperature, electromagnetic interference etc. Google for your computer model or motherboard model in order to find the correct memory type.

---

### Post by TheNerdAL on 2010-05-02
> **Macchi said:**
> 
PS: Beware that there are many parameters to match when extending the system memory, such as latency times, bus speeds, BIOS settings, memory types, etc. Eventual failure can depend on many factors such as temperature, electromagnetic interference etc. Google for your computer model or motherboard model in order to find the correct memory type.

All I know is that my computer is DDR1 and the memory was DDR1. O.o

---

### Post by Random_Dude on 2010-05-02
> **TheNerdAL said:**
> 

Anyways, now that I have more ram, what can I do with it? :D 


Install Windows Vista.:lolflag:

---

### Post by shaka_zulu on 2010-05-02
You can maybe see when you start your computer and memory start to counting. If you know how much RAM you had maybe you will see that you have more now. :) Other thing you can run memory test. How much RAM did you have previously?

---

### Post by TheNerdAL on 2010-05-02
> **EarthMind said:**
> Don't you have a memtest86 option in grub? If so you can test your RAM for defects with it.

My computer doesn't show grub, it just goes to boot up.

---

### Post by TheNerdAL on 2010-05-02
> **shaka_zulu said:**
> You can maybe see when you start your computer and memory start to counting. If you know how much RAM you had maybe you will see that you have more now. :) Other thing you can run memory test. How much RAM did you have previously?

Like 512 MB. :lolflag:

---

### Post by robert shearer on 2010-05-02
in a terminal type..
```
sudo lshw
```

this will produce a listing of your hardware in the terminal.
Scroll down to the memory entries and you can see which slots are populated and with what.

---

### Post by TheNerdAL on 2010-05-02
> **robert shearer said:**
> in a terminal type..
```
sudo lshw
```

this will produce a listing of your hardware in the terminal.
Scroll down to the memory entries and you can see which slots are populated and with what.

I have no idea what to look for:

```
adrian@adrian-desktop:~$ sudo lshw
[sudo] password for adrian: 
adrian-desktop            
    description: Desktop Computer
    product: PP156AA-ABA SR1315CL NA510
    vendor: Compaq Presario 061
    version: 0n41411RE101SALMO00
    serial: CNH4520KSS
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=0B000000-0000-0000-0000-000B0B0B0B0B
  *-core
       description: Motherboard
       product: Salmon
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.04
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.04 (10/29/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3100+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket 754
          size: 1800MHz
          capacity: 3700MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
             resources: ioport:a000(size=4096) memory:dd000000-dd0fffff memory:d0000000-d7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:d0000000-d7ffffff(prefetchable) memory:dd000000-dd01ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6Y160P0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y47E2PQE
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c6e09f94
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 88f77a64-af8b-48d1-9de9-ad173e6b8893
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-01 19:25:58 filesystem=ext4 lastmountpoint=/&#65533;&#65533; &#65533;Q0&#27194;^&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;e&#65533;&#65533;T&#65533;T&#65533;Q0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Eh&#65533;&#65533;Q0&#65533;&&#65533;&#65533;V modified=2010-05-01 19:46:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-02 13:35:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1082MiB
                   capacity: 1082MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1082MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-H492A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e000(size=256) ioport:c000(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:dd121000-dd121fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:dd122000-dd122fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:dd123000-dd123fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:dd124000-dd124fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:11:d8:44:db:e7
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:c400(size=256) memory:dd120000-dd120fff memory:30100000-3011ffff(prefetchable)
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:c800(size=8) ioport:cc00(size=4) ioport:d000(size=8) ioport:d400(size=4) ioport:d800(size=16) ioport:dc00(size=128)
        *-pci:1
             description: PCI bridge
             product: PEX8112 x1 Lane PCI Express-to-PCI Bridge
             vendor: PLX Technology, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: aa
             width: 64 bits
             clock: 66MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             resources: memory:dd100000-dd10ffff(prefetchable) ioport:b000(size=4096) memory:b0000000-cfffffff memory:30000000-300fffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:17 memory:c2000000-c2ffffff memory:b0000000-bfffffff(prefetchable) memory:c0000000-c1ffffff ioport:b000(size=128) memory:30000000-3001ffff(prefetchable)
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:dd110000-dd11ffff ioport:e400(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:16 memory:dd125000-dd1257ff ioport:e800(size=128)
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
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
adrian@adrian-desktop:~$ 


```

---

### Post by linuxman94 on 2010-05-02
> **TheNerdAL said:**
> 
```
adrian@adrian-desktop:~$ sudo lshw
[sudo] password for adrian: 
adrian-desktop            
    description: Desktop Computer
    product: PP156AA-ABA SR1315CL NA510
    vendor: Compaq Presario 061
    version: 0n41411RE101SALMO00
    serial: CNH4520KSS
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=0B000000-0000-0000-0000-000B0B0B0B0B
  *-core
       description: Motherboard
       product: Salmon
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.04
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.04 (10/29/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3100+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket 754
          size: 1800MHz
          capacity: 3700MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
    [COLOR="Red"] *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 768MiB
        *-bank:0
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MiB
             width: 64 bits[/COLOR]
     *-pci:0
          description: Host bridge
          product: 760/M760 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:d8000000-dbffffff
        *-pci:0
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master vga_palette
             resources: ioport:a000(size=4096) memory:dd000000-dd0fffff memory:d0000000-d7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 cap_list
                configuration: latency=0
                resources: memory:d0000000-d7ffffff(prefetchable) memory:dd000000-dd01ffff ioport:a000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
           *-disk
                description: ATA Disk
                product: Maxtor 6Y160P0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y47E2PQE
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=c6e09f94
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 88f77a64-af8b-48d1-9de9-ad173e6b8893
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-01 19:25:58 filesystem=ext4 lastmountpoint=/&#65533;&#65533; &#65533;Q0&#27194;^&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;e&#65533;&#65533;T&#65533;T&#65533;Q0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Eh&#65533;&#65533;Q0&#65533;&&#65533;&#65533;V modified=2010-05-01 19:46:22 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-02 13:35:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1082MiB
                   capacity: 1082MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1082MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-H492A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HP03
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e000(size=256) ioport:c000(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:20 memory:dd121000-dd121fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:21 memory:dd122000-dd122fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: irq:22 memory:dd123000-dd123fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:dd124000-dd124fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:11:d8:44:db:e7
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
             resources: irq:19 ioport:c400(size=256) memory:dd120000-dd120fff memory:30100000-3011ffff(prefetchable)
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:c800(size=8) ioport:cc00(size=4) ioport:d000(size=8) ioport:d400(size=4) ioport:d800(size=16) ioport:dc00(size=128)
        *-pci:1
             description: PCI bridge
             product: PEX8112 x1 Lane PCI Express-to-PCI Bridge
             vendor: PLX Technology, Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             version: aa
             width: 64 bits
             clock: 66MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             resources: memory:dd100000-dd10ffff(prefetchable) ioport:b000(size=4096) memory:b0000000-cfffffff memory:30000000-300fffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:17 memory:c2000000-c2ffffff memory:b0000000-bfffffff(prefetchable) memory:c0000000-c1ffffff ioport:b000(size=128) memory:30000000-3001ffff(prefetchable)
        *-communication UNCLAIMED
             description: Communication controller
             product: Conexant Systems, Inc.
             vendor: Conexant Systems, Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
             resources: memory:dd110000-dd11ffff ioport:e400(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:16 memory:dd125000-dd1257ff ioport:e800(size=128)
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
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
adrian@adrian-desktop:~$ 


```

The part I highlighted in [COLOR="Red"]red[/COLOR] shows the memory.  It looks like it is using the RAM so you are good to go.

Please mark your thread as SOLVED by using "Thread Tools" at the top of your first post.

---

### Post by TheNerdAL on 2010-05-02
> **linuxman94 said:**
> The part I highlighted in [COLOR="Red"]red[/COLOR] shows the memory.  It looks like it is using the RAM so you are good to go.

Please mark your thread as SOLVED by using "Thread Tools" at the top of your first post.

Thanks! :D And do I have good Ram or do I need more? Hulu desktop is playing a bit better now, but a bit of lag still.

---

### Post by mike555 on 2010-05-02
You could install " preload " it might use some of the extra ram to help load stuff faster .......

---

