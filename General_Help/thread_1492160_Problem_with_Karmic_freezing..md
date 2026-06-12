---
title: "Problem with Karmic freezing."
date: 2010-05-24
forum: General Help
---

### Post by CharlesJWelsh on 2010-05-24
I have Ubuntu Karmic installed and it has been freezing since. I dont have access to another computer or another OS. When it freezes I can move my mouse, but nothing else. I have been doing plenty of research, and I have come up with nothing...

---

### Post by CharlesJWelsh on 2010-05-24
I am willing to do anything if you would kindly explain how to.

---

### Post by SlidingHorn on 2010-05-24
what are your system specs?  what programs do you have installed -- which ones are running?  What processes are running?  There's not much we can do with the information you've provided

---

### Post by SlidingHorn on 2010-05-24
> **CharlesJWelsh said:**
> I am willing to do anything if you would kindly explain how to.

...and please wait before bumping threads.  It's recommended to wait about 24 hours

---

### Post by philinux on 2010-05-24
Thread title changed.

---

### Post by jubilee33 on 2010-05-24
Does your system freeze randomly?  Or is it during some specific process?  In the meantime, you might want to read through [this article]("http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/").  It tells you how to reboot your system gracefully when it freezes.

---

### Post by CharlesJWelsh on 2010-05-24
Okay... First off... I have no idea how to check my specs and its random. And I cannot update or download anything without it freezing...


And i have no idea idea what bumping is so no need to lecture :)

And for safe restarts I use Alt + A + PrtSc + U + B. Thats seems to do the job :]

---

### Post by SlidingHorn on 2010-05-24
With so little information, all I can guess is that your system doesn't meet the requirements, causing it to lock up.

bumping means posting a new reply to bring your thread back to the top of the list.  Wasn't meant to be a lecture, just letting you know :)

---

### Post by CharlesJWelsh on 2010-05-24
How can I get you the proper information?

---

### Post by SlidingHorn on 2010-05-24
if your system can stay functional for a long enough period of time, open your terminal and enter:

```
sudo apt-get install sysinfo
```

then, once it's finished installing:

```
sysinfo
```

From there you'll be able to find out your processor speed, RAM, and a lot of other info

---

### Post by CharlesJWelsh on 2010-05-24
E: Internal Error, Could not perform immediate configuration (2) on mountall



??? :[

---

### Post by dark-triad on 2010-05-24
i had an issue with karmic freezing and locking up also, even if no programs were running and it was idle it would happen, i found it to be an issue with pulseaudio as it froze more frequently when running rhythmbox, skype or anything that used pulseaudio, the only solution i found was to kill and restart pulseaudio regularly to "refresh" it, as long as i kept on top of it wouldnt freeze, not an ideal fix but it worked, i installed lucid and everything is fine now, maybe its the same problem, but apart from that i cant help you mate, sorry

---

### Post by CharlesJWelsh on 2010-05-24
I appreciate that... however i never use my computer for music anymore. no point.
 So its not my audio...

---

### Post by dark-triad on 2010-05-24
ok mate but unless you have removed/uninstalled it, pulseaudio still runs in the background in your processes regardless of whether you are using your computer for audio or not, so it could still be the problem as it locked mine all the time even when not using audio

---

### Post by CharlesJWelsh on 2010-05-24
Well its worth the try... how do i do it?

---

### Post by dark-triad on 2010-05-24
Alt + F2

> killall pulseaudio

this will kill it and it will restart after a few seconds automatically

---

### Post by CharlesJWelsh on 2010-05-24
okay so i did that and it closed... what next? and how many times should i do that?

---

### Post by dark-triad on 2010-05-24
well if it freezes again, try that command and see if it resumes back to normal, if everything goes back to normal then you know pulseaudio is the cause, after i found out that pulseaudio was the cause i just ran that command automatically every hour or so as a cron job to stay on top of it, like i said its not much of a fix and i dont really have much else to offer mate sorry, it might be a different issue to what i had, but as far as finding your system specs so other people can try to help try this command:

```
sudo lshw
``` 

That should pump out alot of system info for you, its pretty long and detailed so just pick the most relevant bits and refer to it if someone needs more info

---

### Post by CharlesJWelsh on 2010-05-24
okay... here are specs...


 description: Notebook
    product: Satellite A15
    vendor: TOSHIBA
    version: PSA10U-28RJRV
    serial: X3048200H
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=EFD85D00-091F-11D8-8010-B85283048200
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: **************
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (09/02/2003)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing vesa cdboot bootselect pcmciaboot edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot
     *-cpu
          description: CPU
          product: Mobile Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: uFC-PGA Socket
          size: 2400MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 8KiB
             capacity: 8KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 256KiB
             capacity: 256KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:10 memory:d8000000-dfffffff(prefetchable) memory:d0000000-d007ffff ioport:eff8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:20000000-27ffffff(prefetchable) memory:2c000000-2c07ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:18c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:2c080000-2c0803ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:cff00000-cfffffff memory:28000000-2bffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:91:56:c2
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
                resources: irq:11 memory:cffff000-cfffffff ioport:cf40(size=64)
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5
                resources: irq:11 memory:cff00000-cff00fff ioport:c000(size=256) ioport:c400(size=256) memory:28000000-2bffffff(prefetchable) memory:30000000-33ffffff
              *-network
                   description: AR5001-0000-0000
                   product: Wireless LAN Reference Card
                   vendor: Atheros Communications, Inc.
                   physical id: 0
                   version: 00
                   slot: Socket 0
                   resources: irq:11
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
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
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:2c080400-2c0807ff
           *-disk
                description: ATA Disk
                product: HITACHI_DK23EA-3
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 00K4
                serial: N22316
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=7da97da9
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 5975f547-4f73-4303-aea7-4263521ae01e
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-26 01:42:45 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;I&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;v&#1920;"&#1884;&#65533;Z&#65533;I^&#65533;P`&#65533;P`&#1920;>&#65533;&#65533;&#65533;&#65533;&#65533;Z&#1656;&#65533;Z&#1637;`&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533;&#65533;k modified=2010-05-24 00:05:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-24 14:48:57 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1223MiB
                   capacity: 1223MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1223MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM SD-R2412
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1330
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:11 ioport:1000(size=256) ioport:1880(size=64) memory:2c080800-2c0809ff memory:2c080a00-2c080aff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: ioport:1400(size=256) ioport:1800(size=128)
     *-network
          description: Wireless interface
          product: AR2413 802.11bg NIC
          vendor: Atheros Communications Inc.
          physical id: 1
          bus info: pci@0000:02:00.0
          logical name: wmaster0
          version: 01
          serial: 00:15:e9:5e:f0:c5
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath5k ip=192.168.0.98 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
          resources: irq:11 memory:30000000-3000ffff

---

### Post by dark-triad on 2010-05-24
ok i guess you didnt see the bottom of my post to pick out the most relevant data from it, i suggest you edit the post to cut it down in size to basic things like the make/model of your computer, motherboard, processor, sound card, graphics card etc there is alot of info to sift through there otherwise, and alot of it is not needed, the basics will do

and please try to be a little more descriptive in your posts with as much info provided as possible in regard to the problem, like when it freezes, is it just the graphics which lock up? or is your processor high or maxing out? does your fan really kick in? How much memory is being used? what processes are using alot of memory/cpu etc, the system monitor is a good place to start for this information, it will all help people in solving your problem, otherwise people are just guessing things off the top of their heads

---

