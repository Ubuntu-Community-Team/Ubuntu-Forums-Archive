---
title: "No Sound in 10.04"
date: 2010-12-23
forum: General Help
---

### Post by MickeyPilgrim on 2010-12-23
Hi All
  Have had a system w/ dual boot of XP and 10.04 for six months. If I need sound, I have to re-boot into XP. 
  I saw this was a huge problem when 10.4 was released, and assumed there would be a solution on Ubuntu Forums that I could figure out and follow - no such luck. I only find discussions of tricky sound cards or headphones.
The sound was fine in 8.04 and 9.04 and XP.
  If you see the problem, please advise me as if you are speaking to a dolt!   
=================================================================
mike@mike-desktop:~$ sudo lshw
[sudo] password for mike: 
mike-desktop              
    description: Desktop Computer
    product: G41M-ES2L
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-6CF049C55790
  *-core
       description: Motherboard
       product: G41M-ES2L
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F9 (06/21/2010)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
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
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2933MHz
          capacity: 2933MHz
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
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:fa000000-fcffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc01ffff(prefetchable)
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fdff8000-fdffbfff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:80400000-807fffff ioport:fde00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 6c:f0:49:c5:57:90
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.33.1.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:27 ioport:de00(size=256) memory:fdeff000-fdefffff(prefetchable) memory:fdef8000-fdefbfff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fe00(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:fdd00000-fddfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: uPD72873 IEEE1394 OHCI 1.1 2-port Host Controller
                vendor: NEC Corporation
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=44 mingnt=20
                resources: irq:19 memory:fddff000-fddfffff
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
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
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
             resources: irq:19 ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: BL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: WDC WD1600AAJS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAP92036485
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=628e628e
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: ca784d7d-dc02-8b43-803d-33eccd3cc42c
                   size: 76GiB
                   capacity: 76GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-09-02 19:23:12 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sda2
                   size: 72GiB
                   capacity: 72GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 69GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3087MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
mike@mike-desktop:~$

---

### Post by gordintoronto on 2010-12-23
You posted a long file which has one useful line:
product: N10/ICH 7 Family High Definition Audio Controller

When you click on the speaker icon and select Sound Preferences, does the Hardware tab show your device? Does the Output tab show that sound is muted?

---

### Post by MickeyPilgrim on 2010-12-24
Hi gordintoronto,
  Thank you for your consideration.
Hardware shows
internal audio
1 output/1input
analog stereo duplex

-Output is not muted

Thanks again

MickeyPilgrim

---

### Post by linden940 on 2010-12-24
if you plug in head phones will it then work?

try to plug your sound cord into another spot if you could.

---

### Post by MickeyPilgrim on 2010-12-24
Nothing on headphones.
When I plug into another spot there is a instance of static that indicates the connection is good, but I knew that because XP plays just fine.

MickeyPilgrim
Grass Valley, CA (Where the sun is out for the first time in a month!)

---

### Post by MickeyPilgrim on 2010-12-24
And the speaker icon>Sound Preferences>Applications shows rythmbox is playing the MP3.

---

### Post by tushar maroo on 2010-12-24
download **alsa mixer.**.....it is a graphical interface to control sound.....may be that will help:KS

---

### Post by MickeyPilgrim on 2010-12-24
So you figure it must be a problem with Rhythm Box?
I'm not sure how to best uninstall Rythmbox if it's defective in my set up. If you could point me in the right direction to do an uninstall correctly, I'd appreciate it.

And I have two questions:
-  Any reason not to try Banshee instead of Alsa? I see it's going to be the next default music player> [http://www.omgubuntu.co.uk/2010/12/breaking-news-banshee-close-to-being-madedefault-music-player-in-natty/](http://www.omgubuntu.co.uk/2010/12/breaking-news-banshee-close-to-being-madedefault-music-player-in-natty/)

-Finally, You seemed to imply that I had put to much info in my original post. I just wanted to avoid what seemed like the inevetable follow up question.   Did I committ a Newbie Blunder?

Mickey Pilgrim

---

### Post by linden940 on 2010-12-24
> **MickeyPilgrim said:**
> So you figure it must be a problem with Rhythm Box?
I'm not sure how to best uninstall Rythmbox if it's defective in my set up. If you could point me in the right direction to do an uninstall correctly, I'd appreciate it.

And I have two questions:
-  Any reason not to try Banshee instead of Alsa? I see it's going to be the next default music player> [http://www.omgubuntu.co.uk/2010/12/breaking-news-banshee-close-to-being-madedefault-music-player-in-natty/](http://www.omgubuntu.co.uk/2010/12/breaking-news-banshee-close-to-being-madedefault-music-player-in-natty/)

-Finally, You seemed to imply that I had put to much info in my original post. I just wanted to avoid what seemed like the inevetable follow up question.   Did I committ a Newbie Blunder?

Mickey Pilgrim

seems like you have all your bases covered...not sure what to think on this one..with your computer are you using the on board sound card or after market card? It could be that the sound card is not supported. But I am running out of ideas.

---

### Post by Syed75 on 2010-12-24
You might need to connect to the right speaker.

system<Preferences<Sound

Then go to output. Check off your settings then. 

It's either this or you need a driver.

---

### Post by MickeyPilgrim on 2010-12-24
There is no soundcard, just what's on the gigabyte motherboard.
I have everything going on the system<Preferences<Sound
 as well as speaker icon>sound preferences etc.

Does anyone know of a forum area where sound issues are handled? It when I search  ubuntu forums under "sound", I see a lot of people with the same fundamental problem. Frankly, 10.04 has been a disappointment but going back to 9.04 would be a major hassle.I have to wonder why sound and scanners are such a problem, and still no alternative to QuickBooks.

OK.  I give up. 10.04 is good for security.
Windows for sound and scanning just works.

---

### Post by lidex on 2010-12-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

