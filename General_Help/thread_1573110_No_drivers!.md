---
title: "No drivers!?"
date: 2010-09-12
forum: General Help
---

### Post by ardit ,A, on 2010-09-12
Hello im new here and at ubuntu.
I don't have an idea how to install drivers on ubuntu.
At **'Hardware Drivers****'** didn't show any drivers or anything :S
Please help!
 
My drivers: ViA Technologies.
Web: [www.via.com.tw]("http://www.via.com.tw")

---

### Post by jocko on 2010-09-12
Exactly what driver is missing?

---

### Post by ardit ,A, on 2010-09-12
Sound & Grahpic

---

### Post by jocko on 2010-09-12
What sound card do you have? Can you get it to produce any sound?
What graphics card?

---

### Post by ardit ,A, on 2010-09-12
My drivers: **ViA Technologies**.
Web: [http://www.via.com.tw](http://www.via.com.tw)

---

### Post by jerome1232 on 2010-09-12
I don't think we are understanding each other.

Most drivers come built into the kernel, you don't need to install additional ones.

If sound isn't working right then you might need sound drivers.

If 3D affects aren't working for you then you might need graphics drivers.


Is something not working? So, what drivers exactly are you needing? 

That link you provided doesn't work for me

---

### Post by ardit ,A, on 2010-09-12
-- I need just Graphic drivers for COUNTER-STRIKE
 
-- I think my graphics drivers are: S3 Graphics but really are ViA Technologies
 
[http://www.s3graphics.com/](http://www.s3graphics.com/)
 
-- I have a CD of my graphic and sound drivers but, I think they work just in windows I have installed these drivers on XP in each format.

---

### Post by jocko on 2010-09-12
> **ardit ,A, said:**
> My drivers: **ViA Technologies**.
Web: [http://www.via.com.tw](http://www.via.com.tw)
If your graphics card is a via integrated card, I think you already have the only working driver for it running. It is called "openchrome" and comes preinstalled in ubuntu by default. There is no proprietary (=closed source/non-free) driver for it, which is why the hardware driver manager does not suggest any driver for you.
Is the sound card really a via card? Never seen that they produce sound cards.

Just to see exactly what hardware you have (and if any drivers are really missing), could you run this command in a terminal:
```
sudo lshw
```Then copy and paste the entire output from the terminal to this thread.
Wrap it in code tags, that is paste it between [noparse]```
 and 
```[/noparse].

---

### Post by cascade9 on 2010-09-12
+1 to what you wrote jocko. Just FYI, VIA has made quite a few sound 'cards'.....most of which are onboard really, but a few of them werent. The VIA Envy chip based soundcards were even good cards.....

The drivers for all the VIA sound chips should be supported by the kernel and/or alsa these days.

---

### Post by ardit ,A, on 2010-09-12
> **jocko said:**
> If your graphics card is a via integrated card, I think you already have the only working driver for it running. It is called "openchrome" and comes preinstalled in ubuntu by default. There is no proprietary (=closed source/non-free) driver for it, which is why the hardware driver manager does not suggest any driver for you.
Is the sound card really a via card? Never seen that they produce sound cards.
 
Just to see exactly what hardware you have (and if any drivers are really missing), could you run this command in a terminal:
```
sudo lshw
```Then copy and paste the entire output from the terminal to this thread.
Wrap it in code tags, that is paste it between [noparse]```
 and 
```[/noparse].
 
Yes u're right.
My ViA drivers called: **Chrome** and the full name is: **ViA Chome9 HC IGP Family**
 
Right now i'm using Windows XP but when I will install i will try this:
 
```
sudo lshw
```

---

### Post by ardit ,A, on 2010-09-12
**This shows at TERMINAL**

```
ubuntu                    
    description: Desktop Computer
    product: P4M900T-M2
    vendor: ECS
    version: 2.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4M900T-M2
       vendor: ECS
       physical id: 0
       version: 2.0
       serial: 00000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080014 (01/11/2008)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) D CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: CPU 1
          size: 3066MHz
          capacity: 3066MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: memory:fd000000-feafffff memory:f8000000-fbffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f8000000-fbffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:1000(size=4096) memory:3c000000-3c1fffff memory:3c200000-3c3fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:2000(size=4096) memory:3c400000-3c5fffff memory:3c600000-3c7fffff(prefetchable)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=64
             resources: irq:21 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) ioport:e000(size=256)
           *-disk
                description: ATA Disk
                product: Hitachi HDS72161
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: P22O
                serial: PVG904Z23SJZZV
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005e632
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 90d16c1d-88d9-1b49-b86e-fa15383713c1
                   size: 51GiB
                   capacity: 51GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-09-05 01:04:11 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 97GiB
                   capacity: 97GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/1694EA2594EA06D9
                      capacity: 97GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DH20A4P
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 9P58
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:d480(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:22 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:21 ioport:d880(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: b0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:23 ioport:dc00(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:fcfffc00-fcfffcff
        *-isa
             description: ISA bridge
             product: VT8237S PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:1e:90:91:af:42
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:d000(size=256) memory:fcfff800-fcfff8ff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=128
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:febfc000-febfffff
     *-scsi
          physical id: 2
          bus info: usb@1:2
          logical name: scsi1
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             size: 3830MiB (4016MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=cdf74ddf
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: FAT32
                serial: 4ad7-9422
                size: 3821MiB
                capacity: 3826MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat

```

---

### Post by jocko on 2010-09-12
Hmmm...
Your sound chip is using the correct driver, so it should be working fine:
```
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: [COLOR=Blue]**driver=HDA Intel**[/COLOR] latency=0
          resources: irq:17 memory:febfc000-febfffff
```
If it's not working, you may need to find out if there is some advanced tweaking that has to be done to get sound working with that particular chip.

Unfortunately I have no idea what's up with your video chip.
```
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 mingnt=2
                resources: memory:f8000000-fbffffff(prefetchable) memory:fd000000-fdffffff memory:feaf0000-feafffff(prefetchable)
```
 Check that the openchrome driver is installed: Open up synaptic (System-->Administration-->Synaptic Package Manager) and search for the package "xserver-xorg-video-openchrome". If it's not installed, install it, reboot and keep your fingers crossed. Otherwise you'll have to find some more specific help about your particular video chip...

---

