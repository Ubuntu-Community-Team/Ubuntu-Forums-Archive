---
title: "Configuration Problem"
date: 2010-03-12
forum: General Help
---

### Post by MughalShahzad on 2010-03-12
Hi, I am using UBUNTU 9.10 DESKTOP EDITION moreover I have Huawei ETS-2558 fixed wireless terminal for internet it works fine with XP I don't know how to configure it for UBUNTU 9.10 DESKTOP EDITION. 

Kindly help me to configure my device.

Thanks & Regards

---

### Post by chaanakya_chiraag on 2010-03-12
Could you please post the output of ```
sudo lshw
``` (Enter that in the terminal).  Please put it in CODE tags.  Thanks!

---

### Post by cariboo on 2010-03-12
please don't create multiple threads on the same subject. I have merged your three threads.

---

### Post by MughalShahzad on 2010-03-13
```

shahzad@shahzad-desktop:~$ sudo lshw
[sudo] password for shahzad: 
shahzad-desktop           
    description: Desktop Computer
    product: OptiPlex GX240
    vendor: Dell Computer Corporation
    serial: 5PL8H0J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=desktop cpus=1 power-on_password=enabled uuid=44454C4C-5000-104C-8038-B5C04F48304A
  *-core
       description: Motherboard
       product: OptiPlex GX240
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A03 (03/01/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 2GHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 133 MHz (7.5 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 133MHz (7.5ns)
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff(prefetchable)
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:e000(size=4096) memory:ff800000-ff9fffff memory:f8000000-fbffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 Pro Ultra TF
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:f8000000-fbffffff(prefetchable) ioport:ec00(size=256) memory:ff8fc000-ff8fffff memory:ff800000-ff81ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:ff600000-ff7fffff memory:20000000-200fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 78
                serial: 00:08:74:0e:72:e9
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
                resources: irq:18 ioport:dc80(size=128) memory:ff6ffc00-ff6ffc7f memory:20000000-2001ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-disk
                description: ATA Disk
                product: MAXTOR STM380215
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 6RX4RC0X
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d3cbd3cb
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: ba60bcac-25f9-464d-9215-c51286efaee4
                   size: 10001MiB
                   capacity: 10001MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-15 16:45:43 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 64GiB
                   capacity: 64GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10001MiB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 27GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 3812MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /
                      capacity: 23GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
           *-cdrom
                description: SCSI CD-ROM
                product: CD-ROM  TS-H192C
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: B504
                capabilities: removable audio
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff80(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 12
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ccd0(size=16)
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff60(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:c800(size=256) ioport:cc40(size=64)
shahzad@shahzad-desktop:~$ 


```

---

### Post by chaanakya_chiraag on 2010-03-14
Basically, Ubuntu doesn't recognize it.  Could you try [this]("http://sbjaved.blogspot.com/2008/06/huawei-ets-2558-setup-guide-for-linux.html") and report back?  Thanks!

---

### Post by MughalShahzad on 2010-03-14
i am trying but failed at first command su due to Authentication failure.

Thanks for your time & interest

---

### Post by chaanakya_chiraag on 2010-03-14
Use sudo instead and use your password to authenticate (it will not be shown in the terminal)

---

### Post by MughalShahzad on 2010-03-15
<deleted>

---

### Post by MughalShahzad on 2010-03-16
<deleted>

---

### Post by MughalShahzad on 2010-03-16
Hello Sir,

I tried that but disappointed,

in 3rd step writer said that search the following string, which is as follows
[COLOR=#009900]
ti_usb_3410_5052 1-1:2.0: TI USB 3410 1 port adapter converter detected
[/COLOR]
[COLOR=#009900]usb 1-1: TI USB 3410 1 port adapter converter now attached to /dev/ttyUSB0

[COLOR=Black]i tried but out was different[COLOR=#009900], [COLOR=Black]which was as follows[/COLOR][/COLOR][/COLOR]

[/COLOR][COLOR=#009900]ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected
[/COLOR]
[COLOR=#009900]usb 2-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0

[COLOR=Black]despite this i did all steps, i made the rule, plunged out the cable to plug in again and got the following out put[/COLOR]

[/COLOR][COLOR=#009900]ti_usb_3410_5052 2-2:2.0: TI USB 3410 1 port adapter converter detected[/COLOR]

[COLOR=#009900]usb 2-2: TI USB 3410 1 port adapter converter now attached to ttyUSB0[/COLOR]

while following output was expected

[COLOR=#009900]ti_usb_3410_5052 1-1:2.0: TI USB 3410 1 port adapter converter detected[/COLOR]

[COLOR=#009900]usb 1-1: TI USB 3410 1 port adapter converter now attached to /dev/ttyUSB0[/COLOR]

even than i set-up the account assuming that might be it will work
when i put the following command
[COLOR=#009900]
wvdial ptcl

[COLOR=Black]system said command is not installed first install it, i did but at the end faild[/COLOR]
[/COLOR]
now what to do...
please guide me

Thanks & Regards
Shahzad


> **chaanakya_chiraag said:**
> Use sudo instead and use your password to authenticate (it will not be shown in the terminal)

---

### Post by chaanakya_chiraag on 2010-03-16
How exactly did it fail?  Please post the output of the program.  Thanks!
- Chiraag

---

