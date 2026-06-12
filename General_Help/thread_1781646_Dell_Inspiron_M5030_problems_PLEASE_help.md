---
title: "Dell Inspiron M5030 problems PLEASE help"
date: 2011-06-13
forum: General Help
---

### Post by DanTheMan90 on 2011-06-13
Ok, I got a Dell Inspiron M5030 laptop yesterday and immediately put ubuntu on it, and have run into several problems which I've spent hours and hours trying to resolve to no avail.
My USB mouse is REALLY choppy, the system boots up extremely slowly and I can only log into the Ubuntu Classic (With no effects) Environment, ubuntu classic and unity I can log into, but all that appears is a blank desktop, I can't do anything once logged in other than admire the wallpaper.

I found on a forum that someone had choppy mouse problems, and the environment problem on another (I think) and they installed a graphics propriety driver FGLRX, I tried this and nothing changed at all.

Now that I have installed this over windows 7, I can't return the laptop back to tescos, so please help me find a solution, I've been trying for atleast 5 hours and nothing at all.

Thanks

I've also tried the 32 bit and 64 bit ubuntu operating systems, aswell as many other Linux distros and had the same problem with these also.
My Specs are;

320GB HDD
3GB RAM
ATI Mobility Radeon™ HD4250

Thanks once again, appreciate any help

---

### Post by wildmanne39 on 2011-06-13
> **DanTheMan90 said:**
> Ok, I got a Dell Inspiron M5030 laptop yesterday and immediately put ubuntu on it, and have run into several problems which I've spent hours and hours trying to resolve to no avail.
My USB mouse is REALLY choppy, the system boots up extremely slowly and I can only log into the Ubuntu Classic (With no effects) Environment, ubuntu classic and unity I can log into, but all that appears is a blank desktop, I can't do anything once logged in other than admire the wallpaper.

I found on a forum that someone had choppy mouse problems, and the environment problem on another (I think) and they installed a graphics propriety driver FGLRX, I tried this and nothing changed at all.

Now that I have installed this over windows 7, I can't return the laptop back to tescos, so please help me find a solution, I've been trying for atleast 5 hours and nothing at all.

Thanks

I've also tried the 32 bit and 64 bit ubuntu operating systems, aswell as many other Linux distros and had the same problem with these also.
My Specs are;

320GB HDD
3GB RAM
ATI Mobility Radeon™ HD4250

Thanks once again, appreciate any help
Hi, lets see if we can fix some of these problems. Please log into unity which is ubuntu at the log in screen and hit the windows key we call it the super key and see if the launcher on the left side of the screen comes out. Also please attach a screen shot while you are in unity. Run these commands in a terminal you can get the terminal by hitting ctrl+alt+t.
```
/usr/lib/nux/unity_support_test -p
```
```
sudo lshw
```post the text here by highlighting entire file and click on # in edit panel(code tags) to make it easier to read. If you can not get into unity use ubuntu classic to run these commands. Also here is a guide to use for your video card driver, you may have to remove the flgrx our whatever it was you installed that is not needed.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) This guide will tell you how to remove the other driver first just scroll down the page.

---

### Post by DanTheMan90 on 2011-06-14
I wasn't able to get the terminal nor the launcher, so I've used these commands in Ubuntu Classic (with no effects)

/usr/lib/nux/unity_support_test - p
Gave me this output

```
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

sudo lshw
Gave me this

```
abaddon-inspiron-m5030    
    description: Portable Computer
    version: A03
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=portable cpus=1 sku=To be filled by O.E.M. uuid=44454C4C-4300-1046-8046-B3C04F515031
  *-core
       description: Motherboard
       product: Inspiron M5030
       vendor: Winbond Electronics
       physical id: 0
       version: A03
       serial: .3CFFQP1.CN70166139009D.
       slot: To Be Filled By O.E.M.
     *-cache:0
          description: L1 cache
          physical id: 5
          slot: L1-Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-back unified
     *-cache:1
          description: L2 cache
          physical id: 6
          slot: L2-Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: internal varies data
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron Technology
             physical id: 0
             serial: 3A592AA0
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT312S6BFR6C-H9
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 20130C01
             slot: DIMM_B
             size: 1GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: SODIMM [empty]
             physical id: 2
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A03
          date: 09/10/2010
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD V160 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2400MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc up nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=1 enabledcores=1
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: Dell
             vendor: Winbond Electronics
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:ff300000-ff4fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:11 memory:d0000000-dfffffff ioport:e000(size=256) memory:ff400000-ff40ffff memory:ff300000-ff3fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:ff600000-ff6fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: wlan0
                version: 01
                serial: 00:1b:b1:ab:68:3d
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.76 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:ff600000-ff60ffff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:ff500000-ff5fffff
           *-network
                description: Ethernet interface
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c1
                serial: 78:2b:cb:d1:dd:5e
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:ff500000-ff53ffff ioport:d000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:42 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=16) memory:ff709000-ff7093ff
           *-disk
                description: ATA Disk
                product: SAMSUNG HM321HI
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 2AJ1
                serial: S265JA0B164760
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000de1e6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 043a44f9-8e4f-46c8-99f8-8d094eebef38
                   size: 295GiB
                   capacity: 295GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-06-14 09:14:03 filesystem=ext4 lastmountpoint=/ modified=2011-06-14 09:30:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-06-14 09:37:03 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2811MiB
                   capacity: 2811MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2811MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff708000-ff708fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff707000-ff7070ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff706000-ff706fff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
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
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:ff700000-ff703fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
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
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:ff705000-ff705fff
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:ff704000-ff7040ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: DELL 4YRJH11
       vendor: Sanyo
       physical id: 1
       serial: 915
       slot: Sys. Battery Bay
       capacity: 45000mWh
       configuration: voltage=10.8V
```

I'm going to try the link you provided below about the graphics card now, thanks for the help

---

### Post by DanTheMan90 on 2011-06-14
Ok, I've tried the link you gave for the graphics, and it seems mine is compatible.

RS880                       RadeonHD 4100/4200/4290

Mine is the 4200, but I don't know how I would go about installing this 
and couldn't see anything pointing toward this in the link?
What would I do from here?

---

### Post by wildmanne39 on 2011-06-14
> **DanTheMan90 said:**
> Ok, I've tried the link you gave for the graphics, and it seems mine is compatible.

RS880                       RadeonHD 4100/4200/4290

Mine is the 4200, but I don't know how I would go about installing this 
and couldn't see anything pointing toward this in the link?
What would I do from here?
Hi, I went back to that page and you need to read it carefully everything is on that page or there is a link to it. The driver is installed by default, but it might take some adjustment and you need to follow the instructions for getting rid of the one you installed, look on the right side of the page it lists what is there. This is the link about how the driver is on by default and things you can do to make it work better, installing the other driver caused more problems hopefully you can just get rid of it and it will help. Also is your mouse a wireless mouse?
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by telliott on 2011-06-15
I have the same laptop and am having the same problem.  I'm wandering if I will be able to run Gnome3 with the proper graphics driver?  I played with Fedora 15 on my desktop and I really like Gnome3.  There are instructions on how to get Gnome3 on Ubuntu 11.4.

I'm wandering if it will be worth the trouble.  I had similar issues trying to get Fedora 15 on my laptop.  I had played with Unity but wasn't really happy with it.

Thanks,
Tim

---

