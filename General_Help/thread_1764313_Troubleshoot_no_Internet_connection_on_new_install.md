---
title: "Troubleshoot no Internet connection on new installation"
date: 2011-05-21
forum: General Help
---

### Post by dragonfly41 on 2011-05-21
I have just installed ubuntu 10.10 on an Acer Aspire 3610 notebook.

2 GB RAM.

This notebook had Internet access previously via Windows XP (now erased).

Here is the partitioned drive.
Two ext4 partitions for ubuntu "/" and "/home".
Two ntfs partitions possibly for Windows.

I have booted up the fresh installation of ubuntu 10.10.

I had some glitch where I saw "Operating system not found' on booting from HDD and I wondered if this was due to failing drive.

But I've run a full test using Disk Utility and it shows as healthy.

This message has gone away (I don't know why) and I can boot into ubuntu.

The problem I'm trying to solve is simply no internet connection.

Here are some outputs from commands ..

```

$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbcfcbcfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5100    40960000    7  HPFS/NTFS
/dev/sda2            5100       14594    76259328    5  Extended
/dev/sda5   *        5100        6375    10240000   83  Linux
/dev/sda6            6375       11474    40960000   83  Linux
/dev/sda7           11474       14594    25056256    7  HPFS/NTFS


``````

sudo lspci -k

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Realtek ALC 655 codec (in Acer TravelMate 2410 serie laptop)
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Conexant AC'97 CoDec (in Acer TravelMate 2410 serie laptop)
    Kernel modules: snd-intel8x0m
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: i2c-i801
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket


```Next I looked here ..


```

sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:e5:cc:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43328 (43.3 KB)  TX bytes:43328 (43.3 KB)



```and then ..


```


 sudo lshw -C network

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:21 memory:b0100000-b0101fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:e5:cc:10
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:3000(size=256) memory:b0102000-b01020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:33:f8:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11b



```Can anyone see why I can't have Internet connection .. I use cable and not wireless.

And the Internet connection is good on another ubuntu installation on a Dell Inspiron 1720.

It is this Acer which is not connecting .. although Internet worked fine in Windows XP which I've removed.

Do I need to install any network drivers?

I inspected > System > Administration > Additional Drivers

The result is ..

[B][COLOR=DarkSlateGray]No proprietary drivers are in use in this system
  [/COLOR][/B]

Thanks.

[EDIT]

Just to add for clarification.

There was no Internet connection shown at time of ubuntu installation when the initial checklist comes up.

yes   has at least 2.5 GB available drive space

yes   is plugged into a power source

[COLOR=Red]no    is connected to the Internet[/COLOR]

---

### Post by dragonfly41 on 2011-05-21
I've just read here ..

[http://ubuntuforums.org/showthread.php?p=2343324](http://ubuntuforums.org/showthread.php?p=2343324)

> There aren't any Linux drivers for your [Acer Inspire 3610] wireless card, so you need to use ndiswrapper.[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show)

Does this problem apply to wired Internet connection?   I still see no connection via cable.

---

### Post by linuxinstalledfromhdd on 2011-05-21
I don't recommend to install Ubuntu with only a wireless connection, at first.  You can use a windows wireless ndiswrapper after you get everything else running.  

And it is always a good idea to check and see what the performance of your system will be like before you actually you install Ubuntu on your system with a live bootable USB drive of Ubuntu. Boot from the USB and check to see what works, and what doesn't work.

---

### Post by dragonfly41 on 2011-05-21
Does that mean I might have to drop the idea of running ubuntu 10.10 on Acer and go back to Win XP on that notebook?

Is there another distro which might work with an Acer Inspire 3610?

---

