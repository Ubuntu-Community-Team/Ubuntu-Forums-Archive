---
title: "32 or 64 bit System"
date: 2010-01-10
forum: General Help
---

### Post by corredordebolsas on 2010-01-10
Hey guys, thanks in advance for any help.
I've got a dell inspiron 1420 laptop with a parcial disk with ubuntu and windows xp.
I'm thinking of upgrading my OS's but I don't know the specifics my computer needs.

In one side I want to install windows 7 because my xp version crashed with the blue screen of death, but I don't know if my computer is a 32 or 64 bit compatible because I ran the "lspci" and "lshw" command in the console and I got both numbers many times. (i've found ways to check if my system is 32 or 64 on windows but that's not possible since I can't access anymore).
I've also been regularly updating my ubuntu OS and I think I'm up to date (using Ubuntu 9.10. But I don't know if I can do something else to keep it sharp and running at the max performance.

Here's what I got from the commands on the console:

rodrigo@rodrigo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```
rodrigo@rodrigo-laptop:~$ lshw
WARNING: you should run this program as super-user.
rodrigo-laptop            
    description: Computer
    width: **32 bits**
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 993MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: **64 bits**
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: **64 bits**
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width:** 32 bits**
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: **64 bits**
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:fea00000-feafffff memory:e0000000-efffffff(prefetchable) ioport:eff8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: **64 bits**
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:feb00000-febfffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:fe9fc000-fe9fffff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:fe800000-fe8fffff
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:4a:ac:79
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.65 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:30 memory:fe8ff000-fe8fffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 ioport:d000(size=4096) memory:fe600000-fe7fffff ioport:f0000000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 memory:fe500000-fe5fffff
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:1c:23:f9:03:38
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 multicast=yes
                resources: irq:31 memory:fe5f0000-fe5fffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:fe400000-fe4fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:fe4ff800-fe4fffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:fe4ff400-fe4ff4ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: driver=ricoh-mmc latency=0
                resources: irq:4 memory:fe4ff500-fe4ff5ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:fe4ff600-fe4ff6ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 1.4
                bus info: pci@0000:03:01.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:fe4ff700-fe4ff7ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=32) memory:fe9fb800-fe9fbfff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe9fb700-fe9fb7ff ioport:10c0(size=32)
```

I also ran another command I found on the internet:

rodrigo@rodrigo-laptop:~$ uname -a
Linux rodrigo-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

Thanks in advance for any help about weather my computer is 32 or 64 bits and if it were 64 would it run with the 32 installation. The only problem that I found over the internet is that windows 7 (64 bit installation) would require a 2GB ram memory meanwhile the 32 would only require a 1GB ram memory (That's the one I have), in case I had a 64 bit compatible system I would be able to buy the upgrade to 2 or 4 GB of ram.

---

### Post by warfacegod on 2010-01-10
Intel(R) Core(TM)2 Duo CPU T5250

That's your processor. I just searched for it on the net. It's a 64. Hurray! for you, you get to have more than 3 GB RAM. Assuming your motherboard will fit it.

---

### Post by warfacegod on 2010-01-10
> Thanks in advance for any help about weather my computer is 32 or 64 bits and if it were 64 would it run with the 32 installation. The only problem that I found over the internet is that windows 7 (64 bit installation) would require a 2GB ram memory meanwhile the 32 would only require a 1GB ram memory (That's the one I have), in case I had a 64 bit compatible system I would be able to buy the upgrade to 2 or 4 GB of ram.

It is astonishing to me that Windows minimum RAM is 2 GB. I have Ubuntu 8.10 (which is a bit over a year old now) running decently on my mother's IBM Thinkpad with a P2 233 *Mhz* processor and 128 *MB* of RAM.

---

### Post by Sugi on 2010-01-10
Ok, I just did a quick search and your laptop can be upgraded to 4 Gigs MAX on the memory and it also supports 64 bit OSs.  So, if you wanted to YES you can upgrade to 64 OS and be happy. :)

Too bad though, most specs of the dell inspiron 1420 says it has 2 gigs out of the box, but yours does not. :/

>      *-memory
          description: System memory
          physical id: 0
          size: 993MiB


If you are planning on upgrading your ram to 4 gigs of ram, then sure go for it!  I have four OSs under 64 bit and I love it!  I actually have one computer with only 2 gigs of ram still running 64 bit OS, but I know in the near future I will be upgrading the machine to 4 gigs. So I will be getting the full potential of my hardware and specs.

On the other hand, if you just want to try a 64 bit OS you could also just try it out right now and see how you like it.  I am having a blast with the 64 bit version of vmware.

PS: There are so many companies out now that supports 64 bit OSs.  So it will be a piece of cake finding your faves in 64 bit format.  In my own experience Linux has been a better environment for 64 bit applications versus Windows' environment.

I hope that helps some,
Sugi

---

### Post by corredordebolsas on 2010-01-16
Thank you so much for that information!!!! I'll follow your advise and upgrade my ram memory to 4GB and install the 64 bit windows 7. You're terrific guys!!!!

---

### Post by Cclips on 2010-01-16
I actually just converted my Dell 1420 to 64bit, didn't notice any real downside in the change over. All my programs still work, and it runs a bit cooler/faster.

---

### Post by forsaken_pariah on 2010-01-16
I'll probably end up getting flamed for this, but this is my opinion...

From my experience I can tell you that if you DON'T plan on upgrading to 4 gigs of ram or more, I would recommend using a 32-bit system for now, because they tend to have better software support atm.

As for Windows 7, I suppose using 64-bit with >4 gigs of ram would be beneficial, considering the fact that is requires an absolutely sickening minimum of 2 gigs of ram to run, and I can see you reasonably needing all 4 gigs of ram. However, as for Ubuntu, unless you plan on running 700,000 applications at one time, you'll probably never use 4 gigs of ram, and therefore I'd still recommend a 32-bit system.

---

### Post by warfacegod on 2010-01-16
> **corredordebolsas said:**
> Thank you so much for that information!!!! I'll follow your advise and upgrade my ram memory to 4GB and install the 64 bit windows 7. You're terrific guys!!!!

I am aren't I? Why not do a dual boot with 9.10 Karmic 64? You'l get much more use out of that 4 GB in Linux than 7 will give you.

---

### Post by warfacegod on 2010-01-16
> **forsaken_pariah said:**
> I'll probably end up getting flamed for this, but this is my opinion...

From my experience I can tell you that if you DON'T plan on upgrading to 4 gigs of ram or more, I would recommend using a 32-bit system for now, because they tend to have better software support atm.

As for Windows 7, I suppose using 64-bit with >4 gigs of ram would be beneficial, considering the fact that is requires an absolutely sickening minimum of 2 gigs of ram to run, and I can see you reasonably needing all 4 gigs of ram. However, as for Ubuntu, unless you plan on running 700,000 applications at one time, you'll probably never use 4 gigs of ram, and therefore I'd still recommend a 32-bit system.

Aside from netbooks, most computers manufactured today are 64s. Software support for 32 and 64 is pretty much on a level playing field now. Even 6 months ago I would have agreed with you but not today. 32 systems are a dying breed.

NOTICE: This Is Not A Flame. (None the less I wouldn't hold it near your butt.)

---

### Post by forsaken_pariah on 2010-01-16
> **warfacegod said:**
> Aside from netbooks, most computers manufactured today are 64s. Software support for 32 and 64 is pretty much on a level playing field now. Even 6 months ago I would have agreed with you but not today. 32 systems are a dying breed.

NOTICE: This Is Not A Flame. (None the less I wouldn't hold it near your butt.)

Yes I thought so too, but there actually are some programs that still don't fully worl as expected in 64-bit, most notably Adobe Flash Player. I'm still struggling with that one. Other than that, there are some programs I've tried to install that have 32-bit .debs but not for 64-bit. Some of them install from source as is, some need a little configuration, and this one I'm trying won't compile for anything....

So, I must say I still think that, as far as Ubuntu goes, 32-bit (at least for me, anyway) is the way to go.

---

### Post by warfacegod on 2010-01-16
> **forsaken_pariah said:**
> Yes I thought so too, but there actually are some programs that still don't fully worl as expected in 64-bit, most notably Adobe Flash Player. I'm still struggling with that one. Other than that, there are some programs I've tried to install that have 32-bit .debs but not for 64-bit. Some of them install from source as is, some need a little configuration, and this one I'm trying won't compile for anything....

So, I must say I still think that, as far as Ubuntu goes, 32-bit (at least for me, anyway) is the way to go.

You could be right. I was considering state of computer software as a whole not just Ubuntu Linux. My next laptop will be at least 8 GB RAM so thre's no way I'm sticking with 32 but for now 2 GB suits me fine.

---

### Post by forsaken_pariah on 2010-01-16
> **warfacegod said:**
> You could be right. I was considering state of computer software as a whole not just Ubuntu Linux.
Which would be why I said it would be better to use 64-bit windows.
> **warfacegod said:**
> My next laptop will be at least 8 GB RAM so thre's no way I'm sticking with 32 but for now 2 GB suits me fine.
That's kinda ridiculous. I don't see how anybody would need 8 gigs of ram on an average laptop computer. I have 1 gig and I see no reason to need an upgrade (until the dreaded day that I'm forced to upgrade to Windows 7).

---

### Post by HiImTye on 2010-01-16
> **forsaken_pariah said:**
> I'll probably end up getting flamed for this, but this is my opinion...

From my experience I can tell you that if you DON'T plan on upgrading to 4 gigs of ram or more, I would recommend using a 32-bit system for now, because they tend to have better software support atm.

As for Windows 7, I suppose using 64-bit with >4 gigs of ram would be beneficial, considering the fact that is requires an absolutely sickening minimum of 2 gigs of ram to run, and I can see you reasonably needing all 4 gigs of ram. However, as for Ubuntu, unless you plan on running 700,000 applications at one time, you'll probably never use 4 gigs of ram, and therefore I'd still recommend a 32-bit system.
3+GB of RAM*

remember, it's *address space* not just *RAM*. generally, 3.3GiB is the max for 32 bit architecture

and 64 bit has pretty good support. 64 bit has been pushing more mainstream for quite a while now so theres a ton of resources out there now.

---

### Post by Dayofswords on 2010-01-16
> **warfacegod said:**
> Intel(R) Core(TM)2 Duo CPU T5250

That's your processor. I just searched for it on the net. It's a 64. Hurray! for you, you get to have more than 3 GB RAM. Assuming your motherboard will fit it.
i have this in my laptop,


had no idea it was 64-bit, as it came with 32-bit vista

---

### Post by warfacegod on 2010-01-16
> **Dayofswords said:**
> i have this in my laptop,


had no idea it was 64-bit, as it came with 32-bit vista

That happened allot back when 64s where just coming out. Manufacturers found it easier to install 32 on them because of a lack of support from software for 64. Too many customers calling and complaining that their preinstalled Vista64 was misbehaving.

---

### Post by warfacegod on 2010-01-16
> That's kinda ridiculous. I don't see how anybody would need 8 gigs of ram on an average laptop computer. I have 1 gig and I see no reason to need an upgrade (until the dreaded day that I'm forced to upgrade to Windows 7).

The average desktop and laptop, being sold today, has a minimum of 3 GB RAM. 6 - 8 GB is not uncommon by any means. I have 2 GB in my laptop and I'm starting feeling a bit cramped. Wait, no sorry, that's just the walls closing in, my mistake.

---

### Post by cascade9 on 2010-01-16
> **forsaken_pariah said:**
> Yes I thought so too, but there actually are some programs that still don't fully worl as expected in 64-bit, most notably Adobe Flash Player. I'm still struggling with that one. Other than that, there are some programs I've tried to install that have 32-bit .debs but not for 64-bit. Some of them install from source as is, some need a little configuration, and this one I'm trying won't compile for anything....
 
 So, I must say I still think that, as far as Ubuntu goes, 32-bit (at least for me, anyway) is the way to go.
 
 Funny, I'cve never really had any issues with flash on 64bit. Either with the stock 32bit flash version, or the alpha/beta 64bit version. 
 
 Yeah, some people might find it easier to use 32bit. But I'd rather have 64bit, its a got a lot more power for some of the tasks I do quite often (audio/video encoding). Its got a bit of a performance edge over 32bit in a lot of tasks, even mundane stuff like booting. 

> **forsaken_pariah said:**
> That's kinda ridiculous. I don't see how anybody would need 8 gigs of ram on an average laptop computer. I have 1 gig and I see no reason to need an upgrade (until the dreaded day that I'm forced to upgrade to Windows 7).

I disagree. RAM is cheap as chips now (hahaha) and 8GB is never going to hurt. If you do any DVD encoding, use virtual OSes (and half a dozen other fairly common tasks) 8GB isn't a bad idea at all. 

> **warfacegod said:**
> That happened allot back when 64s where just coming out. Manufacturers found it easier to install 32 on them because of a lack of support from software for 64. Too many customers calling and complaining that their preinstalled Vista64 was misbehaving.

Personally, I hate vista. So I'm not being nice to it. 

But all the people I know who had major issues, hardware and software (apart from 'dear gawds this is slow compared to XP' which I dont count) were using 64bit vista. 32bit vista was much better behaved.

---

### Post by warfacegod on 2010-01-16
> Personally, I hate vista. So I'm not being nice to it.

Absolutely, I've basically hated Windows as a whole since the first time I sat down in front of it (XP). It just took me six years to realize it. If I met Windows in a back alley, I'd steal it's wallet, shank it in the short ribs, and leave it there to slowly bleed out.

---

### Post by cascade9 on 2010-01-16
> **warfacegod said:**
> Absolutely, I've basically hated Windows as a whole since the first time I sat down in front of it (XP). It just took me six years to realize it. If I met Windows in a back alley, I'd steal it's wallet, shank it in the short ribs, and leave it there to slowly bleed out.

I actually do like sone version of widows (95 OSR2.1, 98SE, 2000, winXP post SP2). 

The others versions, well, I wouldnt shank it, but steal its wallet...and drugs, for sure (and if you think that winME doesnt walk around with an oz. of weed on it, then its could only be opium, cause its a slow-working dope :P)

---

### Post by warfacegod on 2010-01-16
> **cascade9 said:**
> I actually do like sone version of widows (95 OSR2.1, 98SE, 2000, winXP post SP2). 

The others versions, well, I wouldnt shank it, but steal its wallet...and drugs, for sure (and if you think that winME doesnt walk around with an oz. of weed on it, then its could only be opium, cause its a slow-working dope :P)

My uncle gave me a desktop with a 1 Ghz AMD and .5 GB RAM running WindowsCE? It was barely able to turn on. It's now running 9.10 just fine. A little sluggish occasionally but fine.

---

### Post by cascade9 on 2010-01-16
> **warfacegod said:**
> My uncle gave me a desktop with a 1 Ghz AMD and .5 GB RAM running WindowsCE? It was barely able to turn on. It's now running 9.10 just fine. A little sluggish occasionally but fine.

CE is 'Compact Embedded' (sometimes call 'compact edition'). It probably would have been ME, the specs sound right for a 2000-2002 computer (athlon 1Ghz released in mid-2000).

---

### Post by warfacegod on 2010-01-16
> **cascade9 said:**
> CE is 'Compact Embedded' (sometimes call 'compact edition'). It probably would have been ME, the specs sound right for a 2000-2002 computer (athlon 1Ghz released in mid-2000).

Yeah, that sounds about right. I only saw the Windows logo once. After an hour of, *oh I just don't feel like it today gosh I wish I were a mainframe*, I said "Sorry Unc, but this thing is getting Linux. He's a Windows fan and it irks him to no end that his DVR has a basic Linux OS.

---

### Post by corredordebolsas on 2010-01-16
Ok, I've just installed the 32 bit windows 7 on my laptop, thank you for everything. The thing is that I installed it where my xp was (aside from ubuntu that is on another parcial hard disk) the thing is that it doesn't give me the option to choose from ubuntu or windows to boot my system.
I found a program on windows (msconfig) that let's you configure your start OS, but it doesn't show ubuntu. I actually don't think it's been erased but I don't know how to access and then to program a menu just after the bios to let me choose wich OS I want to start.
Please help guys, I think this would be my last concern... I hope.

---

### Post by warfacegod on 2010-01-16
> **corredordebolsas said:**
> Ok, I've just installed the 32 bit windows 7 on my laptop, thank you for everything. The thing is that I installed it where my xp was (aside from ubuntu that is on another parcial hard disk) the thing is that it doesn't give me the option to choose from ubuntu or windows to boot my system.
I found a program on windows (msconfig) that let's you configure your start OS, but it doesn't show ubuntu. I actually don't think it's been erased but I don't know how to access and then to program a menu just after the bios to let me choose wich OS I want to start.
Please help guys, I think this would be my last concern... I hope.

No ubuntu shouldn't have been erased. After installing Windows you will need to reinstall GRUB. Give me a moment and I'll dig up how to do that.

---

### Post by warfacegod on 2010-01-16
Try this out:

SIMPLEST - Copy GRUB 2 Files from the LiveCD

This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

   1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
   2.

      Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
   3.

      Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".
         1.

            sudo fdisk -l

            If the user isn't sure of the partition, look for one of the appropriate size or formatting.

            Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently. 
   4. Mount the partition containing the Ubuntu installation.

      sudo mount /dev/sdXY /mnt

      Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
   5.

      Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

      sudo grub-install --root-directory=/mnt/ /dev/sdX

      Example: sudo grub-install --root-directory=/mnt/ /dev/sda
   6. Reboot
   7.

      Refresh the GRUB 2 menu with sudo update-grub

---

### Post by corredordebolsas on 2010-01-16
I appreciate the fast response but you lost me...
The thing is that I can't even access to ubuntu (I actually didn't understood the grub and liveCD instructions). The instructions says that you have to do it from the terminal, but the terminal is in ubuntu... so I'm lost. I'm wondering if there's a key (like the F8 key to access safe mode) you can press while the bios starts and the OS will appear. Or I'm wondering if there's something I can do from windows 7 to allow ubuntu to be shown. This is all in case ubuntu still exist.
 
If ubuntu has dissapeared then how can I download and install it from windows in the other partial disk... That's actually the main problem, sorry if that's the solution you already posted but I don't really understand it. Thank you

---

### Post by warfacegod on 2010-01-16
> **corredordebolsas said:**
> I appreciate the fast response but you lost me...
The thing is that I can't even access to ubuntu (I actually didn't understood the grub and liveCD instructions). The instructions says that you have to do it from the terminal, but the terminal is in ubuntu... so I'm lost. I'm wondering if there's a key (like the F8 key to access safe mode) you can press while the bios starts and the OS will appear. Or I'm wondering if there's something I can do from windows 7 to allow ubuntu to be shown. This is all in case ubuntu still exist.
 
If ubuntu has dissapeared then how can I download and install it from windows in the other partial disk... That's actually the main problem, sorry if that's the solution you already posted but I don't really understand it. Thank you

Put your install disc in the drive and restart. Select run ubuntu without making changes. You will be able to use a Terminal that way and then you can carefully follow the instructions above.

---

### Post by corredordebolsas on 2010-01-16
Ohhhhh... ok. Yeah, now I understand. The thing is that I don't have the ubuntu disk, I'll start to download it right now and do what you told me. 
 
Just to be clear, the way you're telling me to start the LiveCD won't delete the files I had saved on ubuntu.

---

### Post by warfacegod on 2010-01-16
> **corredordebolsas said:**
> Ohhhhh... ok. Yeah, now I understand. The thing is that I don't have the ubuntu disk, I'll start to download it right now and do what you told me. 
 
Just to be clear, the way you're telling me to start the LiveCD won't delete the files I had saved on ubuntu.

No, it will not. As long as you choose the "Run Ubuntu without making changes" or "Try Ubuntu...." something like that any way. There will be an icon on the desktop called "Install.." just don't touch it and you will be fine. When you are in the LiveCD (the Trying ubuntu without...), you will be able to get online and come here to read the instructions. Read them carefully and input the commands exactly. Terminal is under Accessories. Again, doing this will not erase any of your files.

---

### Post by pirateghost on 2010-01-16
there is also a program you can install in windows to set up your boot options
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by 3rdalbum on 2010-01-16
> **pirateghost said:**
> there is also a program you can install in windows to set up your boot options
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I don't think that's a good idea, unless it can reinstall GRUB for you.

---

### Post by warfacegod on 2010-01-16
> **pirateghost said:**
> there is also a program you can install in windows to set up your boot options
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

That link appears to be software for modifying Windows bootloader not GRUB2, ubuntu's bootloader. GRUB2 is the problem in this case.

---

### Post by corredordebolsas on 2010-01-17
> **warfacegod said:**
> Try this out:

SIMPLEST - Copy GRUB 2 Files from the LiveCD

This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods.

   1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
   2.

      Open a terminal by selecting Applications, Accessories, Terminal from the menu bar.
   3.

      Determine the partition with the Ubuntu installation. The fdisk option "-l" is a lowercase "L".
         1.

            sudo fdisk -l

            If the user isn't sure of the partition, look for one of the appropriate size or formatting.

            Running sudo blkid may provide more information to help locate the proper partition, especially if the partitions are labeled. The device/drive is designated by sdX, with X being the device designation. sda is the first device, sdb is the second, etc. For most users the MBR will be installed to sda, the first drive on their system. The partition is designated by the Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently. 
   4. Mount the partition containing the Ubuntu installation.

      sudo mount /dev/sdXY /mnt

      Example: sudo mount /dev/sda1 Note: If the user has a separate /boot partition, this must be mounted to /mnt/boot
   5.

      Run the grub-install command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.

      sudo grub-install --root-directory=/mnt/ /dev/sdX

      Example: sudo grub-install --root-directory=/mnt/ /dev/sda
   6. Reboot
   7.

      Refresh the GRUB 2 menu with sudo update-grub


Ok... I've done every step from 1 to 6... the thing is that once i've mounted and installed it on the terminal I reboot. It asks me to extract the cd and then the grub ''menu'' opens (looks just like ms_dos). I supose that's the part when I have to update the grub, it's just that when I enter the ''sudo update-grub'' command it says that is not a valid command. When I press the tab button it shows me all the available commands and sudo is not one of them. I've already tried without the sudo and update is not a valid command also.

I hope this is the last step to have my ubuntu and windows 7 working. Oh yeah, I almost forgot... when I do the ''sudo fdisk -l'' command it shows me this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12042    96727333+   7  HPFS/NTFS
/dev/sda2           12043       14593    20490907+   5  Extended
/dev/sda5           12043       14481    19591236   83  Linux
/dev/sda6           14482       14593      899608+  82  Linux swap / Solaris

My computer only has like 120 GB in the hard disk, so I'm guessing the sda1 is windows7 and the sda2 is linux... but the sda2  is also divided in sda5 and sda6 for linux. I'm just wondering where's the right place to do the mount... I did it over the sda5 and it installed without errors, just asking if it is better to mount it over the sda2.

---

### Post by warfacegod on 2010-01-17
> My computer only has like 120 GB in the hard disk, so I'm guessing the sda1 is windows7 and the sda2 is linux... but the sda2 is also divided in sda5 and sda6 for linux. I'm just wondering where's the right place to do the mount... I did it over the sda5 and it installed without errors, just asking if it is better to mount it over the sda2.

Yes, sda1 is marked NTFS so that is Windows. It looks like sda5 would be Linux which is a bit strange. Normally, I think it should be:

sda1 Windows
sda2 Linux
sda5 Extended
sad6 Swap

But that's ok. It looks like it will work anyway.

Try using:

```
sudo update-grub2
```

---

### Post by corredordebolsas on 2010-01-17
> **warfacegod said:**
> Yes, sda1 is marked NTFS so that is Windows. It looks like sda5 would be Linux which is a bit strange. Normally, I think it should be:

sda1 Windows
sda2 Linux
sda5 Extended
sad6 Swap

But that's ok. It looks like it will work anyway.

Try using:

```
sudo update-grub2
```

I've already tried that and it doesn't work either. There's a list of command I can do... this webpage has almost all of them: [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html) . The main problem now is that the moment I leave the liveCD ubuntu to restart the computer and access windows well... the grub appears and it doesn't even let me open windows. The only way for me to stay connected is to be on the liveCD. I've already tried exit, reboot (going to the bios and changing the OS to run, it is configure for 1.CD/DVD 2.Internal HDD (wich opens the grub) and I don't know what else to do.

If there's no "sudo" command for the grub then what can I do?

---

### Post by warfacegod on 2010-01-17
> **corredordebolsas said:**
> I've already tried that and it doesn't work either. There's a list of command I can do... this webpage has almost all of them: [http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_12.html) . The main problem now is that the moment I leave the liveCD ubuntu to restart the computer and access windows well... the grub appears and it doesn't even let me open windows. The only way for me to stay connected is to be on the liveCD. I've already tried exit, reboot (going to the bios and changing the OS to run, it is configure for 1.CD/DVD 2.Internal HDD (wich opens the grub) and I don't know what else to do.

If there's no "sudo" command for the grub then what can I do?

Do:

```
update-grub2
```

If that doesn't work, can you get into ubuntu? If so try:

```
sudo update-grub2
```

inside Linux.

---

### Post by corredordebolsas on 2010-01-17
> **warfacegod said:**
> Do:

```
update-grub2
```If that doesn't work, can you get into ubuntu? If so try:

```
sudo update-grub2
```inside Linux.

This is what happens when I do it at the terminal in the liveCD:

ubuntu@ubuntu:~$ sudo update-grub2
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

---

### Post by corredordebolsas on 2010-01-17
This is what I do, everything seems to go fine until the grub appears:

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

---

### Post by Sef on 2010-01-17
> Yes, sda1 is marked NTFS so that is Windows. It looks like sda5 would be Linux which is a bit strange. Normally, I think it should be:

sda1 Windows.
sda2 Linux
sda5 Extended
sad6 Swap

The LInux partiton is sda2.  sda5 is the extended partition which is only swap.

---

### Post by warfacegod on 2010-01-17
I think you are going to have to start all over and put GRUB2 on sda2.

---

### Post by corredordebolsas on 2010-01-17
> **warfacegod said:**
> I think you are going to have to start all over and put GRUB2 on sda2.

Ok, I've started all over again an it doesn't let me mount in sda2, it's asking me for a filesystem, I entered "linux" and this happened:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12042    96727333+   7  HPFS/NTFS
/dev/sda2           12043       14593    20490907+   5  Extended
/dev/sda5           12043       14481    19591236   83  Linux
/dev/sda6           14482       14593      899608+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt linux
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by warfacegod on 2010-01-17
> Ok, I've started all over again an it doesn't let me mount in sda2, it's asking me for a filesystem, I entered "linux" and this happened:


Then either sda5 was indeed correct or you need to use sda1. Be careful if you try sda1.

---

### Post by corredordebolsas on 2010-01-17
> **warfacegod said:**
> I think you are going to have to start all over and put GRUB2 on sda2.
{

I write what the grub says when I reboot the computer:

GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>

}

Note= When I press TAB this happens=

{

sh:grub> (TAB)
Possible commands are:
 . 915resolution [ acpi background_image badram blocklist boot cat chainloader cmp configfile cpuid crc date drivemap dump echo efiemo_loadcore efiemo_pnvram efiemo_prepare efiemo_unload exit export false freebsd freebsd_loadenv freebsd_module freebsd_module_elf gptsync halt handler hdparm hello help hexdump initrd initrd16 insmod keystatus linux linux16 list_env load_env loadfont loopback ls lsfonts lsmod lspci module multiboot netbsd openbsd parser.rescue parser.sh parttool password play probe pxe read read_byte read_dword read_word reader.normal reader.rescue reboot rmmud root save_env search serial set sleep source terminal_input terminal_input.at_keyboard terminal_input.console terminal_input.serial terminal_input.usb_keyboard terminal_output terminal_output.console terminal_output.gfxterm terminal_output.serial terminal_output.vga terminal_output.vga_text terminfo test true unset usb vbeinfo vbetest videotest write_byte write_dword write_word xnu_devtree xnu_kernel xnu_kext xnu_kextdir xnu_mkext xnu_ramdisk xnu_resume xnu_splash xnu_uuid zfs_bootfs zfsinfo

}

Note= When I type sudo update-grub this happens=

{

sh:grub> sudo update-grub
error: unknown command 'sudo'

}

The same happens when I type it without the sudo, or with spaces of with grub2...
And as I posted earlier, it is the only interface I get because I won't let me open windows... when i type 'exit' or 'boot' (I don't remember which one it was), a beep sounds and it says something like=

press F1 to boot again, press F2 for something else and F5 to diagnose... if I press F1 the same beep sounds and nothing happens, for F2 it 'thinks' for a moment and then says that it can't or something and for F5 it doesn't let me do anything else and it freezes.

Please help, I transfer all my files to the ubuntu partial disk and now I can't access... I mean, I can reinstall windows 7 but I don't want to reinstall ubuntu because of my files... Thanks in advance for any help

---

### Post by warfacegod on 2010-01-17
The instructions I posted come directly from the Ubuntu documentation. At this point I can only tell you what I would do. I would use the LiveCD To transfer all of my files to an external hard drive or to the Windows partition if no external was available, being very careful to get everything. Then I would reinstall Ubuntu.

Installing Windows after Ubuntu has always been plagued by isssues such as this. It is always recommended that in a dual boot situation that Linux be installed second.

---

### Post by Kai69 on 2010-01-17
Sorry to butt in i have a question i run a dell xps m1330. What does the 64 bit os do to hardware i mean things like the graphics card does it run hotter etc. I did install 9.10 64 bit last night and then bottled it and went back to 32 bit i do have 4 gb ram but if things run hotter in 64 bit then i dont want to burn out my hardware nvidia graphics card has had overheat problems on this laptop
The reason i reinstalled 32 bit is when in 64 bit the fan started running a lot faster and the area where the HDD sits was a lot warmer i also didnt find anything running faster files and folders still opened at the same sort of speed as before. 
[corredordebolsas]("http://ubuntuforums.org/member.php?u=995471") I hope you get your setup sorted out I still think W7 is a girls os (to many flowery bits) and it still crashes lol

---

### Post by warfacegod on 2010-01-17
> **Kai69 said:**
> Sorry to butt in i have a question i run a dell xps m1330. What does the 64 bit os do to hardware i mean things like the graphics card does it run hotter etc. I did install 9.10 64 bit last night and then bottled it and went back to 32 bit i do have 4 gb ram but if things run hotter in 64 bit then i dont want to burn out my hardware nvidia graphics card has had overheat problems on this laptop
The reason i reinstalled 32 bit is when in 64 bit the fan started running a lot faster and the area where the HDD sits was a lot warmer i also didnt find anything running faster files and folders still opened at the same sort of speed as before. 
[corredordebolsas]("http://ubuntuforums.org/member.php?u=995471") I hope you get your setup sorted out I still think W7 is a girls os (to many flowery bits) and it still crashes lol

As far as I know your system shouldn't run hotter on 64 Bit aside from some additional *minor* heat from using all of the installed RAM. If 32 Bit is just as responsive with 3 GB RAM, then by all means, have at it. Your "hotter" equipment issues sound more like improperly running drivers than it being 64 Bit in and of itself.

---

### Post by pirateghost on 2010-01-17
> **3rdalbum said:**
> I don't think that's a good idea, unless it can reinstall GRUB for you.
except that it will allow you to use windows boot loader and boot to ubuntu...i used it on a vista install one time....

---

### Post by Kai69 on 2010-01-17
Thank you I think I will try 64 bit again and this time run it for a few days to see how it gets on not 2 hours hopefully it will settle down. Mind you i now see 3.9gb kernel is 2.6.31-17-generic pae since i went back to 32 bit.

---

### Post by warfacegod on 2010-01-17
> **Kai69 said:**
> Thank you I think I will try 64 bit again and this time run it for a few days to see how it gets on not 2 hours hopefully it will settle down. Mind you i now see 3.9gb kernel is 2.6.31-17-generic pae since i went back to 32 bit.

```
sudo update-grub2
```

---

### Post by Kai69 on 2010-01-17
[attach]143954[/attach]

---

### Post by warfacegod on 2010-01-17
> **Kai69 said:**
> [attach]143954[/attach]

Okay, great. Now reboot to see if the kernel header is still there.

---

### Post by Kai69 on 2010-01-17
Yes its still there but had to reboot twice first reboot lost panel  happens every now and again dont know why

---

### Post by theozzlives on 2010-01-17
I didn't read the whole thread, just wanted to put my 2 cents in. Why not run 64 bit Ubuntu, with 4 GB RAM, and put 32 bit 7 in a VirtualBox? Just give Windows a Gig.

---

### Post by warfacegod on 2010-01-17
> **Kai69 said:**
> Yes its still there but had to reboot twice first reboot lost panel  happens every now and again dont know why

That means that the kernel is still installed on your system. If it doesn't bother you then leave it.

---

### Post by Kai69 on 2010-01-17
Its ok im going to put 64bit on my laptop during the week and see how it goes i only use ubuntu now so should only take me 2 hours to install everything i was just concerned about the hardware being overworked im running a dell xps m1330 2007model. Im still a newbe to linux os but i love ubuntu my other pcs run vista and w7 but this is my toy and i havent touched them since apart from when something goes wrong the missus wont let me put ubuntu on the other pcs yet lol :D
Thanks for the help :D

---

### Post by warfacegod on 2010-01-17
> **Kai69 said:**
> Its ok im going to put 64bit on my laptop during the week and see how it goes i only use ubuntu now so should only take me 2 hours to install everything i was just concerned about the hardware being overworked im running a dell xps m1330 2007model. Im still a newbe to linux os but i love ubuntu my other pcs run vista and w7 but this is my toy and i havent touched them since apart from when something goes wrong the missus wont let me put ubuntu on the other pcs yet lol :D
Thanks for the help :D

If it's your toy then experiment away. (The missus had no choice about her computer, I did it while she was at work) I wouldn't worry too much about over heating. Linux will do an emergency shutdown if things get too hot, although I've never seen it happen.

---

### Post by Kai69 on 2010-01-17
Thats all ive been doing since i used ubuntu i still cant use terminal unless i cut and paste but i love the fact you can do so much that you couldnt do with windows and i dont need to install drivers etc everything just works out of the box LOL 
Thanks again ...:D

---

### Post by corredordebolsas on 2010-01-17
Ok, I just went to the bookstore and bought a linux book but it is pretty basic. It said that a program called gparted will help me edit partitions and reinstall ubuntu... the thing is that I've managed to open it after granting root privileges using gksudo and then opening gparted... this is what I see when I open it and click the information from the sda2 (which contains both linux and linux swap) and the information from sda5. The book I bought doesn't say what to do next and I was wondering if any of you would know.

[ATTACH]143971[/ATTACH]

[ATTACH]143972[/ATTACH]

[ATTACH]143973[/ATTACH]

Now, you may notice that the only partition that has anything mounted is this one (sda2).

---

### Post by warfacegod on 2010-01-17
If you want to reinstall Ubuntu then use the LiveCD and use Gparted to delete sda2. You can't do that inside your ubuntu install because you can't delete the partition you are using.

---

### Post by Kai69 on 2010-01-18
Hi [warfacegod]("http://ubuntuforums.org/member.php?u=537200") ive just installed 64bit ubuntu but it is running so slow have you any sugestions basicly uploading downloading from inet and installing software even from software centre

---

### Post by warfacegod on 2010-01-18
> **Kai69 said:**
> Hi [warfacegod]("http://ubuntuforums.org/member.php?u=537200") ive just installed 64bit ubuntu but it is running so slow have you any sugestions basicly uploading downloading from inet and installing software even from software centre

Howdy Kai69,

Start a new thread in General help with details about what it's doing and PM me a link to it. That way we don't keep hijacking corredordebolsas's thread. Thanks.

---

### Post by Kai69 on 2010-01-19
HI Warfacegod    [http://ubuntuforums.org/showthread.php?p=8692444#post8692444](http://ubuntuforums.org/showthread.php?p=8692444#post8692444)   sorry

---

