---
title: "64bit os running slow"
date: 2010-01-19
forum: General Help
---

### Post by Kai69 on 2010-01-19
Hi all Ive just installed ubuntu 9.10 64bit os from 32bit on 32bit i had no problems with it running quite fast.
Since 64bit has gone on everything i do is running slower update manager took 2 hours to download 202 updates in 32bit that would have taken less than 2 minutes i net is Virgin media 54 Mbs so i can count that out always super fast on 32bit.
Dell xps m1330 2007model
Intel core 2 duo T7500 2.20 ghz
4 gb ram
320gb HDD 

There is also a lag when opening files and folders and loading programs even in software centre  surely it should be quicker than this . Everything works skype youtube ( vids work but cant pause or adjust vol on player) . Other than that im still loving ubuntu .

---

### Post by warfacegod on 2010-01-19
First thing I would do is open a Terminal and do:

```
top
```

It's stripped down system monitor. Then resize the terminal into a corner of the screen. (It might help to make the Terminal background transparent in Profile Preferences.) Then go about your usual business keeping an eye on top to see what seems to be using allot of hardware. Then post back here with that info.

---

### Post by Kai69 on 2010-01-19
[ATTACH]144193[/ATTACH]        Is this ok.

---

### Post by Mike'sHardLinux on 2010-01-19
Hi.

I assume you are running 64 bit Karmic. Were you running 32 bit Karmic before? I ask because the default file-system has changed since previous version.

---

### Post by Kai69 on 2010-01-19
Yes as far as i know i used the disk from ubuntu user magazine one side had 32bit other side had 64bit.
Install went ok i dont use another os on this laptop so used entire HDD. i just coudnt understand why its running a lot slower than 32bit even doing basic stuff. I dont do to many intensive things on pc maybe watch a vid on i net and msm at the same time .

---

### Post by warfacegod on 2010-01-19
> **Kai69 said:**
> [ATTACH]144193[/ATTACH]        Is this ok.

Yes. That's fine. Did you see anything spiking as you were using your computer?

---

### Post by Mike'sHardLinux on 2010-01-19
Your Top output looks mostly normal to me. I do see you have 1 zombie process. But, CPU usage isn't spiked, and you have plenty of free memory. Not using any swap.

Was your computer running slowly at the time you took that snapshot?

---

### Post by Kai69 on 2010-01-19
No i used system monitor yesterday looking at prosseses as i was doing things but didnt see anything unusual. on this screenshot i was uploading my music folder to rytumbox.

---

### Post by Kai69 on 2010-01-19
Found zombie??  [ATTACH]144196[/ATTACH]

---

### Post by warfacegod on 2010-01-19
What's the HP applet on your upper panel? I see things like that in Windows and I think: Resource hog! Destroy! Destroy!

---

### Post by Kai69 on 2010-01-19
LOL just my wireless printer but its not on at the moment .

---

### Post by warfacegod on 2010-01-19
Use a terminal to post:

```
sudo lshw
```

---

### Post by Kai69 on 2010-01-19
Ok got it up but how do i up load.

---

### Post by warfacegod on 2010-01-19
Highlight the text that you want in the terminal then hit: Shift+Ctrl+C



Then, when you are replying, hit the # icon, put the cursor in between the two bracketed code and hit Ctrl+V

---

### Post by Kai69 on 2010-01-19
#    description: Portable Computer
    product: XPS M1330
    vendor: Dell Inc.
    serial: 3KC973J
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-4B00-1043-8039-B3C04F37334A
  *-core
       description: Motherboard
       product: 0PU073
       vendor: Dell Inc.
       physical id: 0
       serial: .3KC973J.CN7016677H02ZH.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A15 (12/26/2008)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 4MiB
             capacity: 4MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-667G1
             vendor: 2C00000000000000
             physical id: 0
             serial: D510D7E2
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-667G1
             vendor: 2C00000000000000
             physical id: 1
             serial: D510D7E7
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:d000(size=4096) memory:f2000000-f6efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8400M GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f5000000-f5ffffff memory:e0000000-efffffff(prefetchable) memory:f2000000-f3ffffff ioport:df00(size=128) memory:f4000000-f401ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f6ffc000-f6ffffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:f1f00000-f1ffffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:09:ce:e9
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:29 memory:f1fff000-f1ffffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:c000(size=4096) memory:f1c00000-f1efffff ioport:f0000000(size=2097152)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 memory:f1b00000-f1bfffff
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:7c:8a:a0
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:30 memory:f1bf0000-f1bfffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f1a00000-f1afffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:f1aff800-f1afffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f1aff400-f1aff4ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=64
                resources: irq:4 memory:f1aff500-f1aff5ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:f1aff600-f1aff6ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:f1aff700-f1aff7ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
           *-cdrom
                description: DVD writer
                product: DVD+-RW UJ-857G
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: Z111
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) ioport:eff0(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WX20A59F0052
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00025801
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 57fb8455-d935-4337-bb00-0f1f2e8b1ada
                   size: 286GiB
                   capacity: 286GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-01-18 21:48:24 filesystem=ext4 lastmountpoint=/h&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;>8&#65533;+&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&#10504;&#65533;&#65533;@u&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&&#65533; modified=2010-01-18 22:21:11 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-01-19 22:52:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 11GiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6ffbf00-f6ffbfff ioport:10c0(size=32)
  *-battery
       product: DELL FW3027A
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh

---

### Post by warfacegod on 2010-01-19
Close enough.

---

### Post by warfacegod on 2010-01-19
Your hardware looks like it should be handling 64 Bit like a Wile E. Coyote rocket sled on a frozen super fluid track. Check your BIOS. Dells often have clock speed settings maybe your CPU is being scaled back?

---

### Post by Kai69 on 2010-01-19
I take it that width 32 or 64 means if its capable of 32/64 bits there seems to be a lot of 32bit items.
Sorry if its a bit of a mess im still trying to get used to linux os and terminal.:)
just read last post you mean ive got a desent rig then

---

### Post by warfacegod on 2010-01-19
> **Kai69 said:**
> I take it that width 32 or 64 means if its capable of 32/64 bits there seems to be a lot of 32bit items.
Sorry if its a bit of a mess im still trying to get used to linux os and terminal.:)

Like I said: close enough.

---

### Post by warfacegod on 2010-01-19
As long as your CPU, Motherboard, RAM, and Video card say width 64, you're fine. (And they do.)

---

### Post by Kai69 on 2010-01-19
Hi again just had a look at the bios srceen everything looks ok on the settings side.
For some reason this pc seems to be running a bit faster since the last hour or so ive rebooted twice since ive been on it now seems on par to 32bit maybe it just needs to get used to 64bit. :D

---

### Post by john newbuntu on 2010-01-19
Since you did an upgrade from 32 to 64bit, I am not sure if that mattered since I am not an upgrade expert.  If you have time on your hands and do not have too much stuff to backup, just delete the Ubuntu partitions and re-install the 64 bit version(Make sure it is the 64 bit one).
I also noticed that you have  4GB RAM and 11GB swap!  You might want to re-adjust the swap and root partitions.
Or you could even carve a portion of the 11GB partition and install the 64 bit there to see for any difference. But that is up to you.

---

### Post by Kai69 on 2010-01-19
Hi John I didnt do a 64bit upgrade I did a full install from disk and used entire disk to 64 ubuntu 9.10 as for swap partition that was setup with the install. I am still trying to get my head around this ive only been using linux os since Nov 09 because Windows xp went nuts on me and i had enough of messing around with somthing that was so insecure and didnt like doing the things i wanted it to do. 
So far ubuntu has done everything better than windows and faster so i wont be going back to that os I also have a desktop pc on vista and brought the kids a lappy for xmas with W7 dont even get me started on w7 ill be sticking to ubuntu from now on LOL:D

---

### Post by warfacegod on 2010-01-19
I didn't catch the 11 GB swap! That needs to be reduced. If you don't have it get Gparted and resize it. If you Suspend or Hibernate then 4 GB + a little bit. If you don't then 1 GB or less.

---

### Post by warfacegod on 2010-01-19
Gparted:

```
sudo apt-get install gparted
```

---

### Post by Kai69 on 2010-01-19
ok gave swap 5.5 gb now have unallocated partion how do i get rid of this to main HDD[ATTACH]144198[/ATTACH]

---

### Post by warfacegod on 2010-01-19
Hate to tell you this but you moved it the wrong way. Do it again and have it go as far to the right as possible. The unallocated space needs to be next to the partition that you what to have it.

---

### Post by Kai69 on 2010-01-19
Tried swapping linux partion but its part of the /dev/sda2 even tried deleting linux swap cant make /dev/sda2 smaller. if i do i just puts 2 unallocated partions there. i think its something that is installed when you install os but can only change with advanced option on install

---

### Post by warfacegod on 2010-01-19
You need to unmount it.

---

### Post by Kai69 on 2010-01-20
Hi warfacegod tried unmounting cannot be done keeps comming up with error message. Ive just switched the pc on and everything seems to be ok speedwise I cant understand this even firefox took less time to load up ???? I think what ill do is keep an eye on this for a few days.
WOW just did an update 13 packages 9 seconds upload 14 seconds install I think this has sorted itself out.:D

---

### Post by warfacegod on 2010-01-20
> **Kai69 said:**
> Hi warfacegod tried unmounting cannot be done keeps comming up with error message. Ive just switched the pc on and everything seems to be ok speedwise I cant understand this even firefox took less time to load up ???? I think what ill do is keep an eye on this for a few days.
WOW just did an update 13 packages 9 seconds upload 14 seconds install I think this has sorted itself out.:D

Perhaps you should think of it like a muscle car. They need a breaking in period. Once that's over they *go!*

---

### Post by warfacegod on 2010-01-20
Are you turning the swap off before trying to unmount and resize?

---

### Post by Kai69 on 2010-01-20
Tried that last night but woudnt let me it seems this HDD has 10 -12gb swap partion even when windows is on it has that as a swap why i dont know would it do any harm having this? I understand what you mean about the car analogy im a car mechanic by trade and seen this sort of thing when replacing ECUs because even if you load all the manufactures settings because of wear in engine it needs to find a happy medium 
What im trying to say is this pc has been 32bit since 2007 now im using 64bit poor thing has probably doing a lot of head scratching. LOL :D

---

### Post by Kai69 on 2010-01-20
[attach]144281[/attach]

[attach]144282[/attach]

---

### Post by JiuJitsu500 on 2010-01-20
I had to butt in because I know the feeling ALL too well..... my thing has been doing the same thing... switched to 64 bit just so I can use all my RAM and my laptop is moving... accelerating slowly.... but the head scratching thing was funny :)

And no, swappiness (the setting and swap partition) won't kill you, but there's no reason to have much, if any, with 4GB of RAM :) plus, you could use that space for random things....

---

### Post by Kai69 on 2010-01-20
I even tried to delete the partion but it just left 11gb empty space i cannot unmount main HDD.
At least im not the only one that has had this slowdown problem but in 48 hours it seems to be sorting itself out ..Im happier now opening video is a lot quicker.:D

---

### Post by warfacegod on 2010-01-20
> **Kai69 said:**
> I even tried to delete the partion but it just left 11gb empty space i cannot unmount main HDD.
At least im not the only one that has had this slowdown problem but in 48 hours it seems to be sorting itself out ..Im happier now opening video is a lot quicker.:D

You can't unmount your main partition. It's what Linux is running off of. Turn swap off, resize that to the right, unmount sda2 resize to the right, apply.

If that doesn't work then delete the sda2 partition entirely. Then create a new partition all the way to the right and format it as linux-swap.

Then use your LiveCD to resize sda1 into the empty space.

Of course, if you're feeling somewhat brave, you could do away with swap entirely and just resize your sda1 into the entire drive, you have enough RAM to do it. If you want try that then turn swap off every time you boot up and after a few days, if you haven't seen any strange behaviors, then it should be safe to do it. 

I've got 2 GB RAM and my laptop almost never uses swap space at all and I'm probably going to do the same thing.

---

### Post by warfacegod on 2010-01-20
> **Kai69 said:**
> I even tried to delete the partion but it just left 11gb empty space i cannot unmount main HDD.
At least im not the only one that has had this slowdown problem but in 48 hours it seems to be sorting itself out ..Im happier now opening video is a lot quicker.:D

Video tends to be more peppy with 64.

---

### Post by Kai69 on 2010-01-20
Thats what i tried to do last night and wouldnt let me make a new linux swap partition just comes up as unmounted partition i was thinking or doing an install again but in the partition sizeing going for advanced setup and giving it about 5gb. Everytime i do an install it allways has this partition in original settup Vista /drivers there is also the mbr for the media centre button in this partition I think the reason it has 11gb is because the HDD is 320gb as you can see from the screenshot of the main Hdd its not full the only thing that isnt on there is 10gb of photos that i left on my ext hdd .

VIDEO ROCKS NOW resolution spot on windows media  player 11 eat your heart out LOL

---

### Post by Kai69 on 2010-01-20
[attach]144304[/attach]

[attach]144305[/attach]

---

### Post by Kai69 on 2010-01-20
[attach]144307[/attach]

[attach]144308[/attach]


First shot is when i move partitions second shot is after i apply ?? this is why ive been having problems even if i delete partition 2 it creates this..

---

### Post by warfacegod on 2010-01-20
> **Kai69 said:**
> [attach]144307[/attach]

[attach]144308[/attach]


First shot is when i move partitions second shot is after i apply ?? this is why ive been having problems even if i delete partition 2 it creates this..

So what's the issue? If it's that 8 MB unallocated space then resize sda2 and uncheck round to cylinders. Otherwise Use your LiveCD to make sda1 bigger.

---

### Post by Kai69 on 2010-01-20
Sorry me not looking i thought it was 8gb ???? ok what do i do after i startup using live cd sorry for sounding so dim but ive never repartitioned harddrives before thats why they call it windozzzzzzz but now im on linux this is all new to me
Thanks for all this help .:popcorn:

---

### Post by Kai69 on 2010-01-20
Its ok i figured it out is this better
[ATTACH]144315[/ATTACH]

---

### Post by warfacegod on 2010-01-20
If you're happy with it then so am I!:D

---

### Post by Kai69 on 2010-01-20
All I can say is THANK YOU for all your help and more. Im going to see how this os goes because its running a lot faster over the last few days..
Anyone reading this thread if 64bit is slow on install give it a few days to settle down and it should speed up as it has done for me .  :popcorn:

---

