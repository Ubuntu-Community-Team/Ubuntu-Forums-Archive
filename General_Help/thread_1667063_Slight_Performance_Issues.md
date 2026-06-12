---
title: "Slight Performance Issues"
date: 2011-01-14
forum: General Help
---

### Post by minigilani on 2011-01-14
Hello :D

I'm running Kubuntu 10.10 and i'm having a few performance related issues. Firstly, animated minimising of windows takes **ages**. So i turned it off, and flash would freeze and stutter VERY badly, so i disabled hardware acceleration. All this improved performance significantly, but i still feel there's a major lack in performance when i compare it with Windoze. I tried playing an mpeg file in VLC, and it stuttered BADLY, and the same file runs extremely smooth on the same computer with Windows, same thing with the flash. And although the Kubuntu interface is beautiful (especially with all the eye-candy i tried to plug in), it feel feels... well, slow at times.
Am i missing drivers or something, even though i believe i've got all the drivers on, perfectly.

I'm running a [DELL Optiplex GX260]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&osl=en&SystemID=PLX_PNT_P4_GX260&os=WW1"), manuals are [here]("http://support.dell.com/support/edocs/systems/opgx260/en/index.htm"). I have two 512 MB sticks of RAM, and a 80 GB internal HDD, and a 320 GB external HDD, and a GeForce4 MX440 GPU.

I'm still a bit of a newb, but here's the lshw:
```
GumballMachine
    description: Mini Tower Computer
    product: OptiPlex GX260
    vendor: Dell Computer Corporation
    serial: BCPG71S
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=mini-tower cpus=1 power-on_password=disabled uuid=44454C4C-4300-1050-8047-C2C04F373153
  *-core
       description: Motherboard
       product: 00T606
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..CN698612CJ2251.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A09 (11/01/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.06GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 3066MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-e7ffffff
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:fc000000-fdffffff memory:e8000000-f7ffffff
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 440]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master vga_palette cap_list rom
                configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
                resources: irq:16 memory:fc000000-fcffffff memory:f0000000-f7ffffff memory:eff80000-efffffff memory:e8000000-e801ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe300800-fe300bff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:fe100000-fe2fffff
           *-network
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:02:0c.0
                logical name: eth0
                version: 02
                serial: 00:08:74:ce:58:4f
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k6-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100MB/s
                resources: irq:18 memory:fe1e0000-fe1fffff ioport:ecc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: 4JV5JVG2
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=01400140
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e153a16a-c797-4fa7-b219-5f3273dc080e
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-01-06 15:11:17 filesystem=ext4 lastmountpoint=/ï¿œ[ï¿œï¿œ(^ï¿œï¿œï¿œï¿œï¿œP~ï¿œï¿œDq!ï¿œ(^ï¿œï¿œ@~ï¿œï¿œï¿œïï¿œï¿œï¿œï¿œï¿œï¿œïï¿œï¿œï¿œï¿œh~ï¿œï¿œï¿œs!ï¿œ j modified=2011-01-12 20:20:25 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-01-14 22:20:31 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4882MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: W95 FAT32 partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 36GiB
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 19GiB
                   capabilities: primary
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-W54E
                vendor: TEAC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.1B
                serial: [TEAC    CD-W54E         1.1B
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dc80(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:d800(size=256) ioport:dc40(size=64) memory:fe300400-fe3005ff memory:fe300000-fe3000ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Here's a few screens, because i love showing off my desktop. It would be nothing without my wallpaper collection, though :P :
[IMG]http://farm6.static.flickr.com/5285/5355116134_0473ce52d3_b.jpg[/IMG]
[IMG]http://farm6.static.flickr.com/5082/5355117590_9f043238e5_b.jpg[/IMG]
[IMG]http://farm6.static.flickr.com/5081/5355118622_5ac211546f_b.jpg[/IMG]


Thanks in advance :)

---

### Post by TeoBigusGeekus on 2011-01-14
A pentium 4 with 1gb of ram cannot handle KDE.
I have a p4 with 1gb of ram and an ancient geforce 6600 gt and KDE almost fried my motherboard once.
With these specs, I find even gnome slow, so I switched to openbox.
You should consider switching to ubuntu (or even better to lubuntu); alternatively, buy a new pc :P

---

### Post by Zorael on 2011-01-14
This is probably due to the open source nouveau Nvidia drivers being slow. Consider trying the proprietary ones.

Nouveau is still very much a work in progress, and I was happy to see that it finally even had 3D acceleration for my laptop with its Nvidia card.

The Additional Drivers utility under Applications -> System -> should hopefully help you install them. Otherwise, the package name is [**nvidia-current**](apt://nvidia-current).

---

### Post by minigilani on 2011-01-15
> 
The Additional Drivers utility under Applications -> System -> should hopefully help you install them.


hahaha, thanks Zorael, but i'm not that big a newb anymore :P, i can use the CLI to an extent.

I ran into a problem, though, i installed nvidia-current, and i ran the following:

```
sudo nvidia-xconfig
```


Then i rebooted to a broken X server. I tried restoring from the backup, but that didn't work. So i installed lynx, and googled the forums, found a post on how to generate an xorg.conf in my home directory (if memory serves, i think it was a post by you), and tried to make a new one... that didn't work either.
So i removed the nvidia stuff, generated a new one, copied the config file, and finally logged into X. Ironically this thread was the first thing i found :P
I did, however make a backup of the broken X:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Help? :(

**Update:** Upon reboot, the CLI was happily waiting for me again, and attempting to start X give me an error, again. So i Lynxed to Google, and searched the forums to find out that X didn't need an xorg.conf, it only used it if it were present. So i 'mv'-ed "xorg.conf" to "xorg.conf.i.screwed.the.system" and voila. X starts up again at reboot :D

---

### Post by cascade9 on 2011-01-15
> **TeoBigusGeekus said:**
> A pentium 4 with 1gb of ram cannot handle KDE.
I have a p4 with 1gb of ram and an ancient geforce 6600 gt and KDE almost fried my motherboard once.
With these specs, I find even gnome slow, so I switched to openbox.
You should consider switching to ubuntu (or even better to lubuntu); alternatively, buy a new pc :P

Ummm, yeah. 

I've run KDE 4.X on lots of computers, some of them with lower hardware specifications than that. KDE 4.X will not 'fry your motherboard' unless you've already got heat and airflow issues.... 

@minigilani- IMO the GF4 MX series is just not powerful enough for KDE4.X. I had issues on systems with a GF4MX440 (AMD 2100+ 768MB, Celeron 2.4GHz 768MB, P4 2.53 1GB), but the same systems would run much better with a GF6600GT. Still not as well as I would like, but much much smoother and faster than with the GF4MX440. 

If you really want to run KDE 4.X, consider a minimal install + kde-full. Or a new video card (good luck finding a decent AGP 6XXX or 7XXX nvidia card), or maybe try a different disto. ;)

*edit- nvidia-current is for newer cards than the GF4MX440. They use the 96.xx drivers.

---

### Post by minigilani on 2011-01-15
> **cascade9 said:**
> If you really want to run KDE 4.X, consider a minimal install + kde-full. Or a new video card (good luck finding a decent AGP 6XXX or 7XXX nvidia card), or maybe try a different disto. ;)

But *buntu's the only linux distro i've ever fully installed on HD, i don't have any **long-term** experience with any other distro... and until i've mastered it to the core, i don't really want to change :(
And i don't want to leave KDE because i've gotten used to the power. Gnome is fun and all, but i prefer the feel of KDE.. besides, it's Oh, so sexier :cool:

> nvidia-current is for newer cards than the GF4MX440. They use the 96.xx drivers.

Bla, this X server business is just not in my intellectual reach yet, i'll read up on how to mess around with X before i do this :D .. i don't know the first thing about GPU's, let alone what the 96.xx drivers are. Until then, i'll just make do with what i have.

I'm thinking about buying a new laptop, and considering that you've got so much hardware experience, cascade9, any personal favorites when it comes to KDE?

By, the way, i ran into more trouble, but i fixed it, i'll just post it as an update in my last post, instead of typing it here, it's sorta connected to that post, anyways.

---

### Post by cascade9 on 2011-01-15
> **minigilani said:**
> But *buntu's the only linux distro i've ever fully installed on HD, i don't have any **long-term** experience with any other distro... and until i've mastered it to the core, i don't really want to change :(
And i don't want to leave KDE because i've gotten used to the power. Gnome is fun and all, but i prefer the feel of KDE.. besides, it's Oh, so sexier :cool: 

Fair enough. In that case, I'd try a minimal install. Maybe not now, but at some point. BTW, 'minimal install' is just installing only vital programs/apps, you end up with just the command line. Then you add whatever you want as for DE (desktop enviroment)- you could install gnome, KDE, lxde, Xfce and others. 

> **minigilani said:**
> Bla, this X server business is just not in my intellectual reach yet, i'll read up on how to mess around with X before i do this :D .. i don't know the first thing about GPU's, let alone what the 96.xx drivers are. Until then, i'll just make do with what i have. 

nVidia makes different drivers for different cards. Very old cards, up to the original geforce- 71.xx. Geforce 2 to geforce 4- 96.xx. Geforce FX (geforce 5)- 173.xx. All newer cards use 'nvidia-current' (which also has a number, last release is 260.xx) 

> **minigilani said:**
> I'm thinking about buying a new laptop, and considering that you've got so much hardware experience, cascade9, any personal favorites when it comes to KDE?

By, the way, i ran into more trouble, but i fixed it, i'll just post it as an update in my last post, instead of typing it here, it's sorta connected to that post, anyways.

As far as laptops go, I'm actually not that up on things. All I can say is avoid nvidia optimus (optimus has no linux support) and switchable graphics can be dodgy as well. 

I'll probably have to explain that better later, unless some other kind soul does before I come back.

---

### Post by minigilani on 2011-01-15
> **cascade9 said:**
> Fair enough. In that case, I'd try a minimal install.

But won't: **Minimal Install** + **KDE 4.X** = **Exactly Where I Am Right Now**? I always thought the Kubuntu ISO was the minimal install with KDE strapped on.

> **cascade9 said:**
> BTW, 'minimal install' is just installing only vital programs/apps, you end up with just the command line. Then you add whatever you want as for DE (desktop enviroment)- you could install gnome, KDE, lxde, Xfce and others.

Hahaha, yes, i know what a Minimal Install is, i remember the times when Windoze would just randomly stop browsing the internet (probably a virus issue), and i'd quickly fix myself up with the Minimal Install ISO on VirtualBox. Then i'd install Fluxbox and Firefox to serve me some WWW with a slice of lemon. :D

---

### Post by cascade9 on 2011-01-16
> **minigilani said:**
> But won't: **Minimal Install** + **KDE 4.X** = **Exactly Where I Am Right Now**? I always thought the Kubuntu ISO was the minimal install with KDE strapped on.

Not even close, kubuntu has a absolute ton of packages that is not in a minimal install + kde-full-  

[http://packages.ubuntu.com/maverick/kde-full](http://packages.ubuntu.com/maverick/kde-full)

[http://packages.ubuntu.com/maverick/kubuntu-desktop](http://packages.ubuntu.com/maverick/kubuntu-desktop)

---

### Post by jig36 on 2011-01-19
I have a dell optiplex that has the Ati x1100 chipset and the flash is alittle laggy at times but works. i have a Amd X2 that still runs on the DDR400 and 1Gb of ram and Geforece MX440 SE with ubuntu 10.10 Gnome desktop and i haven't seen an issue with speed flash runs amazingly well and mpgs run well music runs well load time take about 1min but thats cause i run a dual boot because there are apps i just cant loose

---

### Post by minigilani on 2011-09-04
I completely forgot about this thread!

As an update, i have now officially given up on this computer, i believe there's something really wrong with it, i just don't know what. I switched back to XP because i decided dual-booting was too much of a hassle for it to cope it, and now it can't even run XP right. I took it all apart, checked and cleaned the entire box, i even pried the CPU off and inspected each pin for bends, all i ended up with was somehow magically breaking one of the RAM slots. Now i'm down to half a gig, and there's no improvement.

I'll just mark this thread as solved, because the problem lies with my computer. Thanks to everyone for their help.

---

