---
title: "AMD 64 Maverick No Effects"
date: 2010-10-15
forum: General Help
---

### Post by pnguine on 2010-10-15
Box specs below. Compiz (effects) won't work. fglrx, proprietary drivers, uninstall, reinstall, software center, synaptic, .... drivers not working - effects can't be enabled. Is this a bug? :confused:

-------- specs -------------

```
harvest
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=C0DEF287-8DFE-D511-B341-001BFC35B3D4
  *-core
       description: Motherboard
       product: M2N-MX SE
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MS9874353456379863
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0406 (09/27/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2200MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:dc00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:dfeff000-dfefffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:dfefec00-dfefecff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:dfef8000-dfefbfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-disk
             description: ATA Disk
             product: ST3160812A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 4LS403YW
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=44754474
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 86377b9a-e9b7-c643-af1a-fbaaebfa1b35
                size: 48GiB
                capacity: 48GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-08-07 17:06:41 filesystem=ntfs label=XP_Root modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/XP_Data
                version: 3.1
                serial: 782f19a2-27e0-411b-a748-bbb4c2bf7250
                size: 100GiB
                capacity: 100GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-09-22 16:18:13 filesystem=ntfs label=XP_Data mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-cdrom
             description: SCSI CD-ROM
             product: CD-ROM CDU5221
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.02
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:1b:fc:35:b3:d4
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
          resources: irq:44 memory:dfefd000-dfefdfff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:dfefc000-dfefcfff
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-H62N
             vendor: HL-DT-ST
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: CL00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: WDC WD5001AALS-0
             vendor: Western Digital
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 05.0
             serial: WD-WCATR1545352
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000b2056
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 1
                serial: 5ec27f99-a9bc-4d53-81ab-33ab5c7c9b56
                size: 2054MiB
                capacity: 2054MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sdb2
                logical name: /media/SuSE_Root
                version: 1.0
                serial: 7be406fb-84a4-42d1-a30c-37a96156d2c9
                size: 20GiB
                capacity: 20GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-08-07 10:28:57 filesystem=ext4 label=SuSE_Root lastmountpoint=/media/7be406fb-84a4-42d1-a30c-37a96156d2c9&#65533;&#65533;U4&#65533;&#65533;&#65533;&#65533;I&#65533;&#4129;}} modified=2010-09-26 15:54:17 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2010-09-26 15:54:17 state=mounted
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@3:0.0.0,3
                logical name: /dev/sdb3
                logical name: /media/SuSE_Data
                version: 1.0
                serial: dec2c3b4-4174-4374-a02c-dbfc508153e2
                size: 199GiB
                capacity: 199GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-08-07 10:29:01 filesystem=ext4 label=SuSE_Data lastmountpoint=/media/dec2c3b4-4174-4374-a02c-dbfc508153e2&#65533;6!&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;&#65533;7! modified=2010-09-26 15:54:37 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2010-09-26 15:54:37 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@3:0.0.0,4
                logical name: /dev/sdb4
                size: 243GiB
                capacity: 243GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /
                   capacity: 46GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sdb6
                   logical name: /home
                   capacity: 197GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:e000(size=4096) memory:dff00000-dfffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: RV620 LE [Radeon HD 3450]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:43 memory:c0000000-cfffffff memory:dfff0000-dfffffff ioport:e800(size=256) memory:dffc0000-dffdffff
        *-multimedia
             description: Audio device
             product: RV620 Audio device [Radeon HD 34xx Series]
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:dffec000-dffeffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=amd64_edac
          resources: irq:0
     *-pci:7
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

### Post by pnguine on 2010-10-16
Is there a better place to ask this question?

---

### Post by bashphoenux on 2010-10-16
do you get any error message while enabling compiz effects?

---

### Post by pnguine on 2010-10-16
Going through System -> Preferences -> Appearance there are no errors during the search for drivers, then the screen flashes on and off a couple of times, then a dialog box pops up with "Desktop effects could not be enabled." and that's it.

---

### Post by metallus on 2010-10-19
Did you do a fresh install of ubuntu, or upgrade?
Compiz effects break when upgrading from 10.04 to 10.10.
If you do a fresh install of ubuntu, the effects should work.
Also install the video drivers with System->Administration->Additional Drivers
Good Luck!!!

---

### Post by pnguine on 2010-10-20
It says I have the 'ATI/AMD proprietary FGLRX graphics driver' and that 'This driver is activated and currently in use.'

And it was a fresh install from about a month ago before the official release.

---

### Post by P4man on 2010-10-20
I had jockey claim I had the accelerated drivers installed, but xorg didnt load it due to my xorg.conf. Try this:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.back
sudo aticonfig --initial
```

then restart X (or reboot).

---

### Post by pnguine on 2010-10-20
That says "cannot stat 'etc/X11/xorg.conf': No such file or directory"

Sure enough using mc I see xorg.conf does not exist!

So I tried aticonfig - it worked!

Thanks P4man - and everyone else.

Now I am happy with my wiggly windows. :-)

---

### Post by P4man on 2010-10-21
I just let you back up xorg.conf in case it existed, but for the opensource drivers its not needed. THe proprietary drivers still need it though, and the installer doesnt always create it (or correctly if one exists). 

Anyway, dont forget to mark the thread as [solved] in thread tools :)

---

