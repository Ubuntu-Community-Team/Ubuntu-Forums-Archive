---
title: "Compiz slow,, Do I need a new video card?"
date: 2010-06-14
forum: General Help
---

### Post by schwabdale on 2010-06-14
Hello, I have Compiz installed on 10.04 and it seems slow. 
It has a 2.2 single core processor and 2 gigs of ram. The Video card is 128mb. 

When I do the cube or any other effects, things seem choppy and slow,, 
Would upgrading to a 256mb video card help?

---

### Post by xsandz on 2010-06-14
can u plz tell me the detail of yr GPU??

---

### Post by Mark Phelps on 2010-06-14
It's not necessarily the low amount of memory; it's more likely that, if it is an ATI card/chip, it's one of the legacy models and you're now running on the open source drivers.

Need to know the make and model of the card/chip to be sure.

---

### Post by schwabdale on 2010-06-14
> **Mark Phelps said:**
> It's not necessarily the low amount of memory; it's more likely that, if it is an ATI card/chip, it's one of the legacy models and you're now running on the open source drivers.

Need to know the make and model of the card/chip to be sure.

How do I find that out?

---

### Post by warfacegod on 2010-06-14
```
sudo lspci
```

or

```
sudo lshw
```

---

### Post by schwabdale on 2010-06-14
Heres the output

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:02.0 USB Controller: NEC Corporation USB (rev 43)
01:02.1 USB Controller: NEC Corporation USB (rev 43)
01:02.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
stephen@stephen-desktop:~$ sudo lshw
stephen-desktop           
    description: Mini Tower Computer
    product: Dell DE051
    vendor: Dell Computer Corporation
    serial: HJVWS91
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-4A00-1056-8057-C8C04F533931
  *-core
       description: Motherboard
       product: 0WF887
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN7082162N05HI.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A01 (01/03/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.9
          serial: 0000-0F49-0000-0000-0000-0000
          slot: Microprocessor
          size: 2533MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_2
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-display
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:feb80000-febfffff ioport:ed98(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ffa80800-ffa80bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network:0
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlan0
                version: 01
                serial: 00:09:5b:84:1b:af
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=10.0.0.173 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:feaf0000-feafffff
           *-usb:0
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:17 memory:feaed000-feaedfff
           *-usb:1
                description: USB Controller
                product: USB
                vendor: NEC Corporation
                physical id: 2.1
                bus info: pci@0000:01:02.1
                version: 43
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
                resources: irq:18 memory:feaee000-feaeefff
           *-usb:2
                description: USB Controller
                product: USB 2.0
                vendor: NEC Corporation
                physical id: 2.2
                bus info: pci@0000:01:02.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ehci_hcd latency=64 maxlatency=34 mingnt=16
                resources: irq:19 memory:feaecf00-feaecfff
           *-network:1
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:16:76:3a:4c:bd
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:20 memory:feaef000-feaeffff ioport:df40(size=64)
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
           *-disk:0
                description: ATA Disk
                product: SAMSUNG SP0802N/
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TK30
                serial: S0DHJ1JL402087
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4f0c1670-5a26-4518-9fef-8ed24dbe9d00
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-11 07:31:40 filesystem=ext4 lastmountpoint=/yMbp&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9&#65533;&#65533;2&#65533;&#65533;p&#65533;L&#65533;u^ &#65533;U/&#65533;d&#65533;L&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;L&#65533;L&#65533;a modified=2010-06-11 09:17:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-14 09:03:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1905MiB
                   capacity: 1905MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1905MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CDRWDVD TS-H492C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE02
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: Maxtor 6Y060L0
                vendor: Maxtor
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/sdb
                version: YAR4
                serial: Y2JJ9Y9E
                size: 57GiB (61GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=09f377e2
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /media/sdb1
                   version: 1.0
                   serial: ecce3580-577c-4f58-bd10-0c1e7e3af601
                   size: 57GiB
                   capacity: 57GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-05-14 11:38:07 filesystem=ext4 label=WindowsXP lastmountpoint=/media/sdb1&#65533;&#65533;&#65533;aO&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u^ &#65533;U/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;aO modified=2010-06-14 09:03:16 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-06-14 09:03:16 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:eda0(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory:feb7fa00-feb7fbff memory:feb7f900-feb7f9ff
     *-scsi:0
          physical id: 1
          bus info: usb@1:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             size: 1944MiB (2038MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=00095b22
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/62D7-8615
                version: FAT32
                serial: 62d7-8615
                size: 1943MiB
                capacity: 1943MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:8
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdd
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=56f419e1
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/D46C3D086C3CE740
                version: 3.1
                serial: d0ad70b7-e838-a241-b8b6-6a28d3a6694d
                size: 232GiB
                capacity: 232GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-05-12 05:40:57 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@2:5
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sde
             version: 9339
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdf
             version: 9339
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdf
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdg
             version: 9339
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdg
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sdh
             version: 9339
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdh
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by warfacegod on 2010-06-14
Do us a favor, edit that post and put code brackets on it. Ctrl+A and click the # icon. Highly unreadable as is. Thanks.

---

### Post by warfacegod on 2010-06-14
Here's your video card:


```
*-display
description: VGA compatible controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:feb80000-febfffff ioport:ed98(size=
```

---

### Post by schwabdale on 2010-06-14
> **warfacegod said:**
> Here's your video card:


```
*-display
description: VGA compatible controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:feb80000-febfffff ioport:ed98(size=
```

How do I install the driver for this?

---

### Post by warfacegod on 2010-06-14
You don't. It's Intel.



As I see it, you have four options.

01. Buy another video card. nVidia 256 - 512 MB should be more than enough.

02. Go to: System> Prefs> Startup Applications> disable everything you can without rendering your system useless.

03. Check your BIOS to see if it supports dedicating more system RAM to video.

04. Disable some of your Compiz settings. (Absolute last resort)

I'd go with options 2 and 3 first.

---

### Post by schwabdale on 2010-06-14
Thanks

---

