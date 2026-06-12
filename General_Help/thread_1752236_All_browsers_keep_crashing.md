---
title: "All browsers keep crashing"
date: 2011-05-07
forum: General Help
---

### Post by HappyLinux on 2011-05-07
I've got an annoying problem. On a regular basis my browsers keep crashing out on various websites. YouTube, Newgrounds, etc.

One moment I'm doing something, the next thing, it just froze. Firefox 4, Opera 11.10 and Chrome 11.

Each crash is different, but they crash never the less.
Firefox freezes and when I try to close it, the whole screen turns to a blank light blue. After a moment a message pops up to allow it to be forcefully terminated.
Opera is similar.
Chrome is different. You just cannot shut it down for quite some time.

I'm guessing it has something to do with Flash, but I'm already running the latest version with the help of Flash-Aid.

Is anyone else experiencing the same sort of problem??

---

### Post by pbpersson on 2011-05-07
You are using Maverick Meerkat?

The first two ideas that come to mind:

1.  Check the system logs to see what is happening behind the scenes
2.  Start the application from a command line prompt.  Quite often some interesting messages will be sent to the console which otherwise get sent nowhere.

---

### Post by Quackers on 2011-05-07
See if updating Flash helps.

---

### Post by Voluntaryist on 2011-05-07
I've also found out that putting the libflashplayer.so file in the plugins folder for chrome will help its performance with flash and will reduce crashes.

---

### Post by neu5eeCh on 2011-05-07
Have you tried this:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

When I was using Ubuntu this addon fixed everything. (I've also switched to Xubuntu.) It might be worth a try

---

### Post by HappyLinux on 2011-05-08
> **pbpersson said:**
> You are using Maverick Meerkat?

The first two ideas that come to mind:

1.  Check the system logs to see what is happening behind the scenes
2.  Start the application from a command line prompt.  Quite often some interesting messages will be sent to the console which otherwise get sent nowhere.

Sorry, which one is Maverick Meerkat?? I don't follow the names, only the version numbers. I'm using Kubuntu 11.04.

1. Where is the system logs??
2. How do I start the applications through command line prompt??

---

### Post by HappyLinux on 2011-05-08
> **Quackers said:**
> See if updating Flash helps.

I already did.

---

### Post by HappyLinux on 2011-05-08
> **VTPoet said:**
> Have you tried this:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

When I was using Ubuntu this addon fixed everything. (I've also switched to Xubuntu.) It might be worth a try

Yes, I've been running that. I mentioned that in my first post.

---

### Post by Duncan Williams on 2011-05-08
One defined issue of late:
goto youtube, click on a video to bring up a flash window.
right click on the video and choose `settings'

here you can enable/disable `hardware acceleration' 

this function causes problems for some users.

---

### Post by HappyLinux on 2011-05-10
> **Duncan Williams said:**
> One defined issue of late:
goto youtube, click on a video to bring up a flash window.
right click on the video and choose `settings'

here you can enable/disable `hardware acceleration' 

this function causes problems for some users.

Hardware Acceleration is already disabled.

---

### Post by Duncan Williams on 2011-05-10
It's starting to sound more like graphic card, video drivers or possibly even bios setting.
I had problems with wrong agp aperture setting on my system bios after changing a graphic card.

Are you using proprietory graphic card drivers?

---

### Post by HappyLinux on 2011-05-15
> **Duncan Williams said:**
> It's starting to sound more like graphic card, video drivers or possibly even bios setting.
I had problems with wrong agp aperture setting on my system bios after changing a graphic card.

Are you using proprietory graphic card drivers?

It's neither BIOS or graphics card problems. It could be a driver problem. I know this, because I dual boot with Win7 and there's zero problems there.

My nVidia drivers under Linux is currently 270.41.06.

---

### Post by Duncan Williams on 2011-05-15
One thing. I had/have dual boot with windows (xp).

I had problems with my ubuntu partition and then lost it as it would not let me past grub. (windows was booting/working fine).
It took me weeks of doing all sorts of things including re-installing, etc.
It wouldn't boot from livecd properly, etc.

Anyway, it turned out to be a bios setting re/ agp aperture and S.M.A.R.T settings.
After resetting the bios it booted into windows,ubuntu and livecd (as it should)

But yes, drivers are usually the source of problems.
You could try the nouveau drivers and suss out the difference. (best to remove all nvidia proprietory stuff in synaptic then reboot (poss in failsafe graphics) then install nouveau drivers and any dependencies.
I would backup first.

---

### Post by HappyLinux on 2011-05-28
> **Duncan Williams said:**
> One thing. I had/have dual boot with windows (xp).

I had problems with my ubuntu partition and then lost it as it would not let me past grub. (windows was booting/working fine).
It took me weeks of doing all sorts of things including re-installing, etc.
It wouldn't boot from livecd properly, etc.

Anyway, it turned out to be a bios setting re/ agp aperture and S.M.A.R.T settings.
After resetting the bios it booted into windows,ubuntu and livecd (as it should)

But yes, drivers are usually the source of problems.
You could try the nouveau drivers and suss out the difference. (best to remove all nvidia proprietory stuff in synaptic then reboot (poss in failsafe graphics) then install nouveau drivers and any dependencies.
I would backup first.

I'm not going to even attempt that. If anything goes wrong, it's too much hassle to start form scratch.

---

### Post by HappyLinux on 2011-05-30
Here's something that may make a huge difference in figuring out my problem. My browsers only seem to crash when viewing 1 website. YouTube.

Doesn't matter which browser it is that I'm using, it always crashes after a while when watching clips on YouTube. It may be immediate, may take an hour. Doesn't matter which resolution, annotations on or off, but it crashes far quicker when the clips are viewed fullscreen.

YouTube uses flash, yet when viewing other websites which use a flash-player, then there's no problem.

---

### Post by HappyLinux on 2011-06-15
Oh yes, I completely forgot to mention. I never had this problem with Ubuntu 10.10 64bit. It only started with Kubuntu 11.04 64bit. So I just got rid of Kubuntu for Ubuntu 11.04. However, the crashing still remains. So it's got to be something different between 10.10 and 11.04. Could be flash, could be Ubuntu/Kubuntu.

---

### Post by Duncan Williams on 2011-06-15
delete all existing flash and references.
install latest flash.

All tools (online) are available from adobe.
[http://www.google.com/search?q=flash](http://www.google.com/search?q=flash)

---

### Post by wildmanne39 on 2011-06-16
> **HappyLinux said:**
> Oh yes, I completely forgot to mention. I never had this problem with Ubuntu 10.10 64bit. It only started with Kubuntu 11.04 64bit. So I just got rid of Kubuntu for Ubuntu 11.04. However, the crashing still remains. So it's got to be something different between 10.10 and 11.04. Could be flash, could be Ubuntu/Kubuntu.
Hi, open fire fox, addons, and install flashaid and follow the directions and it fixes most flash problems with chrome too just by using it in fire fox.

---

### Post by HappyLinux on 2011-06-16
I already have the latest flash installed through flashaid. I've been using flashaid for a while now. no such luck in solving the problem.

---

### Post by wildmanne39 on 2011-06-16
> **HappyLinux said:**
> I already have the latest flash installed through flashaid. I've been using flashaid for a while now. no such luck in solving the problem.Hi, ok run this command in a terminal
```
sudo lshw
```
and post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by HappyLinux on 2011-06-22
> **wildmanne39 said:**
> Hi, ok run this command in a terminal
```
sudo lshw
```and post it back here by clicking on new reply and click # and paste the information between the brackets.

OK, I ran that command and copied everything that was showing. However, I think there is some info missing as both of the 2 terminal programs (Terminal and Terminator) would only scroll up so far.

```
          version: Intel(R) Core(TM) i5 CPU 760 @ 2.80GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1156
          size: 1200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR Synchronous 1333 MHz (0.8 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:f4000000-f7efffff ioport:e4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF106 [GeForce 450 GTS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f4000000-f4ffffff memory:e8000000-efffffff memory:e4000000-e5ffffff ioport:dc00(size=128) memory:f7e00000-f7e7ffff
           *-multimedia
                description: Audio device
                product: GF106 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:17 memory:f7efc000-f7efffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f3ffe000-f3ffe3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:f3ff8000-f3ffbfff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:e0400000-e05fffff ioport:e0600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:e0800000-e09fffff ioport:e0a00000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:f7f00000-f7ffffff ioport:f2f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: bc:ae:c5:96:5e:1b
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:45 ioport:e800(size=256) memory:f2fff000-f2ffffff memory:f2ff8000-f2ffbfff memory:f7ff0000-f7ffffff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f3ffd000-f3ffd3ff
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16) ioport:b080(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1AJ1
                serial: S246J90ZA41541
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=4828d2b9
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c67e0070-2894-2644-8a69-711d0f274944
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-12-14 23:15:30 filesystem=ntfs label=Win_RE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: e6bc-d5b3
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-01-17 22:13:15 filesystem=ntfs label=System Reserved state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: ec21f87a-8903-e842-91a1-e8ee5e105570
                   size: 458GiB
                   capacity: 458GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-01-17 22:14:37 filesystem=ntfs state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 460GiB
                   capacity: 460GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 456GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3998MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW SH-S223C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SB05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f3ffc000-f3ffc0ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:21 ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16) ioport:c080(size=16)
     *-scsi:0
          physical id: 1
          bus info: usb@2:1.1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Ext HDD 1021
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 2002
             serial: WCAV5J518113
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=002346b8
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Elements - 01
                version: 3.1
                serial: 0cf98b62-3de5-d04f-9545-d9cb7511a154
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-07-10 05:38:03 filesystem=ntfs label=Elements - 01 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@2:1.2
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Ext HDD 1021
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
             version: 2002
             serial: WCAV5J591765
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=002c884c
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Elements - 02
                version: 3.1
                serial: 10666135-fd7f-934a-9e2a-f85e360d56d5
                size: 931GiB
                capacity: 931GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-07-10 06:16:20 filesystem=ntfs label=Elements - 02 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
simon@simon-linux:~$ 

```

---

### Post by fermin on 2011-12-20
Hey, did you solve this? I'm having the same problem with an old Pentium 4 machine w/o hardware acceleration (though it does have an old video card). It happened before when it had Ubuntu 11.04 and is still happening after a fresh install of 11.10 32 bit. If you have any information on what could be the problem (I am also thinking it might be hardware related since I have other computers with ubuntu in the same local network and they work just fine).

---

### Post by HappyLinux on 2012-01-05
Sadly, I did not manage to solve it. After going through a few different Ubuntu distros. That's Ubuntu, Kubuntu, Xubuntu etc, I decided to stuff it and switched to LinuxMint. I'm currently running Mint 12 64bit. Apart from Google Chrome, I used the standard repositories. Not only that, I used the Flash plugin that Mint came with, and I've avoided installing add-ons like AdBlock. Since then, I've had zero browser problems. Apart from Chrome crashing now and then.

---

