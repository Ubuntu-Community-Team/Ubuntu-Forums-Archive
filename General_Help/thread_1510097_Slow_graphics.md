---
title: "Slow graphics"
date: 2010-06-15
forum: General Help
---

### Post by Adrian Sarmas on 2010-06-15
Hi! I'm new here. I just installed Ubuntu 10.04 LTS a few days ago and i have a problem. When i run a graphical application, like a game I get a very slow framerate (maybe even 1 frame/sec.) even on games like Mario or SuperTux. I don't have that problem when using OpenOffice for instance. I have an Intel Celeron 2 Ghz processor, 768 MB RAM, 256 MB Video. Is this a problem with OpenGL? Can anyone help me?

---

### Post by cascade9 on 2010-06-15
What video card are you using? Sounds like the drivers arent installed. Try going here- 

System-> Administration-> Hardware drivers. 

If you get nothing avaible from there, you probably have a Intel video card (doubtful with 256MB on a 2Ghz celery) or a card from a manufacturer that had dropped support (ATI most likely). Just to be sure, you can run-

lshw 

Then check the 'display'. Mine looks like this- 

```
*-display                                                                                                                 
                description: VGA compatible controller                                                                               
                product: G84 [GeForce 8600 GT]                                                                                       
                vendor: nVidia Corporation                                                                                           
                physical id: 0                                                                                                       
                bus info: pci@0000:01:00.0                                                                                           
                version: a1                                                                                                          
                width: 64 bits                                                                                                       
                clock: 33MHz                                                                                                         
                capabilities: vga_controller bus_master cap_list rom                                                                 
                configuration: driver=nvidia latency=0                                                                               
                resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:d800(size=128) memory:feae0000-feafffff  
```

---

### Post by Adrian Sarmas on 2010-06-15
I'm using a VIA Chrome9 (onboard). I can set from BIOS between 64MB, 128MB and 256MB of memory from RAM memory. I have 1 GB RAM, so if I set 256MB Video, it remains only 768MB RAM.
I tried going to System-> Administration-> Hardware drivers, but I get an empty list: "No proprietary drivers are in use on this system"

After typing ishw i got the following:

  ```
"sarmas-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1015MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU          440  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          size: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
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
          resources: irq:0 memory:d0000000-dfffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
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
             capabilities: pci bus_master cap_list
             resources: ioport:c000(size=4096) memory:fb000000-fcffffff memory:c0000000-cfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:c0000000-cfffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc00ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:b000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
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
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:e0:4d:77:48:cf
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.2 latency=32 maxlatency=8 mingnt=3 multicast=yes
             resources: irq:23 ioport:d000(size=256) memory:fdffe000-fdffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
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
          product: VT8251 Ultra VLINK Controller
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
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:bfffc000-bfffffff"
```

---

### Post by warfacegod on 2010-06-15
> I'm using a VIA Chrome9 (onboard).

This is your problem.


VIA drivers are almost nonexistent. If you're on a desktop, buy an nVidia card (do some research). If your on a laptop, buy a new laptop. Or you can just deal with it because there's almost nothing else you can do.

May be you can get cascade9 to send you some of the parts he finds laying about in the streets of his town.

---

### Post by warfacegod on 2010-06-15
Do us a favor, if you would. Edit the post with your lshw output and put code brackets on it, instead of quotes. (# icon)

---

### Post by cascade9 on 2010-06-15
> **warfacegod said:**
> This is your problem.

VIA drivers are almost nonexistent. If you're on a desktop, buy an nVidia card (do some research). If your on a laptop, buy a new laptop. Or you can just deal with it because there's almost nothing else you can do.

Yes, agreed, VIA Chrome is the problem, and those are the only real solutions 

> **warfacegod said:**
> May be you can get cascade9 to send you some of the parts he finds laying about in the streets of his town.

Anything else you want to volunteer me for? :lolflag:

Truth be told, its been very dry on the 'finding new bits' front. There hasnt been many of the city council rubbish pickups lately, and the....er.....lets just say the business that owned the "bin of joy" where I used to find stuff has closed, or moved to the middle of nowhere. :( 

I'm down to my last few video cards! The only things I even have not in use currently is a ATI 9600XT, a SIS Xabre 400, a SIS PCI card and I *think* I have an ancient S3 PCI card, somehwere. None of those will help in this case anyway. :(

---

### Post by warfacegod on 2010-06-15
So, in reality, you only have an ATi card. Those SIS cards are just as bad as the VIA's for Linux.

I hereby declare you, by my divine right, as parts provider for all of the Forum. See? Now I don't have to volunteer you for anything else.:twisted::biggrin:

---

### Post by Adrian Sarmas on 2010-06-21
I found a video driver for my VIA card but it's working only on Ubuntu 8.04 LTS. Should I go back and use that system? Is there any posibility to "downgrade" to Ubuntu 8.04, or do I need to uninstall my current version and then to install the older one?
An example:  [http://www.youtube.com/watch?v=wm-oDfBZQAA](http://www.youtube.com/watch?v=wm-oDfBZQAA)

---

### Post by warfacegod on 2010-06-21
Downgrading is theoretically possible but, in reality, you'll break your system. You'll need to do a fresh install of 8.04 but bear in mind that Canonical support for it is going to run out in under a year.

---

