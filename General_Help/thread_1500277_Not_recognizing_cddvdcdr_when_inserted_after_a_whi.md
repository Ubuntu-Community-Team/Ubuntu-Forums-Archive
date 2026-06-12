---
title: "Not recognizing cd/dvd/cdr when inserted after a while."
date: 2010-06-03
forum: General Help
---

### Post by SpaceBison on 2010-06-03
I have a SAMSUNG DVD Burner SH-S182M/BEBM which works fine under previous releases of Ubuntu and Windows XP. If I turn the computer on with a disk already in the drive or insert within a few minutes of turning it on then it'll recognize and play/burn it fine. But if the computer has been on for a little while (10~20 minutes), nothing. It won't mount, nothing shows up under Places, if I click on Places>Computer>CDRom nothing happens. Nor does anything show up with dmesg. Even media that was already in and recognized when I turned it on will just disappear after 10 minutes or so.

I found this bug (fixed?) which seems to be similar, but when I go to the disk utility it just says no media detected.
[https://bugs.launchpad.net/ubuntu/lucid/+source/udev/+bug/554433]("https://bugs.launchpad.net/ubuntu/lucid/+source/udev/+bug/554433")

> ~$ lshw
spacebison                
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2008MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
     *-pci
          description: Host bridge
          product: C55 Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.6
             bus info: pci@0000:00:00.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 0.7
             bus info: pci@0000:00:00.7
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:11 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:12 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:13 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:14 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:15 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:16 UNCLAIMED
             description: RAM memory
             product: C55 Memory Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: C55 PCI Express bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:9000(size=4096) memory:cd000000-ceffffff ioport:a0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:cd000000-cdffffff memory:a0000000-afffffff(prefetchable) memory:be000000-bfffffff(prefetchable) ioport:9c00(size=128.) memory:b0000000-b007ffff(prefetchable)
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:ceffc000-ceffffff
        *-memory:17 UNCLAIMED
             description: RAM memory
             product: MCP55 Memory Controller
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP55 LPC Bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:fc00(size=128.)
        *-serial
             description: SMBus
             product: MCP55 SMBus
             vendor: nVidia Corporation
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:255 ioport:f800(size=64) ioport:f400(size=64) ioport:f000(size=64)
        *-usb:0
             description: USB Controller
             product: MCP55 USB Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:cffff000-cfffffff
        *-usb:1
             description: USB Controller
             product: MCP55 USB Controller
             vendor: nVidia Corporation
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:cfffe000-cfffe0ff
        *-ide:0
             description: IDE interface
             product: MCP55 IDE
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: scsi3
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8.) ioport:3f6 ioport:170(size=8.) ioport:376 ioport:ec00(size=16)
           *-cdrom
                description: DVD-RAM writer
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
        *-ide:1
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:21 ioport:9f0(size=8.) ioport:bf0(size=4) ioport:970(size=8.) ioport:b70(size=4) ioport:d800(size=16) memory:cfffd000-cfffdfff
        *-ide:2
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: nVidia Corporation
             physical id: e.1
             bus info: pci@0000:00:0e.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:20 ioport:9e0(size=8.) ioport:be0(size=4) ioport:960(size=8.) ioport:b60(size=4) ioport:c400(size=16) memory:cfffc000-cfffcfff
        *-ide:3
             description: IDE interface
             product: MCP55 SATA Controller
             vendor: nVidia Corporation
             physical id: e.2
             bus info: pci@0000:00:0e.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:21 ioport:c000(size=8.) ioport:bc00(size=4) ioport:b800(size=8.) ioport:b400(size=4) ioport:b000(size=16) memory:cfffb000-cfffbfff
        *-pci:1
             description: PCI bridge
             product: MCP55 PCI bridge
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:8000(size=4096) memory:c4000000-cbffffff memory:80000000-83ffffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2
                resources: irq:19 memory:cbfff000-cbfff7ff memory:cbff8000-cbffbfff
           *-pcmcia
                description: CardBus bridge
                product: RL5c475
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 81
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603020-b0060301f irq:17 memory:cbffe000-cbffefff ioport:8000(size=256) ioport:8c00(size=256) memory:80000000-83ffffff(prefetchable) memory:c4000000-c7ffffff
           *-multimedia
                description: Multimedia audio controller
                product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
                vendor: VIA Technologies Inc.
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ICE1724 latency=32
                resources: irq:18 ioport:8800(size=32) ioport:8400(size=128.)
        *-bridge:0
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth0
             version: a2
             serial: 00:04:4b:05:c2:92
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.2.102 latency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:25 memory:cfffa000-cfffafff ioport:ac00(size=8.) memory:cfff9000-cfff90ff memory:cfff8000-cfff800f
        *-bridge:1
             description: Ethernet interface
             product: MCP55 Ethernet
             vendor: nVidia Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth1
             version: a2
             serial: 00:04:4b:05:c2:93
             width: 32 bits
             clock: 66MHz
             capabilities: bridge bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes
             resources: irq:26 memory:cfff7000-cfff7fff ioport:a800(size=8.) memory:cfff6000-cfff60ff memory:cfff5000-cfff500f
  *-scsi:0
       physical id: 1
       bus info: scsi@0
       logical name: scsi0
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@11
       logical name: scsi11
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:2
       physical id: 3
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:3
       physical id: 4
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage


> ~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
02:0a.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


---

### Post by SpaceBison on 2010-06-06
bump

---

