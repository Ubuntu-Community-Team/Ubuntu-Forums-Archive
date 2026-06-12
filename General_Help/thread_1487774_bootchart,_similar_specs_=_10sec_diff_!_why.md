---
title: "bootchart, similar specs = 10sec diff ! why?"
date: 2010-05-19
forum: General Help
---

### Post by SlugSlug on 2010-05-19
]Hi all,

My Friend and I have a similar spec PC apart from mine has 4GB DDR2 his 2GB DDR2 and Mine quad core 2.3Ghz  and his Dual core 2.3Ghz....

Both on a fresh 10.04 install with Grub2

His Bootchart beats mine by about 10sec  can anyone see why?

[Files Attached]

Edit files here: (Attached got resized)

Mine : [http://i.imgur.com/nNliN.png](http://i.imgur.com/nNliN.png)
Friend : [http://imgur.com/VBB2y.png](http://imgur.com/VBB2y.png)

Many Thanks,

---

### Post by DawieS on 2010-05-19
I would suggest that you compare the BIOS (and Ubuntu) settings on your and your friend's PC. Generally speaking, the boot-time will be faster if non-existent features are disabled in the BIOS. I have read somewhere that by just disabling a floppy-drive (if it does not exist) cuts about 10 seconds off (saves Ubuntu to search for a non-existent floppy drive if the BIOS indicates otherwise).

Another factor could be the location where Ubuntu is installed on the disk (First partition on outermost edge vs. last partition innermost). The disk RPM stays constant, resulting in a considerable difference in reading speeds.
:smile:

---

### Post by SlugSlug on 2010-05-20
Hi Thanks for your reply,

My BIOS is pretty tidy floppy etc disabled and ubuntu in second on my disk after a 1gig swap...

I noticed dmraid dragged out abit so today am going to shift data and remove / replace the raid with LVM to see if that helps (its purely used as a storage drive)

---

### Post by SlugSlug on 2010-05-20
Replacing the RAID with lvm didn't increase boot time.

---

### Post by dino99 on 2010-05-20
these 2 pc are so different you can compare them, and i suppose the formatting settings and grub settings different too.

---

### Post by cascade9 on 2010-05-20
You cant compare computers just on RAM/CPU speed alone. (this is not really what I think is happening here, I'm just making apoint). Eg- computer 'a', AMD 5000+ dual core (512k x 2) 2.6Ghz, DDR2 667, 320GB SATA vs computer 'b', AMD Phenom II X4 910 (512k x 4, +6MB L3) 2.6Ghz, DDR3 1600, 60GB SATA2 SSD. Computer 'b' will eat compter 'a' for breakfast on everything except data storage space. Boots times would be a lot faster. 

As for the bootchats- dmraid appears to be really slowing the bootimes down. Thats the main diffrence I can see.

---

### Post by SlugSlug on 2010-05-20
I remove the dmraid and my boot did not improve,

both fresh 64bit installs ext4 and grub2

---

### Post by cascade9 on 2010-05-20
> **SlugSlug said:**
> I remove the dmraid and my boot did not improve,

both fresh 64bit installs ext4 and grub2

 I would have expected about 3-6 secodns faster with dmraid removed. 

Do you have more detailed system specifications for the 2 systems?

---

### Post by SlugSlug on 2010-05-20
is there an app that will dump out all the info you want?

---

### Post by cascade9 on 2010-05-21
'sudo lshw' would show all that I would be interested in...and quite a bit more than I need ;)

---

### Post by SlugSlug on 2010-05-21
ok..

MINE: 
```

    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=C0C1A2FE-70A5-DD11-9F4C-0023546F480E
  *-core
       description: Motherboard
       product: P5Q SE2
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MS1C8AB75202743
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0601 (04/29/2009)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU Q8200 @ 2.33GHz
          serial: To Be Filled By O.E.M.
          slot: LGA775
          size: 2003MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 1066 MHz (0.9 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous 1066 MHz (0.9 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:b000(size=4096) memory:fa000000-fe8fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G94 [GeForce 9600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe880000-fe8fffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ac00(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f9fffc00-f9ffffff
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
             resources: irq:22 memory:f9ff8000-f9ffbfff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:f0000000-f03fffff ioport:f8f00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:fea00000-feafffff memory:f0400000-f05fffff(prefetchable)
           *-ide
                description: IDE interface
                product: 88SE6101 single-port PATA133 interface
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: scsi4
                version: b2
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list emulated
                configuration: driver=pata_marvell latency=0
                resources: irq:16 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16) memory:feaffc00-feaffdff
              *-disk
                   description: ATA Disk
                   product: Maxtor 6L200P0
                   vendor: Maxtor
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sdd
                   version: BAH4
                   serial: L40ZYBPG
                   size: 189GiB (203GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=1e59fb24
                 *-volume:0
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@4:0.0.0,1
                      logical name: /dev/sdd1
                      logical name: /Stuff
                      version: 1.0
                      serial: b7161929-e8a1-444e-b1a5-2e7075aca7c9
                      size: 95GiB
                      capacity: 95GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2010-05-13 21:21:07 filesystem=ext4 label=Stuff lastmountpoint=/Stuff}fï¿½ï¿½ï¿½Ø&#8218;R(}fï¿½ï¿½ï¿½Sï¿½ï¿½ï¿½@+ï¿½ï¿½ï¿½ï¿½ï¿½&ï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ modified=2010-05-20 20:48:05 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:48:05 state=mounted
                 *-volume:1
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 2
                      bus info: scsi@4:0.0.0,2
                      logical name: /dev/sdd2
                      logical name: /home/xbox
                      version: 1.0
                      serial: 6274fe06-eead-4b08-9959-f626579161c5
                      size: 59GiB
                      capacity: 59GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2009-10-24 15:34:53 filesystem=ext4 label=xbox lastmountpoint=/home/.xboxï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½(]ï¿½ï¿½ï¿½ï¿½?ï¿½ï¿½ï¿½ï¿½@ï¿½ï¿½ï¿½ï¿½@ï¿½-ï¿½ï¿½ï¿½ï¿½nï¿½ modified=2010-05-20 20:47:53 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:47:53 state=mounted
                 *-volume:2
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@4:0.0.0,3
                      logical name: /dev/sdd3
                      logical name: /Backup
                      version: 1.0
                      serial: 36248dcf-cb1d-4110-ba02-8a324d1ceff6
                      size: 34GiB
                      capacity: 34GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                      configuration: created=2010-03-14 09:19:14 filesystem=ext4 label=Backup lastmountpoint=/Backup8ï¿½ï¿½Qï¿½ï¿½ï¿½&ï¿½ï¿½(ï¿½ï¿½Qï¿½ï¿½ï¿½ï¿½Ë&#710;ï¿½ï¿½@ï¿½ï¿½Qï¿½ï¿½ï¿½ï¿½ï¿½BNï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½ modified=2010-05-20 20:47:52 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:47:52 state=mounted
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:c000(size=4096) memory:fe900000-fe9fffff ioport:f8e00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:54:6f:48:0e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:c800(size=256) memory:f8eff000-f8efffff(prefetchable) memory:f8ee0000-f8eeffff(prefetchable) memory:fe9f0000-fe9fffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f9fff800-f9fffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff memory:f0600000-f06fffff(prefetchable)
           *-storage
                description: RAID bus controller
                product: SiI 3114 [SATALink/SATARaid] Serial ATA Controller
                vendor: Silicon Image, Inc.
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: scsi5
                logical name: scsi7
                logical name: scsi8
                logical name: scsi9
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: storage pm bus_master cap_list rom emulated
                configuration: driver=sata_sil latency=64
                resources: irq:18 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) memory:febffc00-febfffff memory:f0600000-f067ffff(prefetchable)
              *-disk:0
                   description: EXT4 volume
                   product: WDC WD1600AAJS-7
                   vendor: Linux
                   physical id: 0
                   bus info: scsi@5:0.0.0
                   logical name: /dev/sde
                   version: 1.0
                   serial: 4e1d4b5b-3119-480a-85eb-8998b05b4167
                   size: 596GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: ansiversion=5 created=2010-05-20 20:43:53 filesystem=ext4 lastmountpoint=/Downloads]ï¿½ï¿½ï¿½ï¿½{ï¿½ï¿½(]ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½4ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½dï¿½Â&#710;ï¿½ï¿½ï¿½nï¿½ï¿½ modified=2010-05-20 20:48:03 mounted=2010-05-20 20:48:03 state=clean
              *-disk:1
                   description: ATA Disk
                   product: WDC WD1600AAJS-7
                   vendor: Western Digital
                   physical id: 1
                   bus info: scsi@7:0.0.0
                   logical name: /dev/sdf
                   version: 01.0
                   serial: WD-WCAT22387984
                   size: 149GiB (160GB)
                   configuration: ansiversion=5
              *-disk:2
                   description: ATA Disk
                   product: WDC WD1600AAJS-7
                   vendor: Western Digital
                   physical id: 2
                   bus info: scsi@8:0.0.0
                   logical name: /dev/sdg
                   version: 02.0
                   serial: WD-WMAV3C638899
                   size: 149GiB (160GB)
                   configuration: ansiversion=5
              *-disk:3
                   description: ATA Disk
                   product: WDC WD1600AAJS-7
                   vendor: Western Digital
                   physical id: 3
                   bus info: scsi@9:0.0.0
                   logical name: /dev/sdh
                   version: 02.0
                   serial: WD-WMAV3C639779
                   size: 149GiB (160GB)
                   configuration: ansiversion=5
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:9000(size=8) ioport:8c00(size=4) ioport:8880(size=8) ioport:8800(size=4) ioport:8480(size=16) ioport:8400(size=16)
           *-disk:0
                description: ATA Disk
                product: Hitachi HDT72505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: V56O
                serial: VFK401R4D5M29K
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=06af8904
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /home/shared/videos
                   version: 1.0
                   serial: 6ff459d2-c21e-4aa2-beac-b76d90b3e2bd
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-08-01 12:44:23 filesystem=ext4 lastmountpoint=/home/shared/videosï¿½ï¿½ï¿½ï¿½.?ï¿½3(ï¿½`ï¿½ï¿½ï¿½×»&ï¿½ï¿½ï¿½ï¿½)ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½s@+ modified=2010-05-20 20:47:53 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:47:53 state=mounted
           *-disk:1
                description: ATA Disk
                product: Hitachi HDT72101
                vendor: Hitachi
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: ST1O
                serial: STA0D7MB37T3ZF
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=08000000
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 0c6b-f1d6
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-10-24 22:24:51 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 10236MiB
                   capacity: 10236MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 94MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      logical name: /
                      capacity: 10142MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.1.0,3
                   logical name: /dev/sdb3
                   logical name: /home
                   version: 1.0
                   serial: e182f101-b5ed-411b-87c0-3cfd5de6d4b2
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-10-24 14:00:23 filesystem=ext4 lastmountpoint=/homeï¿½ï¿½ï¿½ï¿½ï¿½Ú(hï¿½ï¿½ï¿½ï¿½Ë&#710;ï¿½ï¿½Cï¿½&ï¿½ï¿½ï¿½ï¿½ï¿½#ï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½`ï¿½ modified=2010-05-20 20:47:52 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:47:52 state=mounted
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@0:0.1.0,4
                   logical name: /dev/sdb4
                   version: 3.1
                   serial: 4606738b-d5c1-5141-a46e-6793eafda7ff
                   size: 128GiB
                   capacity: 128GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-10-24 22:27:27 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-disk:2
                description: ATA Disk
                product: WDC WD2000JD-00H
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdc
                version: 08.0
                serial: WD-WMAL81516952
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e5c7e5c7
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /Music
                   version: 1.0
                   serial: 5ce11060-f770-424a-8a06-21a0b69b822a
                   size: 186GiB
                   capacity: 186GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-11-27 20:29:22 filesystem=ext4 label=Music lastmountpoint=/Music8ï¿½ï¿½Å&#710;ï¿½ï¿½ï¿½ï¿½6ï¿½(ï¿½ï¿½Å&#710;ï¿½ï¿½[ï¿½&ï¿½ï¿½ï¿½ï¿½)ï¿½ï¿½ïï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½` modified=2010-05-20 20:47:52 mount.fstype=ext4 mount.options=rw,relatime,acl,barrier=1,data=ordered mounted=2010-05-20 20:47:52 state=mounted
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
             resources: memory:f9fff400-f9fff4ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:a000(size=8) ioport:9c00(size=4) ioport:9880(size=8) ioport:9800(size=4) ioport:9480(size=16) ioport:9400(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW AD-7200S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 101A
                serial: [Optiarc DVD+-RW AD-7200S101A Jan09,2008
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```




Friend:

```

    description: Desktop Computer
    product: 945GC Micro 775
    vendor: Biostar
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00E04D47-685A-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: 945GC Micro 775
       vendor: Biostar
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/28/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R)
          slot: Socket 478
          size: 1998MHz
          capacity: 3066MHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-cache
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G94 [GeForce 9600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:df00(size=128) memory:fb000000-fb07ffff(prefetchable)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fe00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:e000(size=4096) memory:fdd00000-fddfffff ioport:fde00000(size=1048576)
           *-network:0
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: RaLink
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: wlan0
                version: 00
                serial: 00:1c:10:6b:ae:ac
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:fddf0000-fddf7fff
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:e0:4d:47:68:5a
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.64 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:20 ioport:ee00(size=256) memory:fddff000-fddff0ff memory:fde00000-fde0ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fb00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CD/DVDW SH-S182D
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:fa00(size=8) ioport:f900(size=4) ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=16) memory:fdffe000-fdffe3ff
           *-disk:0
                description: ATA Disk
                product: WDC WD1600AAJS-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAT22064581
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e0000000
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 52fdf5fc-1777-4a47-ba25-109c086dc606
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-26 18:02:35 filesystem=ntfs label=Local Disk state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 3d6dded6-2c8d-4739-862a-12d2b1b252ce
                   size: 976MiB
                   capacity: 976MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 8db74498-5ebc-4171-bb63-a82638666684
                   size: 45GiB
                   capacity: 45GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-03 16:35:15 filesystem=ext4 lastmountpoint=/ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½qï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½{ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½@+m}ï¿½ï¿½ï¿½ï¿½nï¿½ï¿½ï¿½ï¿½ï¿½ï¿½w}ï¿½ modified=2010-05-18 22:14:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-19 22:08:22 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 46GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
           *-disk:1
                description: ATA Disk
                product: MAXTOR STM325031
                vendor: Maxtor
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 6RY1F4Y4
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1fb01faf
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/Stuff
                   version: 3.1
                   serial: ce8948d8-44d2-4ee4-8cac-9382ea589295
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-09-27 20:59:10 filesystem=ntfs label=Stuff mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)

```

---

### Post by dcstar on 2010-05-21
I suppose the fast PC having 10 times the pitiful 94MiB Swap space of the slow PC may be a factor.

---

### Post by SlugSlug on 2010-05-21
really? I must have set it to 100MB thinking the 4GB RAM would mean it never would really be used?

Could that really be the cause? and to resize that I'd have to move / unless I put the swap at the far end of the disk -- would that mater?

---

### Post by cascade9 on 2010-05-21
Well, I was half expecting thing to be the other way around...a Q8200 is a faster CPU than a E6550. 

Anyway, the difference IMO is that your friend has 2 HDDs (160 + 250), and your computer has a lot more HDDs- (200 IDE on a POS marvel controller, 500 + 160 + 200, and the SiL RAID arrary). 

All those HDDs and file systems to check will have a major impact on bootimes IMO. 

BTW, unles I'm making a big mistake, that is the 1st time I've seen lshw show an error. Its claimed that the E6550 is a on a socket 478,a nd they never made socket 478 E6550s. Interesting. 

> **dcstar said:**
> I suppose the fast PC having 10 times the pitiful 94MiB Swap space of the slow PC may be a factor.

'Fast' computer? Sorry, boot times arent a measure of speed...well, apart from boot speed LOL. 

Swap size, and amount, will have little effect on bootimes.

---

### Post by SlugSlug on 2010-05-21
So leave the swap as is, and put it down to the amount of HDD's,  

that looks like the answer to this thread.


Cheers guys, all posts were appreciated!!

:popcorn:

---

### Post by cascade9 on 2010-05-21
no problem ;) 

> **SlugSlug said:**
> So leave the swap as is, and put it down to the amount of HDD's,  

that looks like the answer to this thread.


That is my guess, but if some hardware guru has a different idea, I'm all ears ;)

---

### Post by dcstar on 2010-05-22
> **cascade9 said:**
> 
........
Swap size, and amount, will have little effect on bootimes.

Booting is a resource intensive phase where the system is heavily loaded, so having more resources means the ability to perform better.

If processes are loaded into RAM and then not required they are moved into swap to make room for additional processes or disk cache, if they cannot be moved into swap then there is less RAM available for caching or processes.

---

### Post by SlugSlug on 2010-05-22
> 
If processes are loaded into RAM and then not required they are moved into swap to make room for additional processes or disk cache, if they cannot be moved into swap then there is less RAM available for caching or processes.


So with 4GB RAM is 90MB Swap enough or would I benefit from more?

---

### Post by SlugSlug on 2010-05-22
Am going to test (boot charts to follow)

Resizing the 500GB Drive to have a 2GB swap at the front so I'll have swap on a diff drive from boot too

I'll disable the 94MB one and see how it goes......

edit : it's looking like the resize could take three and a half hours...

---

### Post by jocko on 2010-05-22
> **SlugSlug said:**
> So with 4GB RAM is 90MB Swap enough or would I benefit from more?
90 Mb of swap is pointless, if you really filled your ram you would need more swap than that. Think of swap as an extension of ram. When ram gets full, some of the old stuff that are kept there are moved to the swap partition to make some extra space in ram. 90 Mb is just about 2% of your total available memory, so you don't get any significant benefit from having it. I don't know what's the best amount of swap to have, but as a general rule I would say that the more ram you have the less swap you will normally need. But if you want hibernation to work you need to be able to write the entire ram into swap, so you would need a little bit more swap than you have ram.

With 4 Gb of ram, I don't think there is *any* way you need to use swap at all during boot (but you may need it if you do some image editing, 3d rendering or video editing).


From your bootchart, the things that are making your computer boot slower than the other computer is mainly what happens before plymouth and ureadahead, namely the dmraid stuff the first eight seconds.
If you remove the raid, I'm sure boot would speed up to 20 seconds or slightly less.
If your root partition is on the raid array, there is nothing you can do, but otherwise you can at least test to inactivate it in the bios.
I don't have any experience at all with raid, but I guess you would probably need to update the initramfs after you turn it off in the bios, so run:
```
sudo update-initramfs -u
```Not sure if you would actually even need to uninstall dmraid as well...

---

### Post by SlugSlug on 2010-05-22
I did remove the dmraid and it made no difference, (still had the HDD's in just as separate drives.

Also tried using them ad LVM.

The RAID is purley used as a dump ground an storage for non-important stuff

I cancelled the partition and am now moving the data and will resize the empty disk.

Must admit I never ran that command after removing dmraid tho...

---

### Post by SlugSlug on 2010-05-22
OK no  difference between swaps

90MB = [http://imgur.com/Awpi8.png](http://imgur.com/Awpi8.png)

2GB = [http://imgur.com/N3klv.png](http://imgur.com/N3klv.png)

---

### Post by cascade9 on 2010-05-22
> **dcstar said:**
> Booting is a resource intensive phase where the system is heavily loaded, so having more resources means the ability to perform better.

If processes are loaded into RAM and then not required they are moved into swap to make room for additional processes or disk cache, if they cannot be moved into swap then there is less RAM available for caching or processes.

Thats all true...and OK, I guess I shouldnt have phrased what I said without adding the disclaimer 'on your system'. 

As far as I know, you only write to swap if all the RAM is used. With 4GB, I really doubt that all the RAM is being used by the system, so IMO it should make little difference, if any at all in this case.

It would be interesting to know at what RAM level swap size and speed would start impacting on boot times. ;) (for any given distro and version of course, there would be major variants)

> **SlugSlug said:**
> OK no  difference between swaps

90MB = [http://imgur.com/Awpi8.png](http://imgur.com/Awpi8.png)

2GB = [http://imgur.com/N3klv.png](http://imgur.com/N3klv.png)

At risk of disputing what I said before (LOL), there is a difference between those boot charts. 

With 90MB- 28.3? sec. (? because I cant be sure LOL)  
With 2GB- 26.9 sec. 

However, as usual, its dmraid that is making the time difference- @90, its 9.4 seconds untill dmraid has finished, @2 its 6.9 sec.

---

### Post by SlugSlug on 2010-05-22
> **cascade9 said:**
> 
At risk of disputing what I said before (LOL), there is a difference between those boot charts. 

With 90MB- 28.3? sec. (? because I cant be sure LOL)  
With 2GB- 26.9 sec. 

However, as usual, its dmraid that is making the time difference- @90, its 9.4 seconds untill dmraid has finished, @2 its 6.9 sec.


I struck off the 2 seconds as it tends to vary...

I did remove dmraid via apt-get and again there was little difference ( but I never like you also mentioned took out any hard drives)

ubuntu just see through the raid and classes as 4 drives

---

