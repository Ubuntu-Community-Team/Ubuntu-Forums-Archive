---
title: "crashes"
date: 2010-06-09
forum: General Help
---

### Post by ankit.vader on 2010-06-09
i have lucid, and it crashes sometimes. it just stops responding. it  was not happening earlier & i dont know what i did to cause crashes. non-crash tendency of linux was the potential reason behind switching to ubuntu. 
Although i have provided very little info( thats because i dont know much), but can anyone help me with that??

---

### Post by hansdown on 2010-06-09
Hi ankit.vader.

Are you using any particular application when this happens?

---

### Post by ankit.vader on 2010-06-09
> Are you using any particular application when this happens?

no, but browsers are common in all crashes. this includes firefox, chromium and epiphany.

---

### Post by hansdown on 2010-06-09
> **ankit.vader said:**
> no, but browsers are common in all crashes. this includes firefox, chromium and epiphany.

I only have firefox, right now.

If you click tools> add-ons> plugins, do you have shockwave flash installed?

---

### Post by ankit.vader on 2010-06-09
yes i do. is that the problem?

---

### Post by hansdown on 2010-06-09
> **ankit.vader said:**
> yes i do. is that the problem?

Probably not. I was hoping for something easy.

Could you provide some information about your hardware?

Click applications> accessories> terminal.

Copy and paste this, then hit enter.

```
lshw
```

This should give some info for others to help.

---

### Post by ankit.vader on 2010-06-10
output of lshw, hope this helps..

```

ankit-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3015MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.2
          serial: 0000-06F2-0000-0000-0000-0000
          size: 1733MHz
          capacity: 1733MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl e:
st tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
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
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
           resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d4200000-d427ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:d4300000-d433ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
     width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d4280000-d42fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d4340000-d4343fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
   version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:d2000000-d3ffffff ioport:d0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:d4000000-d40fffff memory:d4600000-d47fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
  vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:1b:77:2e:fa:7a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=10.71.244.36 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:27 memory:d4000000-d4000fff
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
 resources: irq:26 ioport:5000(size=4096) memory:d4800000-d49fffff memory:d4a00000-d4bfffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
  capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
 clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d4544000-d45443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
 width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:3000(size=4096) memory:d4100000-d41fffff memory:d8000000-dbffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:1b:38:03:f8:3f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:21 ioport:3000(size=256) memory:d4100000-d41000ff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:d4102000-d4102fff ioport:3400(size=256) ioport:3800(size=256) memory:d8000000-dbffffff(prefetchable) memory:dc000000-dfffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
resources: irq:22 memory:d4100800-d4100fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d4100400-d41004ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
configuration: latency=0
                resources: memory:d4101000-d41010ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d4101400-d41014ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
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
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)

```

---

### Post by hansdown on 2010-06-10
It all looks good. I try to stay with intel.

What happens when you have a crash?

Can you still use your keyboard and mouse?

---

### Post by ankit.vader on 2010-06-10
> What happens when you have a crash?

i cannot use anything. everything stops responding. i've to power off and then start..

---

### Post by hansdown on 2010-06-10
> **ankit.vader said:**
> i cannot use anything. everything stops responding. i've to power off and then start..

Until someone can help fix this, you need to stop using the power button to shut down. This can lead to* file corruption.*= A reinstall.

Could you please click system> preferences> power management> general.

Please change the preference of "when the power button is pressed:", to "shutdown".

I wasn't able to see what graphics controller you are using.

Could you post that?

---

### Post by ankit.vader on 2010-06-11
hope this helps..

```
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Lenovo Device 3801
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

---

### Post by hansdown on 2010-06-11
I may be going in the wrong direction.

[http://www.google.com/search?client=ubuntu&channel=fs&q=Intel+Corporation+Mobile+945GM%2FGMS%2C+943%2F940GML+in+ubuntu+10.04&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Intel+Corporation+Mobile+945GM%2FGMS%2C+943%2F940GML+in+ubuntu+10.04&ie=utf-8&oe=utf-8)

---

### Post by hansdown on 2010-06-12
I just had a similar experience.

Everything greyed-out on the screen. I was able to right click the site in the bottom, left toolbar and close firefox.

I'm also seeing a lot of bug reports.

[http://www.google.com/search?client=ubuntu&channel=fs&q=firefox+freezes+in+ubuntu+10.04&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=firefox+freezes+in+ubuntu+10.04&ie=utf-8&oe=utf-8)

---

### Post by ankit.vader on 2010-06-29
these random crashes have hace started again. is there a way, wherein i do not have to use power button. like Ctrl+Alt+Del in windows

---

### Post by hansdown on 2010-06-29
The power button is safe, as long as you change the preferences in power management.

Could you please click system> preferences> power management> general.

Please change the preference of "when the power button is pressed:", to "shutdown".

If you are able to use your keyboard,try this.

[http://www.unixmen.com/linux-tutorials/768-recover-from-a-frozen-system-with-the-magic-sysrq-key-howto](http://www.unixmen.com/linux-tutorials/768-recover-from-a-frozen-system-with-the-magic-sysrq-key-howto)

ctrl+alt+del no longer works in ubuntu.

It is now, right alt+print screen+k

This will reboot back to the login window.

---

### Post by mbuotidem on 2010-06-30
have you tried updating your kernel to the latest version? it may help. see : [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787), the last page.

---

### Post by ankit.vader on 2010-06-30
> have you tried updating your kernel to the latest version?

yes i'm currently using 2.6.32.22. is that the latest version?

---

