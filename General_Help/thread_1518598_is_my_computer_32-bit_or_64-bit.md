---
title: "is my computer 32-bit or 64-bit"
date: 2010-06-26
forum: General Help
---

### Post by spawn82 on 2010-06-26
hey all just wonder if my computer is 32 0r 64 bit here is some info when i type in    uname -a in my teminal 
Linux doug 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux

if aome could help it would be much appriecated thanks

---

### Post by warfacegod on 2010-06-26
23 UTC 2010 i686 GNU/Linux

The i686 means you have 32 bit.

---

### Post by WorMzy on 2010-06-26
> Linux doug 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 [COLOR="Red"]i686[/COLOR] GNU/Linux

You have 32-bit Ubuntu installed, but that doesn't mean that your computer is incapable of running 64-bit. What processor do you have?

---

### Post by Jakiejake on 2010-06-26
> **spawn82 said:**
> hey all just wonder if my computer is 32 0r 64 bit here is some info when i type in    uname -a in my teminal 
Linux doug 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux

if aome could help it would be much appriecated thanks

As they said 32 Bit
It seems like your processor is incapable of running 64 bit
How old is your cpu? What Model? How old is your pc?

---

### Post by warfacegod on 2010-06-26
A more precise way is:

```
sudo lshw
```

and scroll back to the top and check where it says "width:"

Example:

```
*-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
**          width: 32 bits**

```

---

### Post by Leppie on 2010-06-26
nowadays most processors are 64 bit, however the chipset isn't necessarily 64 bit as well.
type in the following command:
```
lshw -c cpu -c video
```if under both sections you get 64 bits, you've got a 64 bit system.
this is the result of the command on the machine i'm currently on:
```
lshw -c video -c cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Pentium(R) Dual-Core  CPU      E6500  @ 2.93GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.7.10
       serial: 0001-067A-0000-0000-0000-0000
       size: 2950MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority
       configuration: id=0
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
  *-display
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:ec00(size=8)

```it's a 64 bit system, but i installed 32 bit lucid (cuz this machine has only 2gb of RAM).

---

### Post by oldos2er on 2010-06-27
> **Leppie said:**
> it's a 64 bit system, but i installed 32 bit lucid (cuz this machine has only 2gb of RAM).

64-bit Ubuntu runs great on 2GB RAM.

---

### Post by tom.swartz07 on 2010-06-27
> **oldos2er said:**
> 64-bit Ubuntu runs great on 2GB RAM.

+1
Yeah, theres no 'minimum' amount of ram you need for 64 bit system. However, there is a maximum for 32 bit systems; they can only access 4gb of ram, any more than that and you need 64bit.

---

### Post by spawn82 on 2010-06-27
> **WorMzy said:**
> You have 32-bit Ubuntu installed, but that doesn't mean that your computer is incapable of running 64-bit. What processor do you have?
 
im not sure im at work till late tonight i can get back to you on that in the morning 
thanks heaps for ya help

---

### Post by Off Topic on 2010-06-27
I thought this might have been Spawny from the PBB until I realized he can spell and has a job.

---

### Post by Leppie on 2010-06-27
> **tom.swartz07 said:**
> +1
Yeah, theres no 'minimum' amount of ram you need for 64 bit system. However, there is a maximum for 32 bit systems; they can only access 4gb of ram, any more than that and you need 64bit.
the 64 bit os does use more ram using the exact same applications, furthermore a lot of the 64 bit applications are only compiled on 64 bit machines (hence no performance improvement) and not all applications are available as 64 bit.
but again, the 64 bit os does require more ram. i believe the turnover point is somewhere around 6gb.

---

### Post by cascade9 on 2010-06-27
> **oldos2er said:**
> 64-bit Ubuntu runs great on 2GB RAM.
 
 +2. So do all the other 64bit linux OSes I've used in thellast 1.5 years (some of the older versions were a bit flakey, but that is fixed now) 

> **tom.swartz07 said:**
> +1
Yeah, theres no 'minimum' amount of ram you need for 64 bit system. However, there is a maximum for 32 bit systems; they can only access 4gb of ram, any more than that and you need 64bit.

Nope, with PAE 32bit systems can go a  lot higher. AFAIK, there is a theoritical limit of 64GB with PAE, and while I havent tseted it, most (all?) linxu distros with a PAE kernel can go to at least 8GB, and should go all the way to 64GB. 

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

> **Leppie said:**
> the 64 bit os does use more ram using the exact same applications, furthermore a lot of the 64 bit applications are only compiled on 64 bit machines (hence no performance improvement) and not all applications are available as 64 bit.
but again, the 64 bit os does require more ram. i believe the turnover point is somewhere around 6gb.

64bit might use a bit more memory, but I've never seen any hard data on that. Even then, once you have 1GB+, is it really that much of an issue? The only time I use all my 2GB is ripping/encoding video. 

64bit DOES have a performance inprovment, even with older linux versions, and only 2GB of RAM. See here- 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

And here- 
 
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by spawn82 on 2010-06-27
> **warfacegod said:**
> A more precise way is:

```
sudo lshw
```and scroll back to the top and check where it says "width:"

Example:

```
*-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: NWD
          size: 2800MHz
          capacity: 3200MHz
**          width: 32 bits**

```
  

description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: Rev 1.xx
    serial: SYS-1234567890
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=A05E3517-8EFE-D511-A1ED-001FC62E633D
  *-core
       description: Motherboard
       product: P5GC-MX
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev x.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0402 (12/04/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: LGA 775
          size: 1998MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 333MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back instruction
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
     *-memory
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 1998MHz
          capacity: 1998MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff(prefetchable) memory:dfe80000-dfebffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:dfef8000-dfefbfff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096)
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:d000(size=4096) memory:dff00000-dfffffff
           *-network
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: a0
                serial: 00:1f:c6:2e:63:3d
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 duplex=full firmware=L2 ip=10.0.0.1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:26 memory:dffc0000-dfffffff memory:dffa0000-dffbffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:9000(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:9400(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:9800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a000(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:dfeffc00-dfefffff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:c000(size=4096)
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:22 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
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
             resources: irq:23 ioport:b800(size=8) ioport:b400(size=4) ioport:b000(size=8) ioport:a800(size=4) ioport:a400(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200AAJS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCARW5232226
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f0e6f0e6
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 652fa951-2fa6-46e0-ba92-562ded81853a
                   size: 292GiB
                   capacity: 292GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-06-04 21:39:28 filesystem=ext3 modified=2010-06-27 10:24:29 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-06-27 10:29:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 5875MiB
                   capacity: 5875MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5875MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DRW-2014L1T
                vendor: ASUS
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)

---

### Post by spawn82 on 2010-06-27
> **Leppie said:**
> nowadays most processors are 64 bit, however the chipset isn't necessarily 64 bit as well.
type in the following command:
```
lshw -c cpu -c video
```if under both sections you get 64 bits, you've got a 64 bit system.
this is the result of the command on the machine i'm currently on:
```
lshw -c video -c cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Pentium(R) Dual-Core  CPU      E6500  @ 2.93GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.7.10
       serial: 0001-067A-0000-0000-0000-0000
       size: 2950MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority
       configuration: id=0
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
  *-display
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:fe400000-fe7fffff memory:d0000000-dfffffff(prefetchable) ioport:ec00(size=8)

```it's a 64 bit system, but i installed 32 bit lucid (cuz this machine has only 2gb of RAM).


here is what you after from what i can see its 64bit but only running 32bit is that right 

WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       size: 2664MHz
       capacity: 2664MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
       configuration: id=0
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
  *-display
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff(prefetchable) memory:dfe80000-dfebffff

---

### Post by Leppie on 2010-06-27
> **spawn82 said:**
> here is what you after from what i can see its 64bit but only running 32bit is that right 

```
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
       vendor: Intel Corp.
       physical id: 1
       bus info: cpu@0
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       size: 2664MHz
       capacity: 2664MHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
       configuration: id=0
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
  *-display
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       **[COLOR=Red]width: 32 bits[/COLOR]**
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff(prefetchable) memory:dfe80000-dfebffff
```
though your cpu is 64 bit, your chip set seems to be only 32 bit.

---

### Post by warfacegod on 2010-06-27
Yep, your 64 running 32.

---

### Post by spawn82 on 2010-06-27
> **Leppie said:**
> though your cpu is 64 bit, your chip set seems to be only 32 bit.
  


so with the chipset only being 32bit what does that mean and can i use 64bit programs 
and thanks for your help 
:p

---

### Post by warfacegod on 2010-06-27
Okay wait a minute. There are two different readouts here. The one in code brackets is different from the non-bracketed one.

---

### Post by warfacegod on 2010-06-27
```
*-display
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
**       width: 64 bits**
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0

```

This is the one inside the brackets. Which one are we supposed to look at?

---

### Post by warfacegod on 2010-06-27
Never mind. I figured it out. The one in the brackets is a quote from Leppie's post.

---

### Post by spawn82 on 2010-06-27
> **warfacegod said:**
> Okay wait a minute. There are two different readouts here. The one in code brackets is different from the non-bracketed one.


what does that mean im sorry im kinda new to all these codes i only understand a little

---

### Post by Leppie on 2010-06-27
> **spawn82 said:**
> what does that mean im sorry im kinda new to all these codes i only understand a little
it means that your cpu is 64 bit, but the rest of your system isn't.

---

### Post by spawn82 on 2010-06-27
> **Leppie said:**
> it means that your cpu is 64 bit, but the rest of your system isn't.


can i change that so the hole system is 64 bit and how

---

### Post by laithk50 on 2010-06-27
> **spawn82 said:**
> can i change that so the hole system is 64 bit and how

Well, from what I'm reading you could always get a new graphics card. Any one will do, most to all of them are 64-bit anyhow. I prefer Nvidia (just saying)

Good Luck:KS

---

### Post by warfacegod on 2010-06-27
> **spawn82 said:**
> what does that mean im sorry im kinda new to all these codes i only understand a little

It means that I was reading the specs for Leppie's computer that you quoted. It got rather confusing.

I'm not sure how it works with the motherboard. Whether or not *it* needs to be 64 bit or not but it seems safe to assume that it does. I think you'll need to figure that out. As far as the graphics go, it would be a matter of finding a video card that does support 64 bit.

---

### Post by warfacegod on 2010-06-27
I just checked out you Motherboard on newegg.com. It takes 4 GB RAM so I think it's safe to say that it will take 64 bit. FYI: Evidently it's well liked as a starter for people just learning to build their own computers.

---

### Post by spawn82 on 2010-06-27
thanks all for your help and clearing that up i will now look in to making my hole computer 64 bit

---

### Post by warfacegod on 2010-06-27
I agree with laithk50 on recommending nVidia. They have the best Linux support. ATi is getting better but there are still plenty of problems. Intel is worthless. Hell, I'm not even sure they make non-integrated cards.

Whichever way you go, be certain you do your homework on the card to make sure it runs well with Ubuntu. And if you plan on using any of the Visual Effects, such as Compiz, go with at least a 256 MB card. 512 MB or higher would be best.

I guess you can mark this Thread as Solved.

---

### Post by spawn82 on 2010-06-27
> **warfacegod said:**
> I agree with laithk50 on recommending nVidia. They have the best Linux support. ATi is getting better but there are still plenty of problems. Intel is worthless. Hell, I'm not even sure they make non-integrated cards.

Whichever way you go, be certain you do your homework on the card to make sure it runs well with Ubuntu. And if you plan on using any of the Visual Effects, such as Compiz, go with at least a 256 MB card. 512 MB or higher would be best.

I guess you can mark this Thread as Solved.


thanks heaps i will deffenatly do my home work and thaks for clearing all that up

---

### Post by cascade9 on 2010-06-28
> **Leppie said:**
> though your cpu is 64 bit, your chip set seems to be only 32 bit.

OK, why did you highlight the video width? 

> **warfacegod said:**
> I just checked out you Motherboard on newegg.com. It takes 4 GB RAM so I think it's safe to say that it will take 64 bit. FYI: Evidently it's well liked as a starter for people just learning to build their own computers.

4GB support is not a good indicator. There were pentium 3 chipsets that supported 4GB! (VIA Apollo Pro 266/266T). 

As far as I know, if the chipset supports a 64-bit CPU (and of course youhave a 64-bit CPU installed) it will work with a 64-bit OS. There could well be excpetions to this rule, but that would be rare. I've never seen a single example anyway, but if somebody has, gimmie a link please....I'd be intrrested in seeing what/where/how/who, and maybe even figuring out why. 

Just a pit that intel doesnt really mention 64-bit support much on its site. I guess they are/were smarting about AMD beating them to desktop 64-bit. Also probably bit pissed off because that was the final straw for the itanium, which intel was hoping could help push CPU prices back up to 'OMG' which is what intel always wanted. All they tend to have is oblique references to 64bit- 

> Dual-channel  										[DDR2]("http://www.intel.com/technology/memory/index.htm") Memory Support 									Up to 10.7 GB/s of bandwidth and 4GB memory addressability for faster system responsiveness and support for 64-bit computing.

[http://www.intel.com/products/desktop/chipsets/945g/945g-overview.htm](http://www.intel.com/products/desktop/chipsets/945g/945g-overview.htm)

But wait, there is another way to know, for sure, if your motherbaord supports 64-bit. Just get the motherboard model number (P5GC-MX in this case), go to the manufactutrers site, look for drivers..and see if there is any XP 64, vista 64 or win7 64 drivers. There is for the P5GC-MX so I am 100% sure it does support 64bit. 

#&^#%&$& asus. I found the page once, but can I get back? Noooo! Click on the "P5GC-MX" link and it kicks me back to the initial product page. *sigh* I've had this happen before, and its part of the reason why I dont recommend asus anymore. asus, you suck. So badly I wont even capitalise your name at the beginning of a sentance.

---

### Post by Leppie on 2010-06-28
> **cascade9 said:**
> OK, why did you highlight the video width?
because like the machine i was on, his machine's got an integrated video card:
```
product: 82945G/GZ [COLOR=Red]**Integrated**[/COLOR] Graphics Controller
vendor: Intel Corporation
```so yes, he does have a 32 bit chip set and not 64 bit...
the fact that 64 bit cpu's are backwards compatible with 32 bit cpu's, and therefore can be mounted in 32 bit systems without any problem, doesn't mean your whole system is 64 bit capable.

---

### Post by cascade9 on 2010-06-28
> **Leppie said:**
> because like the machine i was on, his machine's got an integrated video card:
```
product: 82945G/GZ [COLOR=Red]**Integrated**[/COLOR] Graphics Controller
vendor: Intel Corporation
```so yes, he does have a 32 bit chip set and not 64 bit...
the fact that 64 bit cpu's are backwards compatible with 32 bit cpu's, and therefore can be mounted in 32 bit systems without any problem, doesn't mean your whole system is 64 bit capable.

32bit video doesnt mean that the system isnt 64bit capable. Lots of 64bit systems withb AGP cards, and AGP is only 32bit....Lots of 64bit systems with 945 video around as well. 

Anyway, there are drivers for 6bit windows OSes on the asus site, including for the video. 

[http://www.asus.com/product.aspx?P_ID=vddABl4wQXZXLyQY](http://www.asus.com/product.aspx?P_ID=vddABl4wQXZXLyQY)

Go there, then to 'downlaod' then select a 64bit OS. Then check the 'video' and you will find this sort of thing-

Intel 945G  Display Driver V6.14.10.4885 for Windows 64bit XP (WHQL)

If the system doesnt support 64bit, then why would there be drivers? :P

---

### Post by Leppie on 2010-06-28
i forgot about this option, but the quickest way to check if your system is 64 bit capable is by issuing the "lshw" command from the ubuntu live environment. it will tell you if so.

---

### Post by warfacegod on 2010-06-28
It's got all kinds of 64 bit hardware in it. The CPU, RAM, Sound Card, even the Ethernet Card is 64. *And* it's a Desktop, why does it matter if the video is integrated? It also has PCIe X4 [http://www.asus.com/Product.aspx?P_ID=PYvbfOokwxUzJky3](http://www.asus.com/Product.aspx?P_ID=PYvbfOokwxUzJky3) which should be fine for 64 bit graphics cards (being certain, of course, to buy a card that will fit in it).

Using the drivers, in this case, as an indicator of 64 bit, isn't going to work. All of the drivers I looked at in the list are 32/64 compliant. Which means they'll work regardless of architecture.

Everything I've seen so far, aside from the drivers, leads me to believe that 64 is fine. However, I think the only *certain* way, at this point, to find out is to contact Asus and ask. "Will the P5GC-MX handle a 64 bit video card *and* run a 64 bit OS?"

---

### Post by cascade9 on 2010-06-28
I dont get the preoccupation with the 32bit width on a 64bit OS. It works, or else you couldnt run PCI or AGP video cards on 64bit. 

BTW, that is the reason why it is a 32bit width, the video uses agpgart. 

> **spawn82 said:**
> 
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff(prefetchable) memory:dfe80000-dfebffff
        

> **warfacegod said:**
> Using the drivers, in this case, as an indicator of 64 bit, isn't going to work. All of the drivers I looked at in the list are 32/64 compliant. Which means they'll work regardless of architecture.

Point on the drivers, but then again, from everything I know and have seen, intel never bothered making 32/64bit drivers for chipsets that will never have a 64bit CPU installed (eg intel 810, 845). (exception- win7 drivers, but they work a little differently to the earlier windows OSes IIRC). 

945GC = GMA 950, and there are lots of people running 64bit on GMA950. 

> **warfacegod said:**
> Everything I've seen so far, aside from the drivers, leads me to believe that 64 is fine. However, I think the only *certain* way, at this point, to find out is to contact Asus and ask. "Will the P5GC-MX handle a 64 bit video card *and* run a 64 bit OS?"

Easier to just try a 64bit live CD. 

But I am 100% certain it will work. I'd even gamble on that, and I never bet unless its a sure thing.

---

### Post by warfacegod on 2010-06-28
> Easier to just try a 64bit live CD.

But I am 100% certain it will work. I'd even gamble on that, and I never bet unless its a sure thing.

Why did it take so long for any of us to recommend that? Oh, wait. Never mind. We're geeks and we like doing things the hard way and nitpicking over the details.

I'd take that bet but I'm on your side. Unless, of course, there's some "street found" computers parts on the line?:p

---

### Post by cascade9 on 2010-06-29
Nitpick? NITPICK? I, sir, do not 'nitpick'- quibble, bicker and niggle, yes, but never nitpick :lolflag:

---

