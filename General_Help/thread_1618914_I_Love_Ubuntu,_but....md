---
title: "I Love Ubuntu, but..."
date: 2010-11-11
forum: General Help
---

### Post by reklame on 2010-11-11
I really love ubuntu. I am almost 30 years old, and have just used Windows until now. I rellay don't want to go back to the crappy and slow virus Windos.

BUT, i have one problem. A huge problem! And without that solved, i can't use Ubuntu.

My grapics are way out. I cant use the HDMI output to my TV, and there are som issues with the nvidia. Its activated but not in use. I have read pages with threads to try to solve this problem, but i just cant handle it.

Can anyone PLEASE help me? Just tell me what to do!! I can post anything you ask me to.

---

### Post by DanaLou on 2010-11-11
Hmmm, I'm new myself to Ubuntu, but from what I've read I can offer an attempt at help;

Try System > Administration > Additional Drivers to see if you need to get Nvidia's proprietary graphics drivers.

</attempt>

---

### Post by reklame on 2010-11-11
> **DanaLou said:**
> Hmmm, I'm new myself to Ubuntu, but from what I've read I can offer an attempt at help;

Try System > Administration > Additional Drivers to see if you need to get Nvidia's proprietary graphics drivers.

</attempt>

Yes, i've tried that. And after trying to install the correct driver, the box is empty.

---

### Post by reklame on 2010-11-11
Here's some specs:

```
notebook-pc               
    description: Notebook
    product: Compaq Presario CQ60 Notebook PC
    vendor: Hewlett-Packard
    version: F.31
    serial: 2CE845594S
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=C9A69D00-B26A-11DD-A225-DAF5CAC7B991
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.47
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.31 (10/17/2008)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon Dual-Core QL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 950MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 1900MHz
          capacity: 1900MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:41 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8A2L-A
             vendor: Slimtype
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 7H63
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: WDC WD3200BEVT-6
             vendor: Western Digital
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 13.0
             serial: WD-WXE908RW0178
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00054e1e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 45316bfa-8bd6-4ed8-8d1e-380d5e66cffc
                size: 289GiB
                capacity: 289GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-11-08 12:56:11 filesystem=ext4 lastmountpoint=/&#65533;(&#1096;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;x]O&#65533;&#65533;l!&#65533;X&#65533;&#65533;&#65533;h]O&#65533;@&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;]O&#65533;yo!&#65533;&#65533;d modified=2010-11-10 20:32:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-11-11 12:42:42 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 8997MiB
                capacity: 8997MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8997MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:4e:d5:98
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4e:1f:a2:5f
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.2.22 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb


```

---

### Post by HermanAB on 2010-11-11
Howdy,

Instead of the buggy Nvidia driver you can use the Vesa driver and you can configure the external ports with xrandr.  Some googling and man paging will get you going.

Note that you can always run Windows XP or 2003 inside a virtual machine in Ubuntu.  I have a WinXP VM that I have used for years just to do my taxes. I now live in a tax free country, so no more QuickTax or WinXP needed, but I'll still keep the VM, in case I go back.

---

### Post by sohlinux on 2010-11-11
GeForce 8200M G [http://ubuntuforums.org/showthread.php?t=955092](http://ubuntuforums.org/showthread.php?t=955092)

---

### Post by reklame on 2010-11-11
> **sohlinux said:**
> GeForce 8200M G [http://ubuntuforums.org/showthread.php?t=955092](http://ubuntuforums.org/showthread.php?t=955092)

Belive me, i have tried everything in that thread. My problem goes beyond that, but i really dont know whats wrong.

When i go to the Nvidia control panel, i get this message:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server"

---

### Post by mastablasta on 2010-11-11
so what happened when you ran "nvidia-xconfig" as root?

---

### Post by Vigh on 2010-11-11
just use open source drivers, and up-date to 10.10 ubuntu which has superior graphics/HDMI etc. support to previous ubuntu versions, I have found in alot of cases that the proprietary graphics drivers are actually worse than the open-source at least in terms of usability, the proprietary drivers may be slightly faster, but for stability the open-source drivers are superior

regards

---

### Post by reklame on 2010-11-11
> **Vigh said:**
> just use open source drivers, and up-date to 10.10 ubuntu which has superior graphics/HDMI etc. support to previous ubuntu versions, I have found in alot of cases that the proprietary graphics drivers are actually worse than the open-source at least in terms of usability, the proprietary drivers may be slightly faster, but for stability the open-source drivers are superior

regards

Thank you Sir. I now have the right nVidia driver. 

But there is one problem. I can't get any sound when i run throug HDMI. I get the picture, but no sound... And sometimes, the movie starts, but the screen is all black and i hear sound from the PC and not TV...

---

### Post by Manyette on 2010-11-11
You should be able to redirect te sound to the TV by Preferences->Sound->Hardware/Output.

---

### Post by reklame on 2010-11-11
> **Manyette said:**
> You should be able to redirect te sound to the TV by Preferences->Sound->Hardware/Output.

Thank you. There is an option called (HDMI), but there's still no sound :-(

---

### Post by Manyette on 2010-11-11
You might find that the sequence of events is important.  TV manual might help here.  For example, in my case, the TV must be on first, before the HDMI output is enabled/pluged in.  Some TV's are a bit touchy on things like this.

---

### Post by axept on 2010-11-11
> **reklame said:**
> Thank you. There is an option called (HDMI), but there's still no sound :-(

Go to termianl, and run alsamixer (when you run a movie/music in the background), go to the right using your arrow-keys, to you find S/PDIF, and try to mute/unmute them, maybe one must be muted and one not, just try, and when you get sound, exit alsamixer (Esc) then run "sudo alsactl store"

This must you do after you have choosen the HDMI output option...

Worked for me...

---

### Post by reklame on 2010-11-12
> **axept said:**
> Go to termianl, and run alsamixer (when you run a movie/music in the background), go to the right using your arrow-keys, to you find S/PDIF, and try to mute/unmute them, maybe one must be muted and one not, just try, and when you get sound, exit alsamixer (Esc) then run "sudo alsactl store"

This must you do after you have choosen the HDMI output option...

Worked for me...

THANK YOU SO MUCH! I finally got it to work. The picture and the sound! There were some scaling problems, but perfect to watch movies.

Anyways, today when i tried it again, it didnt work. I don't have any clue of what i did yesterday, but today it wont work. No picture, no sound, so i guess i back to zero.

Isn there any easyer way to do this?

---

### Post by Aydos on 2010-11-12
I had a similar problem to yours before. I think I might can help. 

I was trying to use the speakers that are built into my desktop monitor that run through the HDMI on my gaming rig. 

I normally play with USB surround sound gaming headset, but I wanted to be able to unplug the headset and go to audio on the monitor when showing someone a you tube video or something.

What I had to do was go to [www.nvidia.com](www.nvidia.com) and download their official drivers for my card for Linux. I have not found an easy install method yet so you might want to do some research in google.

Basically the only way I have found is to download the drivers, save them to your desktop, purge the current drivers, make a blacklist to prevent the nouveau drivers from coming back, control + F2 to go to a console mode, change directory to the desktop and install the drivers from there.

Definitely Google for a guide, because you need the list of stuff to black list.

This is a pain and I hope someone could shed some light on an easier way, but it works. Some people are die hard on using the drivers you get from Ubuntu, but I play alot of current high end Windows games on my system via WINE so I have to use the latest NVIDIA drivers in some cases to get some functions to work.

I have tried this method on 2 video cards and both of them permanently have audio over HDMI afterwards. You still have to swap your sound device in the sound options, but if the HDMI audio is all you ever use then you only have to do it once.

I hope this helps.

Also, I hope someone tells me a better way to install the official drivers lol.

---

### Post by axept on 2010-11-12
> **reklame said:**
> THANK YOU SO MUCH! I finally got it to work. The picture and the sound! There were some scaling problems, but perfect to watch movies.

Anyways, today when i tried it again, it didnt work. I don't have any clue of what i did yesterday, but today it wont work. No picture, no sound, so i guess i back to zero.

Isn there any easyer way to do this?

Well, then I dont know. Its still working for me... Hope someone can help you out.
I've never got problem with the video over HDMI, only sound..

Btw, I did this on a ASRock 330HT-BD ION, with the additional drivers (Hm, right ? I've got it on norwegian) from Nvidia.

---

