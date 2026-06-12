---
title: "HDMI audio not working, I mean video, I mean audio..."
date: 2012-06-15
forum: General Help
---

### Post by seanc712 on 2012-06-15
** Warning: Noob posting **


So I currently use a 32" 1920x1080 television connected to my HP G62 Laptop via hdmi as my main display. After a fresh install of ubuntu 12.04 the video looks fine, but there is no hdmi audio. Also if I try to play a file in movieplayer or a flash video in youtube with [HDMI/DisplayPort (RS880 HDMI Audio {Radeon HD 4200 Series})] selected under sound settings it plays super fast (Again, without audio). Oddly enough this doesn't happen in VLC; It plays at normal speed, just without audio.

I tried the proprietary drivers, which fixed the audio but completely eliminated my computers ability to fit the display properly to the television. I then tried adding Radeon.audio=1 as a boot option in grub, and once again it fixed the hdmi audio but completely screwed up the video. Also I saw somewhere to check in alsa in case it is muted: this does not appear to be the case.

So what's the verdict? Do I have to chose between good hdmi video and working hdmi sound or can I have both?

I'll be far away from an internet connection for the next several days, I just thought I'd post this now and come back then after people have had time to reply. Thanks for reading!

:mrgreen:

---

### Post by imachavel on 2012-06-15
I'd imagine it'd be a driver issue. You said your sound works fine with vlc, which also uses a ton of plug ins as well. Then when you said you go to proprietary drivers, you said the sound works but screen format doesn't.

I'd check for necessary codecs as well. But you said one driver disables another, and vice versa. This sounds so much more like a windows issue then anything else, windows does that, one driver disables another one.

Do me a favor, go to the terminal and first type:

lspci

and then

lshw

first, sudo -i into the terminal, and yes you'll need a password. Post the output of lspci and lshw into this thread. When you are done, also try

sudo apt-get install update

and then

sudo apt-get install upgrade

Now that if this fixes nothing, I'd check all codecs, and try updating them, as well as all plug ins, and try updating them as well. But really sudo update should update everything. Now.....

I would definitely look into advanced drivers and plug ins. Think about it, windows uses direct x, so video and audio usually fail together, codec wise, since direct x should support both video and audio format. Otherwise it's a driver issue. Since Ubuntu I believe still uses opengl, I believe the audio and video codecs are supported separately. I'd try to trouble shoot the audio and video drivers and codecs, try using each as a variable. Sounds like you just need the right set of drivers and codecs together. Google your set up, your hdmi, your graphics card, audio card, supported drivers and codecs for linux to work with hdmi for a t.v. set up, see if you can get an answer. This is my best advice

---

### Post by GuiGuy on 2012-06-15
I don't know if [this]("http://ubuntuforums.org/showpost.php?p=11966245&postcount=97") will help...

---

### Post by seanc712 on 2012-06-19
> **imachavel said:**
> I'd imagine it'd be a driver issue. You said your sound works fine with vlc, which also uses a ton of plug ins as well. Then when you said you go to proprietary drivers, you said the sound works but screen format doesn't.

I'd check for necessary codecs as well. But you said one driver disables another, and vice versa. This sounds so much more like a windows issue then anything else, windows does that, one driver disables another one.

Do me a favor, go to the terminal and first type:

lspci

and then

lshw

first, sudo -i into the terminal, and yes you'll need a password. Post the output of lspci and lshw into this thread. When you are done, also try

sudo apt-get install update

and then

sudo apt-get install upgrade

Now that if this fixes nothing, I'd check all codecs, and try updating them, as well as all plug ins, and try updating them as well. But really sudo update should update everything. Now.....

I would definitely look into advanced drivers and plug ins. Think about it, windows uses direct x, so video and audio usually fail together, codec wise, since direct x should support both video and audio format. Otherwise it's a driver issue. Since Ubuntu I believe still uses opengl, I believe the audio and video codecs are supported separately. I'd try to trouble shoot the audio and video drivers and codecs, try using each as a variable. Sounds like you just need the right set of drivers and codecs together. Google your set up, your hdmi, your graphics card, audio card, supported drivers and codecs for linux to work with hdmi for a t.v. set up, see if you can get an answer. This is my best advice

to clarify, sound does NOT work in vlc, but video does not play at an accelerated rate like it does in everything else.

As for the other info:

```
root@sean-HP-G62-Notebook-PC:~# lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

and

```
root@sean-HP-G62-Notebook-PC:~# lshw
PCI (sysfs)  

sean-hp-g62-notebook-pc   
    description: Notebook
    product: HP G62 Notebook PC (XH058UA#ABA)
    vendor: Hewlett-Packard
    version: 0592110003242710010020100
    serial: CNF0423SQ8
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV sku=XH058UA#ABA uuid=8950A7A6-FB7E-194B-9F7D-1BF3FC5115A9
  *-core
       description: Motherboard
       product: 1444
       vendor: Hewlett-Packard
       physical id: 0
       version: 69.25
       serial: P X210 01 1Z ZL JOU
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.16
          date: 09/15/2010
          size: 1MiB
          capacity: 1984KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II P320 Dual-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: c
          bus info: cpu@0
          version: AMD Athlon(tm) II P320 Dual-Core Processor
          serial: NotSupport
          slot: Socket S1G4
          size: 800MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: d
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: M471B5673FH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 61DC6BF9
             slot: Bottom - Slot 1 (top)
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1066 MHz (0.9 ns)
             product: HMT112S6BFR6C-H9
             vendor: Hynix
             physical id: 1
             serial: 0862EA5C
             slot: Bottom - Slot 2 (under)
             size: 1GiB
             width: 16 bits
             clock: 1066MHz (0.9ns)
     *-generic UNCLAIMED
          description: Non-VGA unclassified device
          product: Gammagraphx, Inc. (or missing ID)
          vendor: Gammagraphx, Inc. (or missing ID)
          physical id: 2
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: RS780/RS880 PCI to PCI bridge (int gfx)
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht normal_decode bus_master cap_list
          resources: ioport:3000(size=4096) memory:d0200000-d03fffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: RS880M [Mobility Radeon HD 4200 Series]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:18 memory:c0000000-cfffffff ioport:3000(size=256) memory:d0300000-d030ffff memory:d0200000-d02fffff
        *-multimedia
             description: Audio device
             product: RS880 HDMI Audio [Radeon HD 4200 Series]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5.1
             bus info: pci@0000:01:05.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:19 memory:d0310000-d0313fff
     *-pci:1
          description: PCI bridge
          product: RS780/RS880 PCI to PCI bridge (PCIE port 1)
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 5
          bus info: pci@0000:00:05.0
          version: 00
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:d0100000-d01fffff
        *-network DISABLED
             description: Wireless interface
             product: AR9285 Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:02:00.0
             logical name: wlan0
             version: 01
             serial: 4c:0f:6e:01:e2:9a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath9k driverversion=3.2.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
             resources: irq:17 memory:d0100000-d010ffff
     *-pci:2
          description: PCI bridge
          product: RS780 PCI to PCI bridge (PCIE port 2)
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 6
          bus info: pci@0000:00:06.0
          version: 00
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:2000(size=4096) memory:d0500000-d05fffff ioport:d0000000(size=1048576)
        *-network
             description: Ethernet interface
             product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth0
             version: 02
             serial: 64:31:50:5e:7c:b6
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
             resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff
     *-storage
          description: SATA controller
          product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 11
          bus info: pci@0000:00:11.0
          logical name: scsi0
          logical name: scsi1
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: storage ahci_1.0 bus_master cap_list emulated
          configuration: driver=ahci latency=64
          resources: irq:19 ioport:4038(size=8) ioport:404c(size=4) ioport:4030(size=8) ioport:4048(size=4) ioport:4010(size=16) memory:d0408000-d04083ff
        *-disk
             description: ATA Disk
             product: WDC WD3200BEVT-6
             vendor: Western Digital
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WX51A7049863
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00062c23
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 6d859d32-b0ae-46c7-8a88-9efb3e2256ab
                size: 295GiB
                capacity: 295GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-14 16:46:03 filesystem=ext4 lastmountpoint=/ modified=2012-06-14 17:05:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-06-19 16:28:42 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2810MiB
                capacity: 2810MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2810MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633N
             vendor: hp
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 0300
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-usb:0
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 12
          bus info: pci@0000:00:12.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master
          configuration: driver=ohci_hcd latency=64
          resources: irq:18 memory:d0407000-d0407fff
     *-usb:1
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 12.2
          bus info: pci@0000:00:12.2
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pm debug ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=64
          resources: irq:17 memory:d0408600-d04086ff
     *-usb:2
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 13
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master
          configuration: driver=ohci_hcd latency=64
          resources: irq:18 memory:d0406000-d0406fff
     *-usb:3
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 13.2
          bus info: pci@0000:00:13.2
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pm debug ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=64
          resources: irq:17 memory:d0408500-d04085ff
     *-serial UNCLAIMED
          description: SMBus
          product: SBx00 SMBus Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 14
          bus info: pci@0000:00:14.0
          version: 42
          width: 32 bits
          clock: 66MHz
          configuration: latency=0
     *-multimedia
          description: Audio device
          product: SBx00 Azalia (Intel HDA)
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 14.2
          bus info: pci@0000:00:14.2
          version: 40
          width: 64 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list
          configuration: driver=snd_hda_intel latency=64
          resources: irq:16 memory:d0400000-d0403fff
     *-isa
          description: ISA bridge
          product: SB7x0/SB8x0/SB9x0 LPC host controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
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
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 14.4
          bus info: pci@0000:00:14.4
          version: 40
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
     *-usb:4
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 14.5
          bus info: pci@0000:00:14.5
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master
          configuration: driver=ohci_hcd latency=64
          resources: irq:18 memory:d0405000-d0405fff
     *-usb:5
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 16
          bus info: pci@0000:00:16.0
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master
          configuration: driver=ohci_hcd latency=64
          resources: irq:18 memory:d0404000-d0404fff
     *-usb:6
          description: USB controller
          product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 16.2
          bus info: pci@0000:00:16.2
          version: 00
          width: 32 bits
          clock: 66MHz
          capabilities: pm debug ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=64
          resources: irq:17 memory:d0408400-d04084ff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-battery
       product: MU06047
       vendor: Conexant (Rockwell)
       physical id: 1
       version: Unknown
       serial: Unknown
       slot: Primary
       capacity: 4400mWh
       configuration: voltage=10.8V
```

as for update and upgrade...i could swear i've tried these before, and it installed but didnt fix the problem. this time when i try it says unable to locate packages.

thanks for the help! hopefully i can get to the bottom of this...

---

### Post by seanc712 on 2012-06-20
i hope bumping isnt considered bad form.


still no hdmi sound without proprietary driver, which doesnt size right (unlike ubuntus preinstalled one)

---

### Post by willis11of12 on 2012-06-21
I believe with three of the HD TVs that I have connected my computer to, they have required me to either use my own separate speakers, or use a separate audio cable along with the HDMI cable, as the sound never comes through the HDMI cable on my TVs for the computer.  I don't know why, I just know that my TV says that when connecting the computer, that I have to use the audio out plug (or headphone jack) on the computer to plug into the audio in on the TV along with the HDMI (or I use a VGA/SVGA cable).

I hope that helps!

---

### Post by Gyokuro on 2012-06-21
> **seanc712 said:**
> ** Warning: Noob posting **


So I currently use a 32" 1920x1080 television connected to my HP G62 Laptop via hdmi as my main display. After a fresh install of ubuntu 12.04 the video looks fine, but there is no hdmi audio. Also if I try to play a file in movieplayer or a flash video in youtube with [HDMI/DisplayPort (RS880 HDMI Audio {Radeon HD 4200 Series})] selected under sound settings it plays super fast (Again, without audio). Oddly enough this doesn't happen in VLC; It plays at normal speed, just without audio.

I tried the proprietary drivers, which fixed the audio but completely eliminated my computers ability to fit the display properly to the television. I then tried adding Radeon.audio=1 as a boot option in grub, and once again it fixed the hdmi audio but completely screwed up the video. Also I saw somewhere to check in alsa in case it is muted: this does not appear to be the case.

So what's the verdict? Do I have to chose between good hdmi video and working hdmi sound or can I have both?

I'll be far away from an internet connection for the next several days, I just thought I'd post this now and come back then after people have had time to reply. Thanks for reading!

:mrgreen:

Hi

What you have discovered is at the moment the standard behaviour - HDMI video is enabled but HDMI audio disabled as otherwise it will cause black screens. NVidia with NVidia driver works, Radeon works (but it depends on the card). Here a link: [http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/](http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/)

Sorry for no better answer but it will take some time to get sound via hdmi. Maybe you can try a daily QQ disk.

---

### Post by seanc712 on 2012-06-21
> **Gyokuro said:**
> Hi

What you have discovered is at the moment the standard behaviour - HDMI video is enabled but HDMI audio disabled as otherwise it will cause black screens. NVidia with NVidia driver works, Radeon works (but it depends on the card). Here a link: [http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/](http://voices.canonical.com/david.henningsson/2012/04/14/audio-over-hdmi-and-displayport-in-ubuntu-12-04/)

Sorry for no better answer but it will take some time to get sound via hdmi. Maybe you can try a daily QQ disk.


thanks for the response! at least now i can stop trying.


looks like i'm switching back to windows 7 as this really is a dealbreaker with my current setup :(

o well, i'll give it another 6 months then see if a linux distro is right for me

---

### Post by jmfal on 2012-06-21
click on the speaker icon (top right in toolbar)

click settings ,  there should be a option for HDMI audio, if your sound card has HDMI capabilities.

---

