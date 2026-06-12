---
title: "dvd drive and other partitions no longer recognised after migration."
date: 2012-09-19
forum: General Help
---

### Post by robert shearer on 2012-09-19
I have migrated a 250Gb disk (containing several Ubuntu and Win installs) to a new 1Tb disk.

My Natty 11.04 and Oneiric 11.10 installs now fail to recognise any other partitions or the optical drive.

The other installs..Win XP, Lucid 10.04 and Maverick 10.10 all behave correctly.
The optical drive will boot a live cd/dvd.

Previously both the optical drive and the hard-drive were IDE and now the hard-drive is Sata, otherwise nothing has changed.

Bios recognises both devices.

It would seem to be something as to how devices are handled by Ubuntu since 10.10.... 

I am about to install 12.04 and would like to solve this before I do as I expect the problem will appear on that install also.

Thank you.

lshw=

```
 description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=F00EF00E-F00E-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: nForce
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (01/18/2005)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          slot: Socket 754
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 2GiB
     *-pci:0
          description: Host bridge
          product: nForce3 250Gb Host Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64
          resources: irq:0 memory:e0000000-e7ffffff(prefetchable)
        *-isa
             description: ISA bridge
             product: nForce3 250Gb LPC Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce 250Gb PCI System Management
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:12 ioport:e000(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
        *-usb:0
             description: USB Controller
             product: CK8S USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:ec003000-ec003fff
        *-usb:1
             description: USB Controller
             product: CK8S USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:ec004000-ec004fff
        *-usb:2
             description: USB Controller
             product: nForce3 EHCI USB 2.0 Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:ec005000-ec0050ff
        *-bridge
             description: Ethernet interface
             product: CK8S Ethernet Controller
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             logical name: eth1
             version: a2
             serial: 00:e0:4c:dd:7a:9e
             size: 100000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.1.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
             resources: irq:21 memory:ec000000-ec000fff ioport:b400(size=8)
        *-multimedia
             description: Multimedia audio controller
             product: nForce3 250Gb AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: irq:20 ioport:b800(size=256) ioport:bc00(size=128) memory:ec001000-ec001fff
        *-ide:0
             description: IDE interface
             product: CK8S Parallel ATA Controller (v2.5)
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH22LP20
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                serial: [HL-DT-STDVD-RAM GH22LP201.0008/05/09 7U01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: nForce3 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: scsi2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) ioport:dc00(size=128)
           *-disk
                description: ATA Disk
                product: ST31000333AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: CC3H
                serial: 9TE1HVXW
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8fdf7df3
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: daee078f-1d77-4046-9585-a76e9c9f7b34
                   size: 24GiB
                   capacity: 24GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2002-07-05 06:35:54 filesystem=ntfs label=winxp state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 799GiB
                   capacity: 799GiB
                   capabilities: primary extended partitioned partitioned:extended
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: d69b1b3a-d083-a144-8d51-12e7e3e92242
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-09-20 19:23:03 filesystem=ntfs state=clean
        *-pci:0
             description: PCI bridge
             product: nForce3 250Gb AGP Host to PCI Bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:e8000000-e9ffffff memory:c0000000-dfffffff(prefetchable)
           *-display:0
                description: VGA compatible controller
                product: RV350 AS [Radeon 9550]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:c0000000-cfffffff(prefetchable) ioport:9000(size=256) memory:e9010000-e901ffff memory:e8000000-e801ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AS [Radeon 9550] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff(prefetchable) memory:e9000000-e900ffff
        *-pci:1
             description: PCI bridge
             product: nForce3 250Gb PCI-to-PCI Bridge
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:ea000000-ebffffff memory:80000000-800fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 3c905B 100BaseTX [Cyclone]
                vendor: 3Com Corporation
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: eth2
                version: 24
                serial: 00:10:5a:72:3c:dc
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
                resources: irq:19 ioport:a000(size=128) memory:eb000000-eb00007f memory:80000000-8001ffff(prefetchable)
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



```

---

### Post by oldfred on 2012-09-20
I do not know about AMD, as I have Intel.

But I would download 12.04.1 liveCD and test it to see if it works. And make sure you have good backups before installing.

Since you have lots of room on new 1TB drive you can just make another 25GB partition and install to that for a longer test if liveCD works. Then you still have all your old installs.

Is BIOS in IDE, SATA, AHCI or other mode?

---

### Post by robert shearer on 2012-09-20
@oldfred > But I would download 12.04.1 liveCD and test it to see if it works. And make sure you have good backups before installing.

Since you have lots of room on new 1TB drive you can just make another 25GB partition and install to that for a longer test if liveCD works. Then you still have all your old installs.

Done :-)   Everything was uber-backed up **before** I migrated to the new drive. ( I am a slow learner but I do learn. :-) eventually. )

Yes, I downloaded and ran the live 12.04 and it didn't give the errors that the two errant installs have so I installed it and it runs just peachey.

Two other strange things now discovered,
 in WinXP all the NTFS partitions show as being removable drives in the taskbar...including the running C-drive !...
Trying to install Vista it threw an error about "not finding a volume that meets **it's** criteria for install" (sheesh, what about my criteria ! Perhaps Tinyflaccid.corp don't know that its **my computer **not theirs.)

So some Googling seems to suggest that this old mobo has sata as an afterthought for some sort of raid work-around and, as such, the drives connected are seen as hot-swappable. Hence Vistas refusal to party and XP's offer to remove itself.... 

This may be at the heart of the problems with my 11.04 and 11.10 though, **as 12.04 is now installed and working as it should**, I think that maybe fstab in those other installs is borked.

Any comments or suggestions for fixing that would be appreciated.

(as the mobo is pre Vista I may try a bios update and see if that fixes the install refusal...any thoughts?)

thank you.

---

### Post by oldfred on 2012-09-20
Windows will not install to removable drives. 

I usually upgrade BIOS, but some suggest not to as that can "brick" computer if not done correctly.

My system is from 2006 and SATA was just becoming the standard. Hard drives were still $10 or $20 more than IDE. And I bought my parts the same day Samsung came out with a SATA DVD drive for only a few $ more than the PATA version, when the Sony SATA DVD was twice the cost of the PATA versions. So I converted 100% to SATA. Have not looked back to IDE, cannot see nor handle those tiny jumpers anymore anyway.

---

### Post by robert shearer on 2012-09-20
> Windows will not install to removable drives. 

Yes, so I have to find some way of getting the mobo to see my sata as not removable. Cannot find anything in the current bios that I could change to do this.
I have seen mention of moving from ahci to ide emulation in bios which is why I may try a bios update to see if this gives that option.

Yes, know about bricks..:-)  Hasn't happened yet but theres always a first time.

>  cannot see nor handle those **tiny jumpers** anymore anyway. 

yes, they are somewhat like a 'flea circus' always pinging off to be lost in the detritus and dust bunnies below the desk. :-)


Edit.. Don't know why, don't know how but the problem on the Ubuntu installs seems to have resolved itself. perhaps several reboots were needed or there has been a disk check or even something I adjusted in bios.  Shrug..?

I will mark this as solved and go try getting Vista to play nice. (oxymoron ?)

thanks for all the views and help.

---

