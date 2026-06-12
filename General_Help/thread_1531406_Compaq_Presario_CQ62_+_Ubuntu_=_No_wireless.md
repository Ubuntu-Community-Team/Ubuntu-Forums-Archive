---
title: "Compaq Presario CQ62 + Ubuntu = No wireless"
date: 2010-07-15
forum: General Help
---

### Post by alexjohnc3 on 2010-07-15
I have a Compaq Presario CQ62 laptop that came pre-installed with Windows 7. I installed Ubuntu over it, but, alas, I cannot connect to the Internet. Any help?

---

### Post by alexjohnc3 on 2010-07-15
Here's the result of lshw:

> *-network
  description: Wireless interface
  product: Realtek Semiconductor Co., Ltd.
  vendor: Realtek Semiconductor Co., Ltd.
  physical id: 0
  bus info: pci@0000:02:00.0
  logical name: wlan0
  version: 10
  serial: 70:f1:a1:a2:29:b6
  width: 32 bits
  clock: 33MHz
  capabilities: bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
  resources: irq:17 ioport:3000(size=256) memory:90100000-90103fff

---

### Post by AceRoom on 2010-07-15
Any chance that there is a proxy involved?

Try the wireless button on the laptop. I have a Compaq too. Ubuntu doesn't perfectly support that button sometimes (Like it's always red when it's supposed to be blue). Press it and refresh your wireless.

Or is it connected to the wireless but just doesn't connect to the internet? In that case, make sure you've added the security key in your Network Manager.

---

### Post by alexjohnc3 on 2010-07-15
> **AceRoom said:**
> Any chance that there is a proxy involved?
Nope, definitely no proxy.

> **AceRoom said:**
> Try the wireless button on the laptop. I have a Compaq too. Ubuntu doesn't perfectly support that button sometimes (Like it's always red when it's supposed to be blue). Press it and refresh your wireless.
When I press it, it turns red, then turns blue when I press it again. Nothing happens though.

> **AceRoom said:**
> Or is it connected to the wireless but just doesn't connect to the internet? In that case, make sure you've added the security key in your Network Manager.
It shows the wireless icon, but with a red "!" on it. I can't see any of the several wireless networks my Windows laptop can, except one that is barely in range of both of them for some strange reason.

---

### Post by AceRoom on 2010-07-15
Try manually adding a wireless connection to it by using the correct name of the wireless and the security key.

---

### Post by alexjohnc3 on 2010-07-15
> **AceRoom said:**
> Try manually adding a wireless connection to it by using the correct name of the wireless and the security key.
I tried that twice after I noticed that for some reason it detected that one router (there are multiple routers in the area, and the router it detects is barely within range on my Windows laptop). It didn't work, though.

---

### Post by alexjohnc3 on 2010-07-15
Well, I plugged my laptop into an ethernet cable, let Ubuntu update in the vain hope that it might fix the problem, and what do you know? It works perfect now! :)

---

### Post by AceRoom on 2010-07-15
The wireless works now? Nice!;)

Who knew all it needed was an update. Make sure to mark the thread as solved.

---

### Post by alexjohnc3 on 2010-07-15
> **AceRoom said:**
> The wireless works now? Nice!;)

Who knew all it needed was an update. Make sure to mark the thread as solved.
Yep! It's lightning fast!

Sorry, immediately started working on fixing the sound, so I kind of forgot about that. :P

---

### Post by nanonils on 2010-08-05
Help! I have the same problem: trace data throughput while WiFi is up. However, in my case updating does not fix it.
I, too, purchased this very cheap but reasonably equipped notebook at BestBuy $329, got rid of Win7 by installing Lucid for 64bit.

type: Compaq Presario CQ63--228DX
router: LINKSYS|WRT160NL R 

Symptoms: WiFi indicated as connected successfully, WiFi button on computer is white/on. Data throughput is almost non-existent with even Google.com loading in 3 minutes or so. Odd thing is it does load one by one (not sure whether this could be a step by step populating from the cache).

All other Lucid computers are connecting and accessing the internet without problems through this router.

MAC filtering is off

We're using WPA2 with TKIP or AES encryption

Of course I'm in big trouble as this computer was supposed to replace my wife's old computer...

Thanks!

---

### Post by nanonils on 2010-08-05
Forgot: Regular LAN access is fast and flawless


 *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 10
                serial: 70:f1:a1:be:74:47
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.105 latency=0 multicast=yes wireless=802.11bgn

Details about output moved to the WiFi section (since this thread is labeled "solved"): [http://ubuntuforums.org/showthread.php?p=9685134#post9685134](http://ubuntuforums.org/showthread.php?p=9685134#post9685134)

---

### Post by Meaghan on 2010-11-11
> **AceRoom said:**
> Try the wireless button on the laptop. I have a Compaq too. Ubuntu doesn't perfectly support that button sometimes (Like it's always red when it's supposed to be blue). Press it and refresh your wireless.

I was reading this thread to try and solve a similar problem I'm having. Then i realized it's not the same but I am having a problem with that button. I press it and it's still red. You got a suggestion? :confused:

---

### Post by nanonils on 2010-11-11
> **Meaghan said:**
> I was reading this thread to try and solve a similar problem I'm having. Then i realized it's not the same but I am having a problem with that button. I press it and it's still red. You got a suggestion? :confused:

What distro are you on? I just purchased one myself as my Lenovo t61 display died and a daily build 64 bit maverick installation is amazingly fast and wifi not a problem. Did you try that button with and without the the tion key?

Since this thread is marked solved I had moved my troubles with my wife's laptop to this thread:
[http://ubuntuforums.org/showthread.php?t=1547049&page=2](http://ubuntuforums.org/showthread.php?t=1547049&page=2)

---

### Post by AceRoom on 2010-11-16
As stupid as it may seem.. Boot into Windows if you have it and make sure the wireless is switched on and make sure it's working. Without changing any options, reboot into Ubuntu and check it out.

---

### Post by AceRoom on 2010-11-16
As stupid as it may seem.. Boot into Windows if you have it and make sure the wireless is switched on and make sure it's working. Without changing any options, reboot into Ubuntu and check it out.

---

### Post by harlock59 on 2012-03-13
Hello,

i have no wifi on my presario cq62.
i don't know the version/flavour of the wireless card and if i do lshw | grep Wireless it returns nothing
i don't know which position of the little light is wifi on (the two positions are red or white).
i guess that white is for on and red for off, but i'm not sure about that
i'll post the complete result of sudo lshw
allison@allison-laptop-compaq:~$ sudo lshw
allison-laptop-compaq     
    description: Notebook
    product: Presario CQ62 Notebook PC
    vendor: Hewlett-Packard
    version: 049B110000202810000020000
    serial: CNF0239MJW
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=434E4630-3233-394D-4A57-C80AA9BA0BF4
  *-core
       description: Motherboard
       product: 1484
       vendor: Hewlett-Packard
       physical id: 0
       version: 77.18
       serial: CNF0239MJW
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.15 (04/26/2010)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: Celeron(R) Dual-Core CPU       T3300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 12
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: CPU
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 13
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 15
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 14
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: HYMP112S64CP6-S6
             vendor: Hynix
             physical id: 0
             serial: 4423D123
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 16HTF25664HZ-800J1
             vendor: Micron
             physical id: 1
             serial: EA68CC16
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: c8:0a:a9:ba:0b:f4
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.64 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: TOSHIBA MK5056GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LH00
                serial: 503TTEETT
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=dd2690f6
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 783ed49d-a93f-4967-841f-8f2367c593e4
                   size: 457GiB
                   capacity: 457GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2012-03-08 06:29:32 filesystem=ext3 modified=2012-03-12 00:35:37 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2012-03-08 08:04:43 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 8660MiB
                   capacity: 8660MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8660MiB
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
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 0300
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 82801I (ICH9 Family) Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-battery
       product: UnKnow
       vendor: UnKnow
       physical id: 1
       slot: In the back
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:57:6d:74:46:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
allison@allison-laptop-compaq:~$

---

