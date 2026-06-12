---
title: "Boot up gone wrong on 9.10!"
date: 2010-05-06
forum: General Help
---

### Post by TheNerdAL on 2010-05-06
When I booted my computer up from coming back to school, it booted weird.

And also it won't let me go to administration or else it freezes. Help. :( 

Thanks. 

I can't attach a screenshot because it usually goes to my desktop but I can't see my icons or I can't go to the desktop folder. :(

---

### Post by TheNerdAL on 2010-05-06
If I don't get any help in like an hour, I am going to reinstall Ubuntu 9.10 and upgrade to 10.04. :/ Which will take some time.

---

### Post by Wee_Guy on 2010-05-06
Is it normal apart from having no icons? If the Places menu is still there, can you open your home folder?
If you're just stuck with a blank desktop, hitting Alt+F2 and entering ```
nautilus
``` might let you browse some folders.

I don't know for certain what the problem might be, but it could be related to your /home folder. Has anything happened to it lately?

Also, if you're contemplating re-installing, have a backup of 100% of ALL your files. Maybe also create an image of Ubuntu as it is just now if you have something like Clonezilla handy. At the very least, shrink the broken Ubuntu's partition and re-install into a new one. That way when you find a fix for this you won't have to reconfigure everything.

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> Is it normal apart from having no icons? If the Places menu is still there, can you open your home folder?
If you're just stuck with a blank desktop, hitting Alt+F2 and entering ```
nautilus
``` might let you browse some folders.

I don't know for certain what the problem might be, but it could be related to your /home folder. Has anything happened to it lately?

Also, if you're contemplating re-installing, have a backup of 100% of ALL your files. Maybe also create an image of Ubuntu as it is just now if you have something like Clonezilla handy. At the very least, shrink the broken Ubuntu's partition and re-install into a new one. That way when you find a fix for this you won't have to reconfigure everything.

Doesn't open, all I hear is my computer making a noise in a pattern. I think it's the ram. I did add 1 GB of ram but I checked using System Monitor and I had like 1.3 GiB of ram, which meant it was installed correctly.

---

### Post by Wee_Guy on 2010-05-06
Try replacing the old RAM, incase the new RAM is faulty.
Or test your RAM with either a Live CD (select test RAM option) or [Memtest86 ]("http://www.memtest86.com/")(same thing as on live CD). Be warned that testing RAM usually takes hours, so the fastest option would be to simply replace the old RAM and see if that fixes anything.

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> Try replacing the old RAM, incase the new RAM is faulty.
Or test your RAM with either a Live CD (select test RAM option) or [Memtest86 ]("http://www.memtest86.com/")(same thing as on live CD). Be warned that testing RAM usually takes hours, so the fastest option would be to simply replace the old RAM and see if that fixes anything.

Is there a way to check how much ram 

According to this: 
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
          size: 1536MiB
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
             size: 1GiB
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
                   configuration: created=2010-05-01 19:25:58 filesystem=ext4 lastmountpoint=/rP&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^d&#65533;&#65533;e&#65533; R&#65533;&#65533; R&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;^d&#65533;^d&#65533;Eh&#65533;&#65533;&#65533;&#65533;&#65533;&&#65533;q modified=2010-05-06 15:28:10 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-06 15:35:29 state=mounted
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
             resources: irq:19 ioport:c400(size=256) memory:dd120000-dd120fff memory:60100000-6011ffff(prefetchable)
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
             resources: memory:dd100000-dd10ffff(prefetchable) ioport:b000(size=4096) memory:b0000000-cfffffff memory:60000000-600fffff(prefetchable)
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
                resources: irq:17 memory:c2000000-c2ffffff memory:b0000000-bfffffff(prefetchable) memory:c0000000-c1ffffff ioport:b000(size=128) memory:60000000-6001ffff(prefetchable)
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

My ram is not faulty.

---

### Post by Wee_Guy on 2010-05-06
I may be wrong here, but it looks like that is just a listing of the hardware in your PC. RAM can be faulty without appearing faulty. Often the only way to tell that RAM is faulty is because the system crashes, and the only tool that can show that the RAM, and not anything else, is faulty is a RAM testing utility.

Also what do you mean by "computer making a noise in a pattern"? Is it coming from the speakers or the PC itself?

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> I may be wrong here, but it looks like that is just a listing of the hardware in your PC. RAM can be faulty without appearing faulty. Often the only way to tell that RAM is faulty is because the system crashes, and the only tool that can show that the RAM, and not anything else, is faulty is a RAM testing utility.

Also what do you mean by "computer making a noise in a pattern"? Is it coming from the speakers or the PC itself?

PC, when my computer loads like windows, it makes that noise, but when I boot up and try going to Administration, it makes that noise in a pattern.

---

### Post by TheNerdAL on 2010-05-06
I'll do the Memtest and post my results later.

---

### Post by Wee_Guy on 2010-05-06
The noise you're referring to could be the hard disk. If a light flashes on the front of the PC its probably the hard drive that's making the noise.

If that is the case, it is *possible *that the hard disk is trying to find data that is corrupt. Worst case scenario would be the hard drive itself being faulty or having a bad sector. 
However, as you mentioned that you've installed new RAM, its much more likely that the new RAM is faulty or not seated correctly, and is causing the system to behave strangely. Anyway, you've got a backup of everything, haven't you?

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> The noise you're referring to could be the hard disk. If a light flashes on the front of the PC its probably the hard drive that's making the noise.

If that is the case, it is *possible *that the hard disk is trying to find data that is corrupt. Worst case scenario would be the hard drive itself being faulty or having a bad sector. 
However, as you mentioned that you've installed new RAM, its much more likely that the new RAM is faulty or not seated correctly, and is causing the system to behave strangely. Anyway, you've got a backup of everything, haven't you?

I did the memtest and there are no errors and I don't have no important things to back up.

---

### Post by Wee_Guy on 2010-05-06
Try running the disk testing utility in Ubuntu Disk Utility. If you can't run that from your install you'd have to run it from a Live CD. It may not be a hardware fault, but it can't hurt to check.

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> Try running the disk testing utility in Ubuntu Disk Utility. If you can't run that from your install you'd have to run it from a Live CD. It may not be a hardware fault, but it can't hurt to check.

Okay, I'll post the results later.

---

### Post by TheNerdAL on 2010-05-06
How to I run disk testing utility?

---

### Post by TheNerdAL on 2010-05-06
Okay, it does have bad sectors. What do I do?

---

### Post by Wee_Guy on 2010-05-06
Don't trust the drive with anything. The drive is most likely failing, so try and get any data that you want to keep off it.

To be entirely sure that the drive is failing, once you've got all your stuff off it, reinstall Ubuntu and try to run it for a few days. Don't use it to store any data!
Scan the drive with the Ubuntu Disk Utility every few days and see if the number of bad sectors increases. If it doesn't increase you _*might *_be able to use the drive, but if it increases then the drive is failing.

I think that's best the way to deal with it, however if anyone thinks that I'm wrong don't hesitate to correct me.

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> Don't trust the drive with anything. The drive is most likely failing, so try and get any data that you want to keep off it.

To be entirely sure that the drive is failing, once you've got all your stuff off it, reinstall Ubuntu and try to run it for a few days. Don't use it to store any data!
Scan the drive with the Ubuntu Disk Utility every few days and see if the number of bad sectors increases. If it doesn't increase you _*might *_be able to use the drive, but if it increases then the drive is failing.

I think that's best the way to deal with it, however if anyone thinks that I'm wrong don't hesitate to correct me.

Can I install Ubuntu 9.10 then upgrade to 10.04?

---

### Post by Wee_Guy on 2010-05-06
Yes you can install whatever you want. You could even put windows on it if you felt so inclined. Just so long as you remember that the drive is probably failing, so anything that you do install will probably get broken eventually.

---

### Post by TheNerdAL on 2010-05-06
> **Wee_Guy said:**
> Yes you can install whatever you want. You could even put windows on it if you felt so inclined. Just so long as you remember that the drive is probably failing, so anything that you do install will probably get broken eventually.

Okay, is there any way to mark the 10 bad sectors so the Hard Drive just ignores them and uses other sectors? 

I might get a new Hard Drive anyways.

---

### Post by TheNerdAL on 2010-05-06
I doubt the problem I had at first had anything to do with the bad sectors, right?

---

### Post by TheNerdAL on 2010-05-06
I doubt the problem I had at first had anything to do with the bad sectors, right?

---

### Post by TheNerdAL on 2010-05-06
I doubt the problem I had at first had anything to do with the bad sectors, right?

---

### Post by TheNerdAL on 2010-05-06
I am thinking that the bad sectors weren't the problem to my original post.

---

### Post by TheNerdAL on 2010-05-06
Sorry, double post.

---

### Post by Wee_Guy on 2010-05-07
They probably are the cause, the data that was on those sectors that have since gone bad can't be acessed by Ubuntu, so that's probably why its not working. Yes, it will automatically ignore the bad sectors that are there now, but as more sectors go bad the data that is on them will dissappear.
The drive is supposed to reallocate bad sectors; ie: move the data to a different sector, but it would appear that the drive didn't manage to do that, and that was why it broke Ubuntu.

---

