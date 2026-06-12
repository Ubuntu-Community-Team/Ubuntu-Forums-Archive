---
title: "BioStar Remote Control"
date: 2011-10-13
forum: General Help
---

### Post by Dan Again on 2011-10-13
I just purchased a BioStar barebones system to use as a media center/HTPC. It came with a remote, but I'm not having any luck getting it to work. Admittedly, the remote only states that it is compatible with Windows. Anyone have any suggestions?

---

### Post by Dan Again on 2011-10-14
Bump. Any ideas?

---

### Post by Dan Again on 2011-10-17
Bump. Has anyone gotten a BioStar remote working?

---

### Post by Dan Again on 2012-03-18
I would really love to get this working. I've been playing around with lirc and am not having any luck...it looks like Ubuntu isn't even recognizing the IR device, as cat /proc/bus/input/devices does not seem to show a remote. Any ideas?

---

### Post by Dan Again on 2012-03-19
Bump

---

### Post by coldraven on 2012-03-19
Have you tried this?
[https://help.ubuntu.com/community/InstallLirc/Maverick](https://help.ubuntu.com/community/InstallLirc/Maverick)

---

### Post by Dan Again on 2012-03-19
Well, I haven't been able to get that far because it looks like Ubuntu isn't even picking up on the fact that there is a IR receiver/remote connected. I purchased this device...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856115039](http://www.newegg.com/Product/Product.aspx?Item=N82E16856115039)

from NewEgg. Any idea how I can get Ubuntu to recognize the IR receiver/remote?

---

### Post by Dan Again on 2012-03-19
If you look at the picture that shows that full back panel, you can see the cord for the IR receiver snaking off to the right.

---

### Post by coldraven on 2012-03-19
I will make a wild guess that if it does not show up when you do
```
sudo lshw
```
then it is probably disabled in the BIOS

---

### Post by Dan Again on 2012-03-19
Well, here is the result of running the command you suggested...

```
mediacenter               
    description: Desktop Computer
    product: TH67B (None)
    vendor: BIOSTAR Group
    version: 6.0
    serial: None
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: chassis=desktop family=None sku=None uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: TH67B
       vendor: BIOSTAR Group
       physical id: 0
       version: 6.0
       serial: None
       slot: None
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 4.6.4
          date: 02/18/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L1 cache
          physical id: 4
          size: 128KiB
          capacity: 128KiB
          capabilities: internal varies
     *-cache:1
          description: L2 cache
          physical id: 5
          size: 512KiB
          capacity: 512KiB
          capabilities: internal varies unified
     *-cache:2
          description: L3 cache
          physical id: 6
          size: 3MiB
          capacity: 3MiB
          capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL8-2GBHK
             vendor: Undefined
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL8-2GBHK
             vendor: Undefined
             physical id: 1
             serial: 00000000
             slot: A1_DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL8-2GBHK
             vendor: Undefined
             physical id: 2
             serial: 00000000
             slot: A1_DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL8-2GBHK
             vendor: Undefined
             physical id: 3
             serial: 00000000
             slot: A1_DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
          vendor: Intel Corp.
          physical id: 15
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
          slot: SOCKET 0
          size: 3100MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt xsave avx lahf_lm arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:fe000000-fe3fffff memory:c0000000-cfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:fe407000-fe40700f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:fe406000-fe4063ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:fe400000-fe403fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) ioport:d0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 06
                serial: 00:30:67:ba:ed:27
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:41 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe405000-fe4053ff
        *-isa
             description: ISA bridge
             product: H67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f0d0(size=16) ioport:f0c0(size=16)
           *-disk
                description: ATA Disk
                product: Hitachi HDS72302
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MN6O
                serial: MN1220F32DDNRD
                size: 1863GiB (2TB)
                capabilities: gpt-1.00 partitioned partitioned:gpt
                configuration: ansiversion=5 guid=46b0b6a9-da7b-45e3-86f5-17944e34c9f6
              *-volume:0
                   description: Data partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: bec48c5e-48eb-45d6-a68a-7d5b2155a024
                   size: 285MiB
                   capabilities: ext2 initialized
                   configuration: filesystem=ext2 modified=2012-03-19 19:56:44 mount.fstype=ext2 mount.options=rw,relatime,errors=continue mounted=2011-11-11 14:19:21 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 426f1c39-52ed-41a5-9b52-16dc5185a241
                   size: 1906MiB
                   capacity: 1906MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4095
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: a576999f-8cae-44d5-b60a-a5fcd072ab53
                   size: 7629MiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-12 16:59:00 filesystem=ext4 lastmountpoint=/ modified=2012-01-25 17:10:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-03-19 19:59:31 state=mounted
              *-volume:3
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: 0c5088ec-ad2d-4d50-a16b-6cf914cfa772
                   size: 1853GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-10-12 16:59:02 filesystem=ext4 lastmountpoint=/home modified=2012-03-19 19:59:31 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered mounted=2012-03-19 19:59:31 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: BC-12B1ST
                vendor: ASUS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe404000-fe4040ff ioport:f040(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=16) ioport:f060(size=16)

```

Is that serial UNCLAIMED device all the way at the bottom the IR receiver? I took a quick look in BIOS but couldn't make too much sense of it and didn't want to go mucking around with a good idea of what I was doing.

---

### Post by Dan Again on 2012-03-20
Bump

---

### Post by coldraven on 2012-03-21
Did you try the testing method in that link that I posted?
So install lirc like so
```
sudo apt-get install lirc
```
Then test by opening a terminal, type ```
irw
``` and start pressing your remote at the sensor.
If that does not work then have another look in your BIOS for "Serial Port" and make sure it is enabled and set to IrDa or FiRDa.

I only got this from Googling, I don't have an infra red port myself. At least this will keep the thread alive until someone clever comes along. Good luck!

---

### Post by Dan Again on 2012-03-21
Thanks for your suggestions, coldraven. I do have LIRC install already. When I run irw in a terminal, there is no response...no matter how many buttons I push on the remote. I do not see anything that looks like what you mentioned in my BIOS. Here is another snippet from the terminal...maybe this sheds more light on the situation?

```
dan@MediaCenter:~$ irrecord -d /dev/lirc/0 /tmp/lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc/0
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
dan@MediaCenter:~$ irrecord -d /dev/lirc0 /tmp/lircd.conf

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc0
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

---

### Post by coldraven on 2012-03-22
Here's something you can try, it will at least resolve one possible fault.
Get a remote that you know is working and point it at your digital camera or web-cam.
You need to hold the remote about six inches away from the camera.
When viewing the screen you should see the LED flashing when you press a button on the remote.
Now do the same with your BioStar and check that it actually works.

I just did this with my stereo system remote and my cheapo web-cam so I know this is true. For viewing I used guvcview but Cheese would do the same.

Hopefully someone else will respond to this thread and solve the problem, I'm out of ideas!

---

### Post by Dan Again on 2012-05-21
So, the problem was that the device was not turned on in BIOS. I should have figured that out sooner, but I'm just not too familiar with BIOS. thanks to everyone for their help!

---

