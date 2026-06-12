---
title: "How do I connect to my wireless router?"
date: 2010-09-27
forum: General Help
---

### Post by morgothaod on 2010-09-27
I just installed Ubuntu 10.04 on one of my computers and the only way I can connect to the internet with it is through a wire.  I have a wireless router and I want to know how I can use the internet wirelessly on that machine.  The router is set up correctly because I am on the internet on my laptop (its a mac with OS X) and it is not connected by a wire.

I also want to know if Verizon DSL works with Ubuntu.

Thanks.

---

### Post by eddier on 2010-09-27
You either need a network card in your pc,something like these[http://www.novatech.co.uk/novatech/prods/networking/wirelessnetworking/wirelesspcicards/]("http://www.novatech.co.uk/novatech/prods/networking/wirelessnetworking/wirelesspcicards/"),or you need to connect to the router from the pc via an rj45 cable.

eddie

---

### Post by 3Miro on 2010-09-27
Assuming you already have a wireless card, then go to System -> Admin -> Hardware Drivers to see if you need special driver for it.

---

### Post by morgothaod on 2010-09-27
How  can I determine if I already have a wireless network adapter?

---

### Post by raafaell on 2010-09-27
> **morgothaod said:**
> How  can I determine if I already have a wireless network adapter?

Look around your desktop, and see if you find any antenna, if not, see if there's something to screw the antenna on the back of the tower, if not, then you don't have an adapter.

---

### Post by 3Miro on 2010-09-27
The command
```
 sudo lshw -X 
```
will display information about all of your hardware. I just cannot remember if it is -x or -X.

---

### Post by raafaell on 2010-09-27
> **3Miro said:**
> The command
```
 sudo lshw -X 
```
will display information about all of your hardware. I just cannot remember if it is -x or -X.

hey thanks, I was looking for that command, I used the sysinfo but that didn't bring so much info..
thanks

---

### Post by garner_nc on 2010-09-27
If you don't have an adapter you can buy a USB adapter pretty cheap. They're easy to use. Do some research and find a brand and model known to work with Linux.

You have anything else that connects to this router via wireless? Has it been configured correctly?

All the Best,
D. White

---

### Post by morgothaod on 2010-09-27
Here is the situation.  I have 2 computers in 2 different buildings.  The buildings are 15-20 feet from each other.  1 of the computers is a mid 1990s desktop with Windows 95 and Verizon DSL.  I would like to make the other computer get free internet.  It has Ubuntu on it.

Would I be better off switching the Windows 95 computer for the Ubuntu one?  That way I don't have to stress over being able to connect wirelessly with it (Since finding compatible wireless network cards for Ubuntu seems difficult and I have no idea how to set them up).  All I would need is to find a Linux router.

Is it easy to find compatible wireless cards (I would prefer a USB) for a Windows 95 machine?    I'm not computer savvy so all I want to do is plug in the card, install the CD (if I have to), and then have the internet work.

---

### Post by morgothaod on 2010-09-27
Does my pc have a wireless adapter?

> ERROR: Sorry, cannot run the X11/GTK interface because /usr/bin/lshw-gtk
 is not available.
HINT: Install the lshw-gtk package in Debian.
compaq-desktop            
    description: Mini Tower Computer
    product: Presario 4090US 470016-303
    vendor: Compaq
    version: W21CDBCB
    serial: 2H17JLD160R1
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=30323031-3030-3031-3030-313546374439
  *-core
       description: Motherboard
       product: 0708h
       vendor: Compaq
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 786K3 (05/03/2001)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.3.1
          slot: U12A
          size: 900MHz
          capacity: 1100MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 5
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 640MiB
          capacity: 1536MiB
        *-bank:0
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: DIMM1
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM2
             size: 128MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:2
             description: DIMM DRAM Synchronous 133 MHz (7.5 ns)
             physical id: 2
             slot: DIMM3
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via
          resources: irq:0 memory:90000000-93ffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:1000(size=4096) memory:80000000-800fffff memory:88000000-8fffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:3 memory:88000000-8fffffff(prefetchable) ioport:1000(size=256) memory:80000000-8000ffff memory:80020000-8003ffff(prefetchable)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 10
             serial: 00:08:54:d4:60:32
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=66 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:10 ioport:2800(size=256) memory:a0000000-a00000ff
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:2480(size=16)
           *-disk
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: APL.
                serial: 653106882166
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00026a18
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: bd7443cb-ec2c-48a6-8ed1-e0992c882105
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-09-27 20:23:59 filesystem=ext4 lastmountpoint=/target/&#65533;>&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;g &#65533;@&#65533;&#65533;B&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-09-27 21:06:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-09-27 21:07:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1224MiB
                   capacity: 1224MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1224MiB
                      capabilities: nofs
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-RW SOHR-5238S
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 4S07
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=66
             resources: irq:11 ioport:2440(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=66
             resources: irq:11 ioport:2460(size=32)
        *-bridge
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: driver=vt596_smbus latency=0
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:10 ioport:2000(size=256) ioport:2490(size=4) ioport:2494(size=4)


---

### Post by morgothaod on 2010-09-27
I think this will be the plan:

Buy a router, a long cable and run it to the Ubuntu computer.  Now, what router will be compatible with Ubuntu and Windows 95/98?  Also, will I need to do anything to set up the router or will it automatically work after I plug it in?

---

### Post by morgothaod on 2010-09-28
bump

---

### Post by morgothaod on 2010-09-28
bump

---

