---
title: "Laptop has no display after upgrading ubuntu."
date: 2011-01-10
forum: General Help
---

### Post by Adrenochrom3 on 2011-01-10
okay so I attempted to install ubuntu 10.10 (64x) on to my Dell Inspiron M5010. it booted to cd, and got to the main menu. i clicked install ubuntu, and it thought for a little while, then turned to a black screen and it had a cursor in the top left that blinked. it didnt do anything for a while. wouldn't let me type or anything.

my brother said it might have been the cd, so i made another one. same thing happened. i assumed ubuntu 10.10 (64x) didnt like my computer, and i gave up.

until, i attempted to install an earlier version of ubuntu.

I managed to get ubuntu 9.04 (64x) installed on to my Dell Inspiron M5010 with no problems. now here is where the problem lies... 

i went to upgrade ubuntu 9.04 to the next avail (ubuntu 9.10) and the updates went smoothly. but when the upgrade was finished and the computer restarted, after booting the computer wouldnt show any display. but i could tell ubuntu was okay because even though i couldnt see, i logged onto my user name. so ubuntu works, it just doesnt have a display.

so i reinstalled 9.04 (64x) that way i would be able to get some insight on this situation, and maybe make some changes before i upgrade again. because ultimately i want to have Ubuntu 10.10 upgraded on here.

thank you for your help.

---

### Post by amsterdamharu on 2011-01-10
You have the 9.04CD and can boot with that (try ubuntu without installing menu item). That's what's called the live CD.

Starting from this CD you might try to fix problems with the updated version.
We could check out what hardware you've got, can you copy and paste the following command in the terminal and post the output here? To open the terminal press alt + F2 and type gnome-terminal then click run.

```
sudo lshw
```

When you post the output here please select the text and press the # button to add code tags or wrap it in &#91;code] &#91;/code] tags.

---

### Post by Bucky Ball on 2011-01-10
10.04 LTS. Download and install. You tried two releases but have missed the LTS, which are generally more stable. 

10.04 should work. 10.10 has numerous problems with its current kernel and I would leave alone for now unless you fancy a trouble-shooting learning curve, which of course you might. ;)

---

### Post by Adrenochrom3 on 2011-01-10
well yea naturally, i love to learn new stuff about ubuntu. this isnt my first time using ubuntu. ive been around the block a few times with my share of other problems. but this situation is a first for me. i just got a new computer and i duel booted with windows 7 (which im currently on.) and i just wanted to get ubuntu upgraded and set up ready to customize. but ubuntu also doesnt see that i have a wireless card, and it wont get drivers for it. so thats another problem for me to fix.. but ill post the output here in a few mins.

---

### Post by Bucky Ball on 2011-01-10
That's also another known issue with the current 10.10 kernel.

The kernel in question is 2.6.35-24

---

### Post by Adrenochrom3 on 2011-01-10
heres the output:


    description: Portable Computer

    product: Inspiron M5010

    vendor: Dell Inc.

    version: A08

    serial: ghfghf

    width: 64 bits

    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32

    configuration: boot=normal chassis=portable uuid=44454C4C-5800-1050-8053-C4C04F5A4D31

  *-core

       description: Motherboard

       product: 08KT6J

       vendor: Dell Inc.

       physical id: 0

       version: A08

       serial: ghfgfhg

       slot: ghfhgfhg
     *-cache:0

          description: L1 cache

          physical id: 5

          slot: L1-Cache

          size: 256KiB

          capacity: 256KiB

          capabilities: internal write-back unified

     *-cache:1

          description: L2 cache

          physical id: 6

          slot: L2-Cache

          size: 1MiB

          capacity: 1MiB

          capabilities: internal varies data

     *-memory

          description: System Memory

          physical id: 1d

          slot: System board or motherboard

          size: 3GiB

        *-bank:0

             description: SODIMM Synchronous 1333 MHz (0.8 ns)

             product: hgfhgfhgf

             vendor: 802C

             physical id: 0

             serial: gfhgfhgf

             slot: DIMM_A

             size: 2GiB

             width: 64 bits

             clock: 1333MHz (0.8ns)

        *-bank:1

             description: SODIMM Synchronous 1333 MHz (0.8 ns)

             product: ghfhgfhgf
             vendor: 80AD

             physical id: 1

             serial: ghfgfh

             slot: DIMM_B

             size: 1GiB

             width: 64 bits

             clock: 1333MHz (0.8ns)

        *-bank:2

             description: SODIMM [empty]

             physical id: 2

     *-firmware

          description: BIOS

          vendor: Dell Inc.

          physical id: 0

          version: A08 (10/12/2010)

          size: 64KiB

          capacity: 1984KiB

          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification

     *-cpu

          description: CPU

          product: AMD Athlon(tm) II P340 Dual-Core Processor

          vendor: Advanced Micro Devices [AMD]

          physical id: 4

          bus info: cpu@0

          version: AMD Athlon(tm) II P340 Dual-Core Processor

          serial: hgfhgf

          slot: CPU 1

          size: 800MHz

          capacity: 2200MHz

          width: 64 bits

          clock: 200MHz

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni monitor cx16 lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt cpufreq

     *-pci:0

          description: Host bridge

          product: RS780 Host Bridge Alternate

          vendor: Advanced Micro Devices [AMD]

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 00

          width: 32 bits

          clock: 66MHz

          configuration: latency=32

        *-pci:0

             description: PCI bridge

             product: RS780 PCI to PCI bridge (ext gfx port 0)

             vendor: Advanced Micro Devices [AMD]

             physical id: 2

             bus info: pci@0000:00:02.0

             version: 00

             width: 32 bits

             clock: 33MHz

             capabilities: pci pm pciexpress msi ht bus_master cap_list

             configuration: driver=pcieport-driver

           *-display

                description: VGA compatible controller

                product: M96 [Mobility Radeon HD 4650]

                vendor: ATI Technologies Inc

                physical id: 0

                bus info: pci@0000:02:00.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: pm pciexpress msi bus_master cap_list

                configuration: driver=fglrx_pci latency=0 module=fglrx

           *-multimedia

                description: Audio device

                product: R700 Audio Device [Radeon HD 4000 Series]

                vendor: ATI Technologies Inc

                physical id: 0.1

                bus info: pci@0000:02:00.1

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: pm pciexpress msi bus_master cap_list

                configuration: driver=HDA Intel latency=0 module=snd_hda_intel

        *-pci:1

             description: PCI bridge

             product: RS780 PCI to PCI bridge (PCIE port 0)

             vendor: Advanced Micro Devices [AMD]

             physical id: 4

             bus info: pci@0000:00:04.0

             version: 00

             width: 32 bits

             clock: 33MHz

             capabilities: pci pm pciexpress msi ht bus_master cap_list

             configuration: driver=pcieport-driver

           *-network UNCLAIMED

                description: Network controller

                product: Broadcom Corporation

                vendor: Broadcom Corporation

                physical id: 0

                bus info: pci@0000:04:00.0

                version: 01

                width: 64 bits

                clock: 33MHz

                capabilities: pm msi pciexpress bus_master cap_list

                configuration: latency=0

        *-pci:2

             description: PCI bridge

             product: RS780 PCI to PCI bridge (PCIE port 1)

             vendor: Advanced Micro Devices [AMD]

             physical id: 5

             bus info: pci@0000:00:05.0

             version: 00

             width: 32 bits

             clock: 33MHz

             capabilities: pci pm pciexpress msi ht bus_master cap_list

             configuration: driver=pcieport-driver

           *-network

                description: Ethernet interface

                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

                vendor: Realtek Semiconductor Co., Ltd.

                physical id: 0

                bus info: pci@0000:05:00.0

                logical name: eth0

                version: 02

                serial: hjghgf

                size: 10MB/s

                capacity: 100MB/s

                width: 64 bits

                clock: 33MHz

                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s

        *-storage

             description: SATA controller

             product: SB700/SB800 SATA Controller [AHCI mode]

             vendor: ATI Technologies Inc

             physical id: 11

             bus info: pci@0000:00:11.0

             logical name: scsi0

             logical name: scsi1

             version: 40

             width: 32 bits

             clock: 66MHz

             capabilities: storage bus_master cap_list emulated

             configuration: driver=ahci latency=32 module=ahci

           *-disk

                description: ATA Disk

                product: WDC WD3200BEVT-7

                vendor: Western Digital

                physical id: 0

                bus info: scsi@0:0.0.0

                logical name: /dev/sda

                version: 01.0

                serial: ghfghfgh

                size: 298GiB (320GB)

                capabilities: partitioned partitioned:dos

                configuration: ansiversion=5 signature=771cb968

              *-volume:0

                   description: Windows NTFS volume

                   physical id: 1

                   bus info: scsi@0:0.0.0,1

                   logical name: /dev/sda1

                   version: 3.1

                   serial: gfghdg

                   size: 98MiB

                   capacity: 100MiB

                   capabilities: primary bootable ntfs initialized

                   configuration: clustersize=4096 created=2011-01-07 23:33:59 filesystem=ntfs label=System Reserved state=clean

              *-volume:1

                   description: Windows NTFS volume

                   physical id: 2

                   bus info: scsi@0:0.0.0,2

                   logical name: /dev/sda2

                   version: 3.1

                   serial: gdfhdfgd

                   size: 148GiB

                   capacity: 148GiB

                   capabilities: primary ntfs initialized

                   configuration: clustersize=4096 created=2011-01-07 23:34:23 filesystem=ntfs state=clean

              *-volume:2

                   description: Extended partition

                   physical id: 3

                   bus info: scsi@0:0.0.0,3

                   logical name: /dev/sda3

                   size: 101MiB

                   capacity: 101MiB

                   capabilities: primary extended partitioned partitioned:extended

                 *-logicalvolume

                      description: Linux swap / Solaris partition

                      physical id: 5

                      logical name: /dev/sda5

                      capacity: 101MiB

                      capabilities: nofs

              *-volume:3

                   description: EXT3 volume

                   vendor: Linux

                   physical id: 4

                   bus info: scsi@0:0.0.0,4

                   logical name: /dev/sda4

                   logical name: /

                   version: 1.0

                   serial: jhghjg

                   size: 148GiB

                   capacity: 148GiB

                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized

                   configuration: created=2011-01-09 15:27:47 filesystem=ext3 modified=2011-01-10 03:42:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2011-01-10 03:42:07 state=mounted

           *-cdrom

                description: DVD-RAM writer

                product: DVD+-RW DS-8A5SH

                vendor: PLDS

                physical id: 1

                bus info: scsi@1:0.0.0

                logical name: /dev/cdrom

                logical name: /dev/cdrw

                logical name: /dev/dvd

                logical name: /dev/dvdrw

                logical name: /dev/scd0

                logical name: /dev/sr0

                version: XD12

                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram

                configuration: ansiversion=5 status=nodisc

        *-usb:0

             description: USB Controller

             product: SB700/SB800 USB OHCI0 Controller

             vendor: ATI Technologies Inc

             physical id: 12

             bus info: pci@0000:00:12.0

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: bus_master

             configuration: driver=ohci_hcd latency=32

        *-usb:1

             description: USB Controller

             product: SB700/SB800 USB EHCI Controller

             vendor: ATI Technologies Inc

             physical id: 12.2

             bus info: pci@0000:00:12.2

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: pm debug bus_master cap_list

             configuration: driver=ehci_hcd latency=32 module=ehci_hcd

        *-usb:2

             description: USB Controller

             product: SB700/SB800 USB OHCI0 Controller

             vendor: ATI Technologies Inc

             physical id: 13

             bus info: pci@0000:00:13.0

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: bus_master

             configuration: driver=ohci_hcd latency=32

        *-usb:3

             description: USB Controller

             product: SB700/SB800 USB EHCI Controller

             vendor: ATI Technologies Inc

             physical id: 13.2

             bus info: pci@0000:00:13.2

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: pm debug bus_master cap_list

             configuration: driver=ehci_hcd latency=32 module=ehci_hcd

        *-serial

             description: SMBus

             product: SBx00 SMBus Controller

             vendor: ATI Technologies Inc

             physical id: 14

             bus info: pci@0000:00:14.0

             version: 42

             width: 32 bits

             clock: 66MHz

             configuration: driver=piix4_smbus latency=0 module=i2c_piix4

        *-multimedia

             description: Audio device

             product: SBx00 Azalia (Intel HDA)

             vendor: ATI Technologies Inc

             physical id: 14.2

             bus info: pci@0000:00:14.2

             version: 40

             width: 64 bits

             clock: 33MHz

             capabilities: pm bus_master cap_list

             configuration: driver=HDA Intel latency=32 module=snd_hda_intel

        *-isa

             description: ISA bridge

             product: SB700/SB800 LPC host controller

             vendor: ATI Technologies Inc

             physical id: 14.3

             bus info: pci@0000:00:14.3

             version: 40

             width: 32 bits

             clock: 66MHz

             capabilities: isa bus_master

             configuration: latency=0

        *-pci:3

             description: PCI bridge

             product: SBx00 PCI to PCI Bridge

             vendor: ATI Technologies Inc

             physical id: 14.4

             bus info: pci@0000:00:14.4

             version: 40

             width: 32 bits

             clock: 66MHz

             capabilities: pci bus_master vga_palette

        *-usb:4

             description: USB Controller

             product: SB700/SB800 USB OHCI0 Controller

             vendor: ATI Technologies Inc

             physical id: 16

             bus info: pci@0000:00:16.0

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: bus_master

             configuration: driver=ohci_hcd latency=32

        *-usb:5

             description: USB Controller

             product: SB700/SB800 USB EHCI Controller

             vendor: ATI Technologies Inc

             physical id: 16.2

             bus info: pci@0000:00:16.2

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: pm debug bus_master cap_list

             configuration: driver=ehci_hcd latency=32 module=ehci_hcd

     *-pci:1

          description: Host bridge

          product: Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration

          vendor: Advanced Micro Devices [AMD]

          physical id: 101

          bus info: pci@0000:00:18.0

          version: 00

          width: 32 bits

          clock: 33MHz

     *-pci:2

          description: Host bridge

          product: Family 10h [Opteron, Athlon64, Sempron] Address Map

          vendor: Advanced Micro Devices [AMD]

          physical id: 102

          bus info: pci@0000:00:18.1

          version: 00

          width: 32 bits

          clock: 33MHz

     *-pci:3

          description: Host bridge

          product: Family 10h [Opteron, Athlon64, Sempron] DRAM Controller

          vendor: Advanced Micro Devices [AMD]

          physical id: 103

          bus info: pci@0000:00:18.2

          version: 00

          width: 32 bits

          clock: 33MHz

     *-pci:4

          description: Host bridge

          product: Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control

          vendor: Advanced Micro Devices [AMD]

          physical id: 104

          bus info: pci@0000:00:18.3

          version: 00

          width: 32 bits

          clock: 33MHz

     *-pci:5

          description: Host bridge

          product: Family 10h [Opteron, Athlon64, Sempron] Link Control

          vendor: Advanced Micro Devices [AMD]

          physical id: 105

          bus info: pci@0000:00:18.4

          version: 00

          width: 32 bits

          clock: 33MHz

  *-battery

       description: Lithium Ion Battery

       product: DELL

       vendor: Sanyo

       physical id: 1

       serial: fhfgh

       slot: Sys. Battery Bay

       capacity: 45000mWh

       configuration: voltage=10.8V

  *-network DISABLED

       description: Ethernet interface

       physical id: 2

       logical name: pan0

       serial: jhbkj
       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Adrenochrom3 on 2011-01-10
sorry its so long i didnt have time to delete each space

---

### Post by Bucky Ball on 2011-01-10
Okay, Broadcom cards are a major issue with the current 10.10 kernel. I really would try 10.04 LTS for now unless you have some hours to kill. Can of worms opening up here.

Question: What is the big attraction with having 10.10? LTS release always more stable with way more support, as you can see from here:

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html) 

If you can get to a terminal and command prompt (boot to the recovery kernel), what does 'startx' yield?

Also, if you can get to the grub menu at boot, choose the 10.10 regular kernel, hit 'e' (not enter), find the kernel line that ends with 'quiet splash' and append on the end of that:

```
acpi=off
```

Hit x to boot. Any different?

---

### Post by Bucky Ball on 2011-01-10
Okay, Broadcom cards are a major issue with the current 10.10 kernel. I really would try 10.04 LTS for now unless you have some hours to kill. Can of worms opening up here.

Question: What is the big attraction with having 10.10? LTS release always more stable with way more support, as you can see from here:

[http://www.ubuntugeek.com/the-ubuntu-release-cycle.html](http://www.ubuntugeek.com/the-ubuntu-release-cycle.html) 

If you can get to a terminal and command prompt (boot to the recovery kernel to do this, watch for any obvious problems or halts, errors, then choose 'drop to root shell' at the recovery options menu), what does 'startx' yield?

Also, if you can get to the grub menu at boot, choose the 10.10 regular kernel, hit 'e' (not enter), find the kernel line that ends with 'quiet splash' and append on the end of that:

```
acpi=off
```Hit control+x to boot. Any different?

---

### Post by Adrenochrom3 on 2011-01-10
well heres the thing. i reinstalled 9.04 to make some changes before i upgrade. 9.04 was the only disc i could get to install correctly. and i dont have an Ethernet cord so i cant plug the ubuntu into the internet until tomorrow. ill upgrade tomorrow, see if it has the same display problem, and if so, ill let you know if what you said works. check back tomorrow night thanks

---

### Post by Bucky Ball on 2011-01-10
k

---

### Post by amsterdamharu on 2011-01-10
[COLOR=Red]When pasting it here please wrap it in &#91;code] &#91;/code] tags.[/COLOR]
In other words [COLOR=Red]&#91;code] [COLOR=Black]Your pasted stuff [/COLOR]&#91;/code]

[COLOR=Black]I can't find the exact model of your broadcom card, if it's a problem with the kernel you're better off getting 10.04.
I assume your wired network works.

[http://manpages.ubuntu.com/manpages/maverick/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/maverick/man4/radeon.4.html)
You have the "Mobility Radeon HD 4650" and should be supported with the [/COLOR][/COLOR][xserver-xorg-video-radeon]("https://launchpad.net/ubuntu/maverick/+package/xserver-xorg-video-radeon") driver.

[http://packages.ubuntu.com/dapper/xorg-driver-fglrx](http://packages.ubuntu.com/dapper/xorg-driver-fglrx)
I don't see any maverick drivers listed for fglrx so no 3D support (yet).

You might be able to boot from a live CD and remove the xorg.conf in /etc/X11 and reboot then add the kernel parameters "acpi=off xforcevesa" but I think you'd be better off using 10.04 for now.

To see what wireless you have exactly you might issue the command:
```
sudo lspci
sudo lsusb
```Depending where it'll show up but as Bucky Ball stated you might have problems using a new kernel that does not (yet) support some hardware.

---

### Post by Bucky Ball on 2011-01-10
> **amsterdamharu said:**
> 

[http://packages.ubuntu.com/dapper/xorg-driver-fglrx](http://packages.ubuntu.com/dapper/xorg-driver-fglrx)
I don't see any maverick drivers listed for fglrx so no 3D support (yet).



Looks like the Dapper packages. Ages old. I am running fglrx driver with my:

```
VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```... using 10.10, but there might not be one for the 4650, true. ;)

---

### Post by amsterdamharu on 2011-01-10
> Looks like the Dapper packages. Ages old. I am running fglrx driver with my:

Top of the page there is a list of distrubutions with their links, maverick is missing there.

How did you install the drivers for maverick (that is 10.10 right?).

---

### Post by Bucky Ball on 2011-01-10
Did an update when I first installed. Check System >Admin  >Additional Drivers. ATI driver in there waiting to be activated.  Click 'Activate'. That's it.

You must be online to download them when you click 'Activate' naturally. ;)

---

### Post by amsterdamharu on 2011-01-10
@Bucky Ball: Strange that the packages site doesn't list maverick as having fglrx drivers.

Does the following command yield a driver?
```
apt-cache search fglrx
```

To see what's installed:
```
dpkg-query -W | grep fglrx
```

I don't have 10.10 so can't check if it's in the repository but according to Ubuntu's site it isn't available for 10.10.

---

### Post by Bucky Ball on 2011-01-10
First command outputs this:

```
binky@tosher:~$ apt-cache search fglrx
fglrx-modaliases - Identifiers supported by the ATI graphics driver
xserver-xorg-video-radeon - X.Org X server -- AMD/ATI Radeon display driver
fglrx - Video driver for the ATI graphics accelerators
fglrx-amdcccle - Catalyst Control Centre for the ATI graphics accelerators
fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
binky@tosher:~$ 
```

Second:

```
binky@tosher:~$ dpkg-query -W | grep fglrx
fglrx    2:8.780-0ubuntu2
fglrx-amdcccle    2:8.780-0ubuntu2
fglrx-modaliases    2:8.780-0ubuntu2
```

Well, I'm running the ATI/AMD proprietary FGLRX graphics driver. That is what is in Additional Drivers and has been since I got this thing and installed about three months ago. I haven't manually installed anything. Took what I was given. :)

---

### Post by amsterdamharu on 2011-01-10
Ok, thank you for clearing that up. The driver is still available but has just been renamed:
[http://packages.ubuntu.com/lucid/fglrx](http://packages.ubuntu.com/lucid/fglrx)

It seems that since lucid it is just fglrx even the xorg-driver-fglrx in lucid just installs the fglrx package:
[http://packages.ubuntu.com/lucid/xorg-driver-fglrx](http://packages.ubuntu.com/lucid/xorg-driver-fglrx)

That means your card has driver support out of the box, with jocky recognizing it and a package available for it.

---

### Post by Bucky Ball on 2011-01-10
> **amsterdamharu said:**
> 
That means your card has driver support out of the box, with jocky recognizing it and a package available for it.

Seems that way. The out of the box support part is a definite. ;)

---

### Post by Adrenochrom3 on 2011-01-10
i just want to remind you that at the moment i am running ubuntu 9.04. im not going to make a new cd to install 10.04, im just going to upgrade to 10.04. but the thing is, that update manager will only let me upgrade to ubuntu 9.10 for now, then ill have to upgrade again to 10.04.  

i did activate the graphics drivers. usually it allows me to activate my wireless drivers there as well, but that didnt happen.

and yes my wired network does work. 

i will do what i can with the information you have listed, and ill post all output later tonight.

---

### Post by Bucky Ball on 2011-01-10
> **Adrenochrom3 said:**
> i just want to remind you that at the moment i am running ubuntu 9.04. im not going to make a new cd to install 10.04, im just going to upgrade to 10.04. but the thing is, that update manager will only let me upgrade to ubuntu 9.10 for now, then ill have to upgrade again to 10.04.  

i did activate the graphics drivers. usually it allows me to activate my wireless drivers there as well, but that didnt happen.

and yes my wired network does work. 

i will do what i can with the information you have listed, and ill post all output later tonight.

There is no 'Automatic' upgrade from that release to the LTS, as you've discovered. LTS releases upgrade to the next LTS though which is another good reason for using LTS releases on your stable partition. You are going to need to do some long-winded stuffing about to get that happening. 9.04 - 9.10 - 10.04 LTS. Hope you have plenty of time. You ARE better off just installing 10.04 LTS if that is where you want to be. Straight install less than an hour.

---

### Post by Adrenochrom3 on 2011-01-11
that is true, but i figure i will just upgrade via update manager. i have time on my hands, and i want to make sure everything works out okay. if i can get past the display problem, i can work on all the other minor problems i have.  i really appreciate you guys helping me get through this.

---

### Post by Bucky Ball on 2011-01-11
> **Adrenochrom3 said:**
> ... i want to make sure everything works out okay.

No guarantee of that! But good luck with it. If you make it to 10.04 LTS I would stick with it if I were you. 10.10 has issues. 

Good luck. ;)

---

### Post by Adrenochrom3 on 2011-01-14
OK awesome! it did end up being the driver for it. i activated it through "Hardware Drivers."   

i realized that when i upgraded the first time, i never activated the driver. thus when i did the upgrade, it screwed with my display.

But at the moment im running 10.04, and its doing fine.

now my next feat is to get the wireless working...

---

### Post by amsterdamharu on 2011-01-14
Your wired network is Realtek, strange that lshw didn't give the model of your wireless.
```
*-network UNCLAIMED
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
```

Is there anything under system -> hardware drivers?

Can you find the exact model of your wireless with the following command?
```
lspci -k
```

---

### Post by Bucky Ball on 2011-01-14
> **Adrenochrom3 said:**
> OK awesome! it did end up being the driver for it. i activated it through "Hardware Drivers."   

i realized that when i upgraded the first time, i never activated the driver. thus when i did the upgrade, it screwed with my display.

But at the moment im running 10.04, and its doing fine.

now my next feat is to get the wireless working...

Please post a new thread regarding wireless and post a link to it here and will see if I can lend a hand. You will get more assistance that way as the thread title will be descriptive.

Great to hear it worked out! ;)

---

