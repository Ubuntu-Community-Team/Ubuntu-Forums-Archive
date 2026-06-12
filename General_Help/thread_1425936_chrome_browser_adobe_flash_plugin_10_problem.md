---
title: "chrome browser adobe flash plugin 10 problem"
date: 2010-03-09
forum: General Help
---

### Post by karthick ayyapillai on 2010-03-09
hi
i have upgraded to ubuntu 9.10 karmic version recently .All the things are working properly except the flash plugin for firefox. When i tried to watch a flash video like youtube. It works fine with the default mode. I cant watch it full screen when i tried to click full screen in firefox it crashes automatically and doesnt give any report. I have tried with the both free version and the non free version of Adobe plugin. I have also tried re installing fire fox no hope . I tried to install chrome browser for ubuntu and  i liked it better than firefox. Still i face the same trouble in full screen videos . Apart from that the pixel rate is very poor when i try to watch a HD video in either of the browsers.I tried in  forum and also googled it no hope.
the system config is 
ubuntu 9.10 karmic kola 
ati radeon 5001 graphic card
using entire  linux partition no windows
flash plugin is adobe flash plugin
i installed it through the synaptic package manager.
in chrome browser if i click the full screen mode i get an error like this 
the following plugin has crashed: usr/lib/adobe-flashplugin/libflashplayer.so
when i tried to search in the chrome bug it was reported as a bug for 64 bit version .
I am using 32 bit version. 
If any one can has a solution please post a reply to the message.
thanks in advance.
#

---

### Post by DomesDKG on 2010-03-09
I used to have the same problem, but a recent update seems to have fixed it.  Have you tried running system update?

---

### Post by karthick ayyapillai on 2010-03-17
> **DomesDKG said:**
> I used to have the same problem, but a recent update seems to have fixed it.  Have you tried running system update?

I have tried the update no use if you have any other solution for the problem please let me know thanks in advance

---

### Post by Muhammad Ahmed on 2010-03-17
copy the file libflashplayer.so and in terminal run the following :::


"sudo nautilus"
and in the windows that opens navigate to "/usr/lib/mozilla/plugins/"
and paste the file there

---

### Post by karthick ayyapillai on 2010-03-19
> **Muhammad Ahmed said:**
> copy the file libflashplayer.so and in terminal run the following :::


"sudo nautilus"
and in the windows that opens navigate to "/usr/lib/mozilla/plugins/"
and paste the file there

Hi
thanks for the help sorry for not getting back to you soon.I have tried what you had posted in reply now i am getting the error like this 
usr/lib/flashplugin-installer/libflashplayer.so
if you have any other alternatives please reply thanks in advance

---

### Post by clhsharky on 2010-03-19
HI

Could you please give more info on hardware and video driver. I could not find any thing useful on the card you listed.
Paste code in terminal will tell your hardware. Post results if you need help understanding them.

```
lshw
```


Sharky

---

### Post by karthick ayyapillai on 2010-03-20
> **clhsharky said:**
> HI

Could you please give more info on hardware and video driver. I could not find any thing useful on the card you listed.
Paste code in terminal will tell your hardware. Post results if you need help understanding them.

```
lshw
```


Sharky
this is my harware description .
the graphics card is ATI radeon
 description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc


 description: Computer
    product: AMILO Li 1718
    vendor: FUJITSU SIEMENS
    version: -1
    serial: 914B901100G720015A4K00B
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=935D4640-0582-11DC-A072-D737462ECFF9
  *-core
       description: Motherboard
       product: AMILO Li 1718
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: Rev.A
       serial: 914B901100G720015A4K00B
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: V1.3 (03/14/07)
          size: 101KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          slot: U23
          size: 800MHz
          capacity: 2048MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: M2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff memory:d0000000-dfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:d0000000-dfffffff(prefetchable) ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:c0000000-c00fffff
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix cap_list
                configuration: latency=0
                resources: memory:c0000000-c000ffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:8440(size=8) ioport:8430(size=4) ioport:8420(size=8) ioport:8410(size=4) ioport:8400(size=16) memory:c0507000-c05071ff memory:38000000-3807ffff(prefetchable)
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXCZ07885799
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=945afe91
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: ee0a590e-c006-415d-9b9c-0ec42e01c517
                   size: 149GiB
                   capacity: 149GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-03-07 21:48:18 filesystem=ext4 lastmountpoint=/A&#65533;+&#65533;&#65533;&#65533;O&#65533;&#65533;2&#65533;&#65533;&#65533;&#65533;&#65533;|~}&#65533;iW&#65533;`&#65533;&#65533;&#65533;`&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;&#65533;~}&#65533;&#65533;~}&#65533;&#65533;Y&#65533;&#65533;&#65533;O&#65533;&#65533;&#65533;%&#65533;&#65533; modified=2010-03-10 21:29:07 mounted=2010-03-17 22:56:43 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2565MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 78GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2565MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0504000-c0504fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0505000-c0505fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0506000-c0506fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 83
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8450(size=16) memory:c0507400-c05077ff
        *-ide:1
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8460(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7540A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.42
                serial: [Optiarc DVD RW AD-7540A 1.42 Jul26,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:c0500000-c0503fff
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:a000(size=4096) memory:f0200000-f02fffff memory:f0300000-f03fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:0a:07.0
                logical name: eth0
                version: 10
                serial: 00:16:d3:65:11:19
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:23 ioport:a000(size=256) memory:c0200000-c02000ff
  *-battery
       description: Lithium Ion Battery
       vendor: Simplo
       physical id: 1
       version: Panasonic
       serial: BTP-B4K8
       slot: main
       capacity: 44000mWh
       configuration: voltage=10.8V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: inbound
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:1e:2a:b4:3c:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.12 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
thanks for the reply and help

---

### Post by cottfcfan on 2010-03-20
Karthick...

I'm having the same problem and also use an ATI graphics card.
This is only a recent issue.
A temporary solution is, when your watching a vid in small screen,
right click on the screen, go to settings and untick "enable hardware acceleration".
That should solve your problem.

---

### Post by karthick ayyapillai on 2010-03-21
cottfcfan
hi thanks for your help . I did the thing wat you mentioned in your post it worked i can go full screen but the pixel rate is terrible so i think i better stay with small screen in youtube. The beauty is all yahoo videos are working fine and pixel rate is way better in yahoo server .
May be this will be rectified on the ubuntu 10.04 version the latest hope for the best .thanks again for your help

---

