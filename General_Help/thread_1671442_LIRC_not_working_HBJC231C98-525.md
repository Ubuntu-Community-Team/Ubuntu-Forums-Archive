---
title: "LIRC not working HBJC231C98-525"
date: 2011-01-20
forum: General Help
---

### Post by thelamer on 2011-01-20
I tried everything here; 

[http://ubuntuforums.org/showthread.php?t=1645241](http://ubuntuforums.org/showthread.php?t=1645241)

When I try to use the Nuvoton IR Receiver it completely locks up the system and I need to chroot into the file system and disable lirc just to get booted again. 

Does anyone have LIRC and the IR receiver working on this box? 

I also went through the list and tried all the cir receivers in the lirc list. 

Here is the hardware info; 

```
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: To be filled by O.E.M.
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080015 (09/15/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: N10 Family DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:fcffc000-fcffffff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:c000(size=4096) memory:fd000000-fe9fffff ioport:ce000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT218 [ION]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:cc00(size=128) memory:fe980000-fe9fffff(prefetchable)
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:fe97c000-fe97ffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:d000(size=4096) memory:fea00000-feafffff ioport:fbf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 03
                serial: 00:30:18:af:2b:4d
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.200 latency=0 link=yes multicast=yes port=MII speed=1GB/s
                resources: irq:27 ioport:d800(size=256) memory:fbfff000-fbffffff(prefetchable) memory:fbff8000-fbffbfff(prefetchable) memory:fbf00000-fbf1ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:feb00000-febfffff memory:80000000-801fffff(prefetchable)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:19 memory:febfe000-febfffff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b880(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b800(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b480(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fcffbc00-fcffbfff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff90(size=16) memory:80200000-802003ff
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
     *-scsi:1
          physical id: 2
          bus info: usb@1:5
          logical name: scsi3
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             size: 7644MiB (8015MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=00036c58
           *-volume
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: bbfc7d7f-e7e5-4f72-89e2-ec12d2c60fc9
                size: 7642MiB
                capacity: 7642MiB
                capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2011-01-19 22:56:14 filesystem=ext3 label=New Volume modified=2011-01-19 23:02:03 mounted=2011-01-19 22:57:28 state=clean

```

Maybe worth mentioning that this system is a disk-less client and the kernel is loaded via tftp. 

The IR receiver plugs into the board on a 4 pin proprietary cir connector not usb. I know it works as I can power the machine on with the remote.

---

### Post by thelamer on 2011-01-21
Ok so I now have it registered as a device, looks like dkms was having problems with a remotely retrieved kernel so I installed a minimal maverick system for testing. 

Now I see the device and lirc0 exists in /dev/ but no output from irw

```
cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=046d Product=c315 Version=0110
N: Name="Logitech Logitech USB Keyboard"
P: Phys=usb-0000:00:1d.3-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0019 Vendor=1050 Product=0001 Version=0000
N: Name="MCE Remote Keyboard"
P: Phys=lirc_wb677
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=sysrq kbd mouse0 event3 
B: EV=7
B: KEY=30000 7 ff87207ac14057ff febeffdfffefffff fffffffffffffffe
B: REL=3

```

---

### Post by RussianNeuroMancer on 2011-01-29
Try that [http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux](http://www.asrock.com/nettop/download.asp?Model=ION%20330HT&o=Linux)

---

### Post by thelamer on 2011-02-04
Thanks Russian, but those are the drivers I used as linked though the forum thread earlier. 

Come on people someone must have this box out there, are you using your remote?

---

### Post by RussianNeuroMancer on 2011-02-04
Looks like Nuvoton provide different CIR to Jetway.

Nuvoton definitely have Linux-drivers for their hardware, but it's available only for original equipment manufacturers, like ASRock and Jetway.

Contact with Jetway tech. support to request Linux-driver for this Nuvoton CIR.

---

### Post by thelamer on 2011-02-06
Yeah way ahead of you, 4 emails in 3 weeks to [email]tech@jetwaycomputer.com[/email] no response. Not a big fan of Jetway right now. 

Thanks for the advice though.

---

### Post by bedege on 2011-02-10
Hi there

Just bought the exact same box from Newegg (D525 + Ion2 Jetway Ion-Top).

Have you had any luck in getting your remote to work with Ubuntu? After looking at this thread [here]("http://ubuntuforums.org/showthread.php?t=1645241"), 
I found that the Asrock Nuvoton drivers worked on the previous release of the Ion Top (Atom 330).

Any idea whether JBC231C98-525 use the same identical CIR receiver as before? From what you explain in this thread, it actually looks like it does not...:confused:

Thanks

---

### Post by bedege on 2011-02-11
Well, I gave the Nuvoton/Asrock drivers a try last night, but no luck :(
I fetched the zip file from Asrock's download page (IR(10.10)2.6.35-22.zip), installed lirc-nct677x-x64-1.1.0-ubuntu10.10-kernel2.6.35.deb and lirc-nct677x-src-1.1.0-ubuntu10.10.deb on my brand new 64bits Maverick 10.10 install, as per Asrock's manual.
As thelamer reported in his previous post, I now have the exact same output from the console, namely something like:
```

cat /proc/bus/input/devices
I: Bus=0019 Vendor=1050 Product=0001 Version=0000
N: Name="MCE Remote Keyboard"
P: Phys=lirc_wb677
...
```
but no joy from [FONT="Courier New"]irw[/FONT] when playing with the remote...

I also noticed than the remote power button stopped working since I've installed lirc and its Nuvoton driver (well, it no longer stops the HTPC, still powers it up from off state though).

Any clue on what the next step might be? Could 32bits vs. 64bits Ubuntu be an issue?

Also, I've noticed from looking at (way too many) other threads on lirc/remote/jetway that the other Jetway D525/Ion2 HTPC (Mini-Top JBC600C99352W) apparently uses a different CIR system that works with Aural Hid driver). Has anybody given it a try on JBC231C98 Ion-Top?

---

### Post by bedege on 2011-02-14
Hi
Just to let you know that I got some feedback from Jetway's Tech Support in California re. IR remote support for JBC231C98-525. :p

> Dear customer,

Thank you for taking the time to write to us with your concerns. I am happy to assist you further. 

We have reviewed your request regarding  Ion Top JBC231C98 issue with CIR & remote under Linux. Please update your Linux Kernel to 2.6.36. And it can support F71809 CIR device then.


We hope this update has been helpful. However, if you have any additional questions, please don't hesitate to contact our Technical Department.

I'll have to give it a try. Though, I Googled "F71809" and wasn't able to find much on that topic vs. 2.6.36 kernel. It's apparently a component from Fintek.
Has anybody any link regarding that component support on Linux or lirc? ):P

---

### Post by bedege on 2011-02-17
Well apparently the Jetway Tech Support was not fully aware when they answered my question...

I've asked the exact same question on the [lirc mailing list]("http://sourceforge.net/mailarchive/forum.php?forum_name=lirc-list&max_rows=25&style=ultimate&viewmonth=201102"). The gentleman that answered me (employed by Red Hat - should know his business :D ) said that there is currently no support for Fintek CIR device in the Linux kernel. That's on his TODO list, he even has the spec sheet from Fintek plus a Jetway NC98 motherboard. So, this driver might happen someday. We just have to be patient!

HTH and may the force be with you!

---

### Post by thelamer on 2011-03-14
So it looks like the exact device is; 

```
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0x0408
    (logical device 2 has address 0x290, could be sensors)

```

Running 2.6.37-12-generic hopefully this is on the choping block somewhere I am not a kernel programmer :)

---

### Post by bedege on 2011-03-14
> **thelamer said:**
> So it looks like the exact device is; 

```
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0x0408
    (logical device 2 has address 0x290, could be sensors)

```

Running 2.6.37-12-generic hopefully this is on the choping block somewhere I am not a kernel programmer :)

Hi
Just curious where this message comes from? Is it lm-sensors?
In any case, does that mean that the remote somehow works now?
Thks

---

### Post by thelamer on 2011-03-20
Yeah, just sensors-detect. Nothing working, but it is there. 

Wish I could run some debugging/testing for someone that knows what they are doing.

---

### Post by bedege on 2011-03-22
> **thelamer said:**
> 
Wish I could run some debugging/testing for someone that knows what they are doing.

Same thing, I'm no kernel programmer (by far!), but still I'd be happy to help testing/troubleshooting code if needed.

I know this new FINTEK circuit is on the TODO list of the kernel guys, so I guess we just need to be patient. :P

---

### Post by bedege on 2011-05-26
Good news! :popcorn:

A patch has been proposed by Jarod Wilson for the Fintek-based Jetway NC98 motherboard.
Please check here:
[https://patchwork.kernel.org/patch/816562/](https://patchwork.kernel.org/patch/816562/)

I haven't given it a try yet, but I wanted to share that piece of code, for those bold enough to compile their kernel! :P

---

### Post by thelamer on 2011-05-28
I rolled the change into a custom kernel, not sure how I am supposed to use it at this point though. The device is still not in lirc .90pre1 . Built it for natty. 

[http://www.ryankuba.com/DropBox/linux-headers-2.6.38.2_2.6.38.2-10.00.Custom_amd64.deb](http://www.ryankuba.com/DropBox/linux-headers-2.6.38.2_2.6.38.2-10.00.Custom_amd64.deb)
[http://www.ryankuba.com/DropBox/linux-image-2.6.38.2_2.6.38.2-10.00.Custom_amd64.deb](http://www.ryankuba.com/DropBox/linux-image-2.6.38.2_2.6.38.2-10.00.Custom_amd64.deb)

Did not roll this with Module Versioning Support disabled as it was just a test. (so no nvidia drivers) 

Does anyone know how I can integrate this into XBMC ?

---

### Post by bedege on 2011-06-01
Haven't tested the patch yet... Time is flying.

FYI, some other feedback on the patch on the mythtv forum
[http://www.gossamer-threads.com/lists/mythtv/users/471580](http://www.gossamer-threads.com/lists/mythtv/users/471580)
that could help in implementing it and making it work.

Cheers

---

### Post by thelamer on 2011-10-22
[http://www.openelec.tv/](http://www.openelec.tv/)

Works out of the box always up to date kernel and lirc nothing to configure, this is my new htpc install on all 3.

---

