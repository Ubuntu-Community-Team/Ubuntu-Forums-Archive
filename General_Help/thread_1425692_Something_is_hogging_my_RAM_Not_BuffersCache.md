---
title: "Something is hogging my RAM **Not Buffers/Cache**"
date: 2010-03-09
forum: General Help
---

### Post by Drewmach on 2010-03-09
Hi Everyone. I'm having the following problem that I just can't figure out. 

At boot, my laptop works great. It uses around 500MB of RAM, and everything runs snappy and I have no issues. However, the longer I keep it running, the higher my RAM usage goes up, and it's not buffers/cache that is using it. My laptop has been up for 12 hours now, and the performance is degrading as more RAM is being used, and eventually I have to restart because it becomes unusable. When I look at the output of top, I can't see what is using all my RAM.

Here is the output of **free -m**:
```
             total       used       free     shared    buffers     cached
Mem:          3894       2499       1395          0         12        384
-/+ buffers/cache:       2101       1792
Swap:            0          0          0

```

This output is telling me that I am using 2.1GB of RAM, correct?


Output of **top**:
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND               
580 root      40   0  203m  54m  10m R   12  1.4  40:36.79 Xorg                  
828 andrew    40   0  241m  23m  17m S    5  0.6   0:24.76 gnome-system-mo       
721 andrew    40   0  391m  54m 2324 S    2  1.4   6:14.55 compiz.real           
947 root      20   0     0    0    0 S    1  0.0   3:07.39 phy0                  
739 andrew    40   0  279m  24m 3224 S    1  0.6  18:57.25 python                
761 andrew    40   0  262m  24m 3680 S    0  0.6   1:44.16 ubuntuone-clien       
750 mysql     40   0  163m  30m  448 S    0  0.8   0:22.67 mysqld                
830 root      40   0 19232 1404  980 S    0  0.0   0:04.92 top                   
229 andrew    20   0  451m  24m  15m S    0  0.6   0:11.03 chrome                
494 andrew    40   0 19132 1400  980 R    0  0.0   0:00.30 top                   
836 andrew    40   0  221m  13m 7796 S    0  0.4   0:08.84 gnome-terminal        
  1 root      40   0 19432 1248  628 S    0  0.0   1:36.97 init                  
  2 root      40   0     0    0    0 S    0  0.0   0:00.00 kthreadd              
  3 root      RT   0     0    0    0 S    0  0.0   0:02.07 migration/0           
  4 root      20   0     0    0    0 S    0  0.0   0:00.33 ksoftirqd/0           
  5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0            
  6 root      RT   0     0    0    0 S    0  0.0   0:02.79 migration/1           
  7 root      20   0     0    0    0 S    0  0.0   0:09.16 ksoftirqd/1           
  8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1            
  9 root      20   0     0    0    0 S    0  0.0   0:02.96 events/0              
 10 root      20   0     0    0    0 S    0  0.0   0:03.02 events/1              
 11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                
 12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper               
 13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                 
 14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr             
 15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers           
 16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default           
 17 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0         
 18 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1         
 19 root      20   0     0    0    0 S    0  0.0   0:00.39 kblockd/0             
 20 root      20   0     0    0    0 S    0  0.0   0:00.63 kblockd/1             
 21 root      20   0     0    0    0 S    0  0.0   0:00.41 kacpid                
 22 root      20   0     0    0    0 S    0  0.0   0:02.06 kacpi_notify          
 23 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug         
 24 root      20   0     0    0    0 S    0  0.0   0:00.00 ata/0                               

```

Perhaps I'm missing something, but the output of free and top don't match up, even when taking into consideration buffers/cache.

Anyone have any ideas what the problem could be?

---

### Post by Peter09 on 2010-03-09
In practice you should only get performance problems when you start using Swap. Linux generally will use as much RAM as possible to speed up your system. If you are seeing degraded performance it will be because of CPU use not RAM.

---

### Post by cpressland on 2010-03-09
System looks fine to me, as long as swap isn't being used everything should be A-OK!

---

### Post by Drewmach on 2010-03-09
Well, I turned off swap because my system will start to use it when the RAM builds up like this and gets even slower. 

At the moment I only have 1 tab in Chrome running, and a few terminal windows. What is using 2 GB of RAM??  I wouldn't normally care how Linux handles my RAM, but something is wrong because it becomes unbearably slow after a few hours.

---

### Post by cpressland on 2010-03-09
You turned off SWAP?! Why? It's there as a failsafe to stop you getting out of memory errors. And if you look at your own output again you'll see you have 1792MB of free memory. The performance issues are not memory related, more likely a conflicting application or driver. Post up a full system spec and the kernel you're using dude.

---

### Post by Drewmach on 2010-03-09
I turned swap off because my system was using it to much, even with lots of RAM available. I don't run any applications that would require more than 4 GB of memory. 

Linux Kernel: 2.6.32-020632-generic

Here is the output of **sudo lshw**

```
description: Portable Computer
    product: M-7315U
    vendor: Gateway
    version: Rev 1
    serial: LXW190X002843296782500
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=portable uuid=04D657CE-6731-3E3A-0328-97193DB97B1D
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 96.05
       serial: QTFCPP84210062&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 96.04 (07/23/2008)
          size: 104KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
          slot: uFCPGA2
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             serial: 63709F6C
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             serial: 6370A089
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:f0000000-f03fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0400000-f04fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f0b04800-f0b04bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f0900000-f0903fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f0500000-f05fffff ioport:f0c00000(size=1048576)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan1
                version: 01
                serial: 00:1f:3a:6c:db:c2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.1.105 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:16 memory:f0500000-f050ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f0600000-f06fffff ioport:f0d00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f0700000-f07fffff memory:bc000000-bc1fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 12
                serial: 00:e0:b8:ea:46:f1
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:f0700000-f0703fff ioport:4000(size=256)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0b04c00-f0b04fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f0800000-f08fffff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 9
                bus info: pci@0000:07:09.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
                resources: memory:f0800000-f0800fff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 9.2
                bus info: pci@0000:07:09.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:16 memory:f0801000-f08010ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f0b04000-f0b047ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54322
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FBEO
                serial: 081017FB2F00LLHV9EMB
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d839ce20
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Windows1
                   version: 3.1
                   serial: ee55-fd68
                   size: 10238MiB
                   capacity: 10GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-10-25 18:52:18 filesystem=ntfs label=PQSERVICE mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Windows2
                   version: 3.1
                   serial: c2edc0ec-5198-2149-a262-27479e0405bf
                   size: 91GiB
                   capacity: 91GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-05-13 01:46:04 filesystem=ntfs label=OS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 11GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /home
                      capacity: 7993MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 886MiB
                      capabilities: nofs
              *-volume:3
                   description: Windows NTFS volume
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /media/Data
                   version: 3.1
                   serial: 2c4be648-3722-8549-8043-38b0ca9fe45f
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-05-13 07:43:58 filesystem=ntfs label=DATA mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SX07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:bc200000-bc2000ff ioport:1c00(size=32)
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SANYO
       physical id: 1
       version: 2008/08/21
       serial: 10568
       slot: In the Back side
       capacity: 4400mWh
       configuration: voltage=11.1V

```

If you prefer another command for the system specs, let me know.
Thanks for the help so far guys, I really appreciate it.

---

### Post by cpressland on 2010-03-09
That is a weird one bud, all your hardware is fully compatable with Linux, it's all bog standard Intel gear.

Hmm, could you turn SWAP back on, reboot the machine. Then run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Complete all upgrades and hope for the best dude. Beyond this, I'm completely stumpped, I can't see anything eating your memory so it's got to be something else....

---

### Post by Drewmach on 2010-03-09
I ran both commands and the only thing that updated was chrome. Thanks for the help. 


> **cpressland said:**
> That is a weird one bud, all your hardware is fully compatable with Linux, it's all bog standard Intel gear.

Hmm, could you turn SWAP back on, reboot the machine. Then run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Complete all upgrades and hope for the best dude. Beyond this, I'm completely stumpped, I can't see anything eating your memory so it's got to be something else....

---

### Post by cpressland on 2010-03-09
I'm completely out of ideas then bud, but memory is deffo not the cause, does CPU spike really high when the slowdowns occur?

---

### Post by Peter09 on 2010-03-09
The only thing I can think of is that your CPU is going over temperature and dropping back to some low frequency. Check your system is not running too hot.

---

### Post by no2498 on 2010-03-09
try this it help me on 910 karmic

open a terminal type. gstreamer-properties click video
set the plugin to. x window system (no xv)
right down what its set to so you can set it back if it does not work for you

i do think you need to restart the computer before it works

---

### Post by Drewmach on 2010-03-09
When my RAM fills up and my system slows down, It seems everything goes haywire. My CPU usage goes up, and my hard drive is always spinning. This all usually happens when my RAM usage reaches around 3GB. It's not because of my processor temp, I monitor it and it rarely goes above 50c.

I'll give this a try, thanks no2498.
> **no2498 said:**
> try this it help me on 910 karmic

open a terminal type. gstreamer-properties click video
set the plugin to. x window system (no xv)
right down what its set to so you can set it back if it does not work for you

i do think you need to restart the computer before it works

---

