---
title: "Ubuntu + Zacate = ???"
date: 2011-02-25
forum: General Help
---

### Post by demonic_bunny on 2011-02-25
So I was thinking of picking up a new 11.6" ultraportable that uses AMD's new Zacate APU architecture, most likely the Lenovo Thinkpad x120e. I know that AMD / Ati are less than awesome under Ubuntu, and this is a new chipset, so I was a little concerned about how compatible the system will be. My experience with Ubuntu troubleshooting still isn't the greatest, so I'd like to have as little headaches as possible.

Anyone have any experience using Ubuntu on any of these systems? How does it work?

Thanks.

---

### Post by landeel on 2011-02-28
BUMP! Just bought a Sony Vaio YB15 and wanted to know too.

---

### Post by Vaphell on 2011-02-28
[http://ubuntuforums.org/showthread.php?t=1641916](http://ubuntuforums.org/showthread.php?t=1641916)

it's about hp dm1z, can be done but tricky though the wifi appears to be the main source of problems (as usual). I'd wait for 11.04 to see if there will be more robust support for ontario/zacate. Of course you can give livecd/usb a spin to see what things look like first hand.

---

### Post by landeel on 2011-03-01
It will arrive in a few days.
As soon as it gets here, I will test 11.04 and post the results.

---

### Post by landeel on 2011-03-03
Tried to boot with Xubuntu Natty alpha.

Used usb-creator to transfer it to a usb disk.

After the splash, the wireless light turns on and all I get is this black screen. CRTL+ALT+F1-4 do not work. System seems frozen.

No success at all. :(

---

### Post by landeel on 2011-03-03
Sometimes it freezes on a black screen, sometimes it gives a seriously scrambled screen with white and black dots.

After several attempts I could get to desktop, but the desktop was cut in the half, and left side was in the right. Very strange!!!

Apart from that, hardware seems to work.

I could connect to wired ethernet, and wireless seems to work as I could see my neighbours' network.

Sound seems to work too, as sound channels appear in the mixer. Sadly I didn't have any sound files to play and confirm.

Well, something is obviously wrong with the default display driver that is loaded for this "GPU".

I will post a picture I took of the weird desktop problem.

If I get it to work again, I will post some lsusb, lspci, lshw for your pleasure. :)

---

### Post by ilembitov on 2011-03-03
> **landeel said:**
> Sometimes it freezes on a black screen, sometimes it gives a seriously scrambled screen with white and black dots.

After several attempts I could get to desktop, but the desktop was cut in the half, and left side was in the right. Very strange!!!

Apart from that, hardware seems to work.


I guess, the obvious reason is that the drivers that ship with 10.10 are just too old to support Fusion. I believe the drivers were updated in January.

Could you please try using 11.04?

Also it would be great if someone tried HD playback on 11.04. Including Flash.

---

### Post by landeel on 2011-03-03
Yeah, I'm trying Xubuntu Natty Alpha 2 (11.04)...

---

### Post by ilembitov on 2011-03-03
> **landeel said:**
> Yeah, I'm trying Xubuntu Natty Alpha 2 (11.04)...

OK... Could you please try OpenSuSE 11.4? I know, it's weird, but ATM it's more recent than Ubuntu 10.10 and close to stable (it's Release Candidate 2 right now).

---

### Post by landeel on 2011-03-03
Sorry, I have a very slow connection right now. Maybe next week.

---

### Post by landeel on 2011-03-03
This is what I see when I manage to get to desktop (lol).

After fighting with Windows 7 all day long I could finally partition my HD the way I wanted, without removing the thing.

I ran the xubuntu installer directly, instead of the live cd thing, and it worked. It probably uses a more simple video driver, like vesa.

Installing now... :)

I will post the results soon.
:popcorn:

---

### Post by landeel on 2011-03-03
hahaha amazing! After the installation it simply worked.

```
user@landeel-yb15:~$ sudo lshw
[sudo] password for user: 
landeel-yb15              
    description: Notebook
    product: VPCYB15AB
    vendor: Sony Corporation
    version: C9006XN4
    serial: 27539749-3002415
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=81606AF8-5D1D-E011-A673-F5AC8FE2F1DB
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: R0160Z7 (12/22/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb smartbattery biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 6
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM 1066 MHz (0.9 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: E1D516E7
             slot: SODIMM1
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM [empty]
             physical id: 1
             slot: SODIMM2
     *-cpu
          description: CPU
          product: AMD E-350 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: b
          bus info: cpu@0
          version: AMD E-350 Processor
          serial: N/A
          slot: N/A
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt npt lbrv svm_lock nrip_save pausefilter cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-display
             description: VGA compatible controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:42 memory:80000000-8fffffff ioport:3000(size=256) memory:90200000-9023ffff
        *-multimedia:0
             description: Audio device
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:90244000-90247fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:90100000-901fffff
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: c0
                serial: 78:84:3c:2b:87:2e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:44 memory:90100000-9013ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:90000000-900fffff
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 4c:0f:6e:d5:5c:92
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.38-1-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:90000000-9000ffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:19 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:9024c000-9024c3ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BEVT-5
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXL1E90EX319
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=3d4e4893
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: b04e-44fe
                   size: 9113MiB
                   capacity: 9115MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-03 20:32:46 filesystem=ntfs label=WinXP state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 36c2ed6c-b314-c645-a44d-3ec05e67821f
                   size: 19GiB
                   capacity: 20GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-01-15 15:54:38 filesystem=ntfs label=Win7 state=clean
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 390GiB
                   capabilities: primary
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 14GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /home
                      capacity: 14GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 3905MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:9024b000-9024bfff
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:9024a000-9024a0ff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:90249000-90249fff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:90248000-902480ff
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
        *-multimedia:1
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:90240000-90243fff
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
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: Family 12h/14h Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 12h/14h Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 12h/14h Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 12h/14h Processor Function 3
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 12h/14h Processor Function 4
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 12h/14h Processor Function 6
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 12h/14h Processor Function 5
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 12h/14h Processor Function 7
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:5
          logical name: scsi1
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@1:0.0.1
             logical name: /dev/sdc

```

All hardware seems to be working fine. I even have \dev\video0 for the webcam :)

For some reaason the screen is blinking, looks like it's out of sync.

I'll try to install catalyst drivers.

---

### Post by landeel on 2011-03-03
More info:

> user@landeel-yb15:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1512
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
user@landeel-yb15:~$ lsusb
Bus 004 Device 002: ID 0489:e00f Foxconn / Hon Hai 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:0186 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04f2:b211 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by hai2lp on 2011-03-04
Hi, i just bought this sony vaio vpc-yb15ag but i got trouble a lot , i use Linux Mint 10 (base on ubuntu 10.10) the Fn keyboard is not work properly , only sound  F3 and F4 working else not work like F5 / F6 for adjust brightness, and F7 for projector / or LCD switch

before the sound and touchpad also not working , after i googling and struggling i found the way to fixed it,

Please anyone who know to fixed the Fn keyboard function , that's should be the last problem

:D

---

### Post by landeel on 2011-03-04
Yeah, just noticed my Fn keys aren't working either...

Tried to install catalyst drivers 11.02 (fglrx) and can't get xserver to start. Had to go back to "ati" driver.

Isn't the e350 APU supposed to be supported already?
Is catalyst 11.02 incompatile with ubuntu 11.04?

---

### Post by landeel on 2011-03-04
Okay, I have uninstalled fglrx and I'm using "ati" driver now.
glxinfo reports Direct Rendering : Yes and many GLX extensions.
But except for glxgears, all OpenGL applications will freeze the system. Even OpenGL screensavers.
I think that's why the live CD was freezing, it seems to turn on the screensaver right after loading.
As I don't want to downgrade to Ubuntu 10.10, I think I'll have to wait for a catalyst driver that works on 11.04.

---

### Post by landeel on 2011-03-04
I had this Linux Mint 9 LXDE edition CD, so I have installed it to another partition.

It worked, I got wireless, the sound card appears in alsamixer, but I can't hear any sounds.

Then I have installed the catalyst 11.02 blob. Got fglrx, mode setting, but no OpenGL at all. Uninstalled it.
Did a apt-get install fglrx (older version), apt installed all the dependencies for me. Did a apt-get purge fglrx.

Used the catalyst blob to create packages for Ubuntu/lucid, wich Mint is based on (sudo sh blahblah.run --buildpkg Ubuntu/lucid). It installed a lot of other dependencies. Then installed all packages (sudo dpkg -i *deb).

Now I have full hardware acceleration and OpenGL, but no sound or touchpad. The battle continues...

---

### Post by landeel on 2011-03-04
This solved my problem with the touchpad:
[http://ubuntuforums.org/showthread.php?t=1565548]("http://ubuntuforums.org/showthread.php?t=1565548")

---

### Post by hai2lp on 2011-03-05
Guys i found the solve for sound problem by upgrading alsa-driver to 1.0.24

heres the link
[http://ubuntuforums.org/showthread.php?t=1681577]("http://ubuntuforums.org/showthread.php?t=1681577")
:P

---

### Post by landeel on 2011-03-09
Just upgrading to alsa 1.0.24 did not solve it for me.
After many many frustrating hours I could get it to work by installing the oss-compat package and creating a .asoundrc file.
I don't know wich one worked, but I'm not undoing it to discover.
Now I have a fully functional system to wait until fglrx works with natty. :)

---

### Post by link141 on 2011-03-10
Hello

You guys might want to check out [this thread](http://ubuntuforums.org/showthread.php?t=1699238&highlight=x120e) as the Thinkpad x120e uses the same APU.  Already there seem to be multiple people posting info about using Zacate on the x120e.

Cheers,
link141

---

### Post by landeel on 2011-03-11
Great machine so far. Loving it.

Only a few annoyances.

The down scroll of my touchpad scrolls down. The up scroll scrolls down really fast (argh!). This is already fixed in Natty.

To play hdmi sound I have to configure the application to output to it. It's a different sound card, with no mixers. Alsa won't accept it as default sound card, so unless the application let me configure the output device, I have no hdmi sound. There's a way to clone the audio output with .asoundrc but I couldn't do it.

fglrx still has a few annoying glitches, but in general it's clearly improving. Every single game I have tried worked, even the wine ones.
There's this annoying bug where, after opening the Catalyst control panel, the red box with the display number identification will display when a game changes the screen mode, and never go away.
I have some graphical glitches in nullDC.
I can't ALT+TAB out of World of Warcraft, and it runs pretty slower than on Windows (~30fps vs. ~50 fps). Wine games feel about 40% slower than running them on windows. As a side note, the open source drivers are 40% slower than fglrx... (ouch)
I hope both the open source and the proprietary drivers continue improving, so someday we will have stable and fast drivers.

---

### Post by hai2lp on 2011-03-13
Everything works fine using ubuntu 10.10 by upgrading kernel into 2.6.37-020637 which it's for Ubuntu 11.04 natty, 

The brightness adjustment works perferct (Fn+F5/F6) and by using latest alsa-driver 1.24 , audio problem also fixed, 

But i still have same problem same like landeel , if i play Dota Alt+Tab make the game dont work,

---

### Post by landeel on 2011-03-14
Got the open source drivers working today by updating to the latest kernel.
Sadly, they are EXTREMELY slow. Most of the games will just display garbage at 1-2 fps...

---

### Post by devguy on 2011-03-15
> **landeel said:**
> Got the open source drivers working today by updating to the latest kernel.
Sadly, they are EXTREMELY slow. Most of the games will just display garbage at 1-2 fps...

Wait for the official 2.6.38 kernel to appear in the Ubuntu PPA.  It has some AMD Fusion fixes in it.  It won't magically make things super fast, but it should be significantly better.

Hopefully Catalyst 11.3 will support both 2.6.38 final and the newer Xorg in Natty.

Edit: nvm, [looks like there's still issues.]("http://www.phoronix.com/scan.php?page=news_item&px=OTIxNw")

---

### Post by hai2lp on 2011-03-19
Yes I'm waiting for AMD catalyst 11.3 too

11.2 not supported for latest kernel

---

### Post by landeel on 2011-03-21
Forgot to mention another annoyance. If the machine boots to Windows 7, when it reboots to Linux I get no sound. No matter what I do with Alsa, restart, reset, force reload, it will be mute.
If I turn off and on the machine, or suspend and resume, sound will be back again.
I'm telling you, there's something evil about Windows 7. It's either setting a flag in the soundcard that doesn't get reset after a reboot, or uploading some crazy firmware that won't let alsa work.

EDIT: Here's my bug : [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/696139]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/696139")

---

### Post by hai2lp on 2011-03-21
> **landeel said:**
> Forgot to mention another annoyance. If the machine boots to Windows 7, when it reboots to Linux I get no sound. No matter what I do with Alsa, restart, reset, force reload, it will be mute.
If I turn off and on the machine, or suspend and resume, sound will be back again.
I'm telling you, there's something evil about Windows 7. It's either setting a flag in the soundcard that doesn't get reset after a reboot, or uploading some crazy firmware that won't let alsa work.

EDIT: Here's my bug : [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/696139]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/696139")

I dont see that kind problem

My sony vaio yb15ag works fine now .. using kernel 2.37

---

### Post by landeel on 2011-03-22
I'm using 2.6.32
I hope this issues will be solved when I upgrade to Natty.
Just waiting for Catalyst 11.03.

---

### Post by landeel on 2011-03-24
The open source video driver gave me a really bad experience yesterday.

I booted to Natty, did a apt-get upgrade, and left to do something else.
When I came back the screen was off because of the power manager.

I moved the mouse and the screen turned back on. The problem is that the screen started to blink a lot.

I have seen this behavior before, when I was testing the live CD. Just a reboot and the screen would go back to normal.

But this time it didn't. After a reboot, the GRUB screen was still blinking. Rebooted again, and still blinking. Booted to Mint with the fglrx driver and still blinking. Booted to Windows and still blinking. Tried messing with the bright adjust and still blinking.

Closing and opening the lid didn't work. Suspend didn't work. Turning off and on the computer didn't work either. I got really worried. I though it was time to activate my warranty.

Well, luckily when I turned it on today, the screen was back to normal.

---

### Post by landeel on 2011-04-01
Sadly catalyst 11.3 doesn't work with natty.

Installed the pre-release version of fglrx from apt, and it worked. So now I have everything working in Natty, including 3d. Still I think fglrx is much slower than the windows driver.

Installed lxde to have a lighter and faster environment. Also, I have removed pulseaudio because it made games so much slower, and sound was clicking and popping a lot. Honestly, I fail to see any advantage in using pulseaudio.

The only serious annoyances left I can remember right now are:

1) Sometimes the integrated bluetooth adapter will randomly disappear.

dmesg just tells "usb 4-4: USB disconnect, address 2". It didn't happen in Lucid / Mint, or Windows.

2) Applications won't play any sounds when a flash applet is playing. It's not firefox' fault because if I play movies with html5, sound from other sources will work as expected.

---

### Post by landeel on 2011-04-04
Okay, I have solved the sound issue.

1) I have added "options snd_hda_intel index=1" to the bottom of my "/etc/modprobe.d/alsa-base.conf".

2) Removed ~/.asoundrc and /etc/asound.conf, and rebooted.

Now the ALC269VB is card 0 and HDA ATI SB (HDMI) is card 1.

All programs can play sound simultaneously, even flash.

As a bonus, for some reason, it made games a bit faster too. I got +2-3 FPS in World of Warcraft (yay!!!!).

---

### Post by landeel on 2011-04-04
Here's a picture of my desktop.

[[IMG]http://img4.imageshack.us/img4/8190/sonyvaioyb15ubuntunatty.th.png[/IMG]](http://img4.imageshack.us/i/sonyvaioyb15ubuntunatty.png/)

LXDE is the window manager, wbar in the top, conky in the right, lxpanel in the bottom.

Also added tilda for a quake-style terminal, parcellite to handle the clipboard and the power manager from xfce.

Installed nm-applet, but I could not get it to show its icon in lxde.

My beautiful wife and our beautiful daughter in the background. :)

---

### Post by Krautmaster on 2011-04-14
in My MSI E350 ubuntu 10.10 with catalyst 11.3 and newest libva + xvba libs runs fine with vaapi enabled in XBMC and full HD support.

The post above fixed my soundproblem too ;)

---

### Post by landeel on 2011-04-17
After an upgrade, it seems the bluetooth issue is gone for good.

Also, I have found a wine tweak for the AMD / ATI / FGLRX / Catalyst creature that improves game performance a lot:

> 
Registry Tweak for FPS Boost

Open a terminal window, (konsole/terminal/x terminal etc..), type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

1. Find HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by left clicking on it. The icon should change to an open folder.
3. Click right on the wine folder and select [NEW] then [KEY].
4. Replace the text "New Key #1" with OpenGL (CaSe Sensitive).
5. Right click in the right hand pane and select [NEW] then [String Value].
6. Replace "New Value #1" with "DisabledExtensions" (CaSe sensitive).
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type "GL_ARB_vertex_buffer_object;GL_ARB_vertex_program" (without the quotes).



Also, winetricks can be used to disable GLSL, which is kinda problematic with fglrx.

Windows OpenGL games on wine are giving me very close to native performance after this tweaks.

---

