---
title: "Fresh install of 10.4 = Internet is slow!"
date: 2010-05-04
forum: General Help
---

### Post by okayneil on 2010-05-04
Guys, 

I installed a fresh copy of 10.4 onto my laptop alongside windows 7 pro. Internet is horribly slow, sometimes taking a minute for the page to render. I have a solid 10/10Mbt LAN line which is working fine in Windows. 

Any ideas on a fix?

---

### Post by TyLLy_4 on 2010-05-04
Had the same issue with my laptop on wireless. 

In order to help you out we need more information. Give us all the details you can. 

ideally you could run some kind of system info program and post the results here. 

most importantly post your motherboard model number and your network card. 

In my particular case it was a driver issue. The ubuntu drivers that installed automatically in my system would only take me to around 100kb/s so i had to install windows drivers with nisdwrapper. after that i have 900 Kb/sec downloads )

---

### Post by okayneil on 2010-05-04
> **TyLLy_4 said:**
> Had the same issue with my laptop on wireless. 

In order to help you out we need more information. Give us all the details you can. 

ideally you could run some kind of system info program and post the results here. 

most importantly post your motherboard model number and your network card. 

In my particular case it was a driver issue. The ubuntu drivers that installed automatically in my system would only take me to around 100kb/s so i had to install windows drivers with nisdwrapper. after that i have 900 Kb/sec downloads )

Here you go matey :)

```
description: Notebook
    product: AMILO Li3710
    vendor: FUJITSU SIEMENS
    version: Rev 1.0
    serial: YL1R036436
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=4FD4BAD0-8189-5516-17FF-203040506099
  *-core
       description: Motherboard
       product: EF7
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: D3A
       serial: EF700930002919D3A
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: 1.09 (03/27/2009)
          size: 108KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1200MHz
          capacity: 2GHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst internal write-back
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
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             physical id: 0
             serial: 76D23C45
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 400 MHz (2.5 ns)
             physical id: 1
             serial: 0380FDB0
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
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
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:31 memory:f2800000-f2bfffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f2100000-f21fffff
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f2504800-f2504bff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f2500000-f2503fff
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
             configuration: driver=pcieport
             resources: irq:24 ioport:4000(size=4096) memory:c0000000-c01fffff memory:c0200000-c03fffff(prefetchable)
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
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) memory:f4000000-f5ffffff ioport:f0000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:5000(size=4096) memory:c0400000-c05fffff memory:c0600000-c07fffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:f2200000-f22fffff memory:c0800000-c09fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 11
                serial: 00:22:5f:bd:cf:a8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:f2200000-f220ffff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:3000(size=4096) memory:c0a00000-c0dfffff ioport:f2000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:fd:09:40
                size: 10MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.18.129.0 latency=0 link=yes multicast=yes port=MII speed=10MB/s
                resources: irq:29 ioport:3000(size=256) memory:f2010000-f2010fff(prefetchable) memory:f2000000-f200ffff(prefetchable) memory:f2020000-f203ffff(prefetchable)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2504c00-f2504fff
        *-pci:5
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
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f2504000-f25047ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXB0A79Y2849
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ea72e14d
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 32c32771-9ec6-7149-bfc4-337abc2a1397
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-12-05 08:11:36 filesystem=ntfs state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 31988cee-a871-4019-bdcf-6a3bc1f30c5f
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-01-12 21:14:24 filesystem=ntfs label=Neil state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 9b87f9e9-c9f3-4d48-a74b-e6cc75ac889b
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-12-05 00:07:14 filesystem=ntfs label=Photos state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 50GiB
                   capacity: 50GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10236MiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 38GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1723MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT20N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CW02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
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
             resources: memory:c0e00000-c0e000ff ioport:1c00(size=32)
     *-scsi
          physical id: 2
          bus info: usb@2:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-battery
       description: Lithium Ion Battery
       product: MAL32b
       vendor: SANYO
       physical id: 1
       version: SANYO
       serial: e04866102D31D25000410
       slot: Main
       capacity: 47520mWh
       configuration: voltage=10.8V
```

---

### Post by okayneil on 2010-05-04
Bump :)

[IMG]http://www.speedtest.net/result/803951696.png[/IMG]

These are the results im getting, it seems then that the speed is not the problem, maybe one that could exist in FF?

The problem is also not with WiFi, its a cable connection!

---

### Post by davec64 on 2010-05-04
HI,

I assume you're using Firefox?

By default IPV6 is enabled, so when Firefox tries resolve a web address it tries IPV6 before IPV4. You can probably safely diaable IPV6 (I have). To do this open Firefox and in the address bar type:

```
about:config
```

Click the button to allow access.
In the filter bar type IPV6.
You'll then only get one entry called **network.dns.disableIPv6**
Double click this to change its value to **True**

Here's a link to some more firefox tweaks you can try:[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html]("http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html")

---

### Post by okayneil on 2010-05-04
> **davec64 said:**
> HI,

I assume you're using Firefox?

By default IPV6 is enabled, so when Firefox tries resolve a web address it tries IPV6 before IPV4. You can probably safely diaable IPV6 (I have). To do this open Firefox and in the address bar type:

```
about:config
```Click the button to allow access.
In the filter bar type IPV6.
You'll then only get one entry called **network.dns.disableIPv6**
Double click this to change its value to **True**

Here's a link to some more firefox tweaks you can try:[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

Many thanks, seems to have sorted that one out :)

---

### Post by davec64 on 2010-05-04
No worries!

---

### Post by dDilla on 2010-05-06
Thanks for the crucial info. This was the only problem I was running into. Upgraded from 9.10 to 10.04 and all seems to be running great now.

---

### Post by Elwood72 on 2010-05-07
> **davec64 said:**
> HI,

I assume you're using Firefox?

By default IPV6 is enabled, so when Firefox tries resolve a web address it tries IPV6 before IPV4. You can probably safely diaable IPV6 (I have). To do this open Firefox and in the address bar type:

```
about:config
```

Click the button to allow access.
In the filter bar type IPV6.
You'll then only get one entry called **network.dns.disableIPv6**
Double click this to change its value to **True**

Here's a link to some more firefox tweaks you can try:[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html]("http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html")

I've tried to disable IPv6 in Firefox twice using this method.....it won't let me.I double-click on it,and nothing happens.

I was able to disable it system-wide,just not in Firefox.

---

### Post by wardolb on 2010-08-10
I tried this and it worked for a few weeks, but now its doing it again. I'm running 10.04 on an acer aspire one netbook. Any help would be great. Thanks

---

### Post by griztown on 2010-08-11
This worked great but for some reason Filezilla is still crazy slow.  Is the whole system affected by this?  Why did they go with IPv6 in the firs place?

---

