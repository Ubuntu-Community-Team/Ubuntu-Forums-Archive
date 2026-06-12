---
title: "ubuntu the only distro that heats up?"
date: 2010-03-06
forum: General Help
---

### Post by sincerelyydavid on 2010-03-06
overheating seems to be a problem for laptops. is ubuntu the only distro having this heating issue? is this a driver problem?

---

### Post by spiderbatdad on 2010-03-06
> **sincerelyydavid said:**
> overheating seems to be a problem for laptops. is ubuntu the only distro having this heating issue? is this a driver problem?

This is spreading FUD. Ubuntu nor Linux in general has anything to do with laptop overheating issues. Mac has had many models overheating > MacBook Air - Wikipedia, the free encyclopedia
Several MacBook Air users since the release of the first-generation product have complained of severe overheating causing CPU lockup. ...
 A one time Dell was having many issues > Dell Inspiron - Wikipedia, the free encyclopedia
The laptop was infamous for a huge number of design failures, overheating, battery failures, connector loosening, motherboard failures.
So just because a few user have posted here with overheating issue does not make it an Ubuntu issue. A very few models need a module tweaking to get the fan to run sooner (very few), again not a Ubuntu issue.

If you're having an overheating issue, it's one thing to post a question regarding that issue, another to ask whether Ubuntu is the only distro with this problem...as if we all have the same problem on our laptops.

---

### Post by Fir3chi3f on 2010-03-06
It would be helpful to provide your system specs along with questions like this sincerelyydavid.

My laptop was overheating a while back and the fan was just clogged with dust. I thought it might be a problem with ubuntu at first because Ubuntu would immediately shut down and windows would stay running. In actuality Windows was just letting my cpu cook

I suggest cleaning out your fan and maybe replacing it if doesn't really spin after being cleaned.

---

### Post by Keith1212 on 2010-03-06
I run Ubuntu on my Dell Latitude D520 with out any over heating at all. I just watch movies and play music while dling other stuff. I don't do any major gaming as my laptop has integrated gfx.

---

### Post by switch10 on 2010-03-06
I think the biggest factor in overheating is dust build up....

---

### Post by sincerelyydavid on 2010-03-06
i don't think it's dust. i've cleaned it. while on windows 7, my laptop stays cool, even after hours of extreme usage. on ubuntu, it overheats even after half an hour of watching a movie. i'm thinking it's a driver issue that's preventing my fan from working or something

---

### Post by flippo on 2010-03-06
Ubuntu should handle your power well, mine handles my macbook pro (a known overheater) just as well as mac does (not that I like how mac handles it...).  If your laptop isn't handling the power well its most likely a bad setting or driver issue.  I installed the gnome-sensors-applet and cpu frequency scaling monitor to help me ensure all of my hardware is working appropriately (The conservative governor is much more power friendly than performance... thats for sure).

Hope this helps.

---

### Post by elliotn on 2010-03-06
Overheating means something is doing its job eg the fans or the dusty heatsink. I+ aint ubuntu problem

---

### Post by 2hot6ft2 on 2010-03-06
> **sincerelyydavid said:**
> overheating seems to be a problem for laptops. is ubuntu the only distro having this heating issue? is this a driver problem?
And this is supposed to let us know what drivers you have.:confused:
There are 2 threads for very specific graphics drivers which the have been removed by the mfg. until they figure out what's going on. Again not a ubuntu issue.

---

### Post by MooPi on 2010-03-06
sinserelydavid, We are going to need some system specs and a minimum of a make and model number to begin to help with your question. With that info we can start to narrow down the cause of your heat problem. So Make , Model and open a terminal and type ```
sudo lshw>specs
``` This will dump a text of your system specs in your home folder. Copy and paste that text here for us to see if your  hardware needs special attention.

---

### Post by sincerelyydavid on 2010-03-06
here are the specs when i did sudo lshw>specs:
```
david-laptop
    description: Notebook
    product: HP Pavilion dv4 Notebook PC
    vendor: Hewlett-Packard
    version: F.55
    serial: CND9251C62
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=0DE7BAEB-5453-11DE-AE63-00235AAA365C
  *-core
       description: Motherboard
       product: 30F7
       vendor: Compal
       physical id: 0
       version: 99.B9
       serial: CND9251C62
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.55 (10/06/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: e
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPU
          size: 1200MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: f
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 10
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 16HTF25664HY-800G1
             vendor: Micron
             physical id: 0
             serial: D51BF226
             slot: Bottom - Slot 2 (under)
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 16HTF25664HY-800G1
             vendor: Micron
             physical id: 1
             serial: D51BF225
             slot: Bottom - Slot 1 (top)
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
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
             resources: irq:31 memory:d0000000-d03fffff memory:c0000000-cfffffff(prefetchable) ioport:60f0(size=8)
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
             resources: memory:d5400000-d54fffff
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
             resources: irq:16 ioport:60c0(size=32)
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
             resources: irq:17 ioport:60a0(size=32)
        *-usb:2
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
             resources: irq:18 memory:da504c00-da504fff
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
             resources: irq:32 memory:da500000-da503fff
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
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:5000(size=4096) memory:d9500000-da4fffff ioport:d0400000(size=16777216)
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
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:4000(size=4096) memory:d8500000-d94fffff ioport:d1400000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth2
                version: 01
                serial: 00:21:00:f2:7f:3d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:d8500000-d8503fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:3000(size=4096) memory:d7500000-d84fffff ioport:d2400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:23:5a:aa:36:5c
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.47 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:30 ioport:3000(size=256) memory:d2410000-d2410fff(prefetchable) memory:d2400000-d240ffff(prefetchable) memory:d2420000-d243ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:2000(size=4096) memory:d6500000-d74fffff ioport:d3400000(size=16777216)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:d6500300-d65003ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d6500200-d65002ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:16 memory:d6500100-d65001ff
           *-generic:3 UNCLAIMED
                description: System peripheral
                product: xD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.4
                bus info: pci@0000:04:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
                resources: memory:d6500000-d65000ff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 ioport:1000(size=4096) memory:d5500000-d64fffff ioport:d4400000(size=16777216)
        *-usb:3
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
             resources: irq:20 ioport:6080(size=32)
        *-usb:4
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
             resources: irq:22 ioport:6060(size=32)
        *-usb:5
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
             resources: irq:18 ioport:6040(size=32)
        *-usb:6
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
             resources: irq:20 memory:da504800-da504bff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             resources: irq:29 ioport:60e8(size=8) ioport:60fc(size=4) ioport:60e0(size=8) ioport:60f8(size=4) ioport:6020(size=32) memory:da504000-da5047ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK3255GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FG01
                serial: 692ET0WIT
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=27265bbe
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d6fe57a0-9949-4c86-8f48-ce275a6bb735
                   size: 289GiB
                   capacity: 289GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-02-28 17:46:02 filesystem=ext4 lastmountpoint=/Y6í&#353;&#8364;Kï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;[cï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;9ï¿&#339;ï¿&#339;@ï¿&#339;sï¿&#339;@ï¿&#339;sï¿&#339;Kï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ïï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;ï¿&#339;Kï¿&#339;4&ï¿&#339; modified=2010-02-28 18:11:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-03-06 19:14:21 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 8581MiB
                   capacity: 8581MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8581MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT20L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DC03
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
             resources: memory:da505000-da5050ff ioport:6000(size=32)
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 10/12/2007
       serial: Battery 0
       slot: Fake 
```

and Moopi: what's a make/model?

---

### Post by MooPi on 2010-03-07
Well it looks as if you own a HP computer (make) and the (model) Pavillion DV4.
Now that we know this info we can research and see if this model has a history of over heating.
[http://www.laptopsarena.com/hp-laptop-pavilion-dv4-overheating/](http://www.laptopsarena.com/hp-laptop-pavilion-dv4-overheating/)
I don't use Intel, but I'm guessing because your issue is not with the Windows side It may have to do with scaling the CPU back when idle. [http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)  The last last paragraph in the blog 
might be of most use for you.

---

### Post by sincerelyydavid on 2010-03-07
> **MooPi said:**
> Well it looks as if you own a HP computer (make) and the (model) Pavillion DV4.
Now that we know this info we can research and see if this model has a history of over heating.
[http://www.laptopsarena.com/hp-laptop-pavilion-dv4-overheating/](http://www.laptopsarena.com/hp-laptop-pavilion-dv4-overheating/)
I don't use Intel, but I'm guessing because your issue is not with the Windows side It may have to do with scaling the CPU back when idle. [http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)  The last last paragraph in the blog 
might be of most use for you.
I'm not understanding the blog. what i'm getting from it is to lower my frequency from like 2.10 Ghz to 1.3 GHz. wouldn't this slow down my computer and not take advantage of the 2.10 GHz laptop i bought?

---

### Post by MooPi on 2010-03-07
I don't use Intel products generally so I'm generalizing from an AMD perspective. If I have something called Kool&Quiet enabled in the bios for my processor, it scales back whenever the computer is idle. Generally half speed during idle periods. I suppose this utility functions similarly. Maybe someone will read this post that uses Intel and will give a definitive response. Or you can try the blogs advice and hope for the best.

---

### Post by adam814 on 2010-03-07
I have a Core 2 Duo T5800 myself.  Each time I've done a clean install of Ubuntu I've had to run sensors-detect from the "lm-sensors" detect.  It's always detected a module or two and offered to add them to /etc/modules to be loaded on boot.  Prior to doing this I've always had my laptops run hotter than I'd like and none of the hardware sensor programs/applets have functioned properly.

As it's always been related to failing to load certain kernel modules it's probably a pretty broad Linux issue, although different distros could handle which modules are built-in/loaded by default differently.  It's certainly not been enough to steer me away from Ubuntu, I'll just continue to run sensors-detect post-install.

---

