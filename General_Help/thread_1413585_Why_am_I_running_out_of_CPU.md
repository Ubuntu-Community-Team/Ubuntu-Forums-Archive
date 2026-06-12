---
title: "Why am I running out of CPU?"
date: 2010-02-22
forum: General Help
---

### Post by chiaboy on 2010-02-22
I did a lot of work on my computer (mostly related to media sharing/Mediatomb and related firewall issues/Firestarter) and since then the computer hangs and runs out of CPU. 
 
I've manually stopped one of the applications that seems to be a CPU hog but the rest are root/Xorg and when you manually kill them the entire system shuts down. 
 
I'm not sure what I changed and why it's impacting the CPU bleed so much. Anyone know if a good fix or a way to clean up? (e.g. something like Ubuntu tweak or someo other utitlity to fix whatever it screwed)

currently I'm doing a virus scan (meh, something to try) and the CPU history in the system monitor is fluctuating between 70-100%. Obviously the scan is running slow and taking forever. The top CPU users are the Avast virus scan, then ksysgaurd (which seems to always be at or near the top of CPU hogs since this problem started) and Xorg, username Root, also always at or near the top. When I kill the Xorg the system shuts down).

Have deleted Firefox. Same problem occurs when using Chrome. Just randomly trying to make changes to computer in hope that something works. Considering throwing out window to see if that does anything helpful

---

### Post by Jive Turkey on 2010-02-22
The virus scanner will only find windows viruses.  These are not likely the culprit.  Can you share with us what procs are hogging your cpu?

---

### Post by Sir Jasper on 2010-02-22
Hi,

I use Wine and so I also use Avast which is heavy on CPU, but as I only test my Home directory (or  just my Wine folders) once a week or so and it is quick and I do not find the CPU usage a problem.

Gnome-System-Monitor always seems heavy on CPU whereas the alternatives of ¨top¨ or ¨htop¨ use hardly any.

See the picture below:

[[img]http://i.imagehost.org/t/0482/Monitor.jpg[/img]](http://i.imagehost.org/view/0482/Monitor)

My regards

---

### Post by oldos2er on 2010-02-22
Which version of Ubuntu are you running? What are your system specs?

---

### Post by chiaboy on 2010-03-01
the only application that constantly runs through this problem is xorg. Generally Firefox is at or near the top followed by xorg. I've seen a lot of stuff on google about firefox and xorg having this problem so I deleted firefox and only run google chrome.

same problem. Google chrome at or near the top of applications taking memory/CPU with Xorg at or near the top.

my computer is almost unusable.

I have no idea about my specs, how would I find that?

---

### Post by natravis on 2010-03-01
> **chiaboy said:**
> the only application that constantly runs through this problem is xorg. Generally Firefox is at or near the top followed by xorg. I've seen a lot of stuff on google about firefox and xorg having this problem so I deleted firefox and only run google chrome.

same problem. Google chrome at or near the top of applications taking memory/CPU with Xorg at or near the top.

my computer is almost unusable.

I have no idea about my specs, how would I find that?

Use the following command line entries and wrap the output with the code tags to make them format nicely (its the number sign when you are posting a response to the right of where you would input a link or picture).

OS info
```
uname -a
```
System Info
```
sudo lshw
```
Uptime
```
uptime
```

---

### Post by switch10 on 2010-03-01
> **chiaboy said:**
> the only application that constantly runs through this problem is xorg. Generally Firefox is at or near the top followed by xorg. I've seen a lot of stuff on google about firefox and xorg having this problem so I deleted firefox and only run google chrome.

same problem. Google chrome at or near the top of applications taking memory/CPU with Xorg at or near the top.

my computer is almost unusable.

I have no idea about my specs, how would I find that?

if you have compiz running I would disable that...

---

### Post by chiaboy on 2010-03-01
~$ uptime
 14:11:09 up 41 min,  2 users,  load average: 4.47, 3.78, 3.37

Uname-a
Linux james-laptop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

the system info and Ishw commands didn't work for me.



(Just so you know, this response took about 15 minutes to click, load, write, and submit. As you can imagine, not very fun)

---

### Post by oldos2er on 2010-03-01
Please copy and paste **sudo lshw** in a terminal, then copy and paste the output here.

---

### Post by chiaboy on 2010-03-01
```
description: Notebook
    product: HP Compaq nc6320 (RH791UC#ABA)
    vendor: Hewlett-Packard
    version: F.08
    serial: CNU6380L09
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=0CA35262-9881-DB11-14A0-6D990C302529
  *-core
       description: Motherboard
       product: 30AA
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 58.11
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68YDU Ver. F.08 (07/27/2006)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U10
          size: 1667MHz
          capacity: 1667MHz
          width: 32 bits
          clock: 166MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: NT1GT64U8HA0BN-3C
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: 8835340F
             slot: DIMM #1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: NT1GT64U8HA0BN-3C
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: 08610C10
             slot: DIMM #2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8400000-e847ffff ioport:6000(size=8) memory:d0000000-dfffffff(prefetchable) memory:e8480000-e84bffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:e8500000-e857ffff
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
             resources: irq:21 memory:e8580000-e8583fff
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
             resources: irq:24 memory:e8000000-e80fffff
           *-network
                description: Wireless interface
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 01
                serial: 00:14:a5:f7:3a:47
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.71 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:e8000000-e8003fff
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:4000(size=8192) memory:e4000000-e7ffffff
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:2000(size=8192) memory:e0000000-e3ffffff
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
             resources: irq:20 ioport:6020(size=32)
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
             resources: irq:21 ioport:6040(size=32)
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
             resources: irq:18 ioport:6060(size=32)
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
             resources: irq:19 ioport:6080(size=32)
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
             resources: irq:20 memory:e8584000-e85843ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:7000(size=4096) memory:e8100000-e83fffff memory:80000000-83ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:e8100000-e8100fff ioport:7000(size=256) ioport:7400(size=256) memory:80000000-83ffffff(prefetchable) memory:84000000-87ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:02:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:e8101000-e81017ff memory:e8104000-e8107fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:19 memory:e8108000-e8108fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:22 memory:e8109000-e81090ff
           *-communication UNCLAIMED
                description: Communication controller
                product: PCIxx12 GemCore based SmartCard controller
                vendor: Texas Instruments
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:e810a000-e810afff memory:e810b000-e810bfff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5788 Gigabit Ethernet
                vendor: Broadcom Corporation
                physical id: e
                bus info: pci@0000:02:0e.0
                logical name: eth0
                version: 03
                serial: 00:17:08:37:3b:01
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5788-v3.26 ip=192.168.1.73 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
                resources: irq:16 memory:e8110000-e811ffff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:60a0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4084N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KQ09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:60d0(size=16) memory:e8585000-e85853ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2080B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 892C
                serial: NW9ZT682H39N
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000a8edc
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: cd0ec75b-118a-4025-bfe8-4b3057c0cdc9
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-07-23 07:59:45 filesystem=ext3 modified=2010-03-01 14:23:24 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-03-01 14:26:39 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3153MiB
                   capacity: 3153MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3153MiB
                      capabilities: nofs
```

---

### Post by natravis on 2010-03-01
1.66GHz dual core, 2x1GB RAM, integrated graphics

Should be capable of running Ubuntu without too much fuss. Latest kernel and your uptime is less than a day so its probably not related to that. Close gnome-system-monitor and when your system is getting pretty bogged down, open a terminal, run top, and take a screenshot. I agree that you may want to have any desktop effects disabled, as that may be the culprit or it may be completely unrelated.

---

### Post by chiaboy on 2010-03-02
so this is what happened shortly before it totally shut down (i.e. got to 100% CPU and I had to reboot) the problem started and the terminal showed this at "top"



(this message took about 15 minutes to write and make teh attachments. Had to use attachments instead of embedding because I was only able to move curosr to attachment button. sorry)

---

### Post by J V on 2010-03-02
Are you running avast *in* wine? That could cause a very significant slowdown...

The top commands show normal cpu usage... are you using ATI?

---

### Post by chiaboy on 2010-03-02
I don't actively use Wine for anything (I'm not sure what it's for) it's installed on my computer though.

It's been installed on my computer for past six months though and it's only been the last few weeks I've had this problem.

the screen grabs come as I was approaching max CPU usage. Here's the conundrum, when it maxs out I can't do anything. I can't make a screen grab, I can't open an application, I can't click a button. So getting a screen grab when it maxes out is impossible as far as I know.

What I can do is some basic operations in the occassional dips that occur. You can the process on the graphical representation on the system monitor. IT will be maxed out 98-100% cpu for X minutes, and then it will crater and go down to "normal" for a few seconds. That is the only time I can use my computer.

---

### Post by chiaboy on 2010-03-02
I just tried again and it's like trying to take a picture of the moment your camera doesn't work.

I had top running and CPU spiked up from 70%-100% and bounced around I hit the screen capture button and nothing happens, nothing happens, the CPU is bouncing all over the place, nothing happens, and then finally the screen capture dialouge box pops up ONLY when CPU drops down to a reasonable %.

but watching that process it doesn't look like the applications change that much. It's mostly Xorg, whatever browser, and the other junk, bouncing around for what's on top, so I'd hope there'd be some information there. 

But I literally can't take a picture of maxed CPU because that moment I can't do anything.

---

### Post by philinux on 2010-03-02
> **chiaboy said:**
> I just tried again and it's like trying to take a picture of the moment your camera doesn't work.

I had top running and CPU spiked up from 70%-100% and bounced around I hit the screen capture button and nothing happens, nothing happens, the CPU is bouncing all over the place, nothing happens, and then finally the screen capture dialouge box pops up ONLY when CPU drops down to a reasonable %.

but watching that process it doesn't look like the applications change that much. It's mostly Xorg, whatever browser, and the other junk, bouncing around for what's on top, so I'd hope there'd be some information there. 

But I literally can't take a picture of maxed CPU because that moment I can't do anything.

Are you running any apps at all at this point.

---

### Post by chiaboy on 2010-03-02
no apps (with the exception of a web browser)

I THINK I can turn on the computer and not touch a single thing and I MIGHT not run out of CPU. but whatever I try to do (i.e. even if I don't open a web broswer) it will run out of CPU at some point in the near future. 

as I said before I am ready to toss laptop out the window to see if smashing it on the ground below will fix my problems.

---

### Post by no2498 on 2010-03-02
try this open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to ( x window system (no xv)

that help me on a dell with 910 on it
did this just start 2 days ago

---

### Post by chiaboy on 2010-03-03
someone asked for me to take a screen shot when my cpu was maxed, here's a representation of why it's so hard. This is a graphical overview of the CPU issue (the top bar) and I'm mostly maxed out. I can only operate my computer in the rare, brief drops in CPU utulization. The ones' that look like stalagmites. (Or is it stalactites?)

I pressed the command shortly after the second dip, nothing occurred until the third dip (the far right of the screen) much later, and that's the point at which I can actually "use" the computer again.  The analogy I used is it's like trying to take a picture of the moment when your camera can't work.

As I've said before, in terms of the top running applications the only constant seems to be Xorg. (running as Root)

---

### Post by chiaboy on 2010-03-03
sorry for the repost, I can't get this problem solved and it's made the laptop almost unusable. I constantly run out of CPU and my computer doesn't work 90% of the time.

I did a lot of work on my computer (mostly related to media sharing/Mediatomb and related firewall issues/Firestarter) and since then the computer hangs and runs out of CPU. 
 
I've manually stopped one of the applications that seems to be a CPU hog but the rest are root/Xorg and when you manually kill them the entire system shuts down. 
 
I'm not sure what I changed and why it's impacting the CPU bleed so much. Anyone know if a good fix or a way to clean up? (e.g. something like Ubuntu tweak or someo other utitlity to fix whatever it screwed)

currently I'm doing a virus scan (meh, something to try) and the CPU history in the system monitor is fluctuating between 70-100%. Obviously the scan is running slow and taking forever. The top CPU users are the Avast virus scan, then ksysgaurd (which seems to always be at or near the top of CPU hogs since this problem started) and Xorg, username Root, also always at or near the top. When I kill the Xorg the system shuts down).

Have deleted Firefox. Same problem occurs when using Chrome. Just randomly trying to make changes to computer in hope that something works. Considering throwing out window to see if that does anything helpful

I've tried every suggestion in this thread. (my specs are in there, and the consensous seems to be that my hardware/software/kernel/ etc is all OK)

at wit's end:  [http://ubuntuforums.org/showthread.php?t=1413585](http://ubuntuforums.org/showthread.php?t=1413585)

---

### Post by QIII on 2010-03-03
Something that often does not show up in top, but can tap your CPU and memory, is vino -- remote desktop sharing.

By default, it is not activated.  But you never know.  Did you activated it?

To be sure, (I am doing this by memory, since I am not at my Ubuntu machine at the moment), go to System | Preferences | Remote Desktop and make sure you don't have it running.

It is not terribly likely that you have it running, but you would be amazed at the number of times I have asked this and found it to be the problem.


(Mnemonic:  Think of clothes and bugs, "Tights go down, mites come up.")

---

### Post by chiaboy on 2010-03-03
no remote desktop sharing is not activated. I just double checked against but it's not.

Also, the weird thing is it's not slow, it's essentially broken. It's constantly at 95%+ cpu utilitzation. Even if it was some sort of application that was a resource hog whatever happens seem excessive.

---

### Post by QIII on 2010-03-03
Please have a look at my post at the end of your previous thread.

Something to try, but can't say it'll help.

---

### Post by QIII on 2010-03-03
Hmmmm...

There were some issues with Jaunty and uxa on Intel GPUs like the one you have, but I thought that was cleared up in Karmic.

I scanned through the thread, but I may have missed it.  Are you using a proprietary video driver?

(Edit:  As far as I know, you shouldn't need one for an Intel GPU, but I could be mistaken...)

---

### Post by QIII on 2010-03-03
> **chiaboy said:**
> I did a lot of work on my computer (mostly related to media sharing/Mediatomb and related firewall issues/Firestarter) and since then the computer hangs and runs out of CPU.

OK.  On further consideration...

Was everything working swimmingly before you did this work?  (I'm asking an obvious question, which you answered in your original post, for a reason...)

---

### Post by cariboo on 2010-03-03
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by chiaboy on 2010-04-02
yes, everything was running just fine before I did all that work

---

### Post by oldos2er on 2010-04-02
Have you run memtest? Or checked your partitions with fsck?

---

### Post by chiaboy on 2010-04-02
no I haven't. How do I do that?

---

### Post by Zukero on 2010-04-02
As everything was running fine before you did your work with mediatomb and firestarter, try to remove them one by one, and see when it is back to normal.

Another possibility would be some device blocking your kernel in I/O wait.
When running top, the third line displays info on where you CPU is used, not in terms of process, but in terms of type of activity : "us" is for userland, that is what applications use; "sy" is for system, that is what the kernel use (or the part of the kernel your applications uses); "id" is for idle, that is the available CPU; "wa" is for IO wait, that what is used when a process is waiting for a disk (or other device) access.

You could run something like "top -b -s 1 5 > ~/top.log" in a terminal, and wait for your system to hog or crash. Then, once you rebooted, read the end of the files (the last few records of top), and try to indentify where your CPU power is going.

Pinpointing the problem is 80% of the solution of performance issues.

---

### Post by oldos2er on 2010-04-03
Run memtest from the grub menu. You might want to let it run overnight, or some time when you don't plan to use the computer for awhile.

 You can have fsck run at next boot with ```
sudo /forcefsck
```

---

### Post by 98cwitr on 2010-04-03
After reading this thread I am still clueless why you are running an antivirus program...

do a pskill on mediatomb and firestarter and see what happens

also can you post a screenshot of system monitor under the processes tab with it sorted by CPU usage?

---

### Post by chiaboy on 2010-04-06
I ran an antivirus (once) out of absolute desperation in the hope that something would be discovered.

I've tried everything and it didn't work so I gave up and reinstalled a fresh install of Ubuntu.

We'll see if this works. Thanks for all the help.

---

### Post by Chromagnum on 2010-04-06
Could it be your CPU Fan is dying? 

About a month ago, my CPU Fan died and I didn't even noticed. Most of the time during that period my cpu running around 20-35% idle condition. When I played 720p video it goes up to 100% and my system just down completely. And my room have air conditioner. Imagine if I didn't have that.

Since I replace CPU Fan with the new one, now, it only running around 1-10% idle condition. And 720p, no problem at all.

You should check it out in Bios, see how low the fan RPM.

---

