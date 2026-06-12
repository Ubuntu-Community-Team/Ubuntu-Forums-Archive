---
title: "Grub has three copies of Ubuntu"
date: 2011-03-16
forum: General Help
---

### Post by 1chess2u Christian on 2011-03-16
Whenever I start my netbook up lately, it shows that I have three copies of Ubuntu (at least there are three text copies.) Only the third one works, because whenever I load the first two, it does not get any farther than a command prompt-like text screen that says something like "Kernel Panic." I know that that is about the equivalent to Windows' "blue screen of death," and i would like to know how to get rid of the first two. I do not know if this is exactly related, but it all started when I tried to do an update, and apparently Compiz is an unauthorized program (which is silly, since I got it from the Software Center. Now, in the third Ubuntu option, the Compiz is non-existant (I used to have multiple desktop areas where I could do work, and have gotten quite used to having many windows open at once, but now, even the icon that i used to use to switch between them isn't there. This is very annoying, and I would like to know how to re-instate that as well.

---

### Post by ubudog on 2011-03-16
I don't know if I can be of any other help besides maybe explaining the three different text copies.

They are probably just different kernel versions, and the one that works is the oldest one you have.  That means that the new kernel that you got from the updates (update manager), is broken, or maybe just doesn't work on your machine.

PS: Could you post your specs please?

---

### Post by 1chess2u Christian on 2011-03-16
> **ubudog said:**
> PS: Could you post your specs please?
What do you mean by specs?

---

### Post by 1chess2u Christian on 2011-03-16
> **ubudog said:**
> They are probably just different kernel versions, and the one that works is the oldest one you have.  That means that the new kernel that you got from the updates (update manager), is broken, or maybe just doesn't work on your machine.
I do not believe that they are different kernel versions (that depends on if you mean different Linux kernels or just different versions of Ubuntu.) I believe that my netbook can handle the Linux kernels, because it had Windows 7 on it when I got it. (I don't know if that would make any difference, but from what I understand, Linux is supposed to be easier on the machine you are using than Windows.

---

### Post by MSPdwalt on 2011-03-16
By specs he means specifications as in hardware specifications.  If you don't have those handy you should post the output of 

```
sudo lshw
```

Another thing I *might* try is booting into the working kernel and run the following commands:

```

sudo apt-get update
sudo apt-get autoremove
sudo apt-get autoclean

```

Update updates your repository cache (so ubuntu knows what the latest packages available are)

autoremove automatically removes packages that were installed as dependencies that are no longer needed (careful, it is actually removing packages from your system)

autoclean automatically deletes old versions of packages that are sometimes left behind after a package has been updated

After that reboot, if you boot up successfully run updates again from update manager and see what happens.

Be careful with my post here, I'm shooting from the hip, but this is what I would try in your shoes. No promises, no warranty.

---

### Post by 1chess2u Christian on 2011-03-16
I'm getting about three pages' worth of "stats". Do you want me to paste the whole thing?

---

### Post by MSPdwalt on 2011-03-16
Yeah,

You can never have too much info.

---

### Post by ubudog on 2011-03-16
But make sure to put it in a code block, or it will take up the whole screen.  :-)

---

### Post by 1chess2u Christian on 2011-03-16
```
laptop                    
    description: Notebook
    product: HP Mini 110-3100
    vendor: Hewlett-Packard
    version: 058F110000202B00000300100
    serial: CNC03845LG
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=796A6751-9CC0-055E-1FA6-0021CC5B696C
  *-core
       description: Motherboard
       product: 148A
       vendor: Hewlett-Packard
       physical id: 0
       version: 79.49
       serial: PBNLF1127ZHNNJ
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.13 (08/17/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
        *-bank
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HMP112S6NFR8C-S6
             vendor: Hynix
             physical id: 0
             serial: 4F248B3000
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 11
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: CPU
          size: 1GHz
          capacity: 1666MHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 12
             slot: Unknown
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 13
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:54180000-541fffff ioport:30c0(size=8) memory:40000000-4fffffff memory:54000000-540fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: N10 Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:54100000-5417ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:54200000-54203fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:53000000-53ffffff ioport:50000000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 04
                serial: 00:21:cc:5b:69:6c
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:42 ioport:2000(size=256) memory:50004000-50004fff memory:50000000-50003fff
           *-generic UNCLAIMED
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list
                configuration: latency=0
                resources: memory:53000000-5300ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:52000000-52ffffff ioport:51000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4313 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: 00:26:82:ce:4a:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.1.5 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:17 memory:52000000-52003fff
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:3040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:54204400-542047ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: N10/ICH7 Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:30b8(size=8) ioport:30cc(size=4) ioport:30b0(size=8) ioport:30c8(size=4) ioport:30a0(size=16) memory:54204000-542043ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM250HI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AC1
                serial: S24FJ90Z924024
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=5083d9ff
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: a8a2a080-69f4-4c07-acce-7987a7197aa1
                   size: 199MiB
                   capacity: 199MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 6afb721c-febe-1741-92c8-0cf6c4f82817
                   size: 65GiB
                   capacity: 216GiB
                   capabilities: primary extended partitioned partitioned:extended ntfs initialized
                   configuration: clustersize=4096 created=2010-07-27 03:16:08 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 108GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 108GiB
                      capabilities: nofs
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: fc12ee77-76bf-41eb-856d-a1ab317f6f04
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-02 16:58:24 filesystem=ext4 lastmountpoint=/8&#65533;3&#65533;&#65533;J&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;l!&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533; &#65533;4B&#65533;yo!&#65533;&#65533;d modified=2011-03-06 10:57:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-16 15:57:04 state=mounted
              *-volume:3
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   version: FAT32
                   serial: a2b4-a1a1
                   size: 96MiB
                   capacity: 103MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:3000(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 1952MiB (2047MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/PENDRIVE
                version: FAT32
                serial: a6f8-e997
                size: 1950MiB
                capacity: 1950MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-cdrom
             description: CD-R writer
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             capabilities: audio cd-r
             configuration: status=ready
  *-battery
       description: Lithium Ion Battery
       product: TY06055
       vendor: CPT-S26G
       physical id: 1
       slot: Primary
       capacity: 5100mWh
       configuration: voltage=10.8V

```
Well, There you go, Hope you like what you find.

---

