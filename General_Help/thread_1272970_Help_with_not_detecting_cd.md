---
title: "Help with not detecting cd"
date: 2009-09-22
forum: General Help
---

### Post by BAMF1501 on 2009-09-22
Ubuntu will not detect no cdrom or dvd 
[IMG]http://i36.tinypic.com/2n6yrds.jpg[/IMG]

and it worked fine in xp but not with ubuntu

---

### Post by spiderbatdad on 2009-09-22
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2007-02/msg00060.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.hardware/2007-02/msg00060.html)

---

### Post by BAMF1501 on 2009-09-22
i don tknow hwo to do that need more specific instructions

---

### Post by spiderbatdad on 2009-09-22
you might be able to select acpi=off from your boot screen with the f6 (more options) menu, or temporarily edit the kernel line by pressing "e" when the grub menu loads. Then use the arrow key to move to the line beginning with the word kernel, and press "e" again. Then go to the end of the kernel line, add "acpi=off" Hit enter, then "b" to boot.To make this change permanent, edit the file /boot/grub/menu.lst and add acpi=off to the end of the kernel line of your default kernel. See here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by BAMF1501 on 2009-09-22
i tried above does not work :(

---

### Post by BAMF1501 on 2009-09-22
bumpp

---

### Post by mc4man on 2009-09-23
A couple of things
If you want to post a screenshot it's better to attach to your reply, Look under "Additional Options" -> "Manage Attachments"

I see you had trouble getting an install going from a live cd
> (initramfs) unable to find a medium containing a live file system

how did you resolve that?

This may show something, may not...

```
cat /etc/fstab
```

---

### Post by BAMF1501 on 2009-09-23
i had to use the alternative installer cause live cd would not work :*( 

an di did that code you said in terminal and this what i get 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0998e42c-0b3a-4dc9-9aa4-afe682e28a15 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=66cdc2cd-8e2c-445c-98b9-c26f5b855a23 none            swap    sw              0       0
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by BAMF1501 on 2009-09-23
bump

---

### Post by BAMF1501 on 2009-09-23
and i dont know if this information will help or not but on everboot up it boots fine but when loading grub right after saying what hdd it booting into it says this in that time interval 
[1.880026] - ata1 soft reset fail device not ready

---

### Post by BAMF1501 on 2009-09-23
Please somebody help.................

---

### Post by mc4man on 2009-09-24
Run this commands, maybe something will show (your fstab is fine
> (when you post the outputs, highlight the text for each output individually in your reply and click on that little 'quote' button in the reply tool bar, so it looks like this

```
grep CD-ROM /var/log/syslog
```
```
 grep UDMA /var/log/syslog
```

(you could substitute or try dmesg instead of syslog, shouldn't matter.

Put some media in the drive ( anything but a blank cd/dvd or audio cd) and wait a few, then run 
```
sudo lshw -C disk
```

---

### Post by BAMF1501 on 2009-09-27
> **mc4man said:**
> Run this commands, maybe something will show (your fstab is fine


```
grep CD-ROM /var/log/syslog
``````
 grep UDMA /var/log/syslog
```(you could substitute or try dmesg instead of syslog, shouldn't matter.

Put some media in the drive ( anything but a blank cd/dvd or audio cd) and wait a few, then run 
```
sudo lshw -C disk
```


the output for 

 grep UDMA /var/log/syslog



is 

Sep 27 12:43:25 ubuntu kernel: [    1.039842] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 22
Sep 27 12:43:25 ubuntu kernel: [    1.039847] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 22
Sep 27 12:43:25 ubuntu kernel: [    1.039852] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 22
Sep 27 12:43:25 ubuntu kernel: [    1.039857] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 22
Sep 27 12:43:25 ubuntu kernel: [    1.042501] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Sep 27 12:43:25 ubuntu kernel: [    1.042505] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Sep 27 12:43:25 ubuntu kernel: [    1.684618] ata1.00: ATA-7: WDC WD1600JS-55NCB1, 10.02E01, max UDMA/133
Sep 27 12:43:25 ubuntu kernel: [    1.685300] ata1.00: configured for UDMA/133

and output for 
sudo lshw -C disk

is 

      description: ATA Disk
       product: WDC WD1600JS-55N
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WCANMJ842861
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00004746

---

### Post by mc4man on 2009-09-27
Well no cd-rom drive is being found so if the workaround previously mentioned didn't work then you may need to search specific to your hardware.

pc model, desktop or laptop, motherboard, _bios settings_, ect.

Also maybe specific to your cd/dvd drive model if you know or can find out. ( also whether cd/dvd drive is ide or sata

---

### Post by BAMF1501 on 2009-09-27
its ide

---

### Post by mc4man on 2009-09-27
you really need to provide more info on what your pc is. If you don't know then run 
```
sudo lshw
```

For ease of reading thru *yourself *this variant will produce a hardware.hmtl in home folder that breaks the entries up in  individual boxes
```

 sudo lshw -html > hardware.html
```

Possible solutions may be a boot option, a bios setting, ect.
 I remember a while back a case that  with certain hardware changing the bootloader to lilo was the only solution that worked.

Better to identify your hardware first than trying this, that, whatever.

---

### Post by BAMF1501 on 2009-09-28
information for 

> sudo lshw



> description: Desktop Computer
    product: RR790AA-ABA SR2150NX
    vendor: Compaq-Presario
    serial: CNH6501LLW
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=24EFE7D9-8F8B-DB11-9B70-590332872BF6
  *-core
       description: Motherboard
       product: Alhena5
       vendor: ECS
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 5.04 (11/30/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          slot: CPU 1
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
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
          physical id: 28
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2800MHz
          capabilities: ht
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
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             resources: ioport:a000(size=4096) memory:f8900000-fe9fffff ioport:bff00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fa000000-fbffffff ioport:ac00(size=128) memory:fe9e0000-fe9fffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16) memory:febffc00-febfffff
           *-disk
                description: ATA Disk
                product: WDC WD1600JS-55N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANMJ842861
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00004746
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 428b3513-b85b-49ad-babb-822de1c2c7d6
                   size: 143GiB
                   capacity: 143GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-09-27 21:42:01 filesystem=ext3 modified=2009-09-27 22:59:47 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2009-09-27 22:13:56 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5891MiB
                   capacity: 5891MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5890MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:febfe000-febfefff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:febfd000-febfdfff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:febfc000-febfcfff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:febfb000-febfbfff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:febfa000-febfafff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:febff800-febff8ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:fed00000-fed003ff
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:febf4000-febf7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:b000(size=4096) memory:fea00000-feafffff
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:feaf0000-feafffff ioport:bc00(size=8)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:19:21:a8:d8:58
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:20 ioport:b800(size=256) memory:feaefc00-feaefcff

---

### Post by BAMF1501 on 2009-09-28
BTW Main cdrom still dont work but i got my external one back from friend about an hour ago and it burns perfectly finebut i still would like to fix my main one

---

### Post by mc4man on 2009-09-28
Well can't realy help you myself, will give this a bit of a bump.

Possibly there could be a bios setting, but being unfamiliar with yours and the ide controller  can't advise 
( though typically major manufacturer's ship a neutered bios with very few settings, the theory being to minimize possible problems while the pc is under warranty and support.

---

### Post by BAMF1501 on 2009-10-01
I reformatted with karmic 9.10 beta and detects cd yay for beta :)

---

