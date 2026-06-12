---
title: "Firefox, Chromium-Browser and ksoftirqd"
date: 2012-07-01
forum: General Help
---

### Post by promet on 2012-07-01
I've just begun to notice that when running Firefox and Chromium-Browser, that they both seem to run at rather high CPU loads (~50-60%) and seem to be "exciting" the ksoftirqd process, generating two processes each at ~10% apiece, steadily.

Once either browser is killed, CPU drops back to single digit "idle" loads and the ksoftirqd processes disappear as well. As I understand it, ksoftirqd spawns to handle "excessive" queued irq requests. I am wondering what it is about Firefox and Chromium that could be exciting ksoftirqd like this, and why they are consuming such a high CPU load generally.

This doesn't occur with Opera Browser, which runs at single digit CPU loads, at "idle" and spawns no active instances of the ksoftirqd process. 

Any thoughts?

Here's my lshw output (Ubuntu 12.04), if it's of any help:

```
description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=200C06E7-08B9-DC11-BCEA-001FC6A19200
  *-core
       description: Motherboard
       product: M3A
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MF7083G01608377
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1206
          date: 06/11/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
          configuration: cores=2 enabledcores=2
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
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM_A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM_B1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM SDRAM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM_A2
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM_B2
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fa000000-fe9fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G94 [GeForce 9600 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:e800(size=128) memory:fe980000-fe9fffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port B)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fea00000-feafffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:feafe000-feafffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: Attansic L1 Gigabit Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: b0
                serial: 00:1f:c6:a1:92:00
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.1.42 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:46 memory:febc0000-febfffff memory:feba0000-febbffff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:d000(size=8) ioport:c000(size=4) ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=16) memory:f9fff800-f9fffbff
           *-disk:0
                description: ATA Disk
                product: WDC WD4000AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WMASY0658857
                size: 372GiB (400GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c8255
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 913e18da-4a35-40f3-825a-f37baa8ff1d9
                   size: 368GiB
                   capacity: 368GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-05-02 21:00:20 filesystem=ext4 lastmountpoint=/ modified=2012-06-30 15:56:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-06-30 15:57:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 4094MiB
                   capacity: 4094MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4094MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: WDC WD4000AAKS-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WMASY0464400
                size: 372GiB (400GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002ffa7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 2c7f-6d06
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-07-03 19:54:07 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   version: 3.1
                   serial: 6e5969df-5f97-5040-912d-edabc8c87310
                   size: 372GiB
                   capacity: 372GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-07-03 19:54:09 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-cdrom
                description: DVD-RAM writer
                product: DRW-2014L1T
                vendor: ASUS
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/LINUX__S1_DVD
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/LINUX__S1_DVD
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f9ffe000-f9ffefff
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffd000-f9ffdfff
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffc000-f9ffcfff
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:f9ffb000-f9ffbfff
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f9ffa000-f9ffafff
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f9fff000-f9fff0ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f9ff4000-f9ff7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@8:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000186ca
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/SHIVUX-POP
                version: 3.1
                serial: 1421b172-293d-4d11-915f-76ffcba751e4
                size: 465GiB
                capacity: 465GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-04-05 20:20:16 filesystem=ntfs label=SHIVUX-POP mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: tap0
       serial: ce:6e:81:c5:26:b8
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A link=no multicast=yes port=twisted pair speed=10Mbit/s
```

Thanks!

---

### Post by dino99 on 2012-07-01
you won the right to file a report ):P

---

### Post by promet on 2012-07-01
> **dino99 said:**
> you won the right to file a report 

Thank you for that wry rejoinder, but the problem seems to have evaporated after a reboot. I'm going to count my blessings for the moment and move on. Hopefully it doesn't return.

Marking this "Solved", for now...duh, duh, duuhhhhhhhh...

---

### Post by erlkonig on 2012-07-05
Not solved, I think.  I'm seeing (on Ubunu 12.04 x86_64) the same problem, with Firefox and Chromium specifically.  The more of them are runnings, the worse it gets.  I didn't really notice until I realized my room was warm (from CPU load) and saw the four ksoftirqd processes at around 40 %CPU each, with the firefoxen processes around 70%-120%.  Installing and running Chromium showed that it wasn't just firefox, although these are the only two clearly involved.  Right now, with 2 FFen running and one stopped (w/ kill -STOP), I'm showing the running FF at 117 %CPU and ~10% on each of the ksoftirqds. Running kill -CONT on the other one immediately brings up the fan (which drops off after a moment), and the ksoftirqds are now averaging around 16-22%.  /proc/interrupts shows that the 'Rescheduling interrupts' are incrementing on CPU0 (of 4) by fewer than 1000 interrupts per second with firefox suspended, but around 500,000 - 700,000 with them both resumed.

Of course, I usually run 4 separate firefox processes to allow for different simultaneous profiles, and use on two X screens.  With which the problem is much more apparent.

Chromium has the problem for every window created, rapidly scaling up the load as one creates windows - a total nonsolution.

Whether either app is showing an actual webpage or not doesn't matter.

---

### Post by erlkonig on 2012-07-05
Ahh, it could be a leap-second interaction.  Running the following abruptly brought ksoftirqd under control:

   sudo date -s "`date`"

Related article: [http://artipc10.vub.ac.be/wordpress/2012/07/01/leap-second-causing-ksoftirqd-and-java-to-use-lots-of-cpu-time/](http://artipc10.vub.ac.be/wordpress/2012/07/01/leap-second-causing-ksoftirqd-and-java-to-use-lots-of-cpu-time/)

---

### Post by clifford427 on 2012-10-25
> **erlkonig said:**
> Ahh, it could be a leap-second interaction.  Running the following abruptly brought ksoftirqd under control:

   sudo date -s "`date`"

Related article: [http://artipc10.vub.ac.be/wordpress/2012/07/01/leap-second-causing-ksoftirqd-and-java-to-use-lots-of-cpu-time/](http://artipc10.vub.ac.be/wordpress/2012/07/01/leap-second-causing-ksoftirqd-and-java-to-use-lots-of-cpu-time/)

Worked perfectly for me. Had a 12.04LTS server bogging badly with just 10 websites. The command above resolved it instantly. Thanks for saving my bacon.

---

