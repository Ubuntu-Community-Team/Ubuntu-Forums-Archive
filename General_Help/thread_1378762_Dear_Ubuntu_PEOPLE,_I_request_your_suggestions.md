---
title: "Dear Ubuntu PEOPLE, I request your suggestions"
date: 2010-01-11
forum: General Help
---

### Post by Dadilious on 2010-01-11
First off, my name is Chris, my roomemate and I alongside my fiance have formed a small little in home computer repair business.  We will be starting with friends and family and branching out from there.

We all run XP and 7, with a lap top running ubuntu and we've all had experience with ubuntu so we like you guys hahah.

We have a website:  xionrepair.com

We have recently come into ownership of an older computer that a friend had no use for, and it had the fittings for our 1.5 TB HD which we thought would be fun to put in it's own computer and install the Ubuntu server for.

The hardware for the computer running the server is:

  description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2047MiB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up rep_good pni lahf_lm cpufreq
     *-pci:0
          description: Host bridge
          product: 755 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-amd64 latency=32
          resources: irq:0 memory:0-7ffffff
        *-pci
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:e8000000-e80fffff memory:e0000000-e7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon R200 QL [Radeon 8500 LE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: memory:e0000000-e7ffffff(prefetchable) ioport:d000(size=256) memory:e8020000-e802ffff memory:e8000000-e801ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e000(size=256) ioport:e100(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:e8124000-e8124fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:e8120000-e8120fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:e8121000-e8121fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:e8122000-e8122fff
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 91
             serial: 00:14:2a:68:cd:7d
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.3 latency=32 maxlatency=11 mingnt=52 multicast=yes
             resources: irq:19 ioport:e200(size=256) memory:e8123000-e8123fff memory:80000000-8001ffff(prefetchable)
        *-ide:1
             description: IDE interface
             product: RAID bus controller 180 SATA/PATA  [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=32
             resources: irq:17 ioport:e300(size=8) ioport:e400(size=4) ioport:e500(size=8) ioport:e600(size=4) ioport:e700(size=16)
        *-usb:4
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:19 ioport:e800(size=32)
        *-usb:5
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: d.1
             bus info: pci@0000:00:0d.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:16 ioport:e900(size=32)
        *-usb:6
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: d.2
             bus info: pci@0000:00:0d.2
             version: 65
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:e8125000-e81250ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
xcr@xcr:~$ 


Here's the deal, we are thinking about, we want to know what we can do with our server to make use of it personall and business-wise

We are also looking into a new report system to replace the old one in the website as the person who set that up for us will no longer be assisting us.  We were wondering if there were any suggestions on that which we as non internet coding savy people could run ourselves.

Any and all suggestions are welcome.

Thanks in advance.

---

### Post by JC Cheloven on 2010-01-11
Hey, get a static IP, setup your server, and have fun !

Sure you can grab ideas from [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Best luck with your new bussines ;-)

---

### Post by boriskarloffinablender on 2010-01-11
subtle spam?

---

### Post by f-teem on 2010-01-11
> **JC Cheloven said:**
> Hey, get a static IP, setup your server, and have fun !

Sure you can grab ideas from [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

Best luck with your new bussines ;-)

+

You can use it as a home or bussiness-wise server,imo that hardware configuration can satisfy your needs (in both options).

GL :-)

---

### Post by Gen2ly on 2010-01-11
> **boriskarloffinablender said:**
> subtle spam?

lol, I was wondering the same thing.

---

### Post by Dadilious on 2010-01-11
> **f-teem said:**
> +

You can use it as a home or bussiness-wise server,imo that hardware configuration can satisfy your needs (in both options).

GL :-)


Thanks, I was actually hoping you guys had some ingenius creative and imaginative ideas for owning a server of our own.  We figure, we've got all this space and a computer to handle it, yet nothing really comes to mind when it comes to uses other than file sharing :P

---

### Post by Iowan on 2010-01-11
Check the provided link... For a business, there are databases to be built, email servers, websites to advertise, blogs , and firewalls - to name but a few.  Throw in a music server for the office, some home/business automation if you wish. Your server can/will be a reflection of your business if it's available to the public, so it should look professional and be available.

---

