---
title: "No sound !!!!!!!!!"
date: 2012-05-06
forum: General Help
---

### Post by jlanier3300 on 2012-05-06
This is my first time with Linux. First time I've built a pc. It was a hand me down minus a HD. Started fresh with a wiped 120 gig and fresh install of Kubuntu 12.04. I must say It looks great. I have never had anything other than windows XP my whole life so it was nice to have something new... but now I'm very confused I have no sound through HDMI at all but video works great. The drivers are in place and its selected as the source and all that jazz I'm new to this but it seems to be in working order I've read some threads on this and did everything but nothing works. Analog sound doesn't work either but whats even weirder is analog will work in photon test but that's it. one guy I talked to said he had similar problems and could never get HDMI sound so out of frustration put windows 7 on it and it worked fine. he also said to try regular ubuntu and other distros on a live cd and see if they work.I tryed ubuntu on cd and get analog sound but still no HDMI.... PLEASE HELP... I really don't want go back to windows

---

### Post by Zvlwab on 2012-05-07
```
sudo apt-get install pavucontrol
pavucontrol
```

There you can set which applications should which audio port, which audio channels should be used, etc.

If you're using a DVI-HDMI converter, keep in mind that only newer DVI models support sound.

---

### Post by jlanier3300 on 2012-05-07
It worked first try it was muted...BUT only the one time tried again after a bunch of restarts and nothing no sound but its still unmuted I'm at a loss for words.. in photon it says my graphics card has been removed but it has always said that and it still has video coming out

---

### Post by mastablasta on 2012-05-08
before you start typing commands and installing osme stuff .... you need to tell us what kind of graphics card you have, what kind of sound card you have and also exactly which graphics drivers you have installed.
 
to get a list of hardware oyu can do this in konsole:
lshw
 
you can then mark the output text, copy and paste it here (use code tags=# icon  so it's more readable).
 
also are you saying it worked once but not again / i.e. after restart?
 
Kubuntu also has a nice system logs applicaiton. might be worth checking the boot log to see if there are any errors regarding sound/video card reported there.

---

### Post by jlanier3300 on 2012-05-08
jlanier3300@jlanier3300-Aspire-T180:~$ sudo lshw
[sudo] password for jlanier3300: 
jlanier3300-aspire-t180   
    description: Desktop Computer
    product: Aspire T180
    vendor: Acer
    version: R01-B4
    serial: PTS560X078725125B82704
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00192116-A04A-2007-0621-230139000000
  *-core
       description: Motherboard
       product: EM61SM/EM61PM
       vendor: Acer
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: R01-B4
          date: 04/27/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: d
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: f
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 7
          bus info: cpu@1
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          clock: 201MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: e
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 10
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 1GiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:c000(size=4096) memory:fdf00000-fdffffff memory:fde00000-fdefffff
        *-communication UNCLAIMED
             description: Modem
             product: SM56 Data Fax Modem
             vendor: Motorola
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0 maxlatency=62 mingnt=1
             resources: memory:fdfff000-fdffffff ioport:cc00(size=256)
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:fdffe000-fdffe7ff memory:fdff8000-fdffbfff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD writer
             product: DVD RW AW-Q170A
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.73
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: Maxtor 6Y120M0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: YAR5
             serial: Y3PLH6ZE
             size: 114GiB (122GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ae6b8
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: c49dc2d1-744a-4f8c-b48e-d00d21d62fa2
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-05-05 20:36:05 filesystem=ext4 lastmountpoint=/ modified=2012-05-05 20:56:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-05-08 17:14:07 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                size: 3069MiB
                capacity: 3069MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3069MiB
                   capabilities: nofs
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:b000(size=4096) memory:fb000000-fcffffff ioport:d0000000(size=536870912)
        *-display
             description: VGA compatible controller
             product: GT218 [GeForce 210]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:fb000000-fbffffff memory:d0000000-dfffffff memory:ee000000-efffffff ioport:bc00(size=128) memory:e0000000-e007ffff
        *-multimedia
             description: Audio device
             product: High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:fcffc000-fcffffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:a000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
        *-network
             description: Ethernet interface
             product: 88E8056 PCI-E Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth0
             version: 12
             serial: 00:19:21:16:a0:4a
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.1.133 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:43 memory:fddfc000-fddfffff ioport:ac00(size=256) memory:fdc00000-fdc1ffff
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:9000(size=4096) memory:fdb00000-fdbfffff ioport:fda00000(size=1048576)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: d
          bus info: usb@2:8
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
jlanier3300@jlanier3300-Aspire-T180:~$ 


does this help?  and yes it only worked once after i unmuted it with pavucontrol but now its back to the same old

---

### Post by scottbomb on 2012-05-08
I don't know about anyone else, but I could only get my sound to work (I have radios feeding Line In and Mic) was to go to a terminal and use alsa-mixer. I had to unmute some items and turn up volume on others.

---

