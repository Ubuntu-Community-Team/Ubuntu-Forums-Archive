---
title: "Unusable lucid..."
date: 2010-05-05
forum: General Help
---

### Post by J V on 2010-05-05
Gripes with lucid that each one make it unusable:


[LIST]
[*]Mouse tends to stop moving (It jerks back and forth rather than move in a straight line)
[*]Firefox stops respond to keyboard - I had to kill the process and restart just to be able to type this as for the onboard keyboard - what a joke... When firefox stops responding I have to juggle some processes and somehow run a command before regaining keyboard control (The whole system - even volume buttons don't respond)
[*]Unlocking the screen re-locks it (After I unlock the screen starts to darken immediately and goes into screen-saver mode)
[*]Screensaver imminent (When screen starts to darken no input at all will stop it going into screensaver (And then I have to deal with problem #3)
[*]Compiz crash - Compiz tends to crash for no reason at all at random times
[/LIST]
The middle 3 of these problems only started occurring recently (After final release)

Has anyone heard of these? I've googled but found no concrete answer...

---

### Post by oneindelijk on 2010-05-05
Is this after a fresh install or an upgrade ?

---

### Post by physic.dude on 2010-05-05
The only one I get is the thing with Firefox. 
Firefox stops respond to keyboard and mouse. - I keep the "Force Quit Button" in my menu bar at the bottom for just that reason.

and I have a fresh install.

---

### Post by ajgreeny on 2010-05-05
What hardware are you using?

Apart from a minor problem of hot running with an old ati video card, I have found Lucid very fast and good.  If an nvidia card was in my machines it would be a real winner I think.

---

### Post by J V on 2010-05-05
Heres an lshw - Also, this is a fresh install (But I installed a daily from just before RC and updated from there)

These problems are fairly serious, high priority is an understatement when the LTS release completely stops functioning on a regular basis...

```
jubuntu                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2006MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1998MHz
          capacity: 1998MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: 82Q35 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82Q35 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:f0000000-f2ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff(prefetchable) memory:f0000000-f1ffffff ioport:1100(size=128)
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: 82Q35 Express MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f3026900-f302690f
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: 82Q35 Express PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide cap_list
             configuration: latency=0
             resources: ioport:2230(size=8) ioport:2268(size=4) ioport:2238(size=8) ioport:226c(size=4) ioport:21e0(size=16)
        *-communication:1
             description: Serial controller
             product: 82Q35 Express Serial KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:2240(size=8) memory:f3024000-f3024fff
        *-network
             description: Ethernet interface
             product: 82566DM-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 02
             serial: 00:0f:fe:ed:af:35
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.3-1 ip=192.168.2.100 latency=0 multicast=yes
             resources: irq:27 memory:f3000000-f301ffff memory:f3025000-f3025fff ioport:2100(size=32)
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:2120(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:2140(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:f3026000-f30263ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f3020000-f3023fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:80000000-801fffff memory:80200000-803fffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:80400000-805fffff memory:80600000-807fffff(prefetchable)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:2160(size=32)
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:2180(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:21a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:f3026400-f30267ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f3100000-f31fffff
           *-network
                description: Wireless interface
                product: RT2800 802.11n PCI
                vendor: RaLink
                physical id: 9
                bus info: pci@0000:07:09.0
                logical name: wlan0
                version: 00
                serial: 00:0c:f6:43:b0:de
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
                resources: irq:21 memory:f3100000-f310ffff
        *-isa
             description: ISA bridge
             product: 82801IO (ICH9DO) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:21f0(size=16) ioport:2200(size=16)
        *-ide:2
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:2258(size=8) ioport:2278(size=4) ioport:2260(size=8) ioport:227c(size=4) ioport:2210(size=16) ioport:2220(size=16)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by romeug on 2010-05-05
I had similar problems with a touchpad in 9.10, seemed that double fingered scrolling was set, acceleration was low and sensitivity high, alleviated with removing double finger for edge, high acceleration with low sensitivity.  I have seen physical mice do similar motion issues on other platforms, but they were mechanical problems with the mice.
I have a slightly different problem with my screensaver that may be related, as opening the configuration file under system/preferences causes a crash when i change from the black screen up top to another- i just reinstalled the gnome screensaver but have not tested it.  if it does not help i may change to the xscreensaver.

---

### Post by Jonny87 on 2010-05-05
I too have had issues with 10:04. At least one major one that I'm still waiting for answers for.
[http://ubuntuforums.org/showthread.php?t=1474226](http://ubuntuforums.org/showthread.php?t=1474226)

Others is the screen goes black when switching users so I havent done it since, I fully log out now. Pitivi freezes up in mid use.  There was a fault in changing permissions. When you right click file/folder click "Properties" then go to the "Permissions" tab, change permissions accordingly, then click _the button near the bottom to apply all to sub-folders and files_, then when finish and go to check it, it doesn't apply to all sub-folders and files. I had use the command line.

---

### Post by J V on 2010-05-08
bump?

---

