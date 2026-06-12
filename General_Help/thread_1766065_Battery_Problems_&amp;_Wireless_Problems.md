---
title: "Battery Problems &amp; Wireless Problems"
date: 2011-05-23
forum: General Help
---

### Post by ShadedCS on 2011-05-23
I just installed the latest version of Ubuntu from ubuntu.com. As soon as it installed it, there was an error with the battery life.

It says 0:05 until full charge, and its at 90% battery, but when I pull it off the charger, it hibernates automatically, its like there is no battery life on my system.

Also, as soon as I started Ubuntu, my wireless was uninstalled saying that the Wireless is disabled by hardware switch, and im not sure what that is.

I have a dell laptop, to white I am not sure of the model.

Please make the answer as simple as possible and if there is a guide, please walk through step-by-step, this is my first time with Ubuntu ever, and I am still getting familiar with the system.

Thank you!

---

### Post by linuxinstalledfromhdd on 2011-05-23
Physically read the manifest on the bottom of the unit.  It will give you model, make, serial number.

---

### Post by ShadedCS on 2011-05-23
Thank you for the fast response.

Also for that part, the sticker is scratched out, so I can not see it.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Okay let's try it from Terminal:

lshw -l

Cut and paste the results.

---

### Post by ShadedCS on 2011-05-23
Hardware Lister (lshw) - B.02.15
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.15)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by linuxinstalledfromhdd on 2011-05-23
In your terminal cut and paste the following:

lshw

Cut and paste results. :)

---

### Post by ShadedCS on 2011-05-23
```
owner@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1969MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6570  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
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
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:f6800000-f6bfffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f6100000-f61fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
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
             capabilities: uhci bus_master cap_list
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
             capabilities: uhci bus_master cap_list
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
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f6504800-f6504bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:49 memory:f6500000-f6503fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f8000000-f9ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:80000000-803fffff ioport:f6000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 03
                serial: 00:24:e8:9d:df:77
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 multicast=yes port=MII speed=100Mbit/s
                resources: irq:47 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:fa000000-fbffffff ioport:f2000000(size=33554432)
           *-network DISABLED
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0e:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:b5:39:9a
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
                resources: irq:18 memory:fa000000-fa003fff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:fc000000-fdffffff ioport:f4000000(size=33554432)
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:6000(size=4096) memory:f6200000-f62fffff ioport:80400000(size=2097152)
           *-firewire
                description: FireWire (IEEE 1394)
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:1a:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:f6200000-f6200fff memory:f6202000-f62027ff
           *-generic
                description: SD Host controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0.1
                bus info: pci@0000:1a:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f6203800-f62038ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0.2
                bus info: pci@0000:1a:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: latency=0
                resources: memory:f6201000-f6201fff memory:f6203000-f62037ff memory:f6202800-f6202fff
        *-pci:5
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:7000(size=4096) memory:80600000-807fffff ioport:80800000(size=2097152)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
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
             capabilities: uhci bus_master cap_list
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
             capabilities: uhci bus_master cap_list
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
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f6504c00-f6504fff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
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
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f6504000-f65047ff
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
             resources: memory:80a00000-80a000ff ioport:1c00(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by linuxinstalledfromhdd on 2011-05-23
My guess at this point is we are looking at a driver issue.  

Did you have this problem with 10.10?

---

### Post by ShadedCS on 2011-05-23
This is the only version of Ubuntu I have ever had. I was recommended from a friend, and I switched from Windows XP.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did this happen with the live bootable disc or usb bootable drive of Ubuntu that you used to install it with?  You can try 10.10 with a live disc and see if the problem still remains?

---

### Post by ShadedCS on 2011-05-23
I used the Windows Installer from ubuntu.com

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by linuxinstalledfromhdd on 2011-05-23
Here is what I would do if I were you..

Okay, I would create a live bootable USB of Ubuntu.

Boot from that USB Drive when you turn on your computer.

After logging into your newly created stick of Ubuntu, see what the environment is like at that point. Do you still have the same problems? 

I've been noticing a few problem with Wubi installation in the help section lately and 11.04. I want to see if it makes any difference.  I bet the USB drive works fine.

---

### Post by ShadedCS on 2011-05-23
because I do not have a USB drive at this point, I will look into borrowing one.

Thank you

Also for the battery problem, it seems that it is fine with the battery reaches 100%. Maybe it just needed to find out how much it had with 100% battery, so I'll look more into that scenario.

Thank you for all your help,
If there was a rep system here, I'd +1 you.

Bryan

---

### Post by linuxinstalledfromhdd on 2011-05-23
I'm sorry I wish I could have been more helpful for you.  It might be a good idea at some point to create a live disc of Ubuntu for later in case your system gets stuck for whatever reason. It makes a nice rescue disc, or drink coaster eventually. :P

---

