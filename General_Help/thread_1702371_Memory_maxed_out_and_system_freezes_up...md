---
title: "Memory maxed out and system freezes up.."
date: 2011-03-07
forum: General Help
---

### Post by oxf on 2011-03-07
Is there something similar to the windows TSR thing in Linux? (terminate & stay resident)

The reason I ask is that after replacing my HD and reinstalling Maverick I've noticed the PC freezing up  afew times. It seems that memory gets used up and then doesnt free up after the application is closed. The last couple of times this happened today I was doing

1. Copying a number of photos from my flash drive to the HD
2. Burnt a disk with Brasero.

After doing this it froze and I had to crash the system and reboot. I don't remeber this happening before.

Apart from this memory problem it's working OK I think. Any advice on what I should do about this? My system specs are below

Thanks..

```
mbdb@M2000:~$ sudo lshw
m2000                     
    description: Notebook
    product: Presario M2000 (EK823EA#ABU)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF5452FZ2
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=A0C6B6B5-3E08-DA11-8B2A-00C09FF39778
  *-core
       description: Motherboard
       product: 3096
       vendor: Quanta
       physical id: 0
       version: 47.0E
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.13 (10/19/2005)
          size: 104KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot int5printscreen int9keyboard int14serial int17printer int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-30
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          slot: U23
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: U5
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: U6
             size: 512MiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff ioport:c8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0000000-c0000fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0001000-c0001fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0002000-c0002fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8400(size=16) memory:c0003000-c00033ff
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM121HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LS10
                serial: S2FDJDRZ800265
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=adf1adf1
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d2a10e86-a389-b94b-8c35-e7ce04fe95d1
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-03-05 12:37:43 filesystem=ntfs state=clean
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: c50b126a-7859-4109-a6ca-dd55cf3e36cd
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-05 18:25:55 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(^&#65533;&#65533;P&#65533;&#65533;&#65533;u!&#65533;(^&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;A&#65533;h&#65533;&#65533;&#65533;Yx!&#65533;o modified=2011-03-06 11:09:28 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-07 23:19:06 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 06d65032-bec4-4427-bceb-6bd7f26df6d4
                   size: 477MiB
                   capacity: 477MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD writer
                product: UJ-840D
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:c0200000-c02fffff memory:40000000-43ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:f3:97:78
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
           *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:20 memory:c0204000-c0205fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:05:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:c0200000-c0200fff ioport:a400(size=256) ioport:a800(size=256) memory:40000000-43ffffff memory:44000000-47ffffff
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003400-c00034ff
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003800-c00038ff
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
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:29:d2:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-27-generic firmware=N/A ip=192.168.1.68 link=yes multicast=yes wireless=IEEE 802.11bg
mbdb@M2000:~$ 

 
```

---

### Post by no2498 on 2011-03-08
open a terminal type free m click enter
or may be free -m
see if that helps

now install htop
to see what is using the memory
just type it in it tells you how to install it click enter
after installed it comes up in system info

---

### Post by oxf on 2011-03-08
> **no2498 said:**
> open a terminal type free m click enter
or may be free -m
see if that helps

now install htop
to see what is using the memory
just type it in it tells you how to install it click enter
after installed it comes up in system info

Thanks! I'll try that..

---

### Post by oxf on 2011-03-10
> **no2498 said:**
> open a terminal type free m click enter
or may be free -m
see if that helps

now install htop
to see what is using the memory
just type it in it tells you how to install it click enter
after installed it comes up in system info

Well I watched this for a day or so and this is whats happening. Firefox bin seems to be taking up quite a lot of memory as does Brasero. 
/user/lib/indicator-aplet seems to have a LOT of about 1.5% memory usages which all add up.

My initial problem seems to be that I tried to copy way too many photo's at once wich used up all the memory and froze system. I don't how much is reasonable to copy in one go since my RAM is 1GB? Brasero took a pile of memory too.

But I have two questions:

1. why isn't the memory freed up again when I've finished? It seems once it's used it's used and I need to eventually reboot. Right now after doing various tests and closing everything I am just using Firefox and almost all my memeory is used up!

2. Why isn't it transfered in to Swap? My swaps not being used in all this.

Any comments appreciated. Thanks

I'm wondering if I have something not configured properly

---

### Post by mcduck on 2011-03-10
> **oxf said:**
> Well I watched this for a day or so and this is whats happening. Firefox bin seems to be taking up quite a lot of memory as does Brasero. 
/user/lib/indicator-aplet seems to have a LOT of about 1.5% memory usages which all add up.

My initial problem seems to be that I tried to copy way too many photo's at once wich used up all the memory and froze system. I don't how much is reasonable to copy in one go since my RAM is 1GB. Brasero took a pile of memory too.

But I have two questions:

1. why isn't the memory freed up again when I've finished? It seems once it's used it's used and I need to eventually reboot. Right now after doing various tests and closing everything I am just using Firefox and almost all my memeory is used up!

2. Why isn't it transfered in to Swap? My swaps not being used in all this.

Any comments appreciated. Thanks

I'm wondering if I have something not configured properly
It should be freed as soon as isn't needed. . Are you looking at the first line in the "free" output, or the "-/+ buffers/cache"-line? As that's the one you should be looking at, the memory usage on the first line should grow close to the total amount of your RAM over time, as the memory not used by running applications is used as disc cache. (The memory used as cache still counts as free from any program's point of view, since if some program needs more memory some cached data can just be dropped. It's just a way of improving the performance by using the otherwise unused memory to store recently accessed data)

..and looking at the wrong numbers would explain the swap not being used as well, if you actually have enough fee memory then the swap shouldn't be used.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1506        506       1000          0         94        168
-/+ buffers/cache:        243       1263
Swap:         1498          0       1498
```
For example here the system & running programs are actually using 243MiB of RAM, with 1263MiB still free.

(That being said, Firefox, especially with lots of extensions and/or open tabs, is definitely a memory hog. And so are all the other browsers these days... Close the browser when doing some work that might need lots of memory)

---

### Post by oxf on 2011-03-10
> **mcduck said:**
> It should be freed as soon as isn't needed. . Are you looking at the first line in the "free" output, or the "-/+ buffers/cache"-line? As that's the one you should be looking at, the memory usage on the first line should grow close to the total amount of your RAM over time, as the memory not used by running applications is used as disc cache. (The memory used as cache still counts as free from any program's point of view, since if some program needs more memory some cached data can just be dropped. It's just a way of improving the performance by using the otherwise unused memory to store recently accessed data)

..and looking at the wrong numbers would explain the swap not being used as well, if you actually have enough fee memory then the swap shouldn't be used.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1506        506       1000          0         94        168
-/+ buffers/cache:        243       1263
Swap:         1498          0       1498
```For example here the system & running programs are actually using 243MiB of RAM, with 1263MiB still free.

(That being said, Firefox, especially with lots of extensions and/or open tabs, is definitely a memory hog. And so are all the other browsers these days... Close the browser when doing some work that might need lots of memory)

OK thanks for the reply. I was looking at "free" NOT +/- buffers/cache line.

This is what I get after doing some photo editing/copying. Does this look normal? I have 1GB Ram and 500MB swap partition
Thanks..

 ```
mbdb@M2000:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           874        825         48          0         13        617
-/+ buffers/cache:        194        679
Swap:          476          0        476
mbdb@M2000:~$ 

```

---

### Post by lithopsian on 2011-03-10
Looks OK.  Very little free memory, but most of the used memory is disk cache.  No swap in use at all.  You might want to look at your swappiness if no swap ever gets used.

---

### Post by jerome1232 on 2011-03-10
That looks fine, hardly any ram is getting used (194 MB's)


The rest is used as file cache and will be dropped if any application needs more ram for it's use.

---

### Post by beatskobe on 2011-03-10
Bump ;[?

---

### Post by oxf on 2011-03-10
> **jerome1232 said:**
> That looks fine, hardly any ram is getting used (194 MB's)


The rest is used as file cache and will be dropped if any application needs more ram for it's use.

OK thanks guys!
I'll maybe increase the swapiness though

---

