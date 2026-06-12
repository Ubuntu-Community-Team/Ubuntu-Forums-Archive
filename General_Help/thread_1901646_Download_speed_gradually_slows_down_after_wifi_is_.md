---
title: "Download speed gradually slows down after wifi is connected"
date: 2011-12-29
forum: General Help
---

### Post by Misodoctakleidist on 2011-12-29
I have just switched from Windows to Ubuntu and I am having some problems with my wifi.

If I run a speed test just after the wifi is connected I get about 6M download speed (pretty much the same as on Windows), but if I then run it a second time it is only 1.5M and it stays that way until I reset the wifi connection.

I thought maybe there was something hogging my connection in the background, but I have installed the Net Speed extension for Gnome and there doesn't seem to be anything else using the connection.

Has anyone else had this problem?

---

### Post by zero2xiii on 2011-12-29
Hay,

This seems to be a common problem with some of the wifi-card drivers. Try updating them or installing a manufacturer driver.

Just thought to let you know, someone else might be able to assist you to fix this.

Good luck

---

### Post by Misodoctakleidist on 2011-12-29
Thanks for the reply zero2xiii.

I tried installing a new driver, but that seems to have actually made the problem worse. It now starts out at about 3.5Mb/s before dropping to less than 1Mb/s after about a minute. :(

---

### Post by zero2xiii on 2011-12-29
Sigh,

Awell. Seeing as no-one else is replying. Lets see if we can tackle this problem together and get it sorted out.

First, please run and post the output of the following commands in a terminal, put them between the CODE tags (the # sign at the top of the reply section):

```
sudo lshw
```
```
sudo lspci
```
```
sudo iwconfig
```
```
cat /proc/net/wireless
```

This will give us all the information we need to see whats cooking down there.

Cherz for now

---

### Post by Misodoctakleidist on 2011-12-29
Thanks zero2xiii. I have run those four commands in terminal and got the following output:

1.

```
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=30303141-3444-3736-3039-4630FFFFFFFF
  *-core
       description: Motherboard
       product: VM900M
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: Tue Mar 27 01:41:06 2007
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6
          date: 07/25/2007
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R)  CPU       E6700  @ 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 3200MHz
          capacity: 3600MHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni monitor tm2 ssse3 lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 2MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 41632 MHz (0.0 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             clock: 2977MHz (0.3ns)
        *-bank:1
             description: DIMM 41632 MHz (0.0 ns)
             physical id: 1
             slot: A1
             size: 2GiB
             clock: 2977MHz (0.3ns)
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 3200MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d0000000-d7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:dfb00000-dfbfffff memory:dfa00000-dfafffff
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:b000(size=4096) memory:dfe00000-dfefffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV730XT [Radeon HD 4670]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:24 memory:c0000000-cfffffff memory:dfee0000-dfeeffff ioport:bc00(size=256) memory:dfe00000-dfe1ffff
           *-multimedia
                description: Audio device
                product: RV710/730
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:25 memory:dfefc000-dfefffff
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:a000(size=4096) memory:dfd00000-dfdfffff ioport:dfc00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
           *-disk
                description: ATA Disk
                product: MAXTOR STM350032
                vendor: Maxtor
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MX15
                serial: 9QM6ZQQK
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=425d8ba5
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/data
                   version: 3.1
                   serial: 7a27dee0-4bad-3d47-9e68-da01192854d0
                   size: 416GiB
                   capacity: 416GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-10-13 11:52:51 filesystem=ntfs label=Data mount.fstype=fuseblk mount.options=rw,sync,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: c8cc96a6-e92a-2548-8513-83d0db065b88
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-02-09 13:48:34 filesystem=ntfs label=W7 state=clean
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             logical name: scsi3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD1600JB-00R
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 20.0
                serial: WD-WCANMF247026
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e72b8a75
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: c0339ae8-2eb8-6445-accf-a883bbb0d729
                   size: 86GiB
                   capacity: 86GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2007-06-15 09:16:59 filesystem=ntfs state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 62GiB
                   capacity: 62GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /
                      capacity: 59GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 3005MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD RW AD-5170A
                vendor: Optiarc
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:dffff000-dffff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:1a:4d:76:09:f0
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:d000(size=256) memory:dfffe000-dfffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:df900000-df9fffff ioport:df800000(size=1048576)
           *-network
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:04:05.0
                logical name: wlan0
                version: 20
                serial: 00:12:0e:4c:3f:a5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 driverversion=3.0.0-14-generic firmware=N/A ip=192.168.1.69 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 ioport:9c00(size=256) memory:df9ff000-df9ff1ff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT8237A/VT8251 HDA Controller
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:bfffc000-bfffffff

```2.

```
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
02:00.1 Audio device: ATI Technologies Inc RV710/730
04:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

```3.

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PlusnetWireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:8A:4D:C9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=40/100  Signal level=40/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2133  Invalid misc:255183   Missed beacon:0

```4.

```
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   36.   36.    0        0      0      0   2141 257018        0

```

---

### Post by zero2xiii on 2011-12-29
Right so lets see,

> *-network
                description: Wireless interface
                product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:04:05.0
                logical name: wlan0
                version: 20
                serial: 00:12:0e:4c:3f:a5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8180 **driverversion=3.0.0-14-generic** firmware=N/A ip=192.168.1.69 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 ioport:9c00(size=256) memory:df9ff000-df9ff1ff

> 04:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

Oka so from these two we have your card is detected correctly. However, you say you have installed drivers? How and what did you install, because I see there (the bold in the first qoute) that it is generic drivers?
That is the hardware and driver section, seems to be fine.

Now:

> wlan0     IEEE 802.11bg  ESSID:"PlusnetWireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:8A:4D:C9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          **Link Quality=40/100  Signal level=40/100**  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2133  Invalid misc:255183   Missed beacon:0

> Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | **link level noise** |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   **36.   36.    0**        0      0      0   2141 257018        0

This shows us there is a VERY bad connection. (anything below 50% quality is a very dodgy connection from my experience.) However there seems to be no packet losses? Nor corrupt packets or missed beacons. Which is intresting for a link with such low quality and signal strength.

So before we try tweaking your settings, lets first get the drivers out of the way. How and what did you install?

---

### Post by Misodoctakleidist on 2011-12-29
I used NdisWrapper to install a windows driver (because I couldn't find a manufacturer driver for linux) as described on [this web page]("http://jimvernon.com/archives/53"). But I have now uninstalled it since it didn't seem to make much difference.

I think the low signal strength may be inaccurate. As I mentioned, I get good speeds for about a minute after I connect to the network, but then the speed drops. The signal strength remains at at one bar throughout though.

---

### Post by zero2xiii on 2011-12-29
hmmm

See the thing is, normaly the configuration is of such that it self addapts the rate te minimize packet losses and such.

So lets see what happens if we adjust the thresthold levels. Raising this, MIGHT make fallback a little less and boost the speed. However there is another thing I am wondering.

Exactly WHAT speed are you talking about? Is web browsing slowing down? Downloading slowing down? Or only network speed, eg copying a file from another local machine over the wireless network?


Answer those, but test the following aswell:

```
sudo ifconfig wlan0 mtu 512 #this sets the mtu value pretty low for a high latency device, might help, or do nothing.
```
```
sudo iwconfig rate 54M #Locks the rate of the connection to54MBs to help with unecesary fallback
```
```
sudo iwconfig sens -80 #the sensitivity of the card set to -80dbm, this may work depending on the drivers and card
```
```
sudo iwconfig power off #set powersaving to off
```
```
sudo iwconfig commit #to force the settings to take imediate effect
```

Some of the commands above may work, some may give errors, try each one in sequence and test, then the next one, test, then the next etc. This changes are temporarily and SHOULD reset upon reboot. If these fix the issues, we will work on getting them permanent.

Cherz

---

### Post by Misodoctakleidist on 2011-12-29
The first one of those makes the connection slower. The other four all give error messages along the lines of "uknown command." Have I done something wrong typing them in?

I am testing the speed by using a browser-based broadband speed test. I haven't tried file transfers within the local network - and I'm not sure if I'd even know how. The speed is noticeably slow for things like file downloads as well though so I don't think it is a browser issue.

Interestingly it is only the download speed which is affected. The upload speed stays at around 350k all the time - similar to what I get in windows.

---

### Post by zero2xiii on 2011-12-30
Interesting,

Yes. Its weird the upload speed stays the same. Try changing 512 to a higher value (such as 2048). And try the other commands without the appended # and the text after that.

This really is strange.

---

### Post by Misodoctakleidist on 2011-12-30
Setting the mtu to 2048 makes no difference as far as I can tell.

For the others I am getting:

```
unknown command "54M"
```

```
unknown command "-80"
```

```
unknown command "off"
```

```
commit    No such device
```

It is the same with or without the comments.

I have just run the speed test on my netbook - also runnung Ubuntu - and it is about ten times faster than my desktop so it seems to be hardware related.

---

### Post by zero2xiii on 2011-12-30
Hmm thats intresting,

Maybe you should place an = sign there:

```
sudo iwconfig wlan0 rate=54M
```

But yes it might be hardware/driver issue rather than config. So lets try:

```
sudo apt-get install linux-backports-modules-compat-wireless-3.1-lucid-generic
```

should install the newest generic drivers for the card.

---

### Post by Misodoctakleidist on 2011-12-30
Now I get:

```
iwconfig: unknown command "rate=54M"
```

and

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-compat-wireless-3.1-lucid-generic
E: Couldn't find any package by regex 'linux-backports-modules-compat-wireless-3.1-lucid-generic'

```

---

### Post by zero2xiii on 2011-12-30
Oka,

Seems like your card does not except those to be set. So lets concentrate on drivers.

Strange. Try searching manualy in synaptic after updating the repros:

```
sudo apt-get update
```

but only search for:

**linux-backports-modules-compat-wireless**-3.1-lucid-**generic**

The non bold section may vary it seems. So only type in the box:
"linux-backports-modules-compat-wireless"
then manualy pay attention to the last section for the newest version that has "Generic" appended.

---

### Post by Misodoctakleidist on 2011-12-30
Okay.

I get two results:

linux-backports-modules-cw-3.1-3.0.0-14-generic
linux-backports-modules-cw-3.1-3.0.0-14-generic-pae

Should I install one of them?

---

### Post by zero2xiii on 2011-12-30
Yes install both.

The pae should give backport support or something.

---

### Post by Misodoctakleidist on 2011-12-30
I've installed both and it doesn't seem to have made any difference. :(

---

### Post by zero2xiii on 2011-12-30
Well this is where why knowledge ends.

I have no idea how to further assist you unfortunately. I have never had a similar issue, even though I have a wireless network with about 5 computers running on it. I never installed or setup drivers or anything.

Maybe some one else can assist you. But further than this I can not.

Sorry :(

---

### Post by Misodoctakleidist on 2012-01-01
Thanks for the help zero2xiii.

I think it might just be some really obscure issue because I can't find any mention of similar problems from googling.

---

### Post by wildmanne39 on 2012-01-02
Hi, please try this, it should work but after all the changes you made it depends if you undid those changes or left them.
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
```
Thanks

---

### Post by Misodoctakleidist on 2012-01-02
I've undone everything I did previously and tried entering that command in the terminal. I get the following:

```
tee: .: Is a directory
nameserver 8.8.8.8

```

It hasn't fixed my problem though.

---

### Post by wildmanne39 on 2012-01-02
Hi, click on the internet icon in the upper right corner of the screen, then on edit connection, wireless and make sure your setting look like the screenshots I am including and see if that helps.
Thanks

---

### Post by Misodoctakleidist on 2012-01-03
I have changed my wifi settings to match the screenshots, but it hasn't solved the problem. :(

---

### Post by wildmanne39 on 2012-01-04
Hi, I am not sure that there is anything we can do to help but please post the results from these commands so I can see exactly where your system is at.
```
cat /etc/lsb-release; uname -a
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by Misodoctakleidist on 2012-01-05
I have given up and set up a wired connection now, but I'll run those commands and post the output if it will help other people with the same problem.

I have also reinstalled the OS since my last post in the hope that it would resolve the problem but to no avail.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux james-desktop 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux          

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_via      71209  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_intel          33390  2 
joydev                 17693  0 
snd_hda_codec         104802  3 snd_hda_codec_via,snd_hda_codec_hdmi,snd_hda_intel
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon               1016226  3 
rtl8180                40710  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
snd                    68266  14 snd_hda_codec_via,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              462092  1 rtl8180
drm                   236290  5 radeon,ttm,drm_kms_helper
eeprom_93cx6           12725  1 rtl8180
cfg80211              199587  2 rtl8180,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 radeon
i2c_viapro             13153  0 
shpchp                 37345  0 
psmouse                73882  0 
serio_raw              13166  0 
ppdev                  17113  0 
parport_pc             36962  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
via_rhine              32192  0 
floppy                 70365  0 
sata_via               13846  1 
pata_via               13670  2 

```

---

### Post by wildmanne39 on 2012-01-05
Hi, I am sorry to hear that you needed to go to a wired connection, many people are having trouble with this brand of wireless card.
thanks

---

