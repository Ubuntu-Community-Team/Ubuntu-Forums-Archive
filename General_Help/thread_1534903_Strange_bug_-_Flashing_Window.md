---
title: "Strange bug - Flashing Window"
date: 2010-07-20
forum: General Help
---

### Post by RabbitWho on 2010-07-20
Hi! 



So I recently did a clean install of Lucid 64bit and there are a few minor problems, 
**1. Flashing window (more later)**
2. Failure to mount anything on Ubuntu whatsoever at random times "Authorization denied" 
all permissions ticked in users and groups
*Both of these solved when I reboot, sometimes I have to do it a few times. *
3. Graphics glitches when i minimize or maximize windows. 


- So the flashing window comes up sometimes when I start up, it's just an "untitled window", small, top right, black inside. 
It doesn't seem to be one window flashing on and off, it's one window/program opening and closing and opening and closing, so if i manage to xkill it it just comes back.. and goes away.. and comes back.. and goes away
It makes it impossible to do anything because everything flashes between active and inactive, so if for example you're typing you're missing out letters when your window goes inactive and no matter how fast I click I can't seem to close it. 

Anyone have this problem and manage to solve it or know what it could be? 

Thanks.

---

### Post by J V on 2010-07-20
1: Flashing window - can you try running xkill and clicking it (To kill it) then checking processes with "ps aux" to find out what you just shut down so we can stop it running every startup?
2: Go to users and groups and give yourself permission to "Administer the system" or "Access external storage devices"
3: What kind of graphical glitches, could just be the "Minimize effect" What graphics chipset do you have?

---

### Post by RabbitWho on 2010-07-20
> **J V said:**
> 1: Flashing window - can you try running xkill and clicking it (To kill it) then checking processes with "ps aux" to find out what you just shut down so we can stop it running every startup? 


Cool, I looked in the system processes list and I couldn't figure out what it was.

It doesn't start every start up, just every now and then. 
I'll try this next time it does and get back here. 
> 
2: Go to users and groups and give yourself permission to "Administer the system" or "Access external storage devices"

See the thing is, why do i have permission sometimes and not others? 
Anyway when I go to users and groups and hit "advanced settings" nothing happens. "Add" does nothing either. 
> 
3: What kind of graphical glitches, could just be the "Minimize effect" What graphics chipset do you have?

It's kind of a white bar with blue or red hairs on it, sometimes it's the whole screen. 
It doesn't only happen when I minimize and it doesn't always happen so I can't make it happen and try and do a screen shot. I had the same problem before with KDE and XFCE but never with GNOME or LXDE and i've it with both of them now.. so I guess it was never a desktop environment issue as I thought it was. 

Graphics  is Intel Intergrated GMA 4500MHD[FONT=arial][SIZE=1]

[/SIZE][/FONT]

---

### Post by J V on 2010-07-20
1: run "ps aux" "xkill" and kill the window, then another "ps aux" and cross reference to find the differences (Wait till the system is fully up before you do this to make the job easier)

2: So it's asking you for your password sometimes? That's normal - it needs admin permission to mount a drive - the time it's not asking for your password you already input it less than 15 minutes ago (Probably gksudo)

3: No idea, guess you'll just have to get a screenie some times, are you using propreitary drivers?

---

### Post by RabbitWho on 2010-07-21
1. Happened again, couldn't kill the window. Very hard to click on it and when i managed it I got a funny message. I couldn't get a screenshot either because it's flashing so quickly, I tried a load of times. 

Look at that! My processor's never that overloaded! 


Recognize anything funny in the process list? 

It's Lubuntu, but the problem is the same in all the environments.. my background didn't even load.. possibly a related problem!? So many problems! 

2. No it's not asking for a password. If it was then I would give it a password. It's just doing what I said it was doing, nothing else.  I know what's normal and what isn't! :P ;)
As I said it says failure to mount drive. The only thing that fixes it is restarting, sometimes I need to restart a few times, and then it works. 

3. Impossible to get a screen-shot of something that lasts for a split second and happens at random.

Drivers! Interesting! I didn't install any drivers yet. I didn't need to with Jaunty, everything worked immediately after instillation. 


```

rabbit@penguincounter:~$ sudo lshw
[sudo] password for rabbit: 
penguincounter            
    description: Portable Computer
    product: Inspiron 1545
    vendor: Dell Inc.
    serial: 22H1XJ1
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-3200-1048-8031-B2C04F584A31
  *-core
       description: Motherboard
       product: 0G848F
       vendor: Dell Inc.
       physical id: 0
       serial: .22H1XJ1.CN7016698E0BFE.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A07 (05/13/2009)
          size: 64KiB
          capacity: 15MiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 1200MHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: NT2GT64U8HD0BN-AD
             vendor: 7F7F7F0B00000000
             physical id: 0
             serial: C010215A
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: NT2GT64U8HD0BN-AD
             vendor: 7F7F7F0B00000000
             physical id: 1
             serial: 9512215A
             slot: DIMM_B
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
             resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
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
             resources: memory:f6b00000-f6bfffff
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
             resources: irq:20 ioport:6f60(size=32)
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
             resources: irq:21 ioport:6f80(size=32)
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
             resources: irq:22 ioport:6fa0(size=32)
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
             resources: irq:22 memory:fed1c400-fed1c7ff
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
             resources: irq:21 memory:f6afc000-f6afffff
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
             resources: irq:24 ioport:2000(size=4096) memory:f0200000-f03fffff memory:f0400000-f05fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f6900000-f69fffff memory:f0600000-f07fffff(prefetchable)
           *-network
                description: Network controller
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f69fc000-f69fffff
        *-pci:2
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
             resources: irq:26 ioport:d000(size=4096) memory:f6800000-f68fffff memory:f0800000-f09fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 13
                serial: 00:25:64:4d:59:17
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
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
             configuration: driver=pcieport
             resources: irq:27 ioport:c000(size=4096) memory:f6600000-f67fffff ioport:f0000000(size=2097152)
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
             resources: irq:20 ioport:6f00(size=32)
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
             resources: irq:21 ioport:6f20(size=32)
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
             resources: irq:22 ioport:6f40(size=32)
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
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:4
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
             resources: irq:29 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=32) memory:fed1c800-fed1cfff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WX70A7961296
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9b17c2d1
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 7ea99be5-f352-4846-879c-013f752c900e
                   size: 28GiB
                   capacity: 28GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-07-18 23:19:44 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 270GiB
                   capacity: 270GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 259GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SD05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
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
             resources: memory:f6afbf00-f6afbfff ioport:1100(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:5
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 970MiB (1017MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                version: FAT16
                serial: 0000-0000
                size: 970MiB
                capacity: 970MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
     *-scsi:1
          physical id: 2
          bus info: usb@2:1
          logical name: scsi9
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0
             bus info: scsi@9:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 2.31
             capabilities: removable audio
             configuration: ansiversion=2 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 17KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   vendor: Mac OS X
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000001000
                   size: 23MiB
                   capacity: 23MiB
                   capabilities: hfsplus initialized
                   configuration: checked=1903-12-31 23:34:39 created=2008-06-16 12:26:37 filesystem=hfsplus lastmountedby=10.0 modified=2008-06-16 13:26:37 state=clean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@10:0.0.0
             logical name: /dev/sdc
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:54:55:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by RabbitWho on 2010-07-21
bump!

---

### Post by RabbitWho on 2010-07-22
bump

---

### Post by RabbitWho on 2010-07-23
Managed to catch it, but it did no good because it's one thing opening and closing so the process list is the same both times, unless maybe I could catch it the split secnd it's closed. 

I can't paste you the process list ecause the thing s flashing riht nw. (as te post wnt on i got mr and morlazy about fixng te spellings) This isso annoying, t taks like1 0 attempts just to clos o open a window

---

### Post by RabbitWho on 2010-07-23
This really makes the computer unusable at times. Plus the wireless doesn't work which means i'll have no Internet after September if I don't do something now. 

Is there a way to "down"grade back to jaunty without doing a clean install?

---

### Post by RabbitWho on 2010-07-23
Bump

---

### Post by RabbitWho on 2010-07-23
Bump!

---

### Post by RabbitWho on 2010-07-23
[IMG]http://www.innocentenglish.com/funny-pics/lolcats/cute-cat-sinking-sofa.jpg[/IMG]

---

### Post by RabbitWho on 2010-07-24
[IMG]http://www.innocentenglish.com/funny-pics/lolcats/kitty-help-fix-computer.jpg[/IMG]

I'm just going to post lolcats to comfort myself.

---

### Post by RabbitWho on 2010-07-25
[IMG]http://icanhascheezburger.files.wordpress.com/2008/08/funny-pictures-cat-does-not-know-how-to-help-his-friend.jpg[/IMG]

---

### Post by RabbitWho on 2010-07-26
I had to restart 3 times this morning, the window kept coming back. bump

---

### Post by RabbitWho on 2010-07-27
about the authorization denied bug, when I'm in users and groups and i hit "manage groups" or "advanced settings" nothing happens. 

Solution?

---

### Post by RabbitWho on 2010-07-28
So I managed to fix that with the command "sudo users-admin" which allowed me to tick all the boxes. But I still can't mount anything most of the time on Ubuntu, so it's not a permissions thing. 

No problems  with that on lubuntu though.. no recycle bin has already led to a few accidents.

---

### Post by RabbitWho on 2010-07-29
Wa wa wa wa wa.

---

### Post by RabbitWho on 2010-07-29
I need help with leaving lucid now: 

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=1541597](http://ubuntuforums.org/showthread.php?mode=hybrid&t=1541597)

---

### Post by Nox_Ignatius on 2011-01-06
Re: Flashing window

I had this same bug. It has something to do with lxdm, because I just switched to gdm and it is gone.

sudo dpkg-reconfigure gdm

Hit Enter on the first screen and then select gdm. Reboot and you'll be fine. :D

---

