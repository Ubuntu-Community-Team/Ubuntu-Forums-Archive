---
title: "experiencing a lot of desktop freezes on Lucid. Any ideas?"
date: 2010-06-23
forum: General Help
---

### Post by shantiq on 2010-06-23
[B][COLOR="Blue"]experiencing a lot of desktop freezes on Lucid. Any ideas?

it goes fine for a while then i cannot minimize or maximize

Sometimes i can open a new window from the top but often not



Any suggestions?  [/COLOR][/B]

---

### Post by mikewhatever on 2010-06-23
Posting your computer specs would have been nice.

---

### Post by Rubi1200 on 2010-06-23
If you are running Compiz try temporarily disabling it and see if the problem goes away/is reduced.

---

### Post by shantiq on 2010-06-23
> **mikewhatever said:**
> Posting your computer specs would have been nice.

[COLOR=Blue][B]hi there mike goodpoint     so i did lshw   my machine is a packard-bell from 3 years ago 

[/B][/COLOR][CENTER][INDENT][INDENT][INDENT][LEFT][COLOR=Blue]**[COLOR=Sienna]shantiq@shantiq-desktop:~$ lshw[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]WARNING: you should run this program as super-user.[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]shantiq-desktop           [/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]    description: Computer[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]    width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]  *-core[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       description: Motherboard[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       physical id: 0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-memory[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: System memory[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          size: 2455MiB[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-cpu[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: AMD Athlon(tm) 64 Processor 3400+[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: Advanced Micro Devices [AMD][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: cpu@0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 15.15.2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          size: 2200MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          capacity: 2200MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 64 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-cache:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: L1 cache[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             size: 128KiB[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-cache:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: L2 cache[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             size: 512KiB[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-pci:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: Host bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: RS480 Host Bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 100[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: pci@0000:00:00.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 10[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-pci:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: PCI bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: RS480 PCI Bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:01.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: pci bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: ioport:7000(size=4096) memory:ff200000-ff2fffff ioport:cff00000(size=268435456)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]           *-display[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                description: VGA compatible controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                product: RS480 [Radeon Xpress 200G Series][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                physical id: 5[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                bus info: pci@0000:01:05.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                capabilities: bus_master cap_list rom[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                configuration: driver=radeon latency=64 mingnt=8[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                resources: irq:17 memory:d0000000-d7ffffff(prefetchable) ioport:7800(size=256) memory:ff2f0000-ff2fffff memory:ff2c0000-ff2dffff(prefetchable)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-ide:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: IDE interface[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 Serial ATA Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 11[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:11.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: ide bus_master cap_list rom[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=sata_sil latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:ff6ffc00-ff6ffdff memory:ff600000-ff67ffff(prefetchable)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-ide:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: IDE interface[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 Serial ATA Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 12[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:12.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: ide bus_master cap_list rom[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=sata_sil latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:ff6ff800-ff6ff9ff memory:ff580000-ff5fffff(prefetchable)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-usb:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: USB Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 USB Host Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 13[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:13.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=ohci_hcd latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:19 memory:ff6fe000-ff6fefff[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-usb:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: USB Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 USB Host Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 13.1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:13.1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=ohci_hcd latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:19 memory:ff6fd000-ff6fdfff[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-usb:2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: USB Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 USB2 Host Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 13.2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:13.2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=ehci_hcd latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:19 memory:ff6fc000-ff6fcfff[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-serial[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: SMBus[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 SMBus Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 14[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:14.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 10[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=piix4_smbus latency=0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:0 ioport:b00(size=16) memory:9c100000-9c1003ff[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-ide:2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: IDE interface[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 IDE Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 14.1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:14.1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             logical name: scsi1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: ide bus_master cap_list emulated[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=pata_atiixp latency=64[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]           *-cdrom[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                description: DVD writer[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                product: DVD_RW ND-3550A[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                vendor: _NEC[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                physical id: 0.0.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                bus info: scsi@1:0.0.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/cdrom[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/cdrw[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/dvd[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/dvdrw[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/scd0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: /dev/sr0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                version: 1.52[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                serial: [_NEC    DVD_RW ND-3550A 1.5205100300[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                capabilities: removable audio cd-r cd-rw dvd dvd-r[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                configuration: ansiversion=5 status=nodisc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-isa[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: ISA bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 PCI-ISA Bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 14.3[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:14.3[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: isa bus_master[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: latency=0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-pci:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: PCI bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 PCI-PCI Bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 14.4[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:14.4[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: pci bus_master[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: ioport:8000(size=4096) memory:ff300000-ff3fffff memory:9c000000-9c0fffff(prefetchable)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]           *-communication[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                description: Modem[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                product: SmartLink SmartPCI562 56K Modem[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                vendor: Smart Link Ltd.[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                physical id: 0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                bus info: pci@0000:02:00.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                version: 04[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                configuration: driver=serial latency=64 maxlatency=62 mingnt=1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                resources: irq:20 memory:ff3ff000-ff3fffff ioport:8800(size=256)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]           *-network[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                description: Ethernet interface[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                product: RTL-8139/8139C/8139C+[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                vendor: Realtek Semiconductor Co., Ltd.[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                physical id: 3[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                bus info: pci@0000:02:03.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                logical name: eth0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                version: 10[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                serial: 00:13:d3:b6:0d:bb[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                capabilities: bus_master cap_list rom ethernet physical[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=81.98.191.227 latency=64 maxlatency=64 mingnt=32 multicast=yes[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                resources: irq:20 ioport:8400(size=256) memory:ff3fec00-ff3fecff memory:9c000000-9c00ffff(prefetchable)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]           *-firewire[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                description: FireWire (IEEE 1394)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                vendor: VIA Technologies, Inc.[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                physical id: 4[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                bus info: pci@0000:02:04.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                version: 80[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                configuration: driver=ohci1394 latency=64 maxlatency=32[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]                resources: irq:21 memory:ff3fe000-ff3fe7ff ioport:8c00(size=128)[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]        *-multimedia[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             description: Multimedia audio controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             product: IXP SB400 AC'97 Audio Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             vendor: ATI Technologies Inc[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             physical id: 14.5[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             bus info: pci@0000:00:14.5[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             version: 01[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             clock: 66MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             capabilities: bus_master cap_list[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]             resources: irq:17 memory:ff6ff400-ff6ff4ff[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-pci:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: Host bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: Advanced Micro Devices [AMD][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 101[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: pci@0000:00:18.0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-pci:2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: Host bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: K8 [Athlon64/Opteron] Address Map[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: Advanced Micro Devices [AMD][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 102[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: pci@0000:00:18.1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-pci:3[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: Host bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: K8 [Athlon64/Opteron] DRAM Controller[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: Advanced Micro Devices [AMD][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 103[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: pci@0000:00:18.2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]     *-pci:4[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          description: Host bridge[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          product: K8 [Athlon64/Opteron] Miscellaneous Control[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          vendor: Advanced Micro Devices [AMD][/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          physical id: 104[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          bus info: pci@0000:00:18.3[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          version: 00[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          width: 32 bits[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          clock: 33MHz[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          configuration: driver=k8temp[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]          resources: irq:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]  *-scsi:0[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       physical id: 1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       bus info: scsi@6[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       logical name: scsi6[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       capabilities: scsi-host[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       configuration: driver=usb-storage[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]  *-scsi:1[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       physical id: 2[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       bus info: scsi@7[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       logical name: scsi7[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       capabilities: scsi-host[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]       configuration: driver=usb-storage[/COLOR]**[/COLOR]
[COLOR=Blue]**[COLOR=Sienna]shantiq@shantiq-desktop:~$ [/COLOR]**[/COLOR]
[/LEFT]
[/INDENT][/INDENT][/INDENT][/CENTER]

---

### Post by shantiq on 2010-06-23
> **Rubi1200 said:**
> If you are running Compiz try temporarily disabling it and see if the problem goes away/is reduced.


[B][COLOR=Blue]yes rubi compiz is installed by default

2 questions if you do not mind

how do I disable it ?   remove it from synaptic/?   or is there code i can enter in terminal and if so can you share it?

how will it affect everything else?   do i need to have it at all?

this is from the synaptic

[/COLOR][/B][INDENT][INDENT][LEFT]> Compiz brings to life a variety of visual effects that make the Linux
desktop easier to use, more powerful and intuitive, and more accessible
for users with special needs.

This metapackage provides the components necessary for running compiz. It
provides the compiz core, a set of standard plugins, a window decorator
using the Gtk toolkit and the files necessary to integrate compiz with the
GNOME desktop environment.


[COLOR=Blue]**so maybe it can come off altogether?**[/COLOR]
[/LEFT]
[/INDENT][/INDENT][B][COLOR=Blue]



[/COLOR][/B]

---

### Post by luctor on 2010-06-23
[B][COLOR="Blue"]
1) Press ALT-F2, this will bring up the 'run' box
2) Type metacity --replace
3) press enter
The screen may flicker for a few seconds and now compiz should be disabled.
[/COLOR][/B]

---

### Post by shantiq on 2010-06-23
[COLOR=Blue]**thank you Luctor will report if any changes.  :p**[/COLOR]

---

### Post by Rubi1200 on 2010-06-23
> **shantiq said:**
> [B][COLOR=Blue]yes rubi compiz is installed by default

2 questions if you do not mind

how do I disable it ?   remove it from synaptic/?   or is there code i can enter in terminal and if so can you share it?

how will it affect everything else?   do i need to have it at all?

this is from the synaptic

[/COLOR][/B][INDENT][INDENT][LEFT]


[COLOR=Blue]**so maybe it can come off altogether?**[/COLOR]
[/LEFT]
[/INDENT][/INDENT][B][COLOR=Blue]



[/COLOR][/B]

Compiz is eye-candy; the effects are nice but you don't *need* it to run your system. I have it turned off and have noticed that RAM usage is significantly lower as a result.

---

### Post by shantiq on 2010-06-23
[COLOR=Blue]**cool thanx turned it off it seems to have cured it**[/COLOR]:p

---

### Post by shantiq on 2010-06-23
[B][COLOR="Blue"]Hummm  only it did not


still freezes


especially when i use rosegarden 10.02 which is a high CPU user    up to 75% on my machine

could it be a factor?


not sure it is that anyway

any other suggestions?[/COLOR][/B]

---

