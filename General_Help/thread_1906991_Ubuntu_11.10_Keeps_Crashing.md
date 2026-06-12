---
title: "Ubuntu 11.10 Keeps Crashing"
date: 2012-01-10
forum: General Help
---

### Post by Th3Blaze on 2012-01-10
After about 1-5 minutes of Ubuntu being loaded, Ubuntu crashes and is completely unusable,the only option after that being reset ( and shut down obviously ) Any one knows how to fix this annoying error ? If so, please reply with your wonderful news. Thanks.

---

### Post by QIII on 2012-01-10
Could you provide a bit of hardware info, exacly what happens and what you are doing at the time?  Wubi or stand alone?  Have you recently upgraded or added new applications?

Did this begin suddenly out of the blue?

---

### Post by Th3Blaze on 2012-01-10
Stand alone, and remind me the command to get the hardware info please.

---

### Post by QIII on 2012-01-10
```
lshw
```

will probably produce more than we need.  But better too much than too little.

Paste it between code tags.

Also, what about the other questions?

---

### Post by Th3Blaze on 2012-01-10
Can't load it at the moment, I will try in 10 minutes, but no, it has been doing it since 10.10 or 11.04, and no new apllications that I know of but, it crashes at the login sometimes

---

### Post by prshah on 2012-01-10
> **Th3Blaze said:**
> After about 1-5 minutes of Ubuntu being loaded, Ubuntu crashes and is completely unusable,

I would strongly suspect overheating; eg, processor fan / GPU fan / SMPS fan / case fan (unlikely) not working.

Please check if the above mentioned fans are working. You can do so physically by removing the cover and inspecting the fans (Careful, please!).

You can also check temperatures in the BIOS after a crash/reboot.

I also suggest a quick memtest from any Ubuntu/Linux live CD; at the starting screen, select the "Test Memory" option. Let it run for about 20-30 mins, and if you don't see anything in RED, then there's probably no problem with memory.

---

### Post by QIII on 2012-01-10
+1. After 35 years, I can't count the number of times that a simple hardware fault has been the culprit.

---

### Post by Th3Blaze on 2012-01-21
Have I got anyway to find out what is wrong via the actual computer ? I had a look inside, nothing looks out of place. Sorry for the late reply.

---

### Post by Th3Blaze on 2012-01-22
Any advances then?Sorry for being impatient, using my Dad's PC, and very limited to the stuff I can do, looking to get back to my own asap. If it is a hardware problem, would lshw still help ?

---

### Post by sixteenornumber on 2012-01-22
I don't mean to forum jack but I'm having the same problem.  

The only thing ive done since the crashing is a apt-get update.  The hardware is only a month or two old.  Again, sorry for the thread jacking. 
```
earth
    description: Desktop Computer
    product: Z68MA-D2H-B3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-50E5494CD213
  *-core
       description: Motherboard
       product: Z68MA-D2H-B3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F8
          date: 07/26/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2120T CPU
          slot: Socket 1155
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt xsave avx lahf_lm arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 3MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 1600 MHz (0.6 ns)
             physical id: 2
             slot: A2
             size: 4GiB
             width: 2052 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM 1600 MHz (0.6 ns)
             physical id: 3
             slot: A3
             size: 4GiB
             width: 2052 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fbb00000-fbcfffff ioport:dfa00000(size=1048576)
           *-scsi
                description: SCSI storage controller
                product: 88SX7042 PCI-e 4-port SATA-II
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: scsi0
                logical name: scsi1
                logical name: scsi2
                logical name: scsi3
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: scsi pm msi pciexpress bus_master cap_list rom emulated
                configuration: driver=sata_mv latency=0
                resources: irq:16 memory:fbc00000-fbcfffff ioport:de00(size=256) memory:dfa00000-dfafffff
              *-disk:0
                   description: ATA Disk
                   product: WDC WD20EARS-00M
                   vendor: Western Digital
                   physical id: 0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/sda
                   version: 51.0
                   serial: WD-WMAZA0799428
                   size: 1863GiB (2TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=0004b676
                 *-volume
                      description: Linux raid autodetect partition
                      physical id: 1
                      bus info: scsi@0:0.0.0,1
                      logical name: /dev/sda1
                      capacity: 1863GiB
                      capabilities: primary multi
              *-disk:1
                   description: ATA Disk
                   product: WDC WD20EARS-00M
                   vendor: Western Digital
                   physical id: 1
                   bus info: scsi@1:0.0.0
                   logical name: /dev/sdb
                   version: 51.0
                   serial: WD-WMAZA0716189
                   size: 1863GiB (2TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=00053597
                 *-volume
                      description: Linux raid autodetect partition
                      physical id: 1
                      bus info: scsi@1:0.0.0,1
                      logical name: /dev/sdb1
                      capacity: 1863GiB
                      capabilities: primary multi
              *-disk:2
                   description: ATA Disk
                   product: WDC WD20EARS-00M
                   vendor: Western Digital
                   physical id: 2
                   bus info: scsi@2:0.0.0
                   logical name: /dev/sdc
                   version: 51.0
                   serial: WD-WMAZA0732744
                   size: 1863GiB (2TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=000b8d05
                 *-volume
                      description: Linux raid autodetect partition
                      physical id: 1
                      bus info: scsi@2:0.0.0,1
                      logical name: /dev/sdc1
                      capacity: 1863GiB
                      capabilities: primary multi
              *-disk:3
                   description: ATA Disk
                   product: WDC WD20EARS-00M
                   vendor: Western Digital
                   physical id: 3
                   bus info: scsi@3:0.0.0
                   logical name: /dev/sdd
                   version: 51.0
                   serial: WD-WMAZA0789405
                   size: 1863GiB (2TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=0002086a
                 *-volume
                      description: Linux raid autodetect partition
                      physical id: 1
                      bus info: scsi@3:0.0.0,1
                      logical name: /dev/sdd1
                      capacity: 1863GiB
                      capabilities: primary multi
        *-pci:1
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:fbd00000-fbdfffff ioport:dfb00000(size=1048576)
           *-network
                description: Ethernet interface
                product: 82574L Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 00
                serial: 00:1b:21:c5:f6:78
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=1.8-0 ip=192.168.2.206 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 memory:fbdc0000-fbddffff memory:fbd00000-fbd7ffff ioport:ef00(size=32) memory:fbdfc000-fbdfffff memory:dfb00000-dfb3ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:fb400000-fb7fffff memory:e0000000-efffffff ioport:ff00(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:fbfff000-fbfff00f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:49 memory:fbff4000-fbff7fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:dfc00000-dfdfffff ioport:dfe00000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:c000(size=4096) ioport:fba00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: 50:e5:49:4c:d2:13
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:ce00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:fbe00000-fbefffff
           *-usb
                description: USB Controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:44 memory:fbef8000-fbefffff
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Z68 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi4
             logical name: scsi9
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:fe00(size=8) ioport:fd00(size=4) ioport:fc00(size=8) ioport:fb00(size=4) ioport:fa00(size=32) memory:fbffc000-fbffc7ff
           *-disk
                description: ATA Disk
                product: Patriot Pyro
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/sde
                version: 332A
                serial: PT1147A00026668
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ac170
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sde1
                   logical name: /boot
                   version: 1.0
                   serial: 2af1db3d-20e3-42ff-9ceb-76ed03b9bb1b
                   size: 118MiB
                   capacity: 118MiB
                   capabilities: primary bootable journaled extended_attributes huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-30 09:34:12 filesystem=ext4 lastmountpoint=/boot modified=2012-01-22 23:54:41 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-22 23:54:41 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sde2
                   version: 1
                   serial: f56729eb-3e20-4e00-a26e-6ec47bde339a
                   size: 3814MiB
                   capacity: 3814MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@4:0.0.0,3
                   logical name: /dev/sde3
                   logical name: /
                   version: 1.0
                   serial: 28f7161c-e591-4010-868a-5f05da69548c
                   size: 52GiB
                   capacity: 52GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-30 09:34:12 filesystem=ext4 lastmountpoint=/ modified=2011-12-30 09:42:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-01-23 00:06:35 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: iHAS224   B
                vendor: ATAPI
                physical id: 1
                bus info: scsi@9:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GL0A
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffb000-fbffb0ff ioport:500(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:1.1
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: USB Flash Drive
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdf
             version: 1.00
             serial: 1108170000000821
             size: 14GiB (15GB)
             capabilities: removable
             configuration: ansiversion=6
           *-medium
                physical id: 0
                logical name: /dev/sdf
                size: 14GiB (15GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000e5247
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   logical name: /dev/sdf1
                   logical name: /media/16-3
                   version: 3.1
                   serial: 1094-88a7
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-01-13 19:32:35 filesystem=ntfs label=16-3 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
```

perhaps this would help? I'm not really sure what im looking at but here is a kern.log

```

...
Jan 22 23:54:42 earth kernel: [   10.908164] /dev/vmnet: port on hub 8 successfully opened
Jan 22 23:54:42 earth kernel: [   10.911803] /dev/vmnet: open called by PID 1400 (vmnet-netifup)
Jan 22 23:54:42 earth kernel: [   10.911816] /dev/vmnet: port on hub 8 successfully opened
Jan 22 23:54:42 earth kernel: [   10.918420] /dev/vmnet: open called by PID 1403 (vmnet-dhcpd)
Jan 22 23:54:42 earth kernel: [   10.918433] /dev/vmnet: port on hub 8 successfully opened
Jan 22 23:54:42 earth kernel: [   10.999440] EXT4-fs (sde3): re-mounted. Opts: errors=remount-ro,commit=0
Jan 22 23:54:42 earth kernel: [   11.001334] EXT4-fs (sde1): re-mounted. Opts: commit=0
Jan 22 23:54:43 earth kernel: [   12.632797] EXT4-fs (sde3): re-mounted. Opts: errors=remount-ro,commit=0
Jan 22 23:54:43 earth kernel: [   12.634828] EXT4-fs (sde1): re-mounted. Opts: commit=0
Jan 22 23:54:44 earth kernel: [   13.282335] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Jan 22 23:54:44 earth kernel: [   13.282961] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 22 23:54:44 earth kernel: [   13.283291] /dev/vmnet: open called by PID 1373 (vmnet-bridge)
Jan 22 23:54:44 earth kernel: [   13.283299] /dev/vmnet: hub 0 does not exist, allocating memory.
Jan 22 23:54:44 earth kernel: [   13.283312] /dev/vmnet: port on hub 0 successfully opened
Jan 22 23:54:44 earth kernel: [   13.283324] bridge-eth1: up
Jan 22 23:54:44 earth kernel: [   13.283326] bridge-eth1: attached
Jan 22 23:54:44 earth kernel: [   13.482805] userif-2: sent link down event.
Jan 22 23:54:45 earth kernel: [   13.482808] userif-2: sent link up event.
Jan 22 23:54:45 earth kernel: [   14.488753] userif-2: sent link down event.
Jan 22 23:54:52 earth kernel: [   14.488757] userif-2: sent link up event.
Jan 22 23:54:52 earth kernel: [   21.030805] vmnet8: no IPv6 routers present
Jan 22 23:54:52 earth kernel: [   21.038789] vmnet1: no IPv6 routers present
Jan 22 23:54:55 earth kernel: [   24.097042] eth1: no IPv6 routers present
Jan 22 23:55:21 earth kernel: [   25.250876] /dev/vmmon[0]: HostIFReadUptimeWork: detected settimeofday: fixed uptimeBase old 18445416831427942515 new 18445416831402731766 attempts 1
Jan 22 23:57:35 earth kernel: [  158.434349] EXT4-fs (md127): recovery complete
Jan 22 23:57:35 earth kernel: [  158.434569] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
Jan 22 23:58:04 earth kernel: [  187.453324] init: plymouth-stop pre-start process (2836) terminated with status 1
Jan 23 00:06:35 earth kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jan 23 00:06:35 earth kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 23 00:06:35 earth kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 23 00:06:35 earth kernel: [    0.000000] Linux version 3.0.0-15-generic (buildd@yellow) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 (Ubuntu 3.0.0-15.25-generic 3.0.13)
Jan 23 00:06:35 earth kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-generic root=UUID=28f7161c-e591-4010-868a-5f05da69548c ro quiet splash vt.handoff=7
Jan 23 00:06:35 earth kernel: [    0.000000] KERNEL supported cpus:
Jan 23 00:06:35 earth kernel: [    0.000000]   Intel GenuineIntel
Jan 23 00:06:35 earth kernel: [    0.000000]   AMD AuthenticAMD
Jan 23 00:06:35 earth kernel: [    0.000000]   Centaur CentaurHauls
Jan 23 00:06:35 earth kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000091800 (usable)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cef80000 (usable)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000cef80000 - 00000000cefa3000 (ACPI NVS)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000cefa3000 - 00000000cefe0000 (ACPI data)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000cefe0000 - 00000000cf000000 (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000021fe00000 (usable)
Jan 23 00:06:35 earth kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 23 00:06:35 earth kernel: [    0.000000] DMI 2.4 present.
Jan 23 00:06:35 earth kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. Z68MA-D2H-B3/Z68MA-D2H-B3, BIOS F8 07/26/2011
Jan 23 00:06:35 earth kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan 23 00:06:35 earth kernel: [    0.000000] No AGP bridge found
Jan 23 00:06:35 earth kernel: [    0.000000] last_pfn = 0x21fe00 max_arch_pfn = 0x400000000
Jan 23 00:06:35 earth kernel: [    0.000000] MTRR default type: uncachable
Jan 23 00:06:35 earth kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 23 00:06:35 earth kernel: [    0.000000]   00000-9FFFF write-back
Jan 23 00:06:35 earth kernel: [    0.000000]   A0000-BFFFF uncachable
Jan 23 00:06:35 earth kernel: [    0.000000]   C0000-DCFFF write-protect
Jan 23 00:06:35 earth kernel: [    0.000000]   DD000-EFFFF uncachable
Jan 23 00:06:35 earth kernel: [    0.000000]   F0000-FFFFF write-through
Jan 23 00:06:35 earth kernel: [    0.000000] MTRR variable ranges enabled:
Jan 23 00:06:35 earth kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Jan 23 00:06:35 earth kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Jan 23 00:06:35 earth kernel: [    0.000000]   2 base 0D0000000 mask FF0000000 uncachable
Jan 23 00:06:35 earth kernel: [    0.000000]   3 base 0CF800000 mask FFF800000 uncachable
Jan 23 00:06:35 earth kernel: [    0.000000]   4 base 100000000 mask F00000000 write-back
Jan 23 00:06:35 earth kernel: [    0.000000]   5 base 200000000 mask FE0000000 write-back
Jan 23 00:06:35 earth kernel: [    0.000000]   6 disabled
Jan 23 00:06:35 earth kernel: [    0.000000]   7 disabled
Jan 23 00:06:35 earth kernel: [    0.000000]   8 disabled
Jan 23 00:06:35 earth kernel: [    0.000000]   9 disabled
Jan 23 00:06:35 earth kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 23 00:06:35 earth kernel: [    0.000000] original variable MTRRs
Jan 23 00:06:35 earth kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
Jan 23 00:06:35 earth kernel: [    0.000000] reg 2, base: 3328MB, range: 256MB, type UC
Jan 23 00:06:35 earth kernel: [    0.000000] reg 3, base: 3320MB, range: 8MB, type UC
Jan 23 00:06:35 earth kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 5, base: 8GB, range: 512MB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] total RAM covered: 7928M
Jan 23 00:06:35 earth kernel: [    0.000000] Found optimal setting for mtrr clean up
Jan 23 00:06:35 earth kernel: [    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 6      lose cover RAM: 0G
Jan 23 00:06:35 earth kernel: [    0.000000] New variable MTRRs
Jan 23 00:06:35 earth kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 3, base: 3320MB, range: 8MB, type UC
Jan 23 00:06:35 earth kernel: [    0.000000] reg 4, base: 4GB, range: 4GB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] reg 5, base: 8GB, range: 512MB, type WB
Jan 23 00:06:35 earth kernel: [    0.000000] e820 update range: 00000000cf800000 - 0000000100000000 (usable) ==> (reserved)
Jan 23 00:06:35 earth kernel: [    0.000000] last_pfn = 0xcef80 max_arch_pfn = 0x400000000
Jan 23 00:06:35 earth kernel: [    0.000000] found SMP MP-table at [ffff8800000f58a0] f58a0
Jan 23 00:06:35 earth kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jan 23 00:06:35 earth kernel: [    0.000000] Base memory trampoline at [ffff88000008c000] 8c000 size 20480
Jan 23 00:06:35 earth kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cef80000
Jan 23 00:06:35 earth kernel: [    0.000000]  0000000000 - 00cee00000 page 2M
Jan 23 00:06:35 earth kernel: [    0.000000]  00cee00000 - 00cef80000 page 4k
Jan 23 00:06:35 earth kernel: [    0.000000] kernel direct mapping tables up to cef80000 @ 1fffa000-20000000
Jan 23 00:06:35 earth kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000021fe00000
Jan 23 00:06:35 earth kernel: [    0.000000]  0100000000 - 021fe00000 page 2M
Jan 23 00:06:35 earth kernel: [    0.000000] kernel direct mapping tables up to 21fe00000 @ cef76000-cef80000
Jan 23 00:06:35 earth kernel: [    0.000000] RAMDISK: 36516000 - 37283000
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: RSDP 00000000000f7490 00014 (v00 GBT   )
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: RSDT 00000000cefa3040 00054 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: FACP 00000000cefa3100 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: DSDT 00000000cefa31c0 04B3C (v01 GBT    GBTUACPI 00001000 MSFT 04000000)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: FACS 00000000cef80000 00040
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: MSDM 00000000cefa7e40 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: HPET 00000000cefa7f00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: MCFG 00000000cefa7f80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: ASPT 00000000cefa8100 00034 (v07 GBT    PerfTune 312E3042 UTBG 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: SSPT 00000000cefa8140 02324 (v01 GBT    SsptHead 312E3042 UTBG 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: EUDS 00000000cefaa470 000C0 (v01 GBT             00000000      00000000)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: MATS 00000000cefaa530 00034 (v01 GBT             00000000      00000000)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: TAMG 00000000cefaa590 00392 (v01 GBT    GBT   B0 5455312E BG?? 45240101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: APIC 00000000cefa7d40 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: SSDT 00000000cefaa940 01B2C (v01  INTEL PPM RCM  80000001 INTL 20061109)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: MATS 00000000cefac480 0995B (v01        MATS RCM 80000001 INTL 20061109)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 23 00:06:35 earth kernel: [    0.000000] No NUMA configuration found
Jan 23 00:06:35 earth kernel: [    0.000000] Faking a node at 0000000000000000-000000021fe00000
Jan 23 00:06:35 earth kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000021fe00000
Jan 23 00:06:35 earth kernel: [    0.000000]   NODE_DATA [000000021fdfb000 - 000000021fdfffff]
Jan 23 00:06:35 earth kernel: [    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217800000-ffff88021e5fffff] on node 0
Jan 23 00:06:35 earth kernel: [    0.000000] Zone PFN ranges:
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan 23 00:06:35 earth kernel: [    0.000000]   Normal   0x00100000 -> 0x0021fe00
Jan 23 00:06:35 earth kernel: [    0.000000] Movable zone start PFN for each node
Jan 23 00:06:35 earth kernel: [    0.000000] early_node_map[3] active PFN ranges
Jan 23 00:06:35 earth kernel: [    0.000000]     0: 0x00000010 -> 0x00000091
Jan 23 00:06:35 earth kernel: [    0.000000]     0: 0x00000100 -> 0x000cef80
Jan 23 00:06:35 earth kernel: [    0.000000]     0: 0x00100000 -> 0x0021fe00
Jan 23 00:06:35 earth kernel: [    0.000000] On node 0 totalpages: 2026753
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA zone: 5 pages reserved
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA zone: 3908 pages, LIFO batch:0
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Jan 23 00:06:35 earth kernel: [    0.000000]   DMA32 zone: 829368 pages, LIFO batch:31
Jan 23 00:06:35 earth kernel: [    0.000000]   Normal zone: 16121 pages used for memmap
Jan 23 00:06:35 earth kernel: [    0.000000]   Normal zone: 1163015 pages, LIFO batch:31
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 23 00:06:35 earth kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 23 00:06:35 earth kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 23 00:06:35 earth kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 23 00:06:35 earth kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Jan 23 00:06:35 earth kernel: [    0.000000] nr_irqs_gsi: 40
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 0000000000091000 - 00000000000a0000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000cef80000 - 00000000cefa3000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000cefa3000 - 00000000cefe0000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000cefe0000 - 00000000cf000000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000cf000000 - 00000000f4000000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
Jan 23 00:06:35 earth kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
Jan 23 00:06:35 earth kernel: [    0.000000] Allocating PCI resources starting at cf000000 (gap: cf000000:25000000)
Jan 23 00:06:35 earth kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 23 00:06:35 earth kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Jan 23 00:06:35 earth kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021fa00000 s79616 r8192 d22784 u262144
Jan 23 00:06:35 earth kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
Jan 23 00:06:35 earth kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Jan 23 00:06:35 earth kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1996291
Jan 23 00:06:35 earth kernel: [    0.000000] Policy zone: Normal
Jan 23 00:06:35 earth kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-generic root=UUID=28f7161c-e591-4010-868a-5f05da69548c ro quiet splash vt.handoff=7
Jan 23 00:06:35 earth kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 23 00:06:35 earth kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Jan 23 00:06:35 earth kernel: [    0.000000] Checking aperture...
Jan 23 00:06:35 earth kernel: [    0.000000] No AGP bridge found
Jan 23 00:06:35 earth kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan 23 00:06:35 earth kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan 23 00:06:35 earth kernel: [    0.000000] Memory: 7898064k/8910848k available (6136k kernel code, 803836k absent, 208948k reserved, 6898k data, 988k init)
Jan 23 00:06:35 earth kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jan 23 00:06:35 earth kernel: [    0.000000] Hierarchical RCU implementation.
Jan 23 00:06:35 earth kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan 23 00:06:35 earth kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Jan 23 00:06:35 earth kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan 23 00:06:35 earth kernel: [    0.000000] Console: colour dummy device 80x25
Jan 23 00:06:35 earth kernel: [    0.000000] console [tty0] enabled
Jan 23 00:06:35 earth kernel: [    0.000000] allocated 65011712 bytes of page_cgroup
Jan 23 00:06:35 earth kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 23 00:06:35 earth kernel: [    0.000000] hpet clockevent registered
Jan 23 00:06:35 earth kernel: [    0.000000] Fast TSC calibration using PIT
Jan 23 00:06:35 earth kernel: [    0.004000] Detected 2594.176 MHz processor.
Jan 23 00:06:35 earth kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.35 BogoMIPS (lpj=10376704)
Jan 23 00:06:35 earth kernel: [    0.000005] pid_max: default: 32768 minimum: 301
Jan 23 00:06:35 earth kernel: [    0.000024] Security Framework initialized
Jan 23 00:06:35 earth kernel: [    0.000035] AppArmor: AppArmor initialized
Jan 23 00:06:35 earth kernel: [    0.000036] Yama: becoming mindful.
Jan 23 00:06:35 earth kernel: [    0.000705] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jan 23 00:06:35 earth kernel: [    0.002294] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 23 00:06:35 earth kernel: [    0.002935] Mount-cache hash table entries: 256
Jan 23 00:06:35 earth kernel: [    0.003020] Initializing cgroup subsys cpuacct
Jan 23 00:06:35 earth kernel: [    0.003023] Initializing cgroup subsys memory
Jan 23 00:06:35 earth kernel: [    0.003029] Initializing cgroup subsys devices
Jan 23 00:06:35 earth kernel: [    0.003030] Initializing cgroup subsys freezer
Jan 23 00:06:35 earth kernel: [    0.003032] Initializing cgroup subsys net_cls
Jan 23 00:06:35 earth kernel: [    0.003033] Initializing cgroup subsys blkio
Jan 23 00:06:35 earth kernel: [    0.003037] Initializing cgroup subsys perf_event
Jan 23 00:06:35 earth kernel: [    0.003058] CPU: Physical Processor ID: 0
Jan 23 00:06:35 earth kernel: [    0.003060] CPU: Processor Core ID: 0
Jan 23 00:06:35 earth kernel: [    0.003064] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Jan 23 00:06:35 earth kernel: [    0.003064] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Jan 23 00:06:35 earth kernel: [    0.003067] mce: CPU supports 7 MCE banks
Jan 23 00:06:35 earth kernel: [    0.003077] CPU0: Thermal monitoring enabled (TM1)
Jan 23 00:06:35 earth kernel: [    0.003083] using mwait in idle threads.
Jan 23 00:06:35 earth kernel: [    0.005199] ACPI: Core revision 20110413
Jan 23 00:06:35 earth kernel: [    0.008320] ftrace: allocating 25729 entries in 101 pages
Jan 23 00:06:35 earth kernel: [    0.017192] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 23 00:06:35 earth kernel: [    0.056803] CPU0: Intel(R) Core(TM) i3-2120T CPU @ 2.60GHz stepping 07
Jan 23 00:06:35 earth kernel: [    0.163645] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Jan 23 00:06:35 earth kernel: [    0.163650] ... version:                3
Jan 23 00:06:35 earth kernel: [    0.163651] ... bit width:              48
Jan 23 00:06:35 earth kernel: [    0.163652] ... generic registers:      4
Jan 23 00:06:35 earth kernel: [    0.163654] ... value mask:             0000ffffffffffff
Jan 23 00:06:35 earth kernel: [    0.163655] ... max period:             000000007fffffff
Jan 23 00:06:35 earth kernel: [    0.163656] ... fixed-purpose events:   3
Jan 23 00:06:35 earth kernel: [    0.163657] ... event mask:             000000070000000f
Jan 23 00:06:35 earth kernel: [    0.163993] Booting Node   0, Processors  #1
Jan 23 00:06:35 earth kernel: [    0.163995] smpboot cpu 1: start_ip = 8c000
Jan 23 00:06:35 earth kernel: [    0.271612]  #2
Jan 23 00:06:35 earth kernel: [    0.271614] smpboot cpu 2: start_ip = 8c000
Jan 23 00:06:35 earth kernel: [    0.379428]  #3
Jan 23 00:06:35 earth kernel: [    0.379430] smpboot cpu 3: start_ip = 8c000
Jan 23 00:06:35 earth kernel: [    0.487088] Brought up 4 CPUs
Jan 23 00:06:35 earth kernel: [    0.487090] Total of 4 processors activated (20752.28 BogoMIPS).
Jan 23 00:06:35 earth kernel: [    0.489363] devtmpfs: initialized
Jan 23 00:06:35 earth kernel: [    0.489462] PM: Registering ACPI NVS region at cef80000 (143360 bytes)
Jan 23 00:06:35 earth kernel: [    0.490586] print_constraints: dummy: 
Jan 23 00:06:35 earth kernel: [    0.490611] Time: 14:36:26  Date: 01/22/12
Jan 23 00:06:35 earth kernel: [    0.490634] NET: Registered protocol family 16
Jan 23 00:06:35 earth kernel: [    0.490708] Trying to unpack rootfs image as initramfs...
Jan 23 00:06:35 earth kernel: [    0.490716] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jan 23 00:06:35 earth kernel: [    0.490718] ACPI: bus type pci registered
Jan 23 00:06:35 earth kernel: [    0.490757] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
Jan 23 00:06:35 earth kernel: [    0.490760] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
Jan 23 00:06:35 earth kernel: [    0.498916] PCI: Using configuration type 1 for base access
Jan 23 00:06:35 earth kernel: [    0.499476] bio: create slab <bio-0> at 0
Jan 23 00:06:35 earth kernel: [    0.500153] ACPI: EC: Look up EC in DSDT
Jan 23 00:06:35 earth kernel: [    0.503225] ACPI: Interpreter enabled
Jan 23 00:06:35 earth kernel: [    0.503228] ACPI: (supports S0 S3 S4 S5)
Jan 23 00:06:35 earth kernel: [    0.503241] ACPI: Using IOAPIC for interrupt routing
Jan 23 00:06:35 earth kernel: [    0.505697] ACPI: No dock devices found.
Jan 23 00:06:35 earth kernel: [    0.505699] HEST: Table not found.
Jan 23 00:06:35 earth kernel: [    0.505701] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan 23 00:06:35 earth kernel: [    0.505738] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
Jan 23 00:06:35 earth kernel: [    0.505806] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Jan 23 00:06:35 earth kernel: [    0.505808] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Jan 23 00:06:35 earth kernel: [    0.505810] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Jan 23 00:06:35 earth kernel: [    0.505812] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
Jan 23 00:06:35 earth kernel: [    0.505814] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
Jan 23 00:06:35 earth kernel: [    0.505815] pci_root PNP0A03:00: host bridge window [mem 0xdfa00000-0xfebfffff]
Jan 23 00:06:35 earth kernel: [    0.505825] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
Jan 23 00:06:35 earth kernel: [    0.505855] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.505877] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.505879] pci 0000:00:01.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.505890] pci 0000:00:01.1: [8086:0105] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.505911] pci 0000:00:01.1: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.505913] pci 0000:00:01.1: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.505927] pci 0000:00:02.0: [8086:0102] type 0 class 0x000300
Jan 23 00:06:35 earth kernel: [    0.505937] pci 0000:00:02.0: reg 10: [mem 0xfb400000-0xfb7fffff 64bit]
Jan 23 00:06:35 earth kernel: [    0.505943] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.505948] pci 0000:00:02.0: reg 20: [io  0xff00-0xff3f]
Jan 23 00:06:35 earth kernel: [    0.505994] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Jan 23 00:06:35 earth kernel: [    0.506016] pci 0000:00:16.0: reg 10: [mem 0xfbfff000-0xfbfff00f 64bit]
Jan 23 00:06:35 earth kernel: [    0.506076] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506079] pci 0000:00:16.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506109] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Jan 23 00:06:35 earth kernel: [    0.506129] pci 0000:00:1a.0: reg 10: [mem 0xfbffe000-0xfbffe3ff]
Jan 23 00:06:35 earth kernel: [    0.506201] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506205] pci 0000:00:1a.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506226] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Jan 23 00:06:35 earth kernel: [    0.506240] pci 0000:00:1b.0: reg 10: [mem 0xfbff4000-0xfbff7fff 64bit]
Jan 23 00:06:35 earth kernel: [    0.506293] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506296] pci 0000:00:1b.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506314] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.506375] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506378] pci 0000:00:1c.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506403] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.506464] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506468] pci 0000:00:1c.6: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506489] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.506550] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506553] pci 0000:00:1c.7: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506579] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Jan 23 00:06:35 earth kernel: [    0.506599] pci 0000:00:1d.0: reg 10: [mem 0xfbffd000-0xfbffd3ff]
Jan 23 00:06:35 earth kernel: [    0.506671] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.506675] pci 0000:00:1d.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506692] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
Jan 23 00:06:35 earth kernel: [    0.506746] pci 0000:00:1f.0: [8086:1c44] type 0 class 0x000601
Jan 23 00:06:35 earth kernel: [    0.506857] pci 0000:00:1f.2: [8086:2822] type 0 class 0x000104
Jan 23 00:06:35 earth kernel: [    0.506875] pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
Jan 23 00:06:35 earth kernel: [    0.506882] pci 0000:00:1f.2: reg 14: [io  0xfd00-0xfd03]
Jan 23 00:06:35 earth kernel: [    0.506889] pci 0000:00:1f.2: reg 18: [io  0xfc00-0xfc07]
Jan 23 00:06:35 earth kernel: [    0.506897] pci 0000:00:1f.2: reg 1c: [io  0xfb00-0xfb03]
Jan 23 00:06:35 earth kernel: [    0.506904] pci 0000:00:1f.2: reg 20: [io  0xfa00-0xfa1f]
Jan 23 00:06:35 earth kernel: [    0.506912] pci 0000:00:1f.2: reg 24: [mem 0xfbffc000-0xfbffc7ff]
Jan 23 00:06:35 earth kernel: [    0.506943] pci 0000:00:1f.2: PME# supported from D3hot
Jan 23 00:06:35 earth kernel: [    0.506946] pci 0000:00:1f.2: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.506960] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Jan 23 00:06:35 earth kernel: [    0.506975] pci 0000:00:1f.3: reg 10: [mem 0xfbffb000-0xfbffb0ff 64bit]
Jan 23 00:06:35 earth kernel: [    0.507002] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
Jan 23 00:06:35 earth kernel: [    0.507053] pci 0000:01:00.0: [11ab:7042] type 0 class 0x000100
Jan 23 00:06:35 earth kernel: [    0.507066] pci 0000:01:00.0: reg 10: [mem 0xfbc00000-0xfbcfffff 64bit]
Jan 23 00:06:35 earth kernel: [    0.507074] pci 0000:01:00.0: reg 18: [io  0xde00-0xdeff]
Jan 23 00:06:35 earth kernel: [    0.507099] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.507134] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan 23 00:06:35 earth kernel: [    0.507137] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Jan 23 00:06:35 earth kernel: [    0.507139] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbcfffff]
Jan 23 00:06:35 earth kernel: [    0.507142] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507181] pci 0000:02:00.0: [8086:10d3] type 0 class 0x000200
Jan 23 00:06:35 earth kernel: [    0.507200] pci 0000:02:00.0: reg 10: [mem 0xfbdc0000-0xfbddffff]
Jan 23 00:06:35 earth kernel: [    0.507213] pci 0000:02:00.0: reg 14: [mem 0xfbd00000-0xfbd7ffff]
Jan 23 00:06:35 earth kernel: [    0.507227] pci 0000:02:00.0: reg 18: [io  0xef00-0xef1f]
Jan 23 00:06:35 earth kernel: [    0.507241] pci 0000:02:00.0: reg 1c: [mem 0xfbdfc000-0xfbdfffff]
Jan 23 00:06:35 earth kernel: [    0.507279] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0003ffff pref]
Jan 23 00:06:35 earth kernel: [    0.507321] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.507326] pci 0000:02:00.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.507358] pci 0000:00:01.1: PCI bridge to [bus 02-02]
Jan 23 00:06:35 earth kernel: [    0.507360] pci 0000:00:01.1:   bridge window [io  0xe000-0xefff]
Jan 23 00:06:35 earth kernel: [    0.507362] pci 0000:00:01.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
Jan 23 00:06:35 earth kernel: [    0.507365] pci 0000:00:01.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507408] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Jan 23 00:06:35 earth kernel: [    0.507412] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507415] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507421] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507485] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
Jan 23 00:06:35 earth kernel: [    0.507505] pci 0000:04:00.0: reg 10: [io  0xce00-0xceff]
Jan 23 00:06:35 earth kernel: [    0.507539] pci 0000:04:00.0: reg 18: [mem 0xfbaff000-0xfbafffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.507561] pci 0000:04:00.0: reg 20: [mem 0xfbaf8000-0xfbafbfff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.507621] pci 0000:04:00.0: supports D1 D2
Jan 23 00:06:35 earth kernel: [    0.507622] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.507627] pci 0000:04:00.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.507667] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
Jan 23 00:06:35 earth kernel: [    0.507671] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
Jan 23 00:06:35 earth kernel: [    0.507674] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507680] pci 0000:00:1c.6:   bridge window [mem 0xfba00000-0xfbafffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.507743] pci 0000:05:00.0: [1b6f:7023] type 0 class 0x000c03
Jan 23 00:06:35 earth kernel: [    0.507769] pci 0000:05:00.0: reg 10: [mem 0xfbef8000-0xfbefffff 64bit]
Jan 23 00:06:35 earth kernel: [    0.507868] pci 0000:05:00.0: supports D1 D2
Jan 23 00:06:35 earth kernel: [    0.507869] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 23 00:06:35 earth kernel: [    0.507874] pci 0000:05:00.0: PME# disabled
Jan 23 00:06:35 earth kernel: [    0.507905] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
Jan 23 00:06:35 earth kernel: [    0.507908] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507912] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
Jan 23 00:06:35 earth kernel: [    0.507918] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507976] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507979] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507983] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507988] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Jan 23 00:06:35 earth kernel: [    0.507990] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507992] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507994] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507995] pci 0000:00:1e.0:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507997] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.507999] pci 0000:00:1e.0:   bridge window [mem 0xdfa00000-0xfebfffff] (subtractive decode)
Jan 23 00:06:35 earth kernel: [    0.508022] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 23 00:06:35 earth kernel: [    0.508113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Jan 23 00:06:35 earth kernel: [    0.508134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG1._PRT]
Jan 23 00:06:35 earth kernel: [    0.508153] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jan 23 00:06:35 earth kernel: [    0.508179] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
Jan 23 00:06:35 earth kernel: [    0.508198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
Jan 23 00:06:35 earth kernel: [    0.508235]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jan 23 00:06:35 earth kernel: [    0.508237]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Jan 23 00:06:35 earth kernel: [    0.508239] ACPI _OSC control for PCIe not granted, disabling ASPM
Jan 23 00:06:35 earth kernel: [    0.513089] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513122] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513155] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513186] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513216] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan 23 00:06:35 earth kernel: [    0.513247] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jan 23 00:06:35 earth kernel: [    0.513278] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513308] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jan 23 00:06:35 earth kernel: [    0.513378] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan 23 00:06:35 earth kernel: [    0.513384] vgaarb: loaded
Jan 23 00:06:35 earth kernel: [    0.513385] vgaarb: bridge control possible 0000:00:02.0
Jan 23 00:06:35 earth kernel: [    0.513503] SCSI subsystem initialized
Jan 23 00:06:35 earth kernel: [    0.513547] libata version 3.00 loaded.
Jan 23 00:06:35 earth kernel: [    0.513576] usbcore: registered new interface driver usbfs
Jan 23 00:06:35 earth kernel: [    0.513583] usbcore: registered new interface driver hub
Jan 23 00:06:35 earth kernel: [    0.513605] usbcore: registered new device driver usb
Jan 23 00:06:35 earth kernel: [    0.513667] PCI: Using ACPI for IRQ routing
Jan 23 00:06:35 earth kernel: [    0.515138] PCI: pci_cache_line_size set to 64 bytes
Jan 23 00:06:35 earth kernel: [    0.515198] reserve RAM buffer: 0000000000091800 - 000000000009ffff 
Jan 23 00:06:35 earth kernel: [    0.515200] reserve RAM buffer: 00000000cef80000 - 00000000cfffffff 
Jan 23 00:06:35 earth kernel: [    0.515202] reserve RAM buffer: 000000021fe00000 - 000000021fffffff 
Jan 23 00:06:35 earth kernel: [    0.515267] NetLabel: Initializing
Jan 23 00:06:35 earth kernel: [    0.515269] NetLabel:  domain hash size = 128
Jan 23 00:06:35 earth kernel: [    0.515270] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 23 00:06:35 earth kernel: [    0.515277] NetLabel:  unlabeled traffic allowed by default
Jan 23 00:06:35 earth kernel: [    0.515307] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jan 23 00:06:35 earth kernel: [    0.515312] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jan 23 00:06:35 earth kernel: [    0.517321] Switching to clocksource hpet
Jan 23 00:06:35 earth kernel: [    0.518968] Switched to NOHz mode on CPU #0
Jan 23 00:06:35 earth kernel: [    0.519033] Switched to NOHz mode on CPU #3
Jan 23 00:06:35 earth kernel: [    0.519084] Switched to NOHz mode on CPU #1
Jan 23 00:06:35 earth kernel: [    0.519108] Switched to NOHz mode on CPU #2
Jan 23 00:06:35 earth kernel: [    0.521440] AppArmor: AppArmor Filesystem Enabled
Jan 23 00:06:35 earth kernel: [    0.521458] pnp: PnP ACPI init
Jan 23 00:06:35 earth kernel: [    0.521470] ACPI: bus type pnp registered
Jan 23 00:06:35 earth kernel: [    0.521532] pnp 00:00: [bus 00-3f]
Jan 23 00:06:35 earth kernel: [    0.521534] pnp 00:00: [io  0x0cf8-0x0cff]
Jan 23 00:06:35 earth kernel: [    0.521535] pnp 00:00: [io  0x0000-0x0cf7 window]
Jan 23 00:06:35 earth kernel: [    0.521537] pnp 00:00: [io  0x0d00-0xffff window]
Jan 23 00:06:35 earth kernel: [    0.521539] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jan 23 00:06:35 earth kernel: [    0.521540] pnp 00:00: [mem 0x000c0000-0x000dffff window]
Jan 23 00:06:35 earth kernel: [    0.521542] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Jan 23 00:06:35 earth kernel: [    0.521543] pnp 00:00: [mem 0xdfa00000-0xfebfffff window]
Jan 23 00:06:35 earth kernel: [    0.521581] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
Jan 23 00:06:35 earth kernel: [    0.521639] pnp 00:01: [io  0x0010-0x001f]
Jan 23 00:06:35 earth kernel: [    0.521640] pnp 00:01: [io  0x0022-0x003f]
Jan 23 00:06:35 earth kernel: [    0.521642] pnp 00:01: [io  0x0044-0x004d]
Jan 23 00:06:35 earth kernel: [    0.521643] pnp 00:01: [io  0x0050-0x005f]
Jan 23 00:06:35 earth kernel: [    0.521644] pnp 00:01: [io  0x0062-0x0063]
Jan 23 00:06:35 earth kernel: [    0.521646] pnp 00:01: [io  0x0065-0x006f]
Jan 23 00:06:35 earth kernel: [    0.521647] pnp 00:01: [io  0x0074-0x007f]
Jan 23 00:06:35 earth kernel: [    0.521648] pnp 00:01: [io  0x0091-0x0093]
Jan 23 00:06:35 earth kernel: [    0.521649] pnp 00:01: [io  0x00a2-0x00bf]
Jan 23 00:06:35 earth kernel: [    0.521651] pnp 00:01: [io  0x00e0-0x00ef]
Jan 23 00:06:35 earth kernel: [    0.521652] pnp 00:01: [io  0x04d0-0x04d1]
Jan 23 00:06:35 earth kernel: [    0.521653] pnp 00:01: [io  0x0290-0x029f]
Jan 23 00:06:35 earth kernel: [    0.521655] pnp 00:01: [io  0x0800-0x0805]
Jan 23 00:06:35 earth kernel: [    0.521656] pnp 00:01: [io  0x0290-0x0294]
Jan 23 00:06:35 earth kernel: [    0.521657] pnp 00:01: [io  0x0880-0x088f]
Jan 23 00:06:35 earth kernel: [    0.521692] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jan 23 00:06:35 earth kernel: [    0.521694] system 00:01: [io  0x0290-0x029f] has been reserved
Jan 23 00:06:35 earth kernel: [    0.521696] system 00:01: [io  0x0800-0x0805] has been reserved
Jan 23 00:06:35 earth kernel: [    0.521697] system 00:01: [io  0x0290-0x0294] has been reserved
Jan 23 00:06:35 earth kernel: [    0.521699] system 00:01: [io  0x0880-0x088f] has been reserved
Jan 23 00:06:35 earth kernel: [    0.521702] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 23 00:06:35 earth kernel: [    0.521710] pnp 00:02: [dma 4]
Jan 23 00:06:35 earth kernel: [    0.521711] pnp 00:02: [io  0x0000-0x000f]
Jan 23 00:06:35 earth kernel: [    0.521713] pnp 00:02: [io  0x0080-0x0090]
Jan 23 00:06:35 earth kernel: [    0.521714] pnp 00:02: [io  0x0094-0x009f]
Jan 23 00:06:35 earth kernel: [    0.521715] pnp 00:02: [io  0x00c0-0x00df]
Jan 23 00:06:35 earth kernel: [    0.521732] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jan 23 00:06:35 earth kernel: [    0.521766] pnp 00:03: [irq 0 disabled]
Jan 23 00:06:35 earth kernel: [    0.521773] pnp 00:03: [irq 8]
Jan 23 00:06:35 earth kernel: [    0.521775] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Jan 23 00:06:35 earth kernel: [    0.521791] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jan 23 00:06:35 earth kernel: [    0.521808] pnp 00:04: [io  0x0070-0x0073]
Jan 23 00:06:35 earth kernel: [    0.521824] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan 23 00:06:35 earth kernel: [    0.521829] pnp 00:05: [io  0x0061]
Jan 23 00:06:35 earth kernel: [    0.521847] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Jan 23 00:06:35 earth kernel: [    0.521853] pnp 00:06: [io  0x00f0-0x00ff]
Jan 23 00:06:35 earth kernel: [    0.521857] pnp 00:06: [irq 13]
Jan 23 00:06:35 earth kernel: [    0.521873] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan 23 00:06:35 earth kernel: [    0.522045] pnp 00:07: [io  0x03f8-0x03ff]
Jan 23 00:06:35 earth kernel: [    0.522049] pnp 00:07: [irq 4]
Jan 23 00:06:35 earth kernel: [    0.522088] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
Jan 23 00:06:35 earth kernel: [    0.522132] pnp 00:08: [io  0x0400-0x04cf]
Jan 23 00:06:35 earth kernel: [    0.522134] pnp 00:08: [io  0x04d2-0x04ff]
Jan 23 00:06:35 earth kernel: [    0.522160] system 00:08: [io  0x0400-0x04cf] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522162] system 00:08: [io  0x04d2-0x04ff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522164] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 23 00:06:35 earth kernel: [    0.522172] pnp 00:09: [io  0x1000-0x107f]
Jan 23 00:06:35 earth kernel: [    0.522174] pnp 00:09: [io  0x1080-0x10ff]
Jan 23 00:06:35 earth kernel: [    0.522176] pnp 00:09: [io  0x1100-0x117f]
Jan 23 00:06:35 earth kernel: [    0.522178] pnp 00:09: [io  0x1180-0x11ff]
Jan 23 00:06:35 earth kernel: [    0.522203] system 00:09: [io  0x1000-0x107f] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522205] system 00:09: [io  0x1080-0x10ff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522207] system 00:09: [io  0x1100-0x117f] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522209] system 00:09: [io  0x1180-0x11ff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522211] system 00:09: Plug and Play ACPI device, IDs ICD0001 PNP0c02 (active)
Jan 23 00:06:35 earth kernel: [    0.522335] pnp 00:0a: [io  0x0454-0x0457]
Jan 23 00:06:35 earth kernel: [    0.522367] system 00:0a: [io  0x0454-0x0457] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522369] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Jan 23 00:06:35 earth kernel: [    0.522381] pnp 00:0b: [mem 0xf4000000-0xf7ffffff]
Jan 23 00:06:35 earth kernel: [    0.522412] system 00:0b: [mem 0xf4000000-0xf7ffffff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522414] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 23 00:06:35 earth kernel: [    0.522538] pnp 00:0c: [mem 0x000dd000-0x000dffff]
Jan 23 00:06:35 earth kernel: [    0.522540] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
Jan 23 00:06:35 earth kernel: [    0.522541] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
Jan 23 00:06:35 earth kernel: [    0.522543] pnp 00:0c: [mem 0x000fc000-0x000fffff]
Jan 23 00:06:35 earth kernel: [    0.522544] pnp 00:0c: [mem 0xcef80000-0xcefdffff]
Jan 23 00:06:35 earth kernel: [    0.522546] pnp 00:0c: [mem 0x00000000-0x0009ffff]
Jan 23 00:06:35 earth kernel: [    0.522547] pnp 00:0c: [mem 0x00100000-0xcef7ffff]
Jan 23 00:06:35 earth kernel: [    0.522549] pnp 00:0c: [mem 0xcefe0000-0xceffffff]
Jan 23 00:06:35 earth kernel: [    0.522550] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
Jan 23 00:06:35 earth kernel: [    0.522551] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
Jan 23 00:06:35 earth kernel: [    0.522553] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
Jan 23 00:06:35 earth kernel: [    0.522554] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
Jan 23 00:06:35 earth kernel: [    0.522556] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
Jan 23 00:06:35 earth kernel: [    0.522557] pnp 00:0c: [mem 0xfff00000-0xffffffff]
Jan 23 00:06:35 earth kernel: [    0.522558] pnp 00:0c: [mem 0x000e0000-0x000effff]
Jan 23 00:06:35 earth kernel: [    0.522560] pnp 00:0c: [mem 0x20000000-0x201fffff]
Jan 23 00:06:35 earth kernel: [    0.522561] pnp 00:0c: [mem 0x40000000-0x400fffff]
Jan 23 00:06:35 earth kernel: [    0.522562] pnp 00:0c: [mem 0xcf000000-0xdf9fffff]
Jan 23 00:06:35 earth kernel: [    0.522576] pnp 00:0c: disabling [mem 0x000dd000-0x000dffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522579] pnp 00:0c: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522582] pnp 00:0c: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522584] pnp 00:0c: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522587] pnp 00:0c: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522590] pnp 00:0c: disabling [mem 0x000e0000-0x000effff] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x000fffff pref]
Jan 23 00:06:35 earth kernel: [    0.522620] system 00:0c: [mem 0xcef80000-0xcefdffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522622] system 00:0c: [mem 0x00100000-0xcef7ffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522624] system 00:0c: [mem 0xcefe0000-0xceffffff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522626] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522628] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522629] system 00:0c: [mem 0xfed20000-0xfed8ffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522631] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522633] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522635] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
Jan 23 00:06:35 earth kernel: [    0.522637] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522639] system 00:0c: [mem 0x40000000-0x400fffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522641] system 00:0c: [mem 0xcf000000-0xdf9fffff] could not be reserved
Jan 23 00:06:35 earth kernel: [    0.522643] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan 23 00:06:35 earth kernel: [    0.522655] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
Jan 23 00:06:35 earth kernel: [    0.522678] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
Jan 23 00:06:35 earth kernel: [    0.522682] pnp: PnP ACPI: found 14 devices
Jan 23 00:06:35 earth kernel: [    0.522683] ACPI: ACPI bus type pnp unregistered
Jan 23 00:06:35 earth kernel: [    0.528041] PCI: max bus depth: 1 pci_try_num: 2
Jan 23 00:06:35 earth kernel: [    0.528082] pci 0000:00:01.0: BAR 15: assigned [mem 0xdfa00000-0xdfafffff pref]
Jan 23 00:06:35 earth kernel: [    0.528085] pci 0000:00:01.1: BAR 15: assigned [mem 0xdfb00000-0xdfbfffff pref]
Jan 23 00:06:35 earth kernel: [    0.528088] pci 0000:00:1c.0: BAR 14: assigned [mem 0xdfc00000-0xdfdfffff]
Jan 23 00:06:35 earth kernel: [    0.528091] pci 0000:00:1c.0: BAR 15: assigned [mem 0xdfe00000-0xdfffffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.528094] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
Jan 23 00:06:35 earth kernel: [    0.528096] pci 0000:01:00.0: BAR 6: assigned [mem 0xdfa00000-0xdfafffff pref]
Jan 23 00:06:35 earth kernel: [    0.528098] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Jan 23 00:06:35 earth kernel: [    0.528100] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Jan 23 00:06:35 earth kernel: [    0.528103] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbcfffff]
Jan 23 00:06:35 earth kernel: [    0.528105] pci 0000:00:01.0:   bridge window [mem 0xdfa00000-0xdfafffff pref]
Jan 23 00:06:35 earth kernel: [    0.528109] pci 0000:02:00.0: BAR 6: assigned [mem 0xdfb00000-0xdfb3ffff pref]
Jan 23 00:06:35 earth kernel: [    0.528110] pci 0000:00:01.1: PCI bridge to [bus 02-02]
Jan 23 00:06:35 earth kernel: [    0.528112] pci 0000:00:01.1:   bridge window [io  0xe000-0xefff]
Jan 23 00:06:35 earth kernel: [    0.528115] pci 0000:00:01.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
Jan 23 00:06:35 earth kernel: [    0.528117] pci 0000:00:01.1:   bridge window [mem 0xdfb00000-0xdfbfffff pref]
Jan 23 00:06:35 earth kernel: [    0.528120] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
Jan 23 00:06:35 earth kernel: [    0.528123] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
Jan 23 00:06:35 earth kernel: [    0.528127] pci 0000:00:1c.0:   bridge window [mem 0xdfc00000-0xdfdfffff]
Jan 23 00:06:35 earth kernel: [    0.528131] pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfffffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.528137] pci 0000:00:1c.6: PCI bridge to [bus 04-04]
Jan 23 00:06:35 earth kernel: [    0.528139] pci 0000:00:1c.6:   bridge window [io  0xc000-0xcfff]
Jan 23 00:06:35 earth kernel: [    0.528144] pci 0000:00:1c.6:   bridge window [mem disabled]
Jan 23 00:06:35 earth kernel: [    0.528147] pci 0000:00:1c.6:   bridge window [mem 0xfba00000-0xfbafffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.528153] pci 0000:00:1c.7: PCI bridge to [bus 05-05]
Jan 23 00:06:35 earth kernel: [    0.528155] pci 0000:00:1c.7:   bridge window [io  disabled]
Jan 23 00:06:35 earth kernel: [    0.528159] pci 0000:00:1c.7:   bridge window [mem 0xfbe00000-0xfbefffff]
Jan 23 00:06:35 earth kernel: [    0.528163] pci 0000:00:1c.7:   bridge window [mem pref disabled]
Jan 23 00:06:35 earth kernel: [    0.528168] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
Jan 23 00:06:35 earth kernel: [    0.528169] pci 0000:00:1e.0:   bridge window [io  disabled]
Jan 23 00:06:35 earth kernel: [    0.528173] pci 0000:00:1e.0:   bridge window [mem disabled]
Jan 23 00:06:35 earth kernel: [    0.528176] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Jan 23 00:06:35 earth kernel: [    0.528194] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    0.528197] pci 0000:00:01.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528200] pci 0000:00:01.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    0.528202] pci 0000:00:01.1: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528207] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Jan 23 00:06:35 earth kernel: [    0.528210] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    0.528214] pci 0000:00:1c.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528222] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 23 00:06:35 earth kernel: [    0.528226] pci 0000:00:1c.6: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528234] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 23 00:06:35 earth kernel: [    0.528237] pci 0000:00:1c.7: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528244] pci 0000:00:1e.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.528247] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan 23 00:06:35 earth kernel: [    0.528249] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan 23 00:06:35 earth kernel: [    0.528250] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan 23 00:06:35 earth kernel: [    0.528252] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
Jan 23 00:06:35 earth kernel: [    0.528253] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
Jan 23 00:06:35 earth kernel: [    0.528255] pci_bus 0000:00: resource 9 [mem 0xdfa00000-0xfebfffff]
Jan 23 00:06:35 earth kernel: [    0.528257] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Jan 23 00:06:35 earth kernel: [    0.528259] pci_bus 0000:01: resource 1 [mem 0xfbb00000-0xfbcfffff]
Jan 23 00:06:35 earth kernel: [    0.528260] pci_bus 0000:01: resource 2 [mem 0xdfa00000-0xdfafffff pref]
Jan 23 00:06:35 earth kernel: [    0.528262] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Jan 23 00:06:35 earth kernel: [    0.528264] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
Jan 23 00:06:35 earth kernel: [    0.528265] pci_bus 0000:02: resource 2 [mem 0xdfb00000-0xdfbfffff pref]
Jan 23 00:06:35 earth kernel: [    0.528267] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
Jan 23 00:06:35 earth kernel: [    0.528269] pci_bus 0000:03: resource 1 [mem 0xdfc00000-0xdfdfffff]
Jan 23 00:06:35 earth kernel: [    0.528270] pci_bus 0000:03: resource 2 [mem 0xdfe00000-0xdfffffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.528272] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
Jan 23 00:06:35 earth kernel: [    0.528274] pci_bus 0000:04: resource 2 [mem 0xfba00000-0xfbafffff 64bit pref]
Jan 23 00:06:35 earth kernel: [    0.528276] pci_bus 0000:05: resource 1 [mem 0xfbe00000-0xfbefffff]
Jan 23 00:06:35 earth kernel: [    0.528277] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
Jan 23 00:06:35 earth kernel: [    0.528279] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
Jan 23 00:06:35 earth kernel: [    0.528281] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
Jan 23 00:06:35 earth kernel: [    0.528282] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000dffff]
Jan 23 00:06:35 earth kernel: [    0.528284] pci_bus 0000:06: resource 8 [mem 0xfed40000-0xfed44fff]
Jan 23 00:06:35 earth kernel: [    0.528286] pci_bus 0000:06: resource 9 [mem 0xdfa00000-0xfebfffff]
Jan 23 00:06:35 earth kernel: [    0.528307] NET: Registered protocol family 2
Jan 23 00:06:35 earth kernel: [    0.528500] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 23 00:06:35 earth kernel: [    0.529346] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan 23 00:06:35 earth kernel: [    0.530479] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 23 00:06:35 earth kernel: [    0.530595] TCP: Hash tables configured (established 524288 bind 65536)
Jan 23 00:06:35 earth kernel: [    0.530597] TCP reno registered
Jan 23 00:06:35 earth kernel: [    0.530610] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jan 23 00:06:35 earth kernel: [    0.530643] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jan 23 00:06:35 earth kernel: [    0.530725] NET: Registered protocol family 1
Jan 23 00:06:35 earth kernel: [    0.530738] pci 0000:00:02.0: Boot video device
Jan 23 00:06:35 earth kernel: [    0.561344] PCI: CLS 4 bytes, default 64
Jan 23 00:06:35 earth kernel: [    0.561346] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan 23 00:06:35 earth kernel: [    0.561348] Placing 64MB software IO TLB between ffff8800caf76000 - ffff8800cef76000
Jan 23 00:06:35 earth kernel: [    0.561350] software IO TLB at phys 0xcaf76000 - 0xcef76000
Jan 23 00:06:35 earth kernel: [    0.561692] audit: initializing netlink socket (disabled)
Jan 23 00:06:35 earth kernel: [    0.561702] type=2000 audit(1327242986.400:1): initialized
Jan 23 00:06:35 earth kernel: [    0.587056] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 23 00:06:35 earth kernel: [    0.601998] VFS: Disk quotas dquot_6.5.2
Jan 23 00:06:35 earth kernel: [    0.602038] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 23 00:06:35 earth kernel: [    0.602444] fuse init (API version 7.16)
Jan 23 00:06:35 earth kernel: [    0.602504] msgmni has been set to 15425
Jan 23 00:06:35 earth kernel: [    0.602768] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan 23 00:06:35 earth kernel: [    0.602787] io scheduler noop registered
Jan 23 00:06:35 earth kernel: [    0.602790] io scheduler deadline registered
Jan 23 00:06:35 earth kernel: [    0.602816] io scheduler cfq registered (default)
Jan 23 00:06:35 earth kernel: [    0.602884] pcieport 0000:00:01.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.602907] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    0.602937] pcieport 0000:00:01.1: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.602955] pcieport 0000:00:01.1: irq 41 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    0.603113] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 23 00:06:35 earth kernel: [    0.603128] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 23 00:06:35 earth kernel: [    0.603170] efifb: probing for efifb
Jan 23 00:06:35 earth kernel: [    0.603173] efifb: framebuffer at 0xa0000, mapped to 0xffff8800000a0000, using 56k, total 64k
Jan 23 00:06:35 earth kernel: [    0.603175] efifb: mode is 640x350x1, linelength=80, pages=1
Jan 23 00:06:35 earth kernel: [    0.603176] efifb: scrolling: redraw
Jan 23 00:06:35 earth kernel: [    0.603177] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jan 23 00:06:35 earth kernel: [    0.603224] Console: switching to colour frame buffer device 80x43
Jan 23 00:06:35 earth kernel: [    0.603235] fb0: EFI VGA frame buffer device
Jan 23 00:06:35 earth kernel: [    0.603239] intel_idle: MWAIT substates: 0x1120
Jan 23 00:06:35 earth kernel: [    0.603240] intel_idle: v0.4 model 0x2A
Jan 23 00:06:35 earth kernel: [    0.603241] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan 23 00:06:35 earth kernel: [    0.603307] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Jan 23 00:06:35 earth kernel: [    0.603311] ACPI: Power Button [PWRB]
Jan 23 00:06:35 earth kernel: [    0.603341] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jan 23 00:06:35 earth kernel: [    0.603343] ACPI: Power Button [PWRF]
Jan 23 00:06:35 earth kernel: [    0.603360] ACPI: acpi_idle yielding to intel_idle
Jan 23 00:06:35 earth kernel: [    0.606646] ERST: Table is not found!
Jan 23 00:06:35 earth kernel: [    0.606706] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan 23 00:06:35 earth kernel: [    0.627097] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 23 00:06:35 earth kernel: [    0.715451] Freeing initrd memory: 13748k freed
Jan 23 00:06:35 earth kernel: [    0.853226] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 23 00:06:35 earth kernel: [    0.853430] Linux agpgart interface v0.103
Jan 23 00:06:35 earth kernel: [    0.853487] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
Jan 23 00:06:35 earth kernel: [    0.853565] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Jan 23 00:06:35 earth kernel: [    0.854449] agpgart-intel 0000:00:00.0: detected 262144K stolen memory
Jan 23 00:06:35 earth kernel: [    0.854526] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
Jan 23 00:06:35 earth kernel: [    0.855193] brd: module loaded
Jan 23 00:06:35 earth kernel: [    0.855502] loop: module loaded
Jan 23 00:06:35 earth kernel: [    0.855764] Fixed MDIO Bus: probed
Jan 23 00:06:35 earth kernel: [    0.855778] PPP generic driver version 2.4.2
Jan 23 00:06:35 earth kernel: [    0.855799] tun: Universal TUN/TAP device driver, 1.6
Jan 23 00:06:35 earth kernel: [    0.855800] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 23 00:06:35 earth kernel: [    0.855847] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 23 00:06:35 earth kernel: [    0.855861] ehci_hcd 0000:00:1a.0: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 23 00:06:35 earth kernel: [    0.855875] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.855878] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jan 23 00:06:35 earth kernel: [    0.855898] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 23 00:06:35 earth kernel: [    0.855919] ehci_hcd 0000:00:1a.0: debug port 2
Jan 23 00:06:35 earth kernel: [    0.859782] ehci_hcd 0000:00:1a.0: cache line size of 4 is not supported
Jan 23 00:06:35 earth kernel: [    0.859795] ehci_hcd 0000:00:1a.0: irq 18, io mem 0xfbffe000
Jan 23 00:06:35 earth kernel: [    0.872695] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jan 23 00:06:35 earth kernel: [    0.872770] hub 1-0:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    0.872773] hub 1-0:1.0: 2 ports detected
Jan 23 00:06:35 earth kernel: [    0.872820] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 23 00:06:35 earth kernel: [    0.872830] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    0.872832] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jan 23 00:06:35 earth kernel: [    0.872854] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 23 00:06:35 earth kernel: [    0.872873] ehci_hcd 0000:00:1d.0: debug port 2
Jan 23 00:06:35 earth kernel: [    0.876750] ehci_hcd 0000:00:1d.0: cache line size of 4 is not supported
Jan 23 00:06:35 earth kernel: [    0.876761] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbffd000
Jan 23 00:06:35 earth kernel: [    0.888665] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jan 23 00:06:35 earth kernel: [    0.888724] hub 2-0:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    0.888727] hub 2-0:1.0: 2 ports detected
Jan 23 00:06:35 earth kernel: [    0.888762] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 23 00:06:35 earth kernel: [    0.888769] uhci_hcd: USB Universal Host Controller Interface driver
Jan 23 00:06:35 earth kernel: [    0.888808] i8042: PNP: No PS/2 controller found. Probing ports directly.
Jan 23 00:06:35 earth kernel: [    0.921395] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
Jan 23 00:06:35 earth kernel: [    0.921396] i8042: If AUX port is really absent please use the 'i8042.noaux' option
Jan 23 00:06:35 earth kernel: [    1.172211] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 23 00:06:35 earth kernel: [    1.172254] mousedev: PS/2 mouse device common for all mice
Jan 23 00:06:35 earth kernel: [    1.172315] rtc_cmos 00:04: RTC can wake from S4
Jan 23 00:06:35 earth kernel: [    1.172392] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Jan 23 00:06:35 earth kernel: [    1.172417] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jan 23 00:06:35 earth kernel: [    1.172482] device-mapper: uevent: version 1.0.3
Jan 23 00:06:35 earth kernel: [    1.172527] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Jan 23 00:06:35 earth kernel: [    1.172590] cpuidle: using governor ladder
Jan 23 00:06:35 earth kernel: [    1.172689] cpuidle: using governor menu
Jan 23 00:06:35 earth kernel: [    1.172690] EFI Variables Facility v0.08 2004-May-17
Jan 23 00:06:35 earth kernel: [    1.172832] TCP cubic registered
Jan 23 00:06:35 earth kernel: [    1.172911] NET: Registered protocol family 10
Jan 23 00:06:35 earth kernel: [    1.173194] NET: Registered protocol family 17
Jan 23 00:06:35 earth kernel: [    1.173205] Registering the dns_resolver key type
Jan 23 00:06:35 earth kernel: [    1.173259] PM: Hibernation image not present or could not be loaded.
Jan 23 00:06:35 earth kernel: [    1.173267] registered taskstats version 1
Jan 23 00:06:35 earth kernel: [    1.184129] usb 1-1: new high speed USB device number 2 using ehci_hcd
Jan 23 00:06:35 earth kernel: [    1.184969]   Magic number: 12:686:637
Jan 23 00:06:35 earth kernel: [    1.185036] rtc_cmos 00:04: setting system clock to 2012-01-22 14:36:27 UTC (1327242987)
Jan 23 00:06:35 earth kernel: [    1.186066] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 23 00:06:35 earth kernel: [    1.186068] EDD information not available.
Jan 23 00:06:35 earth kernel: [    1.187274] Freeing unused kernel memory: 988k freed
Jan 23 00:06:35 earth kernel: [    1.187384] Write protecting the kernel read-only data: 12288k
Jan 23 00:06:35 earth kernel: [    1.192190] Freeing unused kernel memory: 2036k freed
Jan 23 00:06:35 earth kernel: [    1.195673] Freeing unused kernel memory: 1388k freed
Jan 23 00:06:35 earth kernel: [    1.210818] md: linear personality registered for level -1
Jan 23 00:06:35 earth kernel: [    1.213727] md: multipath personality registered for level -4
Jan 23 00:06:35 earth kernel: [    1.216580] md: raid0 personality registered for level 0
Jan 23 00:06:35 earth kernel: [    1.221740] md: raid1 personality registered for level 1
Jan 23 00:06:35 earth kernel: [    1.224576] async_tx: api initialized (async)
Jan 23 00:06:35 earth kernel: [    1.226134] sata_mv 0000:01:00.0: version 1.28
Jan 23 00:06:35 earth kernel: [    1.226157] sata_mv 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    1.226389] sata_mv 0000:01:00.0: Gen-IIE 32 slots 4 ports SCSI mode IRQ via INTx
Jan 23 00:06:35 earth kernel: [    1.226395] sata_mv 0000:01:00.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    1.228530] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 23 00:06:35 earth kernel: [    1.228550] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 23 00:06:35 earth kernel: [    1.228600] r8169 0000:04:00.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    1.228608] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
Jan 23 00:06:35 earth kernel: [    1.228691] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.229112] r8169 0000:04:00.0: eth0: RTL8168b/8111b at 0xffffc90000c7c000, 50:e5:49:4c:d2:13, XID 0c900800 IRQ 42
Jan 23 00:06:35 earth kernel: [    1.229853] scsi0 : sata_mv
Jan 23 00:06:35 earth kernel: [    1.230664] scsi1 : sata_mv
Jan 23 00:06:35 earth kernel: [    1.233573] scsi2 : sata_mv
Jan 23 00:06:35 earth kernel: [    1.235650] ahci 0000:00:1f.2: version 3.0
Jan 23 00:06:35 earth kernel: [    1.235663] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 23 00:06:35 earth kernel: [    1.235710] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.235720] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
Jan 23 00:06:35 earth kernel: [    1.235742] ahci: SSS flag set, parallel bus scan disabled
Jan 23 00:06:35 earth kernel: [    1.236312] scsi3 : sata_mv
Jan 23 00:06:35 earth kernel: [    1.236371] ata1: SATA max UDMA/133 mmio m1048576@0xfbc00000 port 0xfbc22000 irq 16
Jan 23 00:06:35 earth kernel: [    1.236374] ata2: SATA max UDMA/133 mmio m1048576@0xfbc00000 port 0xfbc24000 irq 16
Jan 23 00:06:35 earth kernel: [    1.236378] ata3: SATA max UDMA/133 mmio m1048576@0xfbc00000 port 0xfbc26000 irq 16
Jan 23 00:06:35 earth kernel: [    1.236381] ata4: SATA max UDMA/133 mmio m1048576@0xfbc00000 port 0xfbc28000 irq 16
Jan 23 00:06:35 earth kernel: [    1.239017] xhci_hcd 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan 23 00:06:35 earth kernel: [    1.239045] xhci_hcd 0000:05:00.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    1.239049] xhci_hcd 0000:05:00.0: xHCI Host Controller
Jan 23 00:06:35 earth kernel: [    1.239106] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 3
Jan 23 00:06:35 earth kernel: [    1.239239] xhci_hcd 0000:05:00.0: irq 19, io mem 0xfbef8000
Jan 23 00:06:35 earth kernel: [    1.239262] xhci_hcd 0000:05:00.0: Failed to enable MSI-X
Jan 23 00:06:35 earth kernel: [    1.239323] xhci_hcd 0000:05:00.0: irq 44 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.239461] xHCI xhci_add_endpoint called for root hub
Jan 23 00:06:35 earth kernel: [    1.239464] xHCI xhci_check_bandwidth called for root hub
Jan 23 00:06:35 earth kernel: [    1.239493] hub 3-0:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    1.239501] hub 3-0:1.0: 2 ports detected
Jan 23 00:06:35 earth kernel: [    1.239560] xhci_hcd 0000:05:00.0: xHCI Host Controller
Jan 23 00:06:35 earth kernel: [    1.239599] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 4
Jan 23 00:06:35 earth kernel: [    1.239679] xHCI xhci_add_endpoint called for root hub
Jan 23 00:06:35 earth kernel: [    1.239681] xHCI xhci_check_bandwidth called for root hub
Jan 23 00:06:35 earth kernel: [    1.239709] hub 4-0:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    1.239716] hub 4-0:1.0: 2 ports detected
Jan 23 00:06:35 earth kernel: [    1.241750] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
Jan 23 00:06:35 earth kernel: [    1.241753] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Jan 23 00:06:35 earth kernel: [    1.241774] e1000e 0000:02:00.0: Disabling ASPM L0s 
Jan 23 00:06:35 earth kernel: [    1.241795] e1000e 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 23 00:06:35 earth kernel: [    1.241812] e1000e 0000:02:00.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    1.241979] e1000e 0000:02:00.0: irq 45 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.241985] e1000e 0000:02:00.0: irq 46 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.241993] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    1.248030] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl RAID mode
Jan 23 00:06:35 earth kernel: [    1.248035] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pmp pio slum part ems apst 
Jan 23 00:06:35 earth kernel: [    1.248041] ahci 0000:00:1f.2: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    1.288266] scsi4 : ahci
Jan 23 00:06:35 earth kernel: [    1.288330] scsi5 : ahci
Jan 23 00:06:35 earth kernel: [    1.288387] scsi6 : ahci
Jan 23 00:06:35 earth kernel: [    1.288442] scsi7 : ahci
Jan 23 00:06:35 earth kernel: [    1.288495] scsi8 : ahci
Jan 23 00:06:35 earth kernel: [    1.288543] scsi9 : ahci
Jan 23 00:06:35 earth kernel: [    1.288642] ata5: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc100 irq 43
Jan 23 00:06:35 earth kernel: [    1.288644] ata6: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc180 irq 43
Jan 23 00:06:35 earth kernel: [    1.288647] ata7: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc200 irq 43
Jan 23 00:06:35 earth kernel: [    1.288649] ata8: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc280 irq 43
Jan 23 00:06:35 earth kernel: [    1.288651] ata9: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc300 irq 43
Jan 23 00:06:35 earth kernel: [    1.288653] ata10: SATA max UDMA/133 abar m2048@0xfbffc000 port 0xfbffc380 irq 43
Jan 23 00:06:35 earth kernel: [    1.291921] raid6: int64x1   1999 MB/s
Jan 23 00:06:35 earth kernel: [    1.316419] hub 1-1:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    1.316517] hub 1-1:1.0: 6 ports detected
Jan 23 00:06:35 earth kernel: [    1.346906] e1000e 0000:02:00.0: eth1: (PCI Express:2.5GT/s:Width x1) 00:1b:21:c5:f6:78
Jan 23 00:06:35 earth kernel: [    1.346909] e1000e 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
Jan 23 00:06:35 earth kernel: [    1.346920] e1000e 0000:02:00.0: eth1: MAC: 3, PHY: 8, PBA No: E46981-006
Jan 23 00:06:35 earth kernel: [    1.359791] raid6: int64x2   3099 MB/s
Jan 23 00:06:35 earth kernel: [    1.427661] raid6: int64x4   2675 MB/s
Jan 23 00:06:35 earth kernel: [    1.427670] usb 2-1: new high speed USB device number 2 using ehci_hcd
Jan 23 00:06:35 earth kernel: [    1.495528] raid6: int64x8   2117 MB/s
Jan 23 00:06:35 earth kernel: [    1.559420] Refined TSC clocksource calibration: 2594.107 MHz.
Jan 23 00:06:35 earth kernel: [    1.559424] Switching to clocksource tsc
Jan 23 00:06:35 earth kernel: [    1.563398] raid6: sse2x1    6866 MB/s
Jan 23 00:06:35 earth kernel: [    1.631273] raid6: sse2x2    6542 MB/s
Jan 23 00:06:35 earth kernel: [    1.699145] raid6: sse2x4    6692 MB/s
Jan 23 00:06:35 earth kernel: [    1.699146] raid6: using algorithm sse2x1 (6866 MB/s)
Jan 23 00:06:35 earth kernel: [    1.699680] hub 2-1:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    1.699778] hub 2-1:1.0: 8 ports detected
Jan 23 00:06:35 earth kernel: [    1.707156] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 23 00:06:35 earth kernel: [    1.723160] ata1.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Jan 23 00:06:35 earth kernel: [    1.723162] ata1.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jan 23 00:06:35 earth kernel: [    1.739130] ata1.00: configured for UDMA/133
Jan 23 00:06:35 earth kernel: [    1.739255] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    1.739373] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jan 23 00:06:35 earth kernel: [    1.739376] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 23 00:06:35 earth kernel: [    1.739432] sd 0:0:0:0: [sda] Write Protect is off
Jan 23 00:06:35 earth kernel: [    1.739439] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 23 00:06:35 earth kernel: [    1.739471] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    1.758809]  sda: sda1
Jan 23 00:06:35 earth kernel: [    1.759018] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 23 00:06:35 earth kernel: [    1.810941] usb 3-1: new high speed USB device number 2 using xhci_hcd
Jan 23 00:06:35 earth kernel: [    1.830381] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Jan 23 00:06:35 earth kernel: [    1.832752] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Jan 23 00:06:35 earth kernel: [    1.834498] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Jan 23 00:06:35 earth kernel: [    1.835189] hub 3-1:1.0: USB hub found
Jan 23 00:06:35 earth kernel: [    1.835995] xhci_hcd 0000:05:00.0: WARN: short transfer on control ep
Jan 23 00:06:35 earth kernel: [    1.836135] hub 3-1:1.0: 4 ports detected
Jan 23 00:06:35 earth kernel: [    1.870837] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jan 23 00:06:35 earth kernel: [    1.882730] ata5.00: ATA-8: Patriot Pyro, 332ABBF0, max UDMA/133
Jan 23 00:06:35 earth kernel: [    1.882735] ata5.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 23 00:06:35 earth kernel: [    1.892598] ata5.00: configured for UDMA/133
Jan 23 00:06:35 earth kernel: [    1.910904] usb 1-1.1: new high speed USB device number 3 using ehci_hcd
Jan 23 00:06:35 earth kernel: [    2.005732] usbcore: registered new interface driver uas
Jan 23 00:06:35 earth kernel: [    2.074597] usb 1-1.5: new low speed USB device number 4 using ehci_hcd
Jan 23 00:06:35 earth kernel: [    2.214225] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 23 00:06:35 earth kernel: [    2.230207] ata2.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Jan 23 00:06:35 earth kernel: [    2.230210] ata2.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jan 23 00:06:35 earth kernel: [    2.242280] usb 1-1.6: new low speed USB device number 5 using ehci_hcd
Jan 23 00:06:35 earth kernel: [    2.246179] ata2.00: configured for UDMA/133
Jan 23 00:06:35 earth kernel: [    2.246294] scsi 1:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    2.246383] sd 1:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jan 23 00:06:35 earth kernel: [    2.246411] sd 1:0:0:0: Attached scsi generic sg1 type 0
Jan 23 00:06:35 earth kernel: [    2.246436] sd 1:0:0:0: [sdb] Write Protect is off
Jan 23 00:06:35 earth kernel: [    2.246439] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jan 23 00:06:35 earth kernel: [    2.246462] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    2.266353]  sdb: sdb1
Jan 23 00:06:35 earth kernel: [    2.266567] sd 1:0:0:0: [sdb] Attached SCSI disk
Jan 23 00:06:35 earth kernel: [    2.346202] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input2
Jan 23 00:06:35 earth kernel: [    2.346268] generic-usb 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1a.0-1.5/input0
Jan 23 00:06:35 earth kernel: [    2.349457] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3
Jan 23 00:06:35 earth kernel: [    2.349514] generic-usb 0003:045E:0750.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Wired Keyboard 600] on usb-0000:00:1a.0-1.6/input0
Jan 23 00:06:35 earth kernel: [    2.355679] input: Microsoft Wired Keyboard 600 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input4
Jan 23 00:06:35 earth kernel: [    2.355734] generic-usb 0003:045E:0750.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Wired Keyboard 600] on usb-0000:00:1a.0-1.6/input1
Jan 23 00:06:35 earth kernel: [    2.355744] usbcore: registered new interface driver usbhid
Jan 23 00:06:35 earth kernel: [    2.355745] usbhid: USB HID core driver
Jan 23 00:06:35 earth kernel: [    2.833036] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 23 00:06:35 earth kernel: [    2.849044] ata3.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Jan 23 00:06:35 earth kernel: [    2.849047] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jan 23 00:06:35 earth kernel: [    2.865014] ata3.00: configured for UDMA/133
Jan 23 00:06:35 earth kernel: [    2.865135] scsi 2:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    2.865228] sd 2:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jan 23 00:06:35 earth kernel: [    2.865253] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jan 23 00:06:35 earth kernel: [    2.865279] sd 2:0:0:0: [sdc] Write Protect is off
Jan 23 00:06:35 earth kernel: [    2.865282] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jan 23 00:06:35 earth kernel: [    2.865310] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    3.268689]  sdc: sdc1
Jan 23 00:06:35 earth kernel: [    3.268899] sd 2:0:0:0: [sdc] Attached SCSI disk
Jan 23 00:06:35 earth kernel: [    3.340093] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 23 00:06:35 earth kernel: [    3.356093] ata4.00: ATA-8: WDC WD20EARS-00MVWB0, 51.0AB51, max UDMA/133
Jan 23 00:06:35 earth kernel: [    3.356096] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Jan 23 00:06:35 earth kernel: [    3.372060] ata4.00: configured for UDMA/133
Jan 23 00:06:35 earth kernel: [    3.372164] scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EARS-00M 51.0 PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    3.372252] sd 3:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Jan 23 00:06:35 earth kernel: [    3.372269] sd 3:0:0:0: Attached scsi generic sg3 type 0
Jan 23 00:06:35 earth kernel: [    3.372303] sd 3:0:0:0: [sdd] Write Protect is off
Jan 23 00:06:35 earth kernel: [    3.372306] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Jan 23 00:06:35 earth kernel: [    3.372368] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    3.372375] scsi 4:0:0:0: Direct-Access     ATA      Patriot Pyro     332A PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    3.372482] sd 4:0:0:0: [sde] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
Jan 23 00:06:35 earth kernel: [    3.372501] sd 4:0:0:0: Attached scsi generic sg4 type 0
Jan 23 00:06:35 earth kernel: [    3.372551] sd 4:0:0:0: [sde] Write Protect is off
Jan 23 00:06:35 earth kernel: [    3.372554] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
Jan 23 00:06:35 earth kernel: [    3.372576] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    3.375366]  sde: sde1 sde2 sde3
Jan 23 00:06:35 earth kernel: [    3.375643] sd 4:0:0:0: [sde] Attached SCSI disk
Jan 23 00:06:35 earth kernel: [    3.393053]  sdd: sdd1
Jan 23 00:06:35 earth kernel: [    3.393269] sd 3:0:0:0: [sdd] Attached SCSI disk
Jan 23 00:06:35 earth kernel: [    3.691416] ata6: SATA link down (SStatus 0 SControl 300)
Jan 23 00:06:35 earth kernel: [    4.010815] ata7: SATA link down (SStatus 0 SControl 300)
Jan 23 00:06:35 earth kernel: [    4.330215] ata8: SATA link down (SStatus 0 SControl 300)
Jan 23 00:06:35 earth kernel: [    4.649614] ata9: SATA link down (SStatus 0 SControl 300)
Jan 23 00:06:35 earth kernel: [    5.140687] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 23 00:06:35 earth kernel: [    5.143260] ata10.00: ATAPI: ATAPI   iHAS224   B, GL0A, max UDMA/100
Jan 23 00:06:35 earth kernel: [    5.144085] ata10.00: configured for UDMA/100
Jan 23 00:06:35 earth kernel: [    5.146039] scsi 9:0:0:0: CD-ROM            ATAPI    iHAS224   B      GL0A PQ: 0 ANSI: 5
Jan 23 00:06:35 earth kernel: [    5.149373] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 23 00:06:35 earth kernel: [    5.149377] cdrom: Uniform CD-ROM driver Revision: 3.20
Jan 23 00:06:35 earth kernel: [    5.149466] sr 9:0:0:0: Attached scsi CD-ROM sr0
Jan 23 00:06:35 earth kernel: [    5.149506] sr 9:0:0:0: Attached scsi generic sg5 type 5
Jan 23 00:06:35 earth kernel: [    5.149987] xor: automatically using best checksumming function: generic_sse
Jan 23 00:06:35 earth kernel: [    5.150358] Initializing USB Mass Storage driver...
Jan 23 00:06:35 earth kernel: [    5.157036] scsi10 : usb-storage 1-1.1:1.0
Jan 23 00:06:35 earth kernel: [    5.157343] usbcore: registered new interface driver usb-storage
Jan 23 00:06:35 earth kernel: [    5.157345] USB Mass Storage support registered.
Jan 23 00:06:35 earth kernel: [    5.168617]    generic_sse: 11090.000 MB/sec
Jan 23 00:06:35 earth kernel: [    5.168621] xor: using function: generic_sse (11090.000 MB/sec)
Jan 23 00:06:35 earth kernel: [    5.169344] md: raid6 personality registered for level 6
Jan 23 00:06:35 earth kernel: [    5.169346] md: raid5 personality registered for level 5
Jan 23 00:06:35 earth kernel: [    5.169348] md: raid4 personality registered for level 4
Jan 23 00:06:35 earth kernel: [    5.173782] md: raid10 personality registered for level 10
Jan 23 00:06:35 earth kernel: [    5.200000] EXT4-fs (sde3): INFO: recovery required on readonly filesystem
Jan 23 00:06:35 earth kernel: [    5.200003] EXT4-fs (sde3): write access will be enabled during recovery
Jan 23 00:06:35 earth kernel: [    5.216579] md: bind<sdb1>
Jan 23 00:06:35 earth kernel: [    5.220196] md: bind<sda1>
Jan 23 00:06:35 earth kernel: [    5.234641] md: bind<sdc1>
Jan 23 00:06:35 earth kernel: [    5.236282] md: bind<sdd1>
Jan 23 00:06:35 earth kernel: [    5.237812] bio: create slab <bio-1> at 1
Jan 23 00:06:35 earth kernel: [    5.237817] md/raid0:md127: looking at sdd1
Jan 23 00:06:35 earth kernel: [    5.237818] md/raid0:md127:   comparing sdd1(3907021824) with sdd1(3907021824)
Jan 23 00:06:35 earth kernel: [    5.237821] md/raid0:md127:   END
Jan 23 00:06:35 earth kernel: [    5.237836] md/raid0:md127:   ==> UNIQUE
Jan 23 00:06:35 earth kernel: [    5.237838] md/raid0:md127: 1 zones
Jan 23 00:06:35 earth kernel: [    5.237840] md/raid0:md127: looking at sdc1
Jan 23 00:06:35 earth kernel: [    5.237842] md/raid0:md127:   comparing sdc1(3907021824) with sdd1(3907021824)
Jan 23 00:06:35 earth kernel: [    5.237845] md/raid0:md127:   EQUAL
Jan 23 00:06:35 earth kernel: [    5.237847] md/raid0:md127: looking at sda1
Jan 23 00:06:35 earth kernel: [    5.237849] md/raid0:md127:   comparing sda1(3907021824) with sdd1(3907021824)
Jan 23 00:06:35 earth kernel: [    5.237852] md/raid0:md127:   EQUAL
Jan 23 00:06:35 earth kernel: [    5.237854] md/raid0:md127: looking at sdb1
Jan 23 00:06:35 earth kernel: [    5.237855] md/raid0:md127:   comparing sdb1(3907021824) with sdd1(3907021824)
Jan 23 00:06:35 earth kernel: [    5.237858] md/raid0:md127:   EQUAL
Jan 23 00:06:35 earth kernel: [    5.237860] md/raid0:md127: FINAL 1 zones
Jan 23 00:06:35 earth kernel: [    5.237868] md/raid0:md127: done.
Jan 23 00:06:35 earth kernel: [    5.237870] md/raid0:md127: md_size is 15628087296 sectors.
Jan 23 00:06:35 earth kernel: [    5.237872] ******* md127 configuration *********
Jan 23 00:06:35 earth kernel: [    5.237875] zone0=[sdd1/sdc1/sdb1/sda1/]
Jan 23 00:06:35 earth kernel: [    5.237880]         zone offset=0kb device offset=0kb size=7814043648kb
Jan 23 00:06:35 earth kernel: [    5.237882] **********************************
Jan 23 00:06:35 earth kernel: [    5.237883] 
Jan 23 00:06:35 earth kernel: [    5.237892] md127: detected capacity change from 0 to 8001580695552
Jan 23 00:06:35 earth kernel: [    5.239234]  md127: unknown partition table
Jan 23 00:06:35 earth kernel: [    5.284377] EXT4-fs (sde3): orphan cleanup on readonly fs
Jan 23 00:06:35 earth kernel: [    5.284384] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098343
Jan 23 00:06:35 earth kernel: [    5.284426] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098294
Jan 23 00:06:35 earth kernel: [    5.284447] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098329
Jan 23 00:06:35 earth kernel: [    5.284457] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098289
Jan 23 00:06:35 earth kernel: [    5.284465] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2099925
Jan 23 00:06:35 earth kernel: [    5.284474] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098327
Jan 23 00:06:35 earth kernel: [    5.284482] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2099920
Jan 23 00:06:35 earth kernel: [    5.284491] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2100927
Jan 23 00:06:35 earth kernel: [    5.284500] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098470
Jan 23 00:06:35 earth kernel: [    5.284518] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098347
Jan 23 00:06:35 earth kernel: [    5.284526] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097904
Jan 23 00:06:35 earth kernel: [    5.284535] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097900
Jan 23 00:06:35 earth kernel: [    5.284544] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 528353
Jan 23 00:06:35 earth kernel: [    5.284553] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 526216
Jan 23 00:06:35 earth kernel: [    5.284561] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097849
Jan 23 00:06:35 earth kernel: [    5.284570] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097878
Jan 23 00:06:35 earth kernel: [    5.284578] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097815
Jan 23 00:06:35 earth kernel: [    5.284587] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097816
Jan 23 00:06:35 earth kernel: [    5.284595] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2097811
Jan 23 00:06:35 earth kernel: [    5.284603] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098373
Jan 23 00:06:35 earth kernel: [    5.284612] EXT4-fs (sde3): ext4_orphan_cleanup: deleting unreferenced inode 2098355
Jan 23 00:06:35 earth kernel: [    5.284620] EXT4-fs (sde3): 21 orphan inodes deleted
Jan 23 00:06:35 earth kernel: [    5.284622] EXT4-fs (sde3): recovery complete
Jan 23 00:06:35 earth kernel: [    5.286114] EXT4-fs (sde3): mounted filesystem with ordered data mode. Opts: (null)
Jan 23 00:06:35 earth kernel: [    6.155398] scsi 10:0:0:0: Direct-Access     ADATA    USB Flash Drive  1.00 PQ: 0 ANSI: 6
Jan 23 00:06:35 earth kernel: [    6.259025] sd 10:0:0:0: Attached scsi generic sg6 type 0
Jan 23 00:06:35 earth kernel: [    6.259538] sd 10:0:0:0: [sdf] 30883840 512-byte logical blocks: (15.8 GB/14.7 GiB)
Jan 23 00:06:35 earth kernel: [    6.260034] sd 10:0:0:0: [sdf] Write Protect is off
Jan 23 00:06:35 earth kernel: [    6.260036] sd 10:0:0:0: [sdf] Mode Sense: 23 00 00 00
Jan 23 00:06:35 earth kernel: [    6.260533] sd 10:0:0:0: [sdf] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Jan 23 00:06:35 earth kernel: [    6.263413]  sdf: sdf1
Jan 23 00:06:35 earth kernel: [    6.265399] sd 10:0:0:0: [sdf] Attached SCSI removable disk
Jan 23 00:06:35 earth kernel: [    8.756806] Adding 3905532k swap on /dev/sde2.  Priority:-1 extents:1 across:3905532k SS
Jan 23 00:06:35 earth kernel: [    8.763275] type=1400 audit(1327242995.090:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763284] type=1400 audit(1327242995.090:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=510 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763295] type=1400 audit(1327242995.090:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=542 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763634] type=1400 audit(1327242995.090:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763642] type=1400 audit(1327242995.090:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=510 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763652] type=1400 audit(1327242995.090:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=542 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763864] type=1400 audit(1327242995.090:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763872] type=1400 audit(1327242995.090:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=510 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.763893] type=1400 audit(1327242995.090:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=542 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.764190] lp: driver loaded but no devices found
Jan 23 00:06:35 earth kernel: [    8.775397] mei: module is from the staging directory, the quality is unknown, you have been warned.
Jan 23 00:06:35 earth kernel: [    8.775798] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    8.775805] mei 0000:00:16.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    8.783538] [drm] Initialized drm 1.1.0 20060810
Jan 23 00:06:35 earth kernel: [    8.800715] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 00:06:35 earth kernel: [    8.800721] i915 0000:00:02.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    8.818863] wmi: Mapper loaded
Jan 23 00:06:35 earth kernel: [    8.820680] EXT4-fs (sde3): re-mounted. Opts: errors=remount-ro
Jan 23 00:06:35 earth kernel: [    8.842776] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Jan 23 00:06:35 earth kernel: [    8.850224] i915 0000:00:02.0: irq 48 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    8.850231] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jan 23 00:06:35 earth kernel: [    8.850233] [drm] Driver supports precise vblank timestamp query.
Jan 23 00:06:35 earth kernel: [    8.850267] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan 23 00:06:35 earth kernel: [    8.886422] type=1400 audit(1327242995.214:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=983 comm="apparmor_parser"
Jan 23 00:06:35 earth kernel: [    8.964565] Bluetooth: Core ver 2.16
Jan 23 00:06:35 earth kernel: [    8.964585] NET: Registered protocol family 31
Jan 23 00:06:35 earth kernel: [    8.964587] Bluetooth: HCI device and connection manager initialized
Jan 23 00:06:35 earth kernel: [    8.964589] Bluetooth: HCI socket layer initialized
Jan 23 00:06:35 earth kernel: [    8.964591] Bluetooth: L2CAP socket layer initialized
Jan 23 00:06:35 earth kernel: [    8.964737] Bluetooth: SCO socket layer initialized
Jan 23 00:06:35 earth kernel: [    8.967008] Bluetooth: RFCOMM TTY layer initialized
Jan 23 00:06:35 earth kernel: [    8.967013] Bluetooth: RFCOMM socket layer initialized
Jan 23 00:06:35 earth kernel: [    8.967016] Bluetooth: RFCOMM ver 1.11
Jan 23 00:06:35 earth kernel: [    8.974721] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 23 00:06:35 earth kernel: [    8.974724] Bluetooth: BNEP filters: protocol multicast
Jan 23 00:06:35 earth kernel: [    8.992078] init: failsafe main process (929) killed by TERM signal
Jan 23 00:06:35 earth kernel: [    8.992864] init: apport pre-start process (1038) terminated with status 1
Jan 23 00:06:35 earth kernel: [    8.993766] init: alsa-restore main process (1051) terminated with status 19
Jan 23 00:06:35 earth kernel: [    9.013152] init: apport post-stop process (1141) terminated with status 1
Jan 23 00:06:35 earth kernel: [    9.046447] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 23 00:06:35 earth kernel: [    9.053968] r8169 0000:04:00.0: eth0: link down
Jan 23 00:06:35 earth kernel: [    9.054624] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 23 00:06:35 earth kernel: [    9.226848] /dev/vmmon[1302]: Module vmmon: registered with major=10 minor=165
Jan 23 00:06:35 earth kernel: [    9.226856] /dev/vmmon[1302]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
Jan 23 00:06:35 earth kernel: [    9.226862] /dev/vmmon[1302]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
Jan 23 00:06:35 earth kernel: [    9.226865] /dev/vmmon[1302]: Module vmmon: initialized
Jan 23 00:06:35 earth kernel: [    9.232816] [1310]: VMCI: shared components initialized.
Jan 23 00:06:35 earth kernel: [    9.232855] [1310]: VMCI: host components initialized.
Jan 23 00:06:35 earth kernel: [    9.232906] [1310]: VMCI: Module registered (name=vmci,major=10,minor=57).
Jan 23 00:06:35 earth kernel: [    9.232909] [1310]: VMCI: Using host personality
Jan 23 00:06:35 earth kernel: [    9.232911] [1310]: VMCI: Module (name=vmci) is initialized
Jan 23 00:06:35 earth kernel: [    9.293256] checking generic (a0000 e000) vs hw (e0000000 10000000)
Jan 23 00:06:35 earth kernel: [    9.293259] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
Jan 23 00:06:35 earth kernel: [    9.293284] Console: switching to colour dummy device 80x25
Jan 23 00:06:35 earth kernel: [    9.293415] fbcon: inteldrmfb (fb0) is primary device
Jan 23 00:06:35 earth kernel: [    9.293491] Console: switching to colour frame buffer device 170x48
Jan 23 00:06:35 earth kernel: [    9.293498] fb0: inteldrmfb frame buffer device
Jan 23 00:06:35 earth kernel: [    9.293500] drm: registered panic notifier
Jan 23 00:06:35 earth kernel: [    9.293564] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 23 00:06:35 earth kernel: [    9.294175] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 23 00:06:35 earth kernel: [    9.294240] HDA Intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Jan 23 00:06:35 earth kernel: [    9.294267] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan 23 00:06:35 earth kernel: [    9.304981] ppdev: user-space parallel port driver
Jan 23 00:06:36 earth kernel: [    9.817546] /dev/vmnet: open called by PID 1393 (vmnet-netifup)
Jan 23 00:06:36 earth kernel: [    9.817552] /dev/vmnet: hub 1 does not exist, allocating memory.
Jan 23 00:06:36 earth kernel: [    9.817566] /dev/vmnet: port on hub 1 successfully opened
Jan 23 00:06:36 earth kernel: [    9.825167] /dev/vmnet: open called by PID 1396 (vmnet-dhcpd)
Jan 23 00:06:36 earth kernel: [    9.825178] /dev/vmnet: port on hub 1 successfully opened
Jan 23 00:06:36 earth kernel: [    9.827858] /dev/vmnet: open called by PID 1402 (vmnet-natd)
Jan 23 00:06:36 earth kernel: [    9.827867] /dev/vmnet: hub 8 does not exist, allocating memory.
Jan 23 00:06:36 earth kernel: [    9.827886] /dev/vmnet: port on hub 8 successfully opened
Jan 23 00:06:36 earth kernel: [    9.829616] /dev/vmnet: open called by PID 1403 (vmnet-netifup)
Jan 23 00:06:36 earth kernel: [    9.829625] /dev/vmnet: port on hub 8 successfully opened
Jan 23 00:06:36 earth kernel: [    9.837091] /dev/vmnet: open called by PID 1408 (vmnet-dhcpd)
Jan 23 00:06:36 earth kernel: [    9.837104] /dev/vmnet: port on hub 8 successfully opened
Jan 23 00:06:36 earth kernel: [    9.850566] HDMI hot plug event: Pin=7 Presence_Detect=1 ELD_Valid=0
Jan 23 00:06:36 earth kernel: [    9.850589] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=0
Jan 23 00:06:36 earth kernel: [    9.850621] HDMI status: Pin=7 Presence_Detect=1 ELD_Valid=0
Jan 23 00:06:36 earth kernel: [    9.850960] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
Jan 23 00:06:36 earth kernel: [    9.920692] EXT4-fs (sde3): re-mounted. Opts: errors=remount-ro,commit=0
Jan 23 00:06:36 earth kernel: [    9.922540] EXT4-fs (sde1): re-mounted. Opts: commit=0
Jan 23 00:06:37 earth kernel: [   11.557131] EXT4-fs (sde3): re-mounted. Opts: errors=remount-ro,commit=0
Jan 23 00:06:37 earth kernel: [   11.559154] EXT4-fs (sde1): re-mounted. Opts: commit=0
Jan 23 00:06:38 earth kernel: [   12.256253] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Jan 23 00:06:38 earth kernel: [   12.256879] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 23 00:06:38 earth kernel: [   12.257168] /dev/vmnet: open called by PID 1385 (vmnet-bridge)
Jan 23 00:06:38 earth kernel: [   12.257178] /dev/vmnet: hub 0 does not exist, allocating memory.
Jan 23 00:06:38 earth kernel: [   12.257199] /dev/vmnet: port on hub 0 successfully opened
Jan 23 00:06:38 earth kernel: [   12.257215] bridge-eth1: up
Jan 23 00:06:38 earth kernel: [   12.257217] bridge-eth1: attached
Jan 23 00:06:38 earth kernel: [   12.456769] userif-2: sent link down event.
Jan 23 00:06:39 earth kernel: [   12.456772] userif-2: sent link up event.
Jan 23 00:06:39 earth kernel: [   13.461863] userif-2: sent link down event.
Jan 23 00:06:46 earth kernel: [   13.461866] userif-2: sent link up event.
Jan 23 00:06:46 earth kernel: [   20.519753] vmnet1: no IPv6 routers present
Jan 23 00:06:47 earth kernel: [   20.663484] vmnet8: no IPv6 routers present
Jan 23 00:06:48 earth kernel: [   22.348321] eth1: no IPv6 routers present
Jan 23 00:07:16 earth kernel: [   24.196844] /dev/vmmon[0]: HostIFReadUptimeWork: detected settimeofday: fixed uptimeBase old 18445416830713994670 new 18445416830688470685 attempts 1
Jan 23 00:09:58 earth kernel: [  186.473228] init: plymouth-stop pre-start process (2668) terminated with status 1
Jan 23 00:12:54 earth kernel: [  362.130711] md127: detected capacity change from 8001580695552 to 0
Jan 23 00:12:54 earth kernel: [  362.130717] md: md127 stopped.
Jan 23 00:12:54 earth kernel: [  362.130722] md: unbind<sdd1>
Jan 23 00:12:54 earth kernel: [  362.221282] md: export_rdev(sdd1)
Jan 23 00:12:54 earth kernel: [  362.221487] md: unbind<sdc1>
Jan 23 00:12:54 earth kernel: [  362.253221] md: export_rdev(sdc1)
Jan 23 00:12:54 earth kernel: [  362.253371] md: unbind<sda1>
Jan 23 00:12:54 earth kernel: [  362.253411] md: export_rdev(sda1)
Jan 23 00:12:54 earth kernel: [  362.253555] md: unbind<sdb1>
Jan 23 00:12:54 earth kernel: [  362.260833] md: export_rdev(sdb1)
Jan 23 00:12:56 earth kernel: [  364.025926] md: md0 stopped.
Jan 23 00:12:56 earth kernel: [  364.027486] md: bind<sdc1>
Jan 23 00:12:56 earth kernel: [  364.028056] md: bind<sdb1>
Jan 23 00:12:56 earth kernel: [  364.028173] md: bind<sda1>
Jan 23 00:12:56 earth kernel: [  364.028285] md: bind<sdd1>
Jan 23 00:12:56 earth kernel: [  364.031091] md/raid0:md0: looking at sdd1
Jan 23 00:12:56 earth kernel: [  364.031094] md/raid0:md0:   comparing sdd1(3907021824) with sdd1(3907021824)
Jan 23 00:12:56 earth kernel: [  364.031096] md/raid0:md0:   END
Jan 23 00:12:56 earth kernel: [  364.031097] md/raid0:md0:   ==> UNIQUE
Jan 23 00:12:56 earth kernel: [  364.031098] md/raid0:md0: 1 zones
Jan 23 00:12:56 earth kernel: [  364.031100] md/raid0:md0: looking at sda1
Jan 23 00:12:56 earth kernel: [  364.031101] md/raid0:md0:   comparing sda1(3907021824) with sdd1(3907021824)
Jan 23 00:12:56 earth kernel: [  364.031103] md/raid0:md0:   EQUAL
Jan 23 00:12:56 earth kernel: [  364.031104] md/raid0:md0: looking at sdb1
Jan 23 00:12:56 earth kernel: [  364.031105] md/raid0:md0:   comparing sdb1(3907021824) with sdd1(3907021824)
Jan 23 00:12:56 earth kernel: [  364.031107] md/raid0:md0:   EQUAL
Jan 23 00:12:56 earth kernel: [  364.031108] md/raid0:md0: looking at sdc1
Jan 23 00:12:56 earth kernel: [  364.031109] md/raid0:md0:   comparing sdc1(3907021824) with sdd1(3907021824)
Jan 23 00:12:56 earth kernel: [  364.031111] md/raid0:md0:   EQUAL
Jan 23 00:12:56 earth kernel: [  364.031112] md/raid0:md0: FINAL 1 zones
Jan 23 00:12:56 earth kernel: [  364.031115] md/raid0:md0: done.
Jan 23 00:12:56 earth kernel: [  364.031116] md/raid0:md0: md_size is 15628087296 sectors.
Jan 23 00:12:56 earth kernel: [  364.031118] ******* md0 configuration *********
Jan 23 00:12:56 earth kernel: [  364.031119] zone0=[sdd1/sdc1/sdb1/sda1/]
Jan 23 00:12:56 earth kernel: [  364.031122]         zone offset=0kb device offset=0kb size=7814043648kb
Jan 23 00:12:56 earth kernel: [  364.031123] **********************************
Jan 23 00:12:56 earth kernel: [  364.031124] 
Jan 23 00:12:56 earth kernel: [  364.031135] md0: detected capacity change from 0 to 8001580695552
Jan 23 00:12:56 earth kernel: [  364.033742]  md0: unknown partition table
Jan 23 00:13:10 earth kernel: [  377.675472] EXT4-fs (md0): recovery complete
Jan 23 00:13:10 earth kernel: [  377.675657] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
Jan 23 00:13:26 earth kernel: [  394.410403] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by Th3Blaze on 2012-01-27
Since there has been no helpful replies since, I'll try to use what I've been given, and use lshw. I've had a look inside poked around and nothing seems in place, how do I check what's wrong ?

---

### Post by sixteenornumber on 2012-02-14
:::BUMP:::

im still getting crashes here.  I'm averaging around 2 per day.  I'm wondering more and more if it is hardware related.  I know we probobly dont but it would be interesting if we shared a common part.

Gigabyte Z68MA-D2H-B3
Intel i3-2120T
Patriot Pyro 60GB
Intel EXPI9301CTBLK 10/ 100/ 1000Mbps PCI-Express Network Adapter
Rosewill RC-218 PCI Express SATA II Controller Card 
G.Skill 2x4GB F3-14900CL9D-8GBXL

---

### Post by sixteenornumber on 2012-02-17
I got rid of the raid card and so far I've been stable for 2 days 13 hours compared to the 12 hours at best that i had before.

:p:p:p:p:p:p:P:P

P.S.

I HATE you Rosewill. you and your homo-erotic raid card!

---

