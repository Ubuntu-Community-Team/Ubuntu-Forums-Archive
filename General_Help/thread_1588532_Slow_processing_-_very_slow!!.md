---
title: "Slow processing - very slow!!"
date: 2010-10-05
forum: General Help
---

### Post by rhomp2002 on 2010-10-05
I am using Ubuntu on an old computer and it is going very slow for browsing.  I have tried Firefox, Chromium and Opera and it is so slow as to be useless.  I entered a URL and I have time to make tea while waiting for the computer to bring up the website.

I also have a 32 bit beta version of Wolvix on the computer and it works very fast.  I have no problems with bringing up the websites on the Wolvix.  The Ubuntu is so slow that I am about to give it up on the distro.  This is the 64 bit version of 10.04.  I have found that I cannot enter a URL on the browser and then try to look at any emails at the same time.   It feels like the browser is locking up.  In fact with Chromium I keep getting the message that I can either kill the entry or wait.

I have been using Ubuntu off and on for about 3 years now and this is by far the worst performance I have had.  Earlier versions of Ubuntu were used on this same computer and worked just fine.  I really liked Ubuntu for what it brings to the table but this performance is so bad I am thinking of going with something else instead.

For the most part my use of the computer is for browsing and emails.  Occasionally I will do something else but not often and not heavy computing either.  Right now the distro is set up to have 60 GB and I am using 6 GB so there should be plenty of space out there for whatever I want to do.  The problem is not restricted to certain websites.  It seems to happen with whatever website I am trying to access - NYT or google or even this website.  No idea where to look to try to speed it up.  I added the Faster Fox add-on thinking that might help but it didn't seem to do anything at all.   I don't have any special security programs added to slow things down either.

---

### Post by robert shearer on 2010-10-05
This....
> I am using Ubuntu on an old computer
..is too vague and not likely to get you any help with your problem.

Posting some specifications would be of use.

Try running...
```
sudo lshw
```
in a terminal and copy and paste the output here.

---

### Post by lovinglinux on 2010-10-05
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

Also check my optimization tutorials.

---

### Post by bonixavier on 2010-10-05
Couldn't it be the fact that you're using the 64bit version in an old computer? Have you tried the 32bit? It might work faster.

---

### Post by TBABill on 2010-10-05
Could be a lot of things. Using an open source driver could be causing a problem, conflicting plugins, IPV6 as LovingLinux stated and other things. Adobe Flash, Java, etc. Too many options to narrow down till you provide a bit more info. 

1. What video card? 
2. System specs (RAM, CPU)
3. Adobe flash or open source flash?
4. Sun Java or open source java?
5. All codecs installed? (ubuntu-restricted-extras)
6. Where is the problem beginning or worst at? Any website, even basic text sites, or heavy flash or graphics pages?

Edit: also if you have the iced tea plugin and Sun Java plugin at the same time you will have horrible browser performance

---

### Post by robert shearer on 2010-10-05
> Could be a lot of things.

Yeah, like not enough ram etc etc etc .
Until the o/p posts some specs we're fishing in the dark.

---

### Post by rhomp2002 on 2010-10-07
Here is the lshw:

    description: Desktop Computer
    product: Product Name
    vendor: System Manufacturer
    version: SYS-xxxxxx
    serial: Serial number xxxxxx
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: K8-800T MAX
       vendor: First International Computer, Inc.
       physical id: 0
       version: PCB 1.x
       serial: Serial number xxxxxx
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/15/2003)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3000+
          slot: Socket A
          size: 800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up rep_good cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 512MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
     *-pci:0
          description: Host bridge
          product: VT8385 [K8T800 AGP] Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-amd64 latency=8
          resources: irq:0 memory:0-7ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: memory:e0000000-e1ffffff memory:d8000000-dfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:e0000000-e0ffffff memory:d8000000-dfffffff(prefetchable) memory:e1000000-e101ffff(prefetchable)
        *-multimedia
             description: Multimedia audio controller
             product: SB Live! EMU10k1
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2
             resources: irq:17 ioport:9000(size=32)
        *-input
             description: Input device controller
             product: SB Live! Game Port
             vendor: Creative Labs
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Emu10k1_gameport latency=32
             resources: irq:0 ioport:9400(size=8)
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32
             resources: irq:16 memory:e2000000-e20007ff ioport:9800(size=128)
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32
             resources: irq:20 ioport:9c00(size=8) ioport:a000(size=4) ioport:a400(size=8) ioport:a800(size=4) ioport:ac00(size=16) ioport:b000(size=256)
           *-disk
                description: ATA Disk
                product: Maxtor 6Y120M0
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: YAR5
                serial: Y3MN6DGE
                size: 114GiB (122GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c0de3
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 141afe8c-05de-448a-ac89-aefa93616f53
                   size: 63GiB
                   capacity: 63GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-08-11 14:41:35 filesystem=ext4 lastmountpoint=/(&#65533;&#65533;&#65533;&#65533;G1o&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;8&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&#65533;&#1480;&#65533;&#65533;s&#65533;&#65533;&#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-10-05 04:16:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-07 21:14:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1443MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 28GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1287MiB
                      capabilities: nofs
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1.0
                   serial: 2ba500d4-b8b5-43db-9c60-050f3681093a
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2010-10-02 04:32:53 filesystem=ext3 modified=2010-10-07 19:32:07 mounted=2010-10-07 08:58:12 state=clean
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b400(size=16)
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:b800(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:bc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:c000(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:c400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:e2001000-e20010ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: 00:40:ca:83:61:30
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=24.239.148.221 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:c800(size=256) memory:e2002000-e20020ff
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




Will be out of town over the weekend so will check back on Tuesday.  I will try some of the other things then and maybe someone will see something in the hw list.  Appreciate any help.

I have a newer compute with the i7/860 chip so I can use that but I want to make sure this one also works just in case.  I had to have the MOBO on the newer computer replaced because of manufacturing defects so I broke out the old AMD Athlon XP so I could keep it going.   Last time I had a problem with a computer I came back to over 1000 emails stacked up and spent 2 days just clearing them out.

Any help would be appreciated.  Thanks.

---

### Post by robert shearer on 2010-10-08
This is your **old** computer ?.

I am posting from a computer with the same cpu and chipset/different mobo and it is my **newest** computer ! :).

Runs like a rocket with ubuntu 10.10. so your troubles should be sortable.

From what I can see you only have 512Mb ram which is on the low side but still useable.

Assuming other apps run ok (music, video, photo editing) and the 'slowness' is only web browsing then a couple of things to try would be to disable IPV6 and to try a different dns. Though if Wolvix browser is good then dns is probably not the fault.

So open Firefox and...
Enter in the URL address box:

```
about:config
```

Click "I'll be careful"

Type ipv6 in the filter box to get to the one and only line that's needed; it'll say > network.dns.disableipv6

the default value is "false"; double-click to set the value to "true" (to disable IPv6)

close and restart Firefox.

---

