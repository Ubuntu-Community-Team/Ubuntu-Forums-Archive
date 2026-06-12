---
title: "Hard drive thrashing locking system"
date: 2009-09-05
forum: General Help
---

### Post by IainPurdie on 2009-09-05
I've had this problem for some time, but on a laptop I put to one side a couple of months ago. I'm not back trying to use it and this issue is making it very hard to rely on. It's so bad I'm even using XP on it instead of Ubuntu... *shame*

I cannot figure out what's caused it. It must be something that's been updated or installed. It is also very hard to test for, but I'll detail the symptoms:

After the laptop has been running Ubuntu for some time (usually many hours) the hard drive starts to get busy for no reason *very* quickly. Within thirty seconds, the PC is essentially locked. The mouse doesn't respond and clicking the button can take two minutes upwards to respond. Not that it'll do anything when it does.

It doesn't do it a precise time after bootup, neither does it do it at a certain hour of the day. As such I don't *think* it's a scheduled task that's causing the issue.

I have had it happen when the machine's running day-to-day software (e.g. Firefox) and also when it's not running anything other than background tasks - I've left it just "on" overnight and woken in the morning to find the hard drive going mad and a reboot required.

Yes, I've tried disabling background tasks but as I said, it takes *hours* before the problem manifests to it's very hard ti pinpoint one.

By the time the problem occurs, it's impossible to fire up a command to see what's using the HDD as the system is too slow. Having said that, I'm not 100% sure what I could use to diagnose it.

Does anyone know a way I could retrospectively find out after a reboot, perhaps in a log? I did check the logs before (weeks and weeks ago) but couldn't spot anything. If someone would be kind enough to pinpoint a couple of logs that may be useful I would be happy to post the tails of them on here for perusal. I'm by no means an expert but I couldn't see anything in particular, though logs tend to just list some processes not all of them and don't focus on HDD activity.

I would really appreciate the help on this one as otherwise it's making the machine next to useless in Ubuntu - I daren't work on documents as I risk losing any work due to the speed that it collapses at.

It's an Acer 2410 TravelMate running Ubuntu 9.04 Desktop with all the recent updates and patches. More comprehensive details available on request (or if there's a diagnostic program I could run and post details from, let me know).

Thanks!

---

### Post by aarons6 on 2009-09-06
one of the things i can suggest is checking dmesg and seeing if it saying anything..
i had this kind of happen to me exactly the way you are saying it, found out it was an external drive having some i/o errors due to bad sectors.. if left plugged in it would semi crash the whole system until i unplugged it..

perhaps your drive is going bad.

---

### Post by ckonestroh on 2009-09-06
If this laptop is crashing in XP and Ubuntu its the drive going dead....

or

You have a bad power adapter....??? make sure there is no burn marks around the port which connects the power adapter to the laptop and there are no cuts or nicks in your power connection....


My Money is on the hard drive taking a dive....

---

### Post by IainPurdie on 2009-09-06
Guys, XP runs fine and for days on end (which is unlike XP on any system, frankly) so it's not the hard drive - unless the bad sectors are in the area used only by Ubuntu. I've got an XP partition, an Ubuntu partition and a very large shared data one.#

Is there a hard drive scanning / checking utility I can run under Ubuntu? I'll go have a look for one and see if that's an issue.

Definitely not an external drive as I've had the system go mental when I've not had one connected. And the power supply seems fine - again, there are no issues under XP.

---

### Post by IainPurdie on 2009-09-11
I've used smartmontools and smartctl to check the Ubuntu partitions - no errors at all. So perhaps it's not the HDD at fault? Any other suggestions? Anyone?

---

### Post by oldos2er on 2009-09-11
What are the hardware specs?

---

### Post by IainPurdie on 2009-09-11
Hey Ann - courtesy of the lshw command:

description: Notebook
    product: TravelMate 2410
    vendor: Acer
    version: 0100
    serial: LXTAC0602753409962KS00
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=normal chassis=notebook uuid=E66F7FA0-15B1-11DA-8A3D-B426D31A25E6
  *-core
       description: Motherboard
       product: Morar
       vendor: Acer
       physical id: 0
       version: Rev
       serial: LXTAC0602753409962KS00
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.13 (06/02/2006)
          size: 104KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1280MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: M2
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network:0
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 5
                bus info: pci@0000:06:05.0
                logical name: wlan0
                version: 02
                serial: 00:14:a4:2d:0b:e4
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,12/22/2004, 3.100. ip=192.168.1.100 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:0a:e4:e4:bc:ca
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 9
                bus info: pci@0000:06:09.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: WDC WD1600BEVE-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXE109PV2351
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=259652d8
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 3007-17f2
                   size: 3004MiB
                   capacity: 3004MiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat label=PQSERVICE
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/ACER
                   version: FAT32
                   serial: 1569-13d7
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=ACER mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,gid=100,fmask=0000,dmask=0000,allow_utime=0022,codepage=cp437,iocharset=iso8859-1 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 119GiB
                   capacity: 119GiB
                   capabilities: primary extended partitioned partitioned:extended
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4244N
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

---

