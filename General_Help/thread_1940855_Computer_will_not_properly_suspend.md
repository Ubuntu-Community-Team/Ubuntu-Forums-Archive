---
title: "Computer will not properly suspend"
date: 2012-03-14
forum: General Help
---

### Post by awidearray on 2012-03-14
I am having trouble getting my computer to suspend. I am using Ubuntu 11.10. When I suspend the computer, it does not wake up from being suspended and I have to restart my computer. Also, when I close the lid, I have set it to suspend in "Advanced Settings" but it does nothing when I close the lid.

I am an Asus a53E laptop. The processor is an Intel® Core™ i5-2430M CPU @ 2.40GHz × 4. Graphics is Intel® Sandybridge Mobile x86/MMX/SSE2.

---

### Post by matt_symes on 2012-03-14
Hi

Open a terminal and type

```
acpi_listen
```

Close the lid and wait five seconds. Re-open the lid. Is there anything displayed on the terminal ?

You may see output similar (but not necessarily the same) to this.

```
matthew@matthew-Aspire-7540:~$ acpi_listen
button/lid LID0 00000080 00000007
battery BAT0 00000081 00000001
battery BAT0 00000081 00000001
```

You may also see nothing but the command you typed in (acpi_listen).

Press ctrl + c to stop acpi_listen in the terminal.

Also post back the results of these command

```
cat /var/log/pm-suspend.log | tail -n 100
```

and 

```
grep "PM:" /var/log/syslog | tail -n 100
```

Post the output between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by awidearray on 2012-03-14
Thank you for the reply. 

I must have changed something last night when I was trying to fix it. Now when I close the lid, it does suspend but I am still having trouble waking up the computer. It doesn't shut down but there seems to be nothing that I can do to get the computer to respond other than holding down the power button for about 5 seconds and restarting the computer. It just stays on a black screen until I manually shut it off.

The same thing happens when I use the menu in the upper-right corner to suspend the computer.

---

### Post by matt_symes on 2012-03-14
Hi

Post the log files. They may hold clues.

Can you also post the output of

```
lshw
```

Kind regards

---

### Post by awidearray on 2012-03-14
Here is the output of lshw:


```
gregslaptop@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2813MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          size: 2401MHz
          capacity: 2401MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=3
        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 3.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 3.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 3.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 3.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 3.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 3.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 3.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 3.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 3.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 3.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 3.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 3.10
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:50 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:dfc0b000-dfc0b00f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:dfc08000-dfc083ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:51 memory:dfc00000-dfc03fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:df200000-dfbfffff ioport:d2100000(size=10485760)
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:c000(size=4096) memory:de800000-df1fffff ioport:d1600000(size=10485760)
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 74:2f:68:14:fe:92
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 ioport:c000(size=256) memory:de800000-de803fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:b000(size=4096) memory:dde00000-de7fffff ioport:d0b00000(size=10485760)
           *-usb
                description: USB Controller
                product: ASM1042 SuperSpeed USB Host Controller
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:dde00000-dde07fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:a000(size=4096) memory:dd400000-dddfffff ioport:d0000000(size=10485760)
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: c0
                serial: 14:da:e9:cb:41:48
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
                resources: irq:52 memory:dd400000-dd43ffff ioport:a000(size=128)
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:dfc07000-dfc073ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:e0b0(size=8) ioport:e0a0(size=4) ioport:e090(size=8) ioport:e080(size=4) ioport:e060(size=32) memory:dfc06000-dfc067ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dfc05000-dfc050ff ioport:e040(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by matt_symes on 2012-03-14
Hi

Please use code tags. That is so difficult to read.

[noparse]```
To use code tags wrap your test like this
```[/noparse]

to get output like this

```
To use code tags wrap your test like this
```

That is much easier to read.  You can also use the # button on the toolbar above where you type your message.

Can you edit your last post please.

Take pity on a tired pair of eyes.

Kind regards

---

### Post by awidearray on 2012-03-14
OK, sorry about that. Log files are Greek to me so I don't really know what is or is not easy to read.

```
gregslaptop@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu 
description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 0
size: 2813MiB
*-cpu
product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
vendor: Intel Corp.
physical id: 1
bus info: cpu@0
version: 6.10.7
serial: 0002-06A7-0000-0000-0000-0000
size: 2401MHz
capacity: 2401MHz
width: 64 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
configuration: id=3
*-logicalcpu:0
description: Logical CPU
physical id: 3.1
width: 64 bits
capabilities: logical
*-logicalcpu:1
description: Logical CPU
physical id: 3.2
width: 64 bits
capabilities: logical
*-logicalcpu:2
description: Logical CPU
physical id: 3.3
width: 64 bits
capabilities: logical
*-logicalcpu:3
description: Logical CPU
physical id: 3.4
width: 64 bits
capabilities: logical
*-logicalcpu:4
description: Logical CPU
physical id: 3.5
width: 64 bits
capabilities: logical
*-logicalcpu:5
description: Logical CPU
physical id: 3.6
width: 64 bits
capabilities: logical
*-logicalcpu:6
description: Logical CPU
physical id: 3.7
width: 64 bits
capabilities: logical
*-logicalcpu:7
description: Logical CPU
physical id: 3.8
width: 64 bits
capabilities: logical
*-logicalcpu:8
description: Logical CPU
physical id: 3.9
width: 64 bits
capabilities: logical
*-logicalcpu:9
description: Logical CPU
physical id: 3.a
width: 64 bits
capabilities: logical
*-logicalcpu:10
description: Logical CPU
physical id: 3.b
width: 64 bits
capabilities: logical
*-logicalcpu:11
description: Logical CPU
physical id: 3.c
width: 64 bits
capabilities: logical
*-logicalcpu:12
description: Logical CPU
physical id: 3.d
width: 64 bits
capabilities: logical
*-logicalcpu:13
description: Logical CPU
physical id: 3.e
width: 64 bits
capabilities: logical
*-logicalcpu:14
description: Logical CPU
physical id: 3.f
width: 64 bits
capabilities: logical
*-logicalcpu:15
description: Logical CPU
physical id: 3.10
width: 64 bits
capabilities: logical
*-pci
description: Host bridge
product: 2nd Generation Core Processor Family DRAM Controller
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 09
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-intel
resources: irq:0
*-display
description: VGA compatible controller
product: 2nd Generation Core Processor Family Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 09
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:50 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
*-communication
description: Communication controller
product: 6 Series/C200 Series Chipset Family MEI Controller #1
vendor: Intel Corporation
physical id: 16
bus info: pci@0000:00:16.0
version: 04
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=mei latency=0
resources: irq:16 memory:dfc0b000-dfc0b00f
*-usb:0
description: USB Controller
product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
vendor: Intel Corporation
physical id: 1a
bus info: pci@0000:00:1a.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
resources: irq:16 memory:dfc08000-dfc083ff
*-multimedia
description: Audio device
product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
vendor: Intel Corporation
physical id: 1b
bus info: pci@0000:00:1b.0
version: 05
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0
resources: irq:51 memory:dfc00000-dfc03fff
*-pci:0
description: PCI bridge
product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
vendor: Intel Corporation
physical id: 1c
bus info: pci@0000:00:1c.0
version: b5
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:40 ioport:d000(size=4096) memory:df200000-dfbfffff ioport:d2100000(size=10485760)
*-pci:1
description: PCI bridge
product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
vendor: Intel Corporation
physical id: 1c.1
bus info: pci@0000:00:1c.1
version: b5
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:41 ioport:c000(size=4096) memory:de800000-df1fffff ioport:d1600000(size=10485760)
*-network
description: Wireless interface
product: RTL8188CE 802.11b/g/n WiFi Adapter
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: 74:2f:68:14:fe:92
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 ioport:c000(size=256) memory:de800000-de803fff
*-pci:2
description: PCI bridge
product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
vendor: Intel Corporation
physical id: 1c.3
bus info: pci@0000:00:1c.3
version: b5
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:42 ioport:b000(size=4096) memory:dde00000-de7fffff ioport:d0b00000(size=10485760)
*-usb
description: USB Controller
product: ASM1042 SuperSpeed USB Host Controller
vendor: ASMedia Technology Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: xhci bus_master cap_list
configuration: driver=xhci_hcd latency=0
resources: irq:19 memory:dde00000-dde07fff
*-pci:3
description: PCI bridge
product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
vendor: Intel Corporation
physical id: 1c.5
bus info: pci@0000:00:1c.5
version: b5
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master cap_list
configuration: driver=pcieport
resources: irq:43 ioport:a000(size=4096) memory:dd400000-dddfffff ioport:d0000000(size=10485760)
*-network
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: c0
serial: 14:da:e9:cb:41:48
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
resources: irq:52 memory:dd400000-dd43ffff ioport:a000(size=12
*-usb:1
description: USB Controller
product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: ehci bus_master cap_list
configuration: driver=ehci_hcd latency=0
resources: irq:23 memory:dfc07000-dfc073ff
*-isa
description: ISA bridge
product: HM65 Express Chipset Family LPC Controller
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 05
width: 32 bits
clock: 33MHz
capabilities: isa bus_master cap_list
configuration: latency=0
*-storage
description: SATA controller
product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
vendor: Intel Corporation
physical id: 1f.2
bus info: pci@0000:00:1f.2
version: 05
width: 32 bits
clock: 66MHz
capabilities: storage ahci_1.0 bus_master cap_list
configuration: driver=ahci latency=0
resources: irq:44 ioport:e0b0(size= ioport:e0a0(size=4) ioport:e090(size= ioport:e080(size=4) ioport:e060(size=32) memory:dfc06000-dfc067ff
*-serial UNCLAIMED
description: SMBus
product: 6 Series/C200 Series Chipset Family SMBus Controller
vendor: Intel Corporation
physical id: 1f.3
bus info: pci@0000:00:1f.3
version: 05
width: 64 bits
clock: 33MHz
configuration: latency=0
resources: memory:dfc05000-dfc050ff ioport:e040(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by matt_symes on 2012-03-15
Hi

I could really do with seeing the log files as they are lightly to hold clues as to what is happening.

lshw details the hardware in your system and needs to be used in conjunction with the log files.

Kind regards

---

### Post by awidearray on 2012-03-15
I apologize but I am not familiar with log files. When I open the Log File Viewer and click on "Open..." there are many files and folders that come up and I'm not sure which one you would be interested in looking at.

Thank you so much for your assistance.

---

### Post by awidearray on 2012-03-15
```
gregslaptop@ubuntu:~$ cat /var/log/pm-suspend.log | tail -n 100
gregslaptop@ubuntu:~$ grep "PM:" /var/log/syslog | tail -n 100
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Mar 15 15:30:42 ubuntu kernel: [    0.757670] PM: Registering ACPI NVS region at b2f29000 (389120 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.757680] PM: Registering ACPI NVS region at b2f95000 (339968 bytes)
Mar 15 15:30:42 ubuntu kernel: [    1.488944] PM: Hibernation image not present or could not be loaded.
gregslaptop@ubuntu:~$ 
```


This is the most recently modified log file. It's titled: syslog

```
Mar 15 10:52:18 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="937" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Mar 15 10:52:44 ubuntu anacron[3366]: Job `cron.daily' terminated
Mar 15 10:52:44 ubuntu anacron[3366]: Normal exit (1 job run)
Mar 15 11:02:09 ubuntu dbus[944]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Mar 15 11:02:09 ubuntu dbus[944]: [system] Successfully activated service 'com.ubuntu.SystemService'
Mar 15 11:17:01 ubuntu CRON[3940]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 12:17:01 ubuntu CRON[4361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 12:29:28 ubuntu kernel: [12493.064826] cfg80211: All devices are disconnected, going to restore regulatory settings
Mar 15 12:29:28 ubuntu kernel: [12493.064843] cfg80211: Restoring regulatory settings
Mar 15 12:29:28 ubuntu kernel: [12493.064854] cfg80211: Calling CRDA to update world regulatory domain
Mar 15 12:29:28 ubuntu wpa_supplicant[1143]: CTRL-EVENT-DISCONNECTED bssid=00:22:6b:55:d8:9d reason=4
Mar 15 12:29:28 ubuntu NetworkManager[955]: <info> (wlan0): supplicant interface state: completed -> disconnected
Mar 15 12:29:28 ubuntu kernel: [12493.167931] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
Mar 15 12:29:28 ubuntu NetworkManager[955]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 15 12:29:28 ubuntu kernel: [12493.498901] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Mar 15 12:29:28 ubuntu kernel: [12493.498905] cfg80211: World regulatory domain updated:
Mar 15 12:29:28 ubuntu kernel: [12493.498906] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 15 12:29:28 ubuntu kernel: [12493.498909] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:28 ubuntu kernel: [12493.498912] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:28 ubuntu kernel: [12493.498914] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:28 ubuntu kernel: [12493.498917] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:28 ubuntu kernel: [12493.498919] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:29 ubuntu wpa_supplicant[1143]: Trying to authenticate with 00:22:6b:55:d8:9d (SSID='morgan' freq=2412 MHz)
Mar 15 12:29:29 ubuntu kernel: [12494.231575] wlan0: authenticate with 00:22:6b:55:d8:9d (try 1)
Mar 15 12:29:29 ubuntu NetworkManager[955]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 15 12:29:29 ubuntu wpa_supplicant[1143]: Trying to associate with 00:22:6b:55:d8:9d (SSID='morgan' freq=2412 MHz)
Mar 15 12:29:29 ubuntu NetworkManager[955]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 15 12:29:29 ubuntu kernel: [12494.233891] wlan0: authenticated
Mar 15 12:29:29 ubuntu kernel: [12494.234005] wlan0: associate with 00:22:6b:55:d8:9d (try 1)
Mar 15 12:29:29 ubuntu kernel: [12494.237670] wlan0: RX ReassocResp from 00:22:6b:55:d8:9d (capab=0x401 status=0 aid=1)
Mar 15 12:29:29 ubuntu kernel: [12494.237680] wlan0: associated
Mar 15 12:29:29 ubuntu kernel: [12494.248540] cfg80211: Calling CRDA for country: US
Mar 15 12:29:29 ubuntu wpa_supplicant[1143]: Associated with 00:22:6b:55:d8:9d
Mar 15 12:29:29 ubuntu wpa_supplicant[1143]: CTRL-EVENT-CONNECTED - Connection to 00:22:6b:55:d8:9d completed (reauth) [id=0 id_str=]
Mar 15 12:29:29 ubuntu NetworkManager[955]: <info> (wlan0): supplicant interface state: associating -> completed
Mar 15 12:29:29 ubuntu kernel: [12494.255127] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255138] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255144] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255151] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255156] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255163] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255168] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255174] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255179] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255185] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255190] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255196] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255202] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255208] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255213] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255219] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255224] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255235] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255241] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255246] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 12:29:29 ubuntu kernel: [12494.255252] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255257] cfg80211: Disabling freq 2467 MHz
Mar 15 12:29:29 ubuntu kernel: [12494.255261] cfg80211: Disabling freq 2472 MHz
Mar 15 12:29:29 ubuntu kernel: [12494.255264] cfg80211: Disabling freq 2484 MHz
Mar 15 12:29:29 ubuntu kernel: [12494.255275] cfg80211: Regulatory domain changed to country: US
Mar 15 12:29:29 ubuntu kernel: [12494.255280] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 15 12:29:29 ubuntu kernel: [12494.255286] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255292] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255298] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255303] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255310] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 12:29:29 ubuntu kernel: [12494.255316] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Mar 15 13:17:01 ubuntu CRON[4645]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 14:17:01 ubuntu CRON[4911]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 15:12:07 ubuntu kernel: [22237.499722] init: tty4 main process (1068) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.500080] init: tty5 main process (1076) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.500373] init: tty2 main process (1082) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.500635] init: tty3 main process (1084) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.500850] init: tty6 main process (1086) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.501238] init: irqbalance main process (1100) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.501434] init: cron main process (1102) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: [22237.501792] init: tty1 main process (1428) killed by TERM signal
Mar 15 15:12:07 ubuntu kernel: Kernel logging (proc) stopped.
Mar 15 15:12:07 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="937" x-info="http://www.rsyslog.com"] exiting on signal 15.
Mar 15 15:30:42 ubuntu kernel: imklog 5.8.1, log source = /proc/kmsg started.
Mar 15 15:30:42 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="952" x-info="http://www.rsyslog.com"] start
Mar 15 15:30:42 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Mar 15 15:30:42 ubuntu rsyslogd: rsyslogd's userid changed to 101
Mar 15 15:30:42 ubuntu rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Linux version 3.0.0-16-generic (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   NSC Geode by NSC
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Cyrix CyrixInstead
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Transmeta GenuineTMx86
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Transmeta TransmetaCPU
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   UMC UMC UMC UMC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000040200000 - 00000000b2c0f000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2c0f000 - 00000000b2d8e000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2d8e000 - 00000000b2d95000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2d95000 - 00000000b2d96000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2d96000 - 00000000b2d97000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2d97000 - 00000000b2db8000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2db8000 - 00000000b2dc6000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2dc6000 - 00000000b2de8000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2de8000 - 00000000b2f29000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2f29000 - 00000000b2f88000 (ACPI NVS)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2f88000 - 00000000b2f95000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2f95000 - 00000000b2fe8000 (ACPI NVS)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2fe8000 - 00000000b2ffd000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b2ffd000 - 00000000b3000000 (ACPI data)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000b3000000 - 00000000c0000000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff980000 - 00000000ffc00000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ffd80000 - 0000000100000000 (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001bf800000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Mar 15 15:30:42 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Mar 15 15:30:42 ubuntu kernel: [    0.000000] DMI 2.6 present.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] DMI: ASUSTeK Computer Inc. K53E/K53E, BIOS K53E.213 08/08/2011
Mar 15 15:30:42 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] last_pfn = 0xb2ffd max_arch_pfn = 0x100000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   C0000-CFFFF write-protect
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   D0000-E7FFF uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   E8000-FFFFF write-protect
Mar 15 15:30:42 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Mar 15 15:30:42 ubuntu polkitd[975]: started daemon version 0.102 using authority implementation `local' version `0.102'
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   2 base 0B8000000 mask FF8000000 uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   3 base 0B4000000 mask FFC000000 uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   4 base 0B3000000 mask FFF000000 uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   5 base 100000000 mask F80000000 write-back
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   6 base 180000000 mask FC0000000 write-back
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   7 base 1BF800000 mask FFF800000 uncachable
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   8 disabled
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   9 disabled
Mar 15 15:30:42 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Mar 15 15:30:42 ubuntu kernel: [    0.000000] original variable MTRRs
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 2, base: 2944MB, range: 128MB, type UC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 3, base: 2880MB, range: 64MB, type UC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 4, base: 2864MB, range: 16MB, type UC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 5, base: 4GB, range: 2GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 6, base: 6GB, range: 1GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 7, base: 7160MB, range: 8MB, type UC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] total RAM covered: 5928M
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Found optimal setting for mtrr clean up
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 8  	lose cover RAM: 0G
Mar 15 15:30:42 ubuntu kernel: [    0.000000] New variable MTRRs
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 1, base: 2GB, range: 512MB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 2, base: 2560MB, range: 256MB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 3, base: 2816MB, range: 32MB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 4, base: 2848MB, range: 16MB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 5, base: 4GB, range: 2GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 6, base: 6GB, range: 1GB, type WB
Mar 15 15:30:42 ubuntu kernel: [    0.000000] reg 7, base: 7160MB, range: 8MB, type UC
Mar 15 15:30:42 ubuntu kernel: [    0.000000] e820 update range: 00000000b3000000 - 0000000100000000 (usable) ==> (reserved)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] found SMP MP-table at [c00fcc20] fcc20
Mar 15 15:30:42 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Base memory trampoline at [c009a000] 9a000 size 16384
Mar 15 15:30:42 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Mar 15 15:30:42 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Mar 15 15:30:42 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] RAMDISK: 365ea000 - 372ed000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: RSDP 000f0430 00024 (v02 _ASUS_)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: XSDT b2ffee18 00074 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: FACP b2f9ad98 000F4 (v04 _ASUS_ Notebook 06222004 MSFT 00010013)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI Warning: 32/64 FACS address mismatch in FADT - two FACS tables! (20110413/tbfadt-369)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI Warning: 32/64X FACS address mismatch in FADT - 0xB2FE4E40/0x00000000B2FE4D40, using 32 (20110413/tbfadt-489)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: DSDT b2f69018 112F4 (v01 _ASUS_ Notebook 00000000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: FACS b2fe4e40 00040
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: APIC b2ffdf18 000CC (v02 _ASUS_ Notebook 06222004 MSFT 00010013)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: DBGP b2ffff18 00034 (v01 _ASUS_ Notebook 06222004 MSFT 00010013)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: ECDT b2fe4b18 000C1 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: SLIC b2f9be18 00176 (v01 _ASUS_ Notebook 06222004 ASUS 00000001)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: HPET b2fe5d18 00038 (v01 _ASUS_ Notebook 06222004 AMI. 00000003)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: MCFG b2fe5c98 0003C (v01 _ASUS_ Notebook 06222004 MSFT 00000097)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: SSDT b2f87018 0080B (v01  PmRef  Cpu0Ist 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: SSDT b2f86018 00996 (v01  PmRef    CpuPm 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: ASF! b2fe4a18 000A0 (v32 INTEL       HCG 00000001 TFSM 000F4240)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] 1975MB HIGHMEM available.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Zone PFN ranges:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000b2ffd
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Mar 15 15:30:42 ubuntu kernel: [    0.000000] early_node_map[10] active PFN ranges
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x00020200 -> 0x00040000
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x00040200 -> 0x000b2c0f
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2d8e -> 0x000b2d95
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2d96 -> 0x000b2d97
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2db8 -> 0x000b2dc6
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2de8 -> 0x000b2f29
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2f88 -> 0x000b2f95
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     0: 0x000b2fe8 -> 0x000b2ffd
Mar 15 15:30:42 ubuntu kernel: [    0.000000] On node 0 totalpages: 731414
Mar 15 15:30:42 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map f4f8a200
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   DMA zone: 3950 pages, LIFO batch:0
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   Normal zone: 220974 pages, LIFO batch:31
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   HighMem zone: 3952 pages used for memmap
Mar 15 15:30:42 ubuntu kernel: [    0.000000]   HighMem zone: 500762 pages, LIFO batch:31
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Using APIC driver default
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 15 15:30:42 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 15 15:30:42 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] 16 Processors exceeds NR_CPUS limit of 8
Mar 15 15:30:42 ubuntu kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Mar 15 15:30:42 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Mar 15 15:30:42 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PERCPU: Embedded 12 pages/cpu @f4800000 s26240 r0 d22912 u524288
Mar 15 15:30:42 ubuntu kernel: [    0.000000] pcpu-alloc: s26240 r0 d22912 u524288 alloc=1*4194304
Mar 15 15:30:42 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 725686
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=262485182484EBDD loop=/ubuntu/disks/root.disk ro quiet splash vt.handoff=7
Mar 15 15:30:42 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Initializing CPU#0
Mar 15 15:30:42 ubuntu kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Mar 15 15:30:42 ubuntu kernel: [    0.000000] allocated 11730640 bytes of page_cgroup
Mar 15 15:30:42 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000b2ffd)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Memory: 2867168k/2932724k available (5340k kernel code, 58488k reserved, 2596k data, 696k init, 2018856k highmem)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]       .data : 0xc1537104 - 0xc17c0140   (2596 kB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000]       .text : 0xc1000000 - 0xc1537104   (5340 kB)
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Mar 15 15:30:42 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:744 16
Mar 15 15:30:42 ubuntu kernel: [    0.000000] CPU 0 irqstacks, hard=f380a000 soft=f380c000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Mar 15 15:30:42 ubuntu kernel: [    0.000000] vt handoff: transparent VT on vt#7
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Console: colour dummy device 80x25
Mar 15 15:30:42 ubuntu kernel: [    0.000000] console [tty0] enabled
Mar 15 15:30:42 ubuntu kernel: [    0.000000] hpet clockevent registered
Mar 15 15:30:42 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Mar 15 15:30:42 ubuntu kernel: [    0.004000] Detected 2394.769 MHz processor.
Mar 15 15:30:42 ubuntu kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.53 BogoMIPS (lpj=9579076)
Mar 15 15:30:42 ubuntu kernel: [    0.000005] pid_max: default: 32768 minimum: 301
Mar 15 15:30:42 ubuntu kernel: [    0.000024] Security Framework initialized
Mar 15 15:30:42 ubuntu kernel: [    0.000034] AppArmor: AppArmor initialized
Mar 15 15:30:42 ubuntu kernel: [    0.000035] Yama: becoming mindful.
Mar 15 15:30:42 ubuntu kernel: [    0.000074] Mount-cache hash table entries: 512
Mar 15 15:30:42 ubuntu kernel: [    0.000172] Initializing cgroup subsys cpuacct
Mar 15 15:30:42 ubuntu kernel: [    0.000177] Initializing cgroup subsys memory
Mar 15 15:30:42 ubuntu kernel: [    0.000183] Initializing cgroup subsys devices
Mar 15 15:30:42 ubuntu kernel: [    0.000185] Initializing cgroup subsys freezer
Mar 15 15:30:42 ubuntu kernel: [    0.000187] Initializing cgroup subsys net_cls
Mar 15 15:30:42 ubuntu kernel: [    0.000188] Initializing cgroup subsys blkio
Mar 15 15:30:42 ubuntu kernel: [    0.000193] Initializing cgroup subsys perf_event
Mar 15 15:30:42 ubuntu kernel: [    0.000218] CPU: Physical Processor ID: 0
Mar 15 15:30:42 ubuntu kernel: [    0.000219] CPU: Processor Core ID: 0
Mar 15 15:30:42 ubuntu kernel: [    0.000223] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Mar 15 15:30:42 ubuntu kernel: [    0.000224] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Mar 15 15:30:42 ubuntu kernel: [    0.000227] mce: CPU supports 7 MCE banks
Mar 15 15:30:42 ubuntu kernel: [    0.000238] CPU0: Thermal monitoring enabled (TM1)
Mar 15 15:30:42 ubuntu kernel: [    0.000245] using mwait in idle threads.
Mar 15 15:30:42 ubuntu kernel: [    0.002240] ACPI: Core revision 20110413
Mar 15 15:30:42 ubuntu kernel: [    0.275763] ftrace: allocating 24901 entries in 49 pages
Mar 15 15:30:42 ubuntu kernel: [    0.284635] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 15 15:30:42 ubuntu kernel: [    0.285046] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 15 15:30:42 ubuntu kernel: [    0.324674] CPU0: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz stepping 07
Mar 15 15:30:42 ubuntu kernel: [    0.431308] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Mar 15 15:30:42 ubuntu kernel: [    0.431314] ... version:                3
Mar 15 15:30:42 ubuntu kernel: [    0.431315] ... bit width:              48
Mar 15 15:30:42 ubuntu kernel: [    0.431316] ... generic registers:      4
Mar 15 15:30:42 ubuntu kernel: [    0.431318] ... value mask:             0000ffffffffffff
Mar 15 15:30:42 ubuntu kernel: [    0.431319] ... max period:             000000007fffffff
Mar 15 15:30:42 ubuntu kernel: [    0.431320] ... fixed-purpose events:   3
Mar 15 15:30:42 ubuntu kernel: [    0.431321] ... event mask:             000000070000000f
Mar 15 15:30:42 ubuntu kernel: [    0.431638] CPU 1 irqstacks, hard=f38d6000 soft=f38e0000
Mar 15 15:30:42 ubuntu kernel: [    0.431639] Booting Node   0, Processors  #1
Mar 15 15:30:42 ubuntu kernel: [    0.431641] smpboot cpu 1: start_ip = 9a000
Mar 15 15:30:42 ubuntu kernel: [    0.441876] Initializing CPU#1
Mar 15 15:30:42 ubuntu kernel: [    0.539254] CPU 2 irqstacks, hard=f390a000 soft=f390c000
Mar 15 15:30:42 ubuntu kernel: [    0.539256]  #2
Mar 15 15:30:42 ubuntu kernel: [    0.539257] smpboot cpu 2: start_ip = 9a000
Mar 15 15:30:42 ubuntu kernel: [    0.549537] Initializing CPU#2
Mar 15 15:30:42 ubuntu kernel: [    0.647172] CPU 3 irqstacks, hard=f3916000 soft=f3918000
Mar 15 15:30:42 ubuntu kernel: [    0.647174]  #3
Mar 15 15:30:42 ubuntu kernel: [    0.647175] smpboot cpu 3: start_ip = 9a000
Mar 15 15:30:42 ubuntu kernel: [    0.657409] Initializing CPU#3
Mar 15 15:30:42 ubuntu kernel: [    0.754924] Brought up 4 CPUs
Mar 15 15:30:42 ubuntu kernel: [    0.754926] Total of 4 processors activated (19156.23 BogoMIPS).
Mar 15 15:30:42 ubuntu kernel: [    0.757550] devtmpfs: initialized
Mar 15 15:30:42 ubuntu kernel: [    0.757670] PM: Registering ACPI NVS region at b2f29000 (389120 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.757680] PM: Registering ACPI NVS region at b2f95000 (339968 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.759203] print_constraints: dummy: 
Mar 15 15:30:42 ubuntu kernel: [    0.759230] Time: 15:30:24  Date: 03/15/12
Mar 15 15:30:42 ubuntu kernel: [    0.759261] NET: Registered protocol family 16
Mar 15 15:30:42 ubuntu kernel: [    0.759343] Trying to unpack rootfs image as initramfs...
Mar 15 15:30:42 ubuntu kernel: [    0.759349] EISA bus registered
Mar 15 15:30:42 ubuntu kernel: [    0.759355] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Mar 15 15:30:42 ubuntu kernel: [    0.759358] ACPI: bus type pci registered
Mar 15 15:30:42 ubuntu kernel: [    0.759414] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Mar 15 15:30:42 ubuntu kernel: [    0.759417] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
Mar 15 15:30:42 ubuntu kernel: [    0.759419] PCI: Using MMCONFIG for extended config space
Mar 15 15:30:42 ubuntu kernel: [    0.759420] PCI: Using configuration type 1 for base access
Mar 15 15:30:42 ubuntu kernel: [    0.760121] bio: create slab <bio-0> at 0
Mar 15 15:30:42 ubuntu kernel: [    0.762713] ACPI: EC: EC description table is found, configuring boot EC
Mar 15 15:30:42 ubuntu kernel: [    0.762718] ACPI: EC: Look up EC in DSDT
Mar 15 15:30:42 ubuntu kernel: [    0.765411] ACPI: Executed 1 blocks of module-level executable AML code
Mar 15 15:30:42 ubuntu kernel: [    0.794924] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Mar 15 15:30:42 ubuntu kernel: [    0.827215] ACPI: SSDT b2dca798 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.827852] ACPI: Dynamic OEM Table Load:
Mar 15 15:30:42 ubuntu kernel: [    0.827855] ACPI: SSDT   (null) 0073F (v01  PmRef  Cpu0Cst 00003001 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.851049] ACPI: SSDT b2dcba98 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.851728] ACPI: Dynamic OEM Table Load:
Mar 15 15:30:42 ubuntu kernel: [    0.851730] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.882859] ACPI: SSDT b2dc9d98 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.883495] ACPI: Dynamic OEM Table Load:
Mar 15 15:30:42 ubuntu kernel: [    0.883497] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20091112)
Mar 15 15:30:42 ubuntu kernel: [    0.907285] ACPI: Interpreter enabled
Mar 15 15:30:42 ubuntu kernel: [    0.907293] ACPI: (supports S0 S3 S4 S5)
Mar 15 15:30:42 ubuntu kernel: [    0.907315] ACPI: Using IOAPIC for interrupt routing
Mar 15 15:30:42 ubuntu kernel: [    0.913607] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
Mar 15 15:30:42 ubuntu kernel: [    0.913814] ACPI: No dock devices found.
Mar 15 15:30:42 ubuntu kernel: [    0.913815] HEST: Table not found.
Mar 15 15:30:42 ubuntu kernel: [    0.913819] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Mar 15 15:30:42 ubuntu kernel: [    0.914288] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Mar 15 15:30:42 ubuntu kernel: [    0.914716] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Mar 15 15:30:42 ubuntu kernel: [    0.914718] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Mar 15 15:30:42 ubuntu kernel: [    0.914720] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Mar 15 15:30:42 ubuntu kernel: [    0.914723] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Mar 15 15:30:42 ubuntu kernel: [    0.914725] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Mar 15 15:30:42 ubuntu kernel: [    0.914726] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Mar 15 15:30:42 ubuntu kernel: [    0.914728] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Mar 15 15:30:42 ubuntu kernel: [    0.914730] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Mar 15 15:30:42 ubuntu kernel: [    0.914732] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Mar 15 15:30:42 ubuntu kernel: [    0.914735] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfeafffff]
Mar 15 15:30:42 ubuntu kernel: [    0.914736] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
Mar 15 15:30:42 ubuntu kernel: [    0.914749] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
Mar 15 15:30:42 ubuntu kernel: [    0.914788] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
Mar 15 15:30:42 ubuntu kernel: [    0.914799] pci 0000:00:02.0: reg 10: [mem 0xdd000000-0xdd3fffff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.914805] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.914810] pci 0000:00:02.0: reg 20: [io  0xe000-0xe03f]
Mar 15 15:30:42 ubuntu kernel: [    0.914867] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Mar 15 15:30:42 ubuntu kernel: [    0.914892] pci 0000:00:16.0: reg 10: [mem 0xdfc0b000-0xdfc0b00f 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.914971] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.914976] pci 0000:00:16.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915011] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Mar 15 15:30:42 ubuntu kernel: [    0.915032] pci 0000:00:1a.0: reg 10: [mem 0xdfc08000-0xdfc083ff]
Mar 15 15:30:42 ubuntu kernel: [    0.915127] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915131] pci 0000:00:1a.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915157] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Mar 15 15:30:42 ubuntu kernel: [    0.915174] pci 0000:00:1b.0: reg 10: [mem 0xdfc00000-0xdfc03fff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.915247] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915251] pci 0000:00:1b.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915273] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Mar 15 15:30:42 ubuntu kernel: [    0.915357] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915361] pci 0000:00:1c.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915385] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
Mar 15 15:30:42 ubuntu kernel: [    0.915468] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915473] pci 0000:00:1c.1: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915497] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
Mar 15 15:30:42 ubuntu kernel: [    0.915580] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915585] pci 0000:00:1c.3: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915609] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Mar 15 15:30:42 ubuntu kernel: [    0.915692] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915696] pci 0000:00:1c.5: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915726] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Mar 15 15:30:42 ubuntu kernel: [    0.915749] pci 0000:00:1d.0: reg 10: [mem 0xdfc07000-0xdfc073ff]
Mar 15 15:30:42 ubuntu kernel: [    0.915843] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.915848] pci 0000:00:1d.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.915873] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
Mar 15 15:30:42 ubuntu kernel: [    0.916002] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
Mar 15 15:30:42 ubuntu kernel: [    0.916022] pci 0000:00:1f.2: reg 10: [io  0xe0b0-0xe0b7]
Mar 15 15:30:42 ubuntu kernel: [    0.916031] pci 0000:00:1f.2: reg 14: [io  0xe0a0-0xe0a3]
Mar 15 15:30:42 ubuntu kernel: [    0.916039] pci 0000:00:1f.2: reg 18: [io  0xe090-0xe097]
Mar 15 15:30:42 ubuntu kernel: [    0.916048] pci 0000:00:1f.2: reg 1c: [io  0xe080-0xe083]
Mar 15 15:30:42 ubuntu kernel: [    0.916057] pci 0000:00:1f.2: reg 20: [io  0xe060-0xe07f]
Mar 15 15:30:42 ubuntu kernel: [    0.916065] pci 0000:00:1f.2: reg 24: [mem 0xdfc06000-0xdfc067ff]
Mar 15 15:30:42 ubuntu kernel: [    0.916113] pci 0000:00:1f.2: PME# supported from D3hot
Mar 15 15:30:42 ubuntu kernel: [    0.916117] pci 0000:00:1f.2: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.916136] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Mar 15 15:30:42 ubuntu kernel: [    0.916153] pci 0000:00:1f.3: reg 10: [mem 0xdfc05000-0xdfc050ff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.916175] pci 0000:00:1f.3: reg 20: [io  0xe040-0xe05f]
Mar 15 15:30:42 ubuntu kernel: [    0.916249] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Mar 15 15:30:42 ubuntu kernel: [    0.916254] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
Mar 15 15:30:42 ubuntu kernel: [    0.916259] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdfbfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.916266] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.916340] pci 0000:02:00.0: [10ec:8176] type 0 class 0x000280
Mar 15 15:30:42 ubuntu kernel: [    0.916367] pci 0000:02:00.0: reg 10: [io  0xc000-0xc0ff]
Mar 15 15:30:42 ubuntu kernel: [    0.916415] pci 0000:02:00.0: reg 18: [mem 0xde800000-0xde803fff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.916560] pci 0000:02:00.0: supports D1 D2
Mar 15 15:30:42 ubuntu kernel: [    0.916561] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.916567] pci 0000:02:00.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.922710] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
Mar 15 15:30:42 ubuntu kernel: [    0.922714] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
Mar 15 15:30:42 ubuntu kernel: [    0.922719] pci 0000:00:1c.1:   bridge window [mem 0xde800000-0xdf1fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.922726] pci 0000:00:1c.1:   bridge window [mem 0xd1600000-0xd1ffffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.922807] pci 0000:03:00.0: [1b21:1042] type 0 class 0x000c03
Mar 15 15:30:42 ubuntu kernel: [    0.922845] pci 0000:03:00.0: reg 10: [mem 0xdde00000-0xdde07fff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.923037] pci 0000:03:00.0: PME# supported from D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.923043] pci 0000:03:00.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.930694] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Mar 15 15:30:42 ubuntu kernel: [    0.930699] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Mar 15 15:30:42 ubuntu kernel: [    0.930704] pci 0000:00:1c.3:   bridge window [mem 0xdde00000-0xde7fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.930711] pci 0000:00:1c.3:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.930783] pci 0000:04:00.0: [1969:1083] type 0 class 0x000200
Mar 15 15:30:42 ubuntu kernel: [    0.930814] pci 0000:04:00.0: reg 10: [mem 0xdd400000-0xdd43ffff 64bit]
Mar 15 15:30:42 ubuntu kernel: [    0.930829] pci 0000:04:00.0: reg 18: [io  0xa000-0xa07f]
Mar 15 15:30:42 ubuntu kernel: [    0.930963] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 15 15:30:42 ubuntu kernel: [    0.930969] pci 0000:04:00.0: PME# disabled
Mar 15 15:30:42 ubuntu kernel: [    0.938682] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
Mar 15 15:30:42 ubuntu kernel: [    0.938688] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
Mar 15 15:30:42 ubuntu kernel: [    0.938692] pci 0000:00:1c.5:   bridge window [mem 0xdd400000-0xdddfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.938699] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.938722] pci_bus 0000:00: on NUMA node 0
Mar 15 15:30:42 ubuntu kernel: [    0.938727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 15 15:30:42 ubuntu kernel: [    0.938963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Mar 15 15:30:42 ubuntu kernel: [    0.938999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Mar 15 15:30:42 ubuntu kernel: [    0.939040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Mar 15 15:30:42 ubuntu kernel: [    0.939080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Mar 15 15:30:42 ubuntu kernel: [    0.939286]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Mar 15 15:30:42 ubuntu kernel: [    0.939585]  pci0000:00: ACPI _OSC control (0x1d) granted
Mar 15 15:30:42 ubuntu kernel: [    0.943449] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943495] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943537] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943579] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943621] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Mar 15 15:30:42 ubuntu kernel: [    0.943663] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
Mar 15 15:30:42 ubuntu kernel: [    0.943705] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943747] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 12)
Mar 15 15:30:42 ubuntu kernel: [    0.943823] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Mar 15 15:30:42 ubuntu kernel: [    0.943831] vgaarb: loaded
Mar 15 15:30:42 ubuntu kernel: [    0.943832] vgaarb: bridge control possible 0000:00:02.0
Mar 15 15:30:42 ubuntu kernel: [    0.943996] SCSI subsystem initialized
Mar 15 15:30:42 ubuntu kernel: [    0.944042] libata version 3.00 loaded.
Mar 15 15:30:42 ubuntu kernel: [    0.944074] usbcore: registered new interface driver usbfs
Mar 15 15:30:42 ubuntu kernel: [    0.944082] usbcore: registered new interface driver hub
Mar 15 15:30:42 ubuntu kernel: [    0.944103] usbcore: registered new device driver usb
Mar 15 15:30:42 ubuntu kernel: [    0.944169] PCI: Using ACPI for IRQ routing
Mar 15 15:30:42 ubuntu kernel: [    0.945727] PCI: pci_cache_line_size set to 64 bytes
Mar 15 15:30:42 ubuntu kernel: [    0.945807] reserve RAM buffer: 000000000009e800 - 000000000009ffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945810] reserve RAM buffer: 00000000b2c0f000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945814] reserve RAM buffer: 00000000b2d95000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945817] reserve RAM buffer: 00000000b2d97000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945820] reserve RAM buffer: 00000000b2dc6000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945823] reserve RAM buffer: 00000000b2f29000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945825] reserve RAM buffer: 00000000b2f95000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945827] reserve RAM buffer: 00000000b2ffd000 - 00000000b3ffffff 
Mar 15 15:30:42 ubuntu kernel: [    0.945900] NetLabel: Initializing
Mar 15 15:30:42 ubuntu kernel: [    0.945902] NetLabel:  domain hash size = 128
Mar 15 15:30:42 ubuntu kernel: [    0.945903] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 15 15:30:42 ubuntu kernel: [    0.945913] NetLabel:  unlabeled traffic allowed by default
Mar 15 15:30:42 ubuntu kernel: [    0.945948] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Mar 15 15:30:42 ubuntu kernel: [    0.945954] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Mar 15 15:30:42 ubuntu kernel: [    0.948971] Switching to clocksource hpet
Mar 15 15:30:42 ubuntu kernel: [    0.950518] Switched to NOHz mode on CPU #0
Mar 15 15:30:42 ubuntu kernel: [    0.950569] Switched to NOHz mode on CPU #1
Mar 15 15:30:42 ubuntu kernel: [    0.950631] Switched to NOHz mode on CPU #3
Mar 15 15:30:42 ubuntu kernel: [    0.950649] Switched to NOHz mode on CPU #2
Mar 15 15:30:42 ubuntu kernel: [    0.954592] AppArmor: AppArmor Filesystem Enabled
Mar 15 15:30:42 ubuntu kernel: [    0.954612] pnp: PnP ACPI init
Mar 15 15:30:42 ubuntu kernel: [    0.954623] ACPI: bus type pnp registered
Mar 15 15:30:42 ubuntu kernel: [    0.954860] pnp 00:00: [bus 00-3e]
Mar 15 15:30:42 ubuntu kernel: [    0.954862] pnp 00:00: [io  0x0000-0x0cf7 window]
Mar 15 15:30:42 ubuntu kernel: [    0.954864] pnp 00:00: [io  0x0cf8-0x0cff]
Mar 15 15:30:42 ubuntu kernel: [    0.954866] pnp 00:00: [io  0x0d00-0xffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954868] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954870] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954873] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954875] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954877] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954879] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954881] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954883] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954884] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954886] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954888] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954890] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954892] pnp 00:00: [mem 0x000ec000-0x000effff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954894] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954895] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954897] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
Mar 15 15:30:42 ubuntu kernel: [    0.954960] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.954988] pnp 00:01: [io  0x0000-0x001f]
Mar 15 15:30:42 ubuntu kernel: [    0.954990] pnp 00:01: [io  0x0081-0x0091]
Mar 15 15:30:42 ubuntu kernel: [    0.954992] pnp 00:01: [io  0x0093-0x009f]
Mar 15 15:30:42 ubuntu kernel: [    0.954993] pnp 00:01: [io  0x00c0-0x00df]
Mar 15 15:30:42 ubuntu kernel: [    0.954995] pnp 00:01: [dma 4]
Mar 15 15:30:42 ubuntu kernel: [    0.955016] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955023] pnp 00:02: [mem 0xff000000-0xffffffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955043] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955111] pnp 00:03: [mem 0xfed00000-0xfed003ff]
Mar 15 15:30:42 ubuntu kernel: [    0.955134] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955142] pnp 00:04: [io  0x00f0]
Mar 15 15:30:42 ubuntu kernel: [    0.955151] pnp 00:04: [irq 13]
Mar 15 15:30:42 ubuntu kernel: [    0.955171] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955181] pnp 00:05: [io  0x002e-0x002f]
Mar 15 15:30:42 ubuntu kernel: [    0.955182] pnp 00:05: [io  0x004e-0x004f]
Mar 15 15:30:42 ubuntu kernel: [    0.955184] pnp 00:05: [io  0x0061]
Mar 15 15:30:42 ubuntu kernel: [    0.955185] pnp 00:05: [io  0x0063]
Mar 15 15:30:42 ubuntu kernel: [    0.955187] pnp 00:05: [io  0x0065]
Mar 15 15:30:42 ubuntu kernel: [    0.955188] pnp 00:05: [io  0x0067]
Mar 15 15:30:42 ubuntu kernel: [    0.955190] pnp 00:05: [io  0x0070]
Mar 15 15:30:42 ubuntu kernel: [    0.955191] pnp 00:05: [io  0x0080]
Mar 15 15:30:42 ubuntu kernel: [    0.955192] pnp 00:05: [io  0x0092]
Mar 15 15:30:42 ubuntu kernel: [    0.955194] pnp 00:05: [io  0x00b2-0x00b3]
Mar 15 15:30:42 ubuntu kernel: [    0.955196] pnp 00:05: [io  0x0680-0x069f]
Mar 15 15:30:42 ubuntu kernel: [    0.955197] pnp 00:05: [io  0x1000-0x100f]
Mar 15 15:30:42 ubuntu kernel: [    0.955199] pnp 00:05: [io  0xffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955200] pnp 00:05: [io  0xffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955202] pnp 00:05: [io  0x0400-0x0453]
Mar 15 15:30:42 ubuntu kernel: [    0.955203] pnp 00:05: [io  0x0458-0x047f]
Mar 15 15:30:42 ubuntu kernel: [    0.955205] pnp 00:05: [io  0x0500-0x057f]
Mar 15 15:30:42 ubuntu kernel: [    0.955206] pnp 00:05: [io  0x164e-0x164f]
Mar 15 15:30:42 ubuntu kernel: [    0.955247] system 00:05: [io  0x0680-0x069f] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955250] system 00:05: [io  0x1000-0x100f] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955252] system 00:05: [io  0xffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955254] system 00:05: [io  0xffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955255] system 00:05: [io  0x0400-0x0453] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955258] system 00:05: [io  0x0458-0x047f] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955260] system 00:05: [io  0x0500-0x057f] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955262] system 00:05: [io  0x164e-0x164f] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955264] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955271] pnp 00:06: [io  0x0070-0x0077]
Mar 15 15:30:42 ubuntu kernel: [    0.955276] pnp 00:06: [irq 8]
Mar 15 15:30:42 ubuntu kernel: [    0.955296] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955315] pnp 00:07: [io  0x0454-0x0457]
Mar 15 15:30:42 ubuntu kernel: [    0.955347] system 00:07: [io  0x0454-0x0457] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955350] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955360] pnp 00:08: [io  0x0240-0x0259]
Mar 15 15:30:42 ubuntu kernel: [    0.955391] system 00:08: [io  0x0240-0x0259] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955393] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955426] pnp 00:09: [irq 12]
Mar 15 15:30:42 ubuntu kernel: [    0.955451] pnp 00:09: Plug and Play ACPI device, IDs ETD0101 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955467] pnp 00:0a: [io  0x0060]
Mar 15 15:30:42 ubuntu kernel: [    0.955468] pnp 00:0a: [io  0x0064]
Mar 15 15:30:42 ubuntu kernel: [    0.955473] pnp 00:0a: [irq 1]
Mar 15 15:30:42 ubuntu kernel: [    0.955496] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955689] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955691] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
Mar 15 15:30:42 ubuntu kernel: [    0.955693] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
Mar 15 15:30:42 ubuntu kernel: [    0.955694] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
Mar 15 15:30:42 ubuntu kernel: [    0.955696] pnp 00:0b: [mem 0xe0000000-0xe3ffffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955698] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955699] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
Mar 15 15:30:42 ubuntu kernel: [    0.955701] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955703] pnp 00:0b: [mem 0xff000000-0xffffffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955704] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955706] pnp 00:0b: [mem 0x00000000-0xffffffff disabled]
Mar 15 15:30:42 ubuntu kernel: [    0.955759] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955761] system 00:0b: [mem 0xfed10000-0xfed17fff] could not be reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955763] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955765] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955768] system 00:0b: [mem 0xe0000000-0xe3ffffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955770] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955772] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955774] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955776] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955779] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955781] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955825] pnp 00:0c: [mem 0xd2b00000-0xd2b00fff]
Mar 15 15:30:42 ubuntu kernel: [    0.955872] system 00:0c: [mem 0xd2b00000-0xd2b00fff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.955875] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.955978] pnp 00:0d: [mem 0x20000000-0x201fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.955980] pnp 00:0d: [mem 0x40000000-0x401fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.956030] system 00:0d: [mem 0x20000000-0x201fffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.956032] system 00:0d: [mem 0x40000000-0x401fffff] has been reserved
Mar 15 15:30:42 ubuntu kernel: [    0.956035] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
Mar 15 15:30:42 ubuntu kernel: [    0.956055] pnp: PnP ACPI: found 14 devices
Mar 15 15:30:42 ubuntu kernel: [    0.956056] ACPI: ACPI bus type pnp unregistered
Mar 15 15:30:42 ubuntu kernel: [    0.956059] PnPBIOS: Disabled by ACPI PNP
Mar 15 15:30:42 ubuntu kernel: [    0.991592] PCI: max bus depth: 1 pci_try_num: 2
Mar 15 15:30:42 ubuntu kernel: [    0.991631] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Mar 15 15:30:42 ubuntu kernel: [    0.991635] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991641] pci 0000:00:1c.0:   bridge window [mem 0xdf200000-0xdfbfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991646] pci 0000:00:1c.0:   bridge window [mem 0xd2100000-0xd2afffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991652] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
Mar 15 15:30:42 ubuntu kernel: [    0.991655] pci 0000:00:1c.1:   bridge window [io  0xc000-0xcfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991661] pci 0000:00:1c.1:   bridge window [mem 0xde800000-0xdf1fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991666] pci 0000:00:1c.1:   bridge window [mem 0xd1600000-0xd1ffffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991673] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Mar 15 15:30:42 ubuntu kernel: [    0.991676] pci 0000:00:1c.3:   bridge window [io  0xb000-0xbfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991682] pci 0000:00:1c.3:   bridge window [mem 0xdde00000-0xde7fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991687] pci 0000:00:1c.3:   bridge window [mem 0xd0b00000-0xd14fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991693] pci 0000:00:1c.5: PCI bridge to [bus 04-04]
Mar 15 15:30:42 ubuntu kernel: [    0.991697] pci 0000:00:1c.5:   bridge window [io  0xa000-0xafff]
Mar 15 15:30:42 ubuntu kernel: [    0.991702] pci 0000:00:1c.5:   bridge window [mem 0xdd400000-0xdddfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991707] pci 0000:00:1c.5:   bridge window [mem 0xd0000000-0xd09fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991730] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 15 15:30:42 ubuntu kernel: [    0.991737] pci 0000:00:1c.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    0.991747] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 15 15:30:42 ubuntu kernel: [    0.991752] pci 0000:00:1c.1: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    0.991762] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Mar 15 15:30:42 ubuntu kernel: [    0.991767] pci 0000:00:1c.3: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    0.991773] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Mar 15 15:30:42 ubuntu kernel: [    0.991778] pci 0000:00:1c.5: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    0.991782] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Mar 15 15:30:42 ubuntu kernel: [    0.991784] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991786] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991788] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
Mar 15 15:30:42 ubuntu kernel: [    0.991790] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
Mar 15 15:30:42 ubuntu kernel: [    0.991792] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991794] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991796] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
Mar 15 15:30:42 ubuntu kernel: [    0.991797] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
Mar 15 15:30:42 ubuntu kernel: [    0.991799] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfeafffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991801] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
Mar 15 15:30:42 ubuntu kernel: [    0.991803] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991805] pci_bus 0000:01: resource 1 [mem 0xdf200000-0xdfbfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991807] pci_bus 0000:01: resource 2 [mem 0xd2100000-0xd2afffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991809] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991811] pci_bus 0000:02: resource 1 [mem 0xde800000-0xdf1fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991813] pci_bus 0000:02: resource 2 [mem 0xd1600000-0xd1ffffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991815] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
Mar 15 15:30:42 ubuntu kernel: [    0.991817] pci_bus 0000:03: resource 1 [mem 0xdde00000-0xde7fffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991819] pci_bus 0000:03: resource 2 [mem 0xd0b00000-0xd14fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991821] pci_bus 0000:04: resource 0 [io  0xa000-0xafff]
Mar 15 15:30:42 ubuntu kernel: [    0.991823] pci_bus 0000:04: resource 1 [mem 0xdd400000-0xdddfffff]
Mar 15 15:30:42 ubuntu kernel: [    0.991825] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xd09fffff 64bit pref]
Mar 15 15:30:42 ubuntu kernel: [    0.991854] NET: Registered protocol family 2
Mar 15 15:30:42 ubuntu kernel: [    0.991899] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.992027] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.992235] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.992324] TCP: Hash tables configured (established 131072 bind 65536)
Mar 15 15:30:42 ubuntu kernel: [    0.992326] TCP reno registered
Mar 15 15:30:42 ubuntu kernel: [    0.992328] UDP hash table entries: 512 (order: 2, 16384 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.992332] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Mar 15 15:30:42 ubuntu kernel: [    0.992398] NET: Registered protocol family 1
Mar 15 15:30:42 ubuntu kernel: [    0.992409] pci 0000:00:02.0: Boot video device
Mar 15 15:30:42 ubuntu kernel: [    0.992502] PCI: CLS 64 bytes, default 64
Mar 15 15:30:42 ubuntu kernel: [    0.992893] audit: initializing netlink socket (disabled)
Mar 15 15:30:42 ubuntu kernel: [    0.992900] type=2000 audit(1331825424.564:1): initialized
Mar 15 15:30:42 ubuntu kernel: [    1.005677] Freeing initrd memory: 13324k freed
Mar 15 15:30:42 ubuntu kernel: [    1.012966] highmem bounce pool size: 64 pages
Mar 15 15:30:42 ubuntu kernel: [    1.012971] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 15 15:30:42 ubuntu kernel: [    1.017505] VFS: Disk quotas dquot_6.5.2
Mar 15 15:30:42 ubuntu kernel: [    1.017558] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 15 15:30:42 ubuntu kernel: [    1.018054] fuse init (API version 7.16)
Mar 15 15:30:42 ubuntu kernel: [    1.018123] msgmni has been set to 1682
Mar 15 15:30:42 ubuntu kernel: [    1.018451] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Mar 15 15:30:42 ubuntu kernel: [    1.018478] io scheduler noop registered
Mar 15 15:30:42 ubuntu kernel: [    1.018479] io scheduler deadline registered
Mar 15 15:30:42 ubuntu kernel: [    1.018490] io scheduler cfq registered (default)
Mar 15 15:30:42 ubuntu kernel: [    1.018576] pcieport 0000:00:1c.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.018625] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.018694] pcieport 0000:00:1c.1: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.018736] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.018802] pcieport 0000:00:1c.3: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.018844] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.018909] pcieport 0000:00:1c.5: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.018952] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.019033] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019038] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Mar 15 15:30:42 ubuntu kernel: [    1.019055] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019057] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019061] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
Mar 15 15:30:42 ubuntu kernel: [    1.019078] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019080] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019085] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Mar 15 15:30:42 ubuntu kernel: [    1.019102] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019103] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Mar 15 15:30:42 ubuntu kernel: [    1.019108] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
Mar 15 15:30:42 ubuntu kernel: [    1.019120] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 15 15:30:42 ubuntu kernel: [    1.019138] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Mar 15 15:30:42 ubuntu kernel: [    1.019189] intel_idle: MWAIT substates: 0x21120
Mar 15 15:30:42 ubuntu kernel: [    1.019190] intel_idle: v0.4 model 0x2A
Mar 15 15:30:42 ubuntu kernel: [    1.019192] intel_idle: lapic_timer_reliable_states 0xffffffff
Mar 15 15:30:42 ubuntu kernel: [    1.019254] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Mar 15 15:30:42 ubuntu kernel: [    1.019289] ACPI: AC Adapter [AC0] (on-line)
Mar 15 15:30:42 ubuntu kernel: [    1.019374] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Mar 15 15:30:42 ubuntu kernel: [    1.033356] ACPI: Lid Switch [LID]
Mar 15 15:30:42 ubuntu kernel: [    1.033389] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Mar 15 15:30:42 ubuntu kernel: [    1.033394] ACPI: Sleep Button [SLPB]
Mar 15 15:30:42 ubuntu kernel: [    1.033422] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 15 15:30:42 ubuntu kernel: [    1.033425] ACPI: Power Button [PWRF]
Mar 15 15:30:42 ubuntu kernel: [    1.033449] ACPI: acpi_idle yielding to intel_idle
Mar 15 15:30:42 ubuntu kernel: [    1.035281] thermal LNXTHERM:00: registered as thermal_zone0
Mar 15 15:30:42 ubuntu kernel: [    1.035283] ACPI: Thermal Zone [THRM] (58 C)
Mar 15 15:30:42 ubuntu kernel: [    1.035303] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Mar 15 15:30:42 ubuntu kernel: [    1.035318] ERST: Table is not found!
Mar 15 15:30:42 ubuntu kernel: [    1.035365] isapnp: Scanning for PnP cards...
Mar 15 15:30:42 ubuntu kernel: [    1.035388] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Mar 15 15:30:42 ubuntu kernel: [    1.048620] ACPI: Battery Slot [BAT0] (battery present)
Mar 15 15:30:42 ubuntu kernel: [    1.389646] isapnp: No Plug & Play device found
Mar 15 15:30:42 ubuntu kernel: [    1.444910] Linux agpgart interface v0.103
Mar 15 15:30:42 ubuntu kernel: [    1.444989] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
Mar 15 15:30:42 ubuntu kernel: [    1.445067] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Mar 15 15:30:42 ubuntu kernel: [    1.446039] agpgart-intel 0000:00:00.0: detected 196608K stolen memory
Mar 15 15:30:42 ubuntu kernel: [    1.446129] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Mar 15 15:30:42 ubuntu kernel: [    1.447035] brd: module loaded
Mar 15 15:30:42 ubuntu kernel: [    1.447468] loop: module loaded
Mar 15 15:30:42 ubuntu kernel: [    1.447807] Fixed MDIO Bus: probed
Mar 15 15:30:42 ubuntu kernel: [    1.447824] PPP generic driver version 2.4.2
Mar 15 15:30:42 ubuntu kernel: [    1.447853] tun: Universal TUN/TAP device driver, 1.6
Mar 15 15:30:42 ubuntu kernel: [    1.447854] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Mar 15 15:30:42 ubuntu kernel: [    1.447908] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Mar 15 15:30:42 ubuntu kernel: [    1.447924] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 15 15:30:42 ubuntu kernel: [    1.447937] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.447941] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Mar 15 15:30:42 ubuntu kernel: [    1.447966] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 15 15:30:42 ubuntu kernel: [    1.447989] ehci_hcd 0000:00:1a.0: debug port 2
Mar 15 15:30:42 ubuntu kernel: [    1.451860] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Mar 15 15:30:42 ubuntu kernel: [    1.451876] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xdfc08000
Mar 15 15:30:42 ubuntu kernel: [    1.464513] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Mar 15 15:30:42 ubuntu kernel: [    1.464680] hub 1-0:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    1.464683] hub 1-0:1.0: 2 ports detected
Mar 15 15:30:42 ubuntu kernel: [    1.464737] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 15 15:30:42 ubuntu kernel: [    1.464748] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.464752] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Mar 15 15:30:42 ubuntu kernel: [    1.464776] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Mar 15 15:30:42 ubuntu kernel: [    1.464796] ehci_hcd 0000:00:1d.0: debug port 2
Mar 15 15:30:42 ubuntu kernel: [    1.468680] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Mar 15 15:30:42 ubuntu kernel: [    1.468694] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xdfc07000
Mar 15 15:30:42 ubuntu kernel: [    1.484482] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Mar 15 15:30:42 ubuntu kernel: [    1.484638] hub 2-0:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    1.484640] hub 2-0:1.0: 2 ports detected
Mar 15 15:30:42 ubuntu kernel: [    1.484683] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Mar 15 15:30:42 ubuntu kernel: [    1.484692] uhci_hcd: USB Universal Host Controller Interface driver
Mar 15 15:30:42 ubuntu kernel: [    1.484749] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Mar 15 15:30:42 ubuntu kernel: [    1.486263] i8042: Detected active multiplexing controller, rev 1.1
Mar 15 15:30:42 ubuntu kernel: [    1.487406] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 15 15:30:42 ubuntu kernel: [    1.487412] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar 15 15:30:42 ubuntu kernel: [    1.487420] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar 15 15:30:42 ubuntu kernel: [    1.487422] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar 15 15:30:42 ubuntu kernel: [    1.487424] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar 15 15:30:42 ubuntu kernel: [    1.487539] mousedev: PS/2 mouse device common for all mice
Mar 15 15:30:42 ubuntu kernel: [    1.487650] rtc_cmos 00:06: RTC can wake from S4
Mar 15 15:30:42 ubuntu kernel: [    1.487737] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Mar 15 15:30:42 ubuntu kernel: [    1.487764] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Mar 15 15:30:42 ubuntu kernel: [    1.487831] device-mapper: uevent: version 1.0.3
Mar 15 15:30:42 ubuntu kernel: [    1.487884] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Mar 15 15:30:42 ubuntu kernel: [    1.487905] EISA: Probing bus 0 at eisa.0
Mar 15 15:30:42 ubuntu kernel: [    1.487908] EISA: Cannot allocate resource for mainboard
Mar 15 15:30:42 ubuntu kernel: [    1.487910] Cannot allocate resource for EISA slot 1
Mar 15 15:30:42 ubuntu kernel: [    1.487912] Cannot allocate resource for EISA slot 2
Mar 15 15:30:42 ubuntu kernel: [    1.487913] Cannot allocate resource for EISA slot 3
Mar 15 15:30:42 ubuntu kernel: [    1.487914] Cannot allocate resource for EISA slot 4
Mar 15 15:30:42 ubuntu kernel: [    1.487916] Cannot allocate resource for EISA slot 5
Mar 15 15:30:42 ubuntu kernel: [    1.487917] Cannot allocate resource for EISA slot 6
Mar 15 15:30:42 ubuntu kernel: [    1.487918] Cannot allocate resource for EISA slot 7
Mar 15 15:30:42 ubuntu kernel: [    1.487920] Cannot allocate resource for EISA slot 8
Mar 15 15:30:42 ubuntu kernel: [    1.487921] EISA: Detected 0 cards.
Mar 15 15:30:42 ubuntu kernel: [    1.487928] cpufreq-nforce2: No nForce2 chipset.
Mar 15 15:30:42 ubuntu kernel: [    1.488029] cpuidle: using governor ladder
Mar 15 15:30:42 ubuntu kernel: [    1.488192] cpuidle: using governor menu
Mar 15 15:30:42 ubuntu kernel: [    1.488194] EFI Variables Facility v0.08 2004-May-17
Mar 15 15:30:42 ubuntu kernel: [    1.488374] TCP cubic registered
Mar 15 15:30:42 ubuntu kernel: [    1.488486] NET: Registered protocol family 10
Mar 15 15:30:42 ubuntu kernel: [    1.488862] NET: Registered protocol family 17
Mar 15 15:30:42 ubuntu kernel: [    1.488873] Registering the dns_resolver key type
Mar 15 15:30:42 ubuntu kernel: [    1.488889] Using IPI No-Shortcut mode
Mar 15 15:30:42 ubuntu kernel: [    1.488944] PM: Hibernation image not present or could not be loaded.
Mar 15 15:30:42 ubuntu kernel: [    1.488952] registered taskstats version 1
Mar 15 15:30:42 ubuntu kernel: [    1.496128]   Magic number: 4:177:538
Mar 15 15:30:42 ubuntu kernel: [    1.496144] tty ttyS18: hash matches
Mar 15 15:30:42 ubuntu kernel: [    1.496231] rtc_cmos 00:06: setting system clock to 2012-03-15 15:30:25 UTC (1331825425)
Mar 15 15:30:42 ubuntu kernel: [    1.496993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 15 15:30:42 ubuntu kernel: [    1.496994] EDD information not available.
Mar 15 15:30:42 ubuntu kernel: [    1.497134] Freeing unused kernel memory: 696k freed
Mar 15 15:30:42 ubuntu kernel: [    1.497251] Write protecting the kernel text: 5344k
Mar 15 15:30:42 ubuntu kernel: [    1.497301] Write protecting the kernel read-only data: 2188k
Mar 15 15:30:42 ubuntu kernel: [    1.530048] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Mar 15 15:30:42 ubuntu kernel: [    1.536008] ahci 0000:00:1f.2: version 3.0
Mar 15 15:30:42 ubuntu kernel: [    1.536022] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 15 15:30:42 ubuntu kernel: [    1.536072] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.537047] xhci_hcd 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 15 15:30:42 ubuntu kernel: [    1.537072] xhci_hcd 0000:03:00.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.537077] xhci_hcd 0000:03:00.0: xHCI Host Controller
Mar 15 15:30:42 ubuntu kernel: [    1.537135] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
Mar 15 15:30:42 ubuntu kernel: [    1.546326] atl1c 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 15 15:30:42 ubuntu kernel: [    1.546339] atl1c 0000:04:00.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.547110] xhci_hcd 0000:03:00.0: irq 19, io mem 0xdde00000
Mar 15 15:30:42 ubuntu kernel: [    1.547184] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.547189] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.547194] xhci_hcd 0000:03:00.0: irq 47 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.547199] xhci_hcd 0000:03:00.0: irq 48 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.547204] xhci_hcd 0000:03:00.0: irq 49 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [    1.547404] xHCI xhci_add_endpoint called for root hub
Mar 15 15:30:42 ubuntu kernel: [    1.547406] xHCI xhci_check_bandwidth called for root hub
Mar 15 15:30:42 ubuntu kernel: [    1.547436] hub 3-0:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    1.547445] hub 3-0:1.0: 2 ports detected
Mar 15 15:30:42 ubuntu kernel: [    1.547506] xhci_hcd 0000:03:00.0: xHCI Host Controller
Mar 15 15:30:42 ubuntu kernel: [    1.547542] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
Mar 15 15:30:42 ubuntu kernel: [    1.547632] xHCI xhci_add_endpoint called for root hub
Mar 15 15:30:42 ubuntu kernel: [    1.547633] xHCI xhci_check_bandwidth called for root hub
Mar 15 15:30:42 ubuntu kernel: [    1.547659] hub 4-0:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    1.547668] hub 4-0:1.0: 2 ports detected
Mar 15 15:30:42 ubuntu kernel: [    1.548469] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
Mar 15 15:30:42 ubuntu kernel: [    1.548474] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
Mar 15 15:30:42 ubuntu kernel: [    1.548480] ahci 0000:00:1f.2: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [    1.557063] scsi0 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.557154] scsi1 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.557279] scsi2 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.558829] scsi3 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.558888] scsi4 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.558938] scsi5 : ahci
Mar 15 15:30:42 ubuntu kernel: [    1.559158] ata1: SATA max UDMA/133 abar m2048@0xdfc06000 port 0xdfc06100 irq 44
Mar 15 15:30:42 ubuntu kernel: [    1.559160] ata2: DUMMY
Mar 15 15:30:42 ubuntu kernel: [    1.559164] ata3: SATA max UDMA/133 abar m2048@0xdfc06000 port 0xdfc06200 irq 44
Mar 15 15:30:42 ubuntu kernel: [    1.559166] ata4: DUMMY
Mar 15 15:30:42 ubuntu kernel: [    1.559168] ata5: DUMMY
Mar 15 15:30:42 ubuntu kernel: [    1.559169] ata6: DUMMY
Mar 15 15:30:42 ubuntu kernel: [    1.672866] atl1c 0000:04:00.0: version 1.0.1.0-NAPI
Mar 15 15:30:42 ubuntu kernel: [    1.776152] usb 1-1: new high speed USB device number 2 using ehci_hcd
Mar 15 15:30:42 ubuntu kernel: [    1.876003] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 15 15:30:42 ubuntu kernel: [    1.876047] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 15 15:30:42 ubuntu kernel: [    1.878495] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Mar 15 15:30:42 ubuntu kernel: [    1.878507] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.880255] ata3.00: ATAPI: MATSHITADVD-RAM UJ8B0, 1.00, max UDMA/100
Mar 15 15:30:42 ubuntu kernel: [    1.881008] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.881244] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Mar 15 15:30:42 ubuntu kernel: [    1.881256] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.882966] ata3.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Mar 15 15:30:42 ubuntu kernel: [    1.882978] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.884730] ata3.00: configured for UDMA/100
Mar 15 15:30:42 ubuntu kernel: [    1.886513] ata1.00: ATA-8: WDC WD6400BPVT-80HXZT3, 01.01A01, max UDMA/133
Mar 15 15:30:42 ubuntu kernel: [    1.886522] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Mar 15 15:30:42 ubuntu kernel: [    1.891755] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.891948] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
Mar 15 15:30:42 ubuntu kernel: [    1.891951] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Mar 15 15:30:42 ubuntu kernel: [    1.897293] ata1.00: configured for UDMA/133
Mar 15 15:30:42 ubuntu kernel: [    1.897486] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BPVT-8 01.0 PQ: 0 ANSI: 5
Mar 15 15:30:42 ubuntu kernel: [    1.897621] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 15 15:30:42 ubuntu kernel: [    1.897659] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Mar 15 15:30:42 ubuntu kernel: [    1.897663] sd 0:0:0:0: [sda] 4096-byte physical blocks
Mar 15 15:30:42 ubuntu kernel: [    1.897742] sd 0:0:0:0: [sda] Write Protect is off
Mar 15 15:30:42 ubuntu kernel: [    1.897745] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 15 15:30:42 ubuntu kernel: [    1.897775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 15 15:30:42 ubuntu kernel: [    1.899405] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8B0    1.00 PQ: 0 ANSI: 5
Mar 15 15:30:42 ubuntu kernel: [    1.901491] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 15 15:30:42 ubuntu kernel: [    1.901500] cdrom: Uniform CD-ROM driver Revision: 3.20
Mar 15 15:30:42 ubuntu kernel: [    1.901636] sr 2:0:0:0: Attached scsi CD-ROM sr0
Mar 15 15:30:42 ubuntu kernel: [    1.901674] sr 2:0:0:0: Attached scsi generic sg1 type 5
Mar 15 15:30:42 ubuntu kernel: [    1.908680] hub 1-1:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    1.908773] hub 1-1:1.0: 6 ports detected
Mar 15 15:30:42 ubuntu kernel: [    1.950798]  sda: sda1 sda2 sda3 < sda5 >
Mar 15 15:30:42 ubuntu kernel: [    1.951182] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 15 15:30:42 ubuntu kernel: [    1.987776] Refined TSC clocksource calibration: 2394.559 MHz.
Mar 15 15:30:42 ubuntu kernel: [    1.987790] Switching to clocksource tsc
Mar 15 15:30:42 ubuntu kernel: [    2.019763] usb 2-1: new high speed USB device number 2 using ehci_hcd
Mar 15 15:30:42 ubuntu kernel: [    2.156164] hub 2-1:1.0: USB hub found
Mar 15 15:30:42 ubuntu kernel: [    2.156245] hub 2-1:1.0: 6 ports detected
Mar 15 15:30:42 ubuntu kernel: [    2.227527] usb 1-1.2: new high speed USB device number 3 using ehci_hcd
Mar 15 15:30:42 ubuntu kernel: [    2.729432] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
Mar 15 15:30:42 ubuntu kernel: [   17.347474] lp: driver loaded but no devices found
Mar 15 15:30:42 ubuntu kernel: [   17.367213] mei: module is from the staging directory, the quality is unknown, you have been warned.
Mar 15 15:30:42 ubuntu kernel: [   17.367496] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 15 15:30:42 ubuntu kernel: [   17.367503] mei 0000:00:16.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [   17.379956] [drm] Initialized drm 1.1.0 20060810
Mar 15 15:30:42 ubuntu kernel: [   17.392076] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 15 15:30:42 ubuntu kernel: [   17.392082] i915 0000:00:02.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [   17.419875] wmi: Mapper loaded
Mar 15 15:30:42 ubuntu kernel: [   17.436324] i915 0000:00:02.0: irq 50 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [   17.436330] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Mar 15 15:30:42 ubuntu kernel: [   17.436332] [drm] Driver supports precise vblank timestamp query.
Mar 15 15:30:42 ubuntu kernel: [   17.436368] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Mar 15 15:30:42 ubuntu kernel: [   17.488310] cfg80211: Calling CRDA to update world regulatory domain
Mar 15 15:30:42 ubuntu kernel: [   17.503124] rtl8192ce 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 15 15:30:42 ubuntu kernel: [   17.503135] rtl8192ce 0000:02:00.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [   17.509206] type=1400 audit(1331843441.535:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=628 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   17.509642] type=1400 audit(1331843441.535:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   17.509919] type=1400 audit(1331843441.535:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   17.581205] asus_wmi: ASUS WMI generic driver loaded
Mar 15 15:30:42 ubuntu kernel: [   17.581531] asus_wmi: Initialization: 0x1
Mar 15 15:30:42 ubuntu kernel: [   17.581568] asus_wmi: BIOS WMI version: 1792.6
Mar 15 15:30:42 ubuntu kernel: [   17.581623] asus_wmi: SFUN value: 0x1a0877
Mar 15 15:30:42 ubuntu kernel: [   17.583690] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
Mar 15 15:30:42 ubuntu kernel: [   17.586994] cfg80211: World regulatory domain updated:
Mar 15 15:30:42 ubuntu kernel: [   17.586997] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 15 15:30:42 ubuntu kernel: [   17.587001] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.587003] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.587006] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.587008] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.587011] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.621005] Linux video capture interface: v2.00
Mar 15 15:30:42 ubuntu kernel: [   17.621924] uvcvideo: Found UVC 1.00 device USB 2.0 UVC VGA WebCam (13d3:5710)
Mar 15 15:30:42 ubuntu kernel: [   17.623097] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 15 15:30:42 ubuntu kernel: [   17.629815] input: USB 2.0 UVC VGA WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
Mar 15 15:30:42 ubuntu kernel: [   17.630062] usbcore: registered new interface driver uvcvideo
Mar 15 15:30:42 ubuntu kernel: [   17.630065] USB Video Class driver (v1.1.0)
Mar 15 15:30:42 ubuntu kernel: [   17.640402] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Mar 15 15:30:42 ubuntu kernel: [   17.657505] asus_wmi: Backlight controlled by ACPI video driver
Mar 15 15:30:42 ubuntu kernel: [   17.701921] psmouse serio4: ID: 10 00 64
Mar 15 15:30:42 ubuntu kernel: [   17.717603] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717607] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717610] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717623] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717626] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717629] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717631] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717634] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717636] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717638] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717640] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717643] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717645] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717647] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717649] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717652] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717654] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717656] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717658] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717661] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717663] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717665] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717667] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717669] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717671] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.717674] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.717676] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Mar 15 15:30:42 ubuntu kernel: [   17.717819] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Mar 15 15:30:42 ubuntu kernel: [   17.717941] cfg80211: Calling CRDA for country: EC
Mar 15 15:30:42 ubuntu kernel: [   17.720220] fbcon: inteldrmfb (fb0) is primary device
Mar 15 15:30:42 ubuntu kernel: [   17.720277] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Mar 15 15:30:42 ubuntu kernel: [   17.720317] Console: switching to colour frame buffer device 170x48
Mar 15 15:30:42 ubuntu kernel: [   17.720347] fb0: inteldrmfb frame buffer device
Mar 15 15:30:42 ubuntu kernel: [   17.720349] drm: registered panic notifier
Mar 15 15:30:42 ubuntu kernel: [   17.720844] rtlwifi: wireless switch is on
Mar 15 15:30:42 ubuntu kernel: [   17.721456] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721459] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721461] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721463] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721464] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721466] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721468] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721469] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721471] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721473] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721474] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721476] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721477] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721479] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721480] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721482] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721484] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721485] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721487] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721488] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721490] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721492] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721493] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721495] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721496] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:42 ubuntu kernel: [   17.721498] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721499] cfg80211: Disabling freq 2484 MHz
Mar 15 15:30:42 ubuntu kernel: [   17.721502] cfg80211: Regulatory domain changed to country: EC
Mar 15 15:30:42 ubuntu kernel: [   17.721503] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 15 15:30:42 ubuntu kernel: [   17.721505] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721507] cfg80211:     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721508] cfg80211:     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.721510] cfg80211:     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
Mar 15 15:30:42 ubuntu kernel: [   17.741219] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
Mar 15 15:30:42 ubuntu kernel: [   17.741568] acpi device:45: registered as cooling_device4
Mar 15 15:30:42 ubuntu kernel: [   17.741916] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
Mar 15 15:30:42 ubuntu kernel: [   17.741975] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar 15 15:30:42 ubuntu kernel: [   17.742030] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Mar 15 15:30:42 ubuntu kernel: [   17.742071] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 15 15:30:42 ubuntu kernel: [   17.742127] HDA Intel 0000:00:1b.0: irq 51 for MSI/MSI-X
Mar 15 15:30:42 ubuntu kernel: [   17.742156] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar 15 15:30:42 ubuntu kernel: [   17.784782] elantech: assuming hardware version 3, firmware version 69.15.1
Mar 15 15:30:42 ubuntu kernel: [   17.815512] elantech: Synaptics capabilities query result 0x78, 0x15, 0x0c.
Mar 15 15:30:42 ubuntu kernel: [   17.882771] elantech: x_max = 2508, y_max = 1320
Mar 15 15:30:42 ubuntu kernel: [   17.896057] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
Mar 15 15:30:42 ubuntu kernel: [   18.285967] hda_codec: ALC269VB: BIOS auto-probing.
Mar 15 15:30:42 ubuntu kernel: [   18.294421] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
Mar 15 15:30:42 ubuntu kernel: [   18.294609] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Mar 15 15:30:42 ubuntu kernel: [   18.294782] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Mar 15 15:30:42 ubuntu kernel: [   18.294846] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Mar 15 15:30:42 ubuntu kernel: [   18.337164] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
Mar 15 15:30:42 ubuntu kernel: [   18.361637] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
Mar 15 15:30:42 ubuntu kernel: [   18.472397] ppdev: user-space parallel port driver
Mar 15 15:30:42 ubuntu kernel: [   18.475618] type=1400 audit(1331843442.503:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=994 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.478231] type=1400 audit(1331843442.503:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=998 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.482100] type=1400 audit(1331843442.507:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=995 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.482750] type=1400 audit(1331843442.507:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=998 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.484189] type=1400 audit(1331843442.511:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=995 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.484198] type=1400 audit(1331843442.511:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1002 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu kernel: [   18.484483] type=1400 audit(1331843442.511:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=995 comm="apparmor_parser"
Mar 15 15:30:42 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: init!
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: update_system_hostname
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPluginIfupdown: management mode: unmanaged
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0, iface: eth0)
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: end _init.
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    Ifupdown: get unmanaged devices count: 0
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: (158897544) ... get_connections.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: (158897544) ... get_connections (managed=false): return empty list.
Mar 15 15:30:42 ubuntu NetworkManager[971]:    keyfile: parsing morgan ... 
Mar 15 15:30:42 ubuntu NetworkManager[971]:    keyfile:     read connection 'morgan'
Mar 15 15:30:42 ubuntu NetworkManager[971]:    Ifupdown: get unmanaged devices count: 0
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> modem-manager is now available
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> monitoring kernel firmware directory '/lib/firmware'.
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/asus-nb-wmi/rfkill/rfkill0) (driver asus-nb-wmi)
Mar 15 15:30:42 ubuntu kernel: [   18.581427] init: failsafe main process (930) killed by TERM signal
Mar 15 15:30:42 ubuntu kernel: [   18.581869] init: apport pre-start process (1078) terminated with status 1
Mar 15 15:30:42 ubuntu cron[1086]: (CRON) INFO (pidfile fd = 3)
Mar 15 15:30:42 ubuntu anacron[1100]: Anacron 2.3 started on 2012-03-15
Mar 15 15:30:42 ubuntu kernel: [   18.589070] init: apport post-stop process (1101) terminated with status 1
Mar 15 15:30:42 ubuntu acpid: starting up with proc fs
Mar 15 15:30:42 ubuntu acpid: 32 rules loaded
Mar 15 15:30:42 ubuntu acpid: waiting for events: event logging is off
Mar 15 15:30:42 ubuntu cron[1104]: (CRON) STARTUP (fork ok)
Mar 15 15:30:42 ubuntu cron[1104]: (CRON) INFO (Running @reboot jobs)
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> WiFi enabled by radio killswitch; enabled by state file
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> WWAN enabled by radio killswitch; enabled by state file
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> WiMAX enabled by radio killswitch; enabled by state file
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> Networking is enabled by state file
Mar 15 15:30:42 ubuntu kernel: [   18.611611] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): now managed
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): bringing up device.
Mar 15 15:30:42 ubuntu anacron[1100]: Normal exit (0 jobs run)
Mar 15 15:30:42 ubuntu acpid: client connected from 1131[0:0]
Mar 15 15:30:42 ubuntu acpid: 1 client rule loaded
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): preparing device.
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar 15 15:30:42 ubuntu kernel: [   18.951415] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 15 15:30:42 ubuntu dbus[958]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): carrier is OFF
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): now managed
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 15 15:30:42 ubuntu NetworkManager[971]: <info> (eth0): bringing up device.
Mar 15 15:30:42 ubuntu kernel: [   18.957356] atl1c 0000:04:00.0: irq 52 for MSI/MSI-X
Mar 15 15:30:42 ubuntu dbus[958]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Mar 15 15:30:42 ubuntu bluetoothd[1168]: Bluetooth daemon 4.96
Mar 15 15:30:42 ubuntu bluetoothd[1168]: Starting SDP server
Mar 15 15:30:43 ubuntu kernel: [   18.971888] Bluetooth: Core ver 2.16
Mar 15 15:30:43 ubuntu kernel: [   18.971909] NET: Registered protocol family 31
Mar 15 15:30:43 ubuntu kernel: [   18.971911] Bluetooth: HCI device and connection manager initialized
Mar 15 15:30:43 ubuntu kernel: [   18.971913] Bluetooth: HCI socket layer initialized
Mar 15 15:30:43 ubuntu kernel: [   18.971915] Bluetooth: L2CAP socket layer initialized
Mar 15 15:30:43 ubuntu kernel: [   18.971960] Bluetooth: SCO socket layer initialized
Mar 15 15:30:43 ubuntu kernel: [   18.973464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 15 15:30:43 ubuntu kernel: [   18.973467] Bluetooth: BNEP filters: protocol multicast
Mar 15 15:30:43 ubuntu kernel: [   18.973859] Bluetooth: RFCOMM TTY layer initialized
Mar 15 15:30:43 ubuntu kernel: [   18.973863] Bluetooth: RFCOMM socket layer initialized
Mar 15 15:30:43 ubuntu kernel: [   18.973865] Bluetooth: RFCOMM ver 1.11
Mar 15 15:30:43 ubuntu udev-configure-printer: add /module/lp
Mar 15 15:30:43 ubuntu udev-configure-printer: Failed to get parent
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> (eth0): preparing device.
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> (eth0): deactivating device (reason 'managed') [2]
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0
Mar 15 15:30:43 ubuntu kernel: [   19.039547] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 15 15:30:43 ubuntu NetworkManager[971]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> wpa_supplicant started
Mar 15 15:30:43 ubuntu NetworkManager[971]: <warn> bluez error getting default adapter: No such adapter
Mar 15 15:30:43 ubuntu anacron[1255]: Anacron 2.3 started on 2012-03-15
Mar 15 15:30:43 ubuntu anacron[1255]: Normal exit (0 jobs run)
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: starting -> ready
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 15 15:30:43 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar 15 15:30:43 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Mar 15 15:30:43 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.Accounts'
Mar 15 15:30:43 ubuntu accounts-daemon[1266]: started daemon version 0.6.14
Mar 15 15:30:43 ubuntu kernel: [   19.085530] rtl8192c: Loading firmware file rtlwifi/rtl8192cfw.bin
Mar 15 15:30:43 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Mar 15 15:30:44 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Mar 15 15:30:45 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Mar 15 15:30:45 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.UPower'
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Auto-activating connection 'morgan'.
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) starting connection 'morgan'
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0/wireless): connection 'morgan' requires no security.  No secrets needed.
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Config: added 'ssid' value 'morgan'
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Config: added 'scan_ssid' value '1'
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Config: added 'key_mgmt' value 'NONE'
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> Config: set interface ap_scan to 1
Mar 15 15:30:45 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 15 15:30:45 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Mar 15 15:30:45 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Mar 15 15:30:45 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully called chroot.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully dropped privileges.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully limited resources.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Running.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Canary thread running.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Watchdog thread running.
Mar 15 15:30:45 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully made thread 1447 of process 1447 (n/a) owned by '104' high priority at nice level -11.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Supervising 1 threads of 1 processes of 1 users.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully made thread 1456 of process 1447 (n/a) owned by '104' RT at priority 5.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Supervising 2 threads of 1 processes of 1 users.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Successfully made thread 1457 of process 1447 (n/a) owned by '104' RT at priority 5.
Mar 15 20:30:45 ubuntu rtkit-daemon[1449]: Supervising 3 threads of 1 processes of 1 users.
Mar 15 15:30:46 ubuntu wpa_supplicant[1151]: Trying to authenticate with 00:22:6b:55:d8:9d (SSID='morgan' freq=2412 MHz)
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar 15 15:30:46 ubuntu kernel: [   22.016294] wlan0: authenticate with 00:22:6b:55:d8:9d (try 1)
Mar 15 15:30:46 ubuntu wpa_supplicant[1151]: Trying to associate with 00:22:6b:55:d8:9d (SSID='morgan' freq=2412 MHz)
Mar 15 15:30:46 ubuntu kernel: [   22.018425] wlan0: authenticated
Mar 15 15:30:46 ubuntu kernel: [   22.018618] wlan0: associate with 00:22:6b:55:d8:9d (try 1)
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: authenticating -> associating
Mar 15 15:30:46 ubuntu kernel: [   22.026062] wlan0: RX AssocResp from 00:22:6b:55:d8:9d (capab=0x401 status=0 aid=1)
Mar 15 15:30:46 ubuntu kernel: [   22.026072] wlan0: associated
Mar 15 15:30:46 ubuntu wpa_supplicant[1151]: Associated with 00:22:6b:55:d8:9d
Mar 15 15:30:46 ubuntu wpa_supplicant[1151]: CTRL-EVENT-CONNECTED - Connection to 00:22:6b:55:d8:9d completed (auth) [id=0 id_str=]
Mar 15 15:30:46 ubuntu kernel: [   22.036666] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 15 15:30:46 ubuntu kernel: [   22.036752] cfg80211: Calling CRDA for country: US
Mar 15 15:30:46 ubuntu kernel: [   22.039306] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039310] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039311] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039313] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039315] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039317] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039318] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039320] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039321] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039323] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039324] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039326] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039328] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039329] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039331] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039332] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039334] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039336] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039337] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039339] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039340] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 15 15:30:46 ubuntu kernel: [   22.039342] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039343] cfg80211: Disabling freq 2467 MHz
Mar 15 15:30:46 ubuntu kernel: [   22.039344] cfg80211: Disabling freq 2472 MHz
Mar 15 15:30:46 ubuntu kernel: [   22.039345] cfg80211: Disabling freq 2484 MHz
Mar 15 15:30:46 ubuntu kernel: [   22.039349] cfg80211: Regulatory domain changed to country: US
Mar 15 15:30:46 ubuntu kernel: [   22.039350] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 15 15:30:46 ubuntu kernel: [   22.039352] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039353] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039355] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039357] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039358] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 15 15:30:46 ubuntu kernel: [   22.039360] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): supplicant interface state: associating -> completed
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'morgan'.
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> dhclient started with pid 1461
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 15 15:30:46 ubuntu dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Mar 15 15:30:46 ubuntu dhclient: Copyright 2004-2010 Internet Systems Consortium.
Mar 15 15:30:46 ubuntu dhclient: All rights reserved.
Mar 15 15:30:46 ubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 15 15:30:46 ubuntu dhclient: 
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 15 15:30:46 ubuntu dhclient: Listening on LPF/wlan0/74:2f:68:14:fe:92
Mar 15 15:30:46 ubuntu dhclient: Sending on   LPF/wlan0/74:2f:68:14:fe:92
Mar 15 15:30:46 ubuntu dhclient: Sending on   Socket/fallback
Mar 15 15:30:46 ubuntu dhclient: DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
Mar 15 15:30:46 ubuntu dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Mar 15 15:30:46 ubuntu dhclient: bound to 192.168.1.100 -- renewal in 41304 seconds.
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   address 192.168.1.100
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   prefix 24 (255.255.255.0)
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   gateway 192.168.1.1
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   nameserver '75.75.75.75'
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   nameserver '75.75.76.76'
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info>   domain name 'hsd1.ms.comcast.net.'
Mar 15 15:30:46 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 15 15:30:46 ubuntu kernel: [   22.446796] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
Mar 15 15:30:47 ubuntu kernel: [   23.039016] init: plymouth-stop pre-start process (1499) terminated with status 1
Mar 15 15:30:47 ubuntu NetworkManager[971]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 15 15:30:47 ubuntu NetworkManager[971]: <info> Policy set 'morgan' (wlan0) as default for IPv4 routing and DNS.
Mar 15 15:30:47 ubuntu NetworkManager[971]: <info> Activation (wlan0) successful, device activated.
Mar 15 15:30:47 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 15 15:30:47 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 15 15:30:47 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 15 15:30:47 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 15 15:30:49 ubuntu nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Successfully made thread 1716 of process 1716 (n/a) owned by '1000' high priority at nice level -11.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Supervising 4 threads of 2 processes of 2 users.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Successfully made thread 1717 of process 1716 (n/a) owned by '1000' RT at priority 5.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Supervising 5 threads of 2 processes of 2 users.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Successfully made thread 1718 of process 1716 (n/a) owned by '1000' RT at priority 5.
Mar 15 20:30:52 ubuntu rtkit-daemon[1449]: Supervising 6 threads of 2 processes of 2 users.
Mar 15 15:30:52 ubuntu dbus[958]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Mar 15 15:30:52 ubuntu dbus[958]: [system] Successfully activated service 'org.freedesktop.UDisks'
Mar 15 15:30:56 ubuntu kernel: [   32.741904] wlan0: no IPv6 routers present
Mar 15 15:30:59 ubuntu ntpdate[1601]: adjust time server 91.189.94.4 offset -0.377355 sec
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 15 15:31:06 ubuntu NetworkManager[971]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Mar 15 15:31:54 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 15:31:55 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 15:31:55 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 15:31:55 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 15:31:55 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 15:31:55 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ae596d940f6543ff8146f65338fead84
Mar 15 15:31:57 ubuntu dbus[958]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Mar 15 15:31:58 ubuntu dbus[958]: [system] Successfully activated service 'com.ubuntu.SystemService'
Mar 15 15:31:59 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 15:36:55 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 15:36:55 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 16:17:01 ubuntu CRON[2679]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 16:47:56 ubuntu kernel: [ 4646.019426] kbd_keycode: 21 callbacks suppressed
Mar 15 16:47:56 ubuntu kernel: [ 4646.019435] keyboard: can't emulate rawmode for keycode 240
Mar 15 16:47:56 ubuntu kernel: [ 4646.019453] keyboard: can't emulate rawmode for keycode 240
Mar 15 16:47:56 ubuntu kernel: [ 4646.019462] asus_wmi: Unknown key 57 pressed
Mar 15 16:47:57 ubuntu kernel: [ 4646.770751] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
Mar 15 16:54:25 ubuntu kernel: [ 5034.816212] CPU3: Package power limit notification (total events = 1)
Mar 15 16:54:25 ubuntu kernel: [ 5034.816216] CPU1: Package power limit notification (total events = 1)
Mar 15 16:54:25 ubuntu kernel: [ 5034.816219] CPU2: Package power limit notification (total events = 1)
Mar 15 16:54:25 ubuntu kernel: [ 5034.816223] CPU0: Package power limit notification (total events = 1)
Mar 15 16:54:25 ubuntu kernel: [ 5034.827223] CPU2: Package power limit normal
Mar 15 16:54:25 ubuntu kernel: [ 5034.827234] CPU3: Package power limit normal
Mar 15 16:54:25 ubuntu kernel: [ 5034.827242] CPU1: Package power limit normal
Mar 15 16:54:25 ubuntu kernel: [ 5034.827251] CPU0: Package power limit normal
Mar 15 16:55:24 ubuntu kernel: [ 5093.262547] [Hardware Error]: Machine check events logged
Mar 15 17:07:38 ubuntu kernel: [ 5826.122915] CPU2: Package power limit notification (total events = 2)
Mar 15 17:07:38 ubuntu kernel: [ 5826.122919] CPU3: Package power limit notification (total events = 2)
Mar 15 17:07:38 ubuntu kernel: [ 5826.122922] CPU1: Package power limit notification (total events = 2)
Mar 15 17:07:38 ubuntu kernel: [ 5826.122925] CPU0: Package power limit notification (total events = 2)
Mar 15 17:07:38 ubuntu kernel: [ 5826.133913] CPU1: Package power limit normal
Mar 15 17:07:38 ubuntu kernel: [ 5826.133916] CPU3: Package power limit normal
Mar 15 17:07:38 ubuntu kernel: [ 5826.133929] CPU2: Package power limit normal
Mar 15 17:07:38 ubuntu kernel: [ 5826.133931] CPU0: Package power limit normal
Mar 15 17:07:54 ubuntu kernel: [ 5842.146812] [Hardware Error]: Machine check events logged
Mar 15 17:16:31 ubuntu kernel: [ 6358.526037] keyboard: can't emulate rawmode for keycode 240
Mar 15 17:16:31 ubuntu kernel: [ 6358.526058] keyboard: can't emulate rawmode for keycode 240
Mar 15 17:16:31 ubuntu kernel: [ 6358.526069] asus_wmi: Unknown key 58 pressed
Mar 15 17:16:31 ubuntu anacron[3330]: Anacron 2.3 started on 2012-03-15
Mar 15 17:16:31 ubuntu anacron[3330]: Normal exit (0 jobs run)
Mar 15 17:16:33 ubuntu kernel: [ 6360.498701] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
Mar 15 17:17:01 ubuntu CRON[3385]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 18:17:01 ubuntu CRON[3905]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 18:33:22 ubuntu kernel: [10962.649820] keyboard: can't emulate rawmode for keycode 240
Mar 15 18:33:22 ubuntu kernel: [10962.649847] keyboard: can't emulate rawmode for keycode 240
Mar 15 18:33:22 ubuntu kernel: [10962.649857] asus_wmi: Unknown key 57 pressed
Mar 15 18:33:24 ubuntu kernel: [10964.314828] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
Mar 15 18:38:02 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 18:38:02 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 18:38:02 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 18:38:02 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 18:38:02 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 18:38:02 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/dc092968cc9a4e1a9694b8ebae1bbe37
Mar 15 18:38:03 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 18:38:19 ubuntu AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'cheese')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Mar 15 18:38:19 ubuntu AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/a5bc8a8fa8a14a76bfacc08feada8a7a
Mar 15 18:38:56 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/a5bc8a8fa8a14a76bfacc08feada8a7a
Mar 15 18:38:56 ubuntu AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'cheese')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Mar 15 18:38:57 ubuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/a5bc8a8fa8a14a76bfacc08feada8a7a
Mar 15 18:38:57 ubuntu AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'cheese')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Mar 15 18:39:51 ubuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/a5bc8a8fa8a14a76bfacc08feada8a7a
Mar 15 18:45:04 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 18:45:04 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 18:45:04 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 18:45:04 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 18:45:04 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 18:45:04 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 18:45:04 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 18:45:04 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/629fe60637044e29a5f7f21ab8622ecd
Mar 15 18:45:05 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 18:45:27 ubuntu kernel: [11686.103467] CPU2: Package power limit notification (total events = 3)
Mar 15 18:45:27 ubuntu kernel: [11686.103470] CPU0: Package power limit notification (total events = 3)
Mar 15 18:45:27 ubuntu kernel: [11686.103474] CPU3: Package power limit notification (total events = 3)
Mar 15 18:45:27 ubuntu kernel: [11686.103477] CPU1: Package power limit notification (total events = 3)
Mar 15 18:45:27 ubuntu kernel: [11686.114468] CPU0: Package power limit normal
Mar 15 18:45:27 ubuntu kernel: [11686.114471] CPU3: Package power limit normal
Mar 15 18:45:27 ubuntu kernel: [11686.114474] CPU2: Package power limit normal
Mar 15 18:45:27 ubuntu kernel: [11686.114476] CPU1: Package power limit normal
Mar 15 18:50:05 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 18:50:05 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 18:50:05 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 18:50:05 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 18:50:05 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 18:50:05 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 18:50:05 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 18:50:05 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/492d9f5a5dd14f8b961b9ad15008881b
Mar 15 18:50:06 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 18:50:24 ubuntu kernel: [11982.997818] [Hardware Error]: Machine check events logged
Mar 15 18:56:05 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 18:56:05 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 18:56:05 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 18:56:05 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 18:56:05 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 18:56:05 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 18:56:05 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 18:56:05 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/a796da21d70e4d3dadb7ded634164da7
Mar 15 18:56:06 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:02:05 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:02:05 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:02:05 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:02:05 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:02:05 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:02:05 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:02:05 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:02:05 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/662bf5459d0e473b9f9829718b5aab45
Mar 15 19:02:06 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:07:06 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:07:06 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:07:06 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:07:06 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:07:06 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:07:06 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:07:06 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:07:06 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/27757bf536c54df08d135e546beecbec
Mar 15 19:07:07 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:12:07 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:12:07 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:12:07 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:12:07 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:12:07 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:12:07 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:12:07 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:12:07 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/7a646eb1fd4c4c4c90969bf7e66078d4
Mar 15 19:12:08 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:14:39 ubuntu kernel: [13435.960480] CPU2: Package power limit notification (total events = 4)
Mar 15 19:14:39 ubuntu kernel: [13435.960484] CPU3: Package power limit notification (total events = 4)
Mar 15 19:14:39 ubuntu kernel: [13435.960487] CPU1: Package power limit notification (total events = 4)
Mar 15 19:14:39 ubuntu kernel: [13435.960491] CPU0: Package power limit notification (total events = 4)
Mar 15 19:14:39 ubuntu kernel: [13435.971473] CPU0: Package power limit normal
Mar 15 19:14:39 ubuntu kernel: [13435.971483] CPU2: Package power limit normal
Mar 15 19:14:39 ubuntu kernel: [13435.971493] CPU1: Package power limit normal
Mar 15 19:14:39 ubuntu kernel: [13435.971501] CPU3: Package power limit normal
Mar 15 19:15:24 ubuntu kernel: [13480.778338] [Hardware Error]: Machine check events logged
Mar 15 19:16:37 ubuntu kernel: [13553.242581] usb 2-1.2: new high speed USB device number 3 using ehci_hcd
Mar 15 19:16:39 ubuntu mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Mar 15 19:16:39 ubuntu mtp-probe: bus: 2, device: 3 was not an MTP device
Mar 15 19:16:39 ubuntu kernel: [13556.165571] usbcore: registered new interface driver uas
Mar 15 19:16:39 ubuntu kernel: [13556.180728] Initializing USB Mass Storage driver...
Mar 15 19:16:39 ubuntu kernel: [13556.180957] scsi6 : usb-storage 2-1.2:1.0
Mar 15 19:16:39 ubuntu kernel: [13556.181144] usbcore: registered new interface driver usb-storage
Mar 15 19:16:39 ubuntu kernel: [13556.181148] USB Mass Storage support registered.
Mar 15 19:16:40 ubuntu kernel: [13557.177829] scsi 6:0:0:0: Direct-Access     Seagate  Desktop          0146 PQ: 0 ANSI: 4
Mar 15 19:16:41 ubuntu kernel: [13557.312934] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar 15 19:16:41 ubuntu kernel: [13557.314768] sd 6:0:0:0: [sdb] 732566644 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 15 19:16:41 ubuntu kernel: [13557.317483] sd 6:0:0:0: [sdb] Write Protect is off
Mar 15 19:16:41 ubuntu kernel: [13557.317497] sd 6:0:0:0: [sdb] Mode Sense: 1c 00 00 00
Mar 15 19:16:41 ubuntu kernel: [13557.318999] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 15 19:16:41 ubuntu kernel: [13557.321459] sd 6:0:0:0: [sdb] 732566644 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 15 19:16:41 ubuntu kernel: [13557.341280]  sdb: sdb1
Mar 15 19:16:41 ubuntu kernel: [13557.342621] sd 6:0:0:0: [sdb] 732566644 4096-byte logical blocks: (3.00 TB/2.72 TiB)
Mar 15 19:16:41 ubuntu kernel: [13557.343857] sd 6:0:0:0: [sdb] Attached SCSI disk
Mar 15 19:16:44 ubuntu ntfs-3g[5285]: Version 2011.4.12AR.4 external FUSE 28
Mar 15 19:16:44 ubuntu ntfs-3g[5285]: Mounted /dev/sdb1 (Read-Write, label "Expansion Drive", NTFS 3.1)
Mar 15 19:16:44 ubuntu ntfs-3g[5285]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Mar 15 19:16:44 ubuntu ntfs-3g[5285]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096,default_permissions
Mar 15 19:16:44 ubuntu ntfs-3g[5285]: Global ownership and permissions enforced, configuration type 7
Mar 15 19:17:01 ubuntu CRON[5299]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 19:17:08 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:17:08 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:17:08 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:17:08 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:17:08 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:17:08 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:17:08 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:17:08 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/77cb0226f0f04b76bc21e7d929de96ca
Mar 15 19:17:09 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:20:18 ubuntu kernel: [13774.158498] CPU3: Package power limit notification (total events = 16)
Mar 15 19:20:18 ubuntu kernel: [13774.158502] CPU1: Package power limit notification (total events = 16)
Mar 15 19:20:18 ubuntu kernel: [13774.158506] CPU2: Package power limit notification (total events = 16)
Mar 15 19:20:18 ubuntu kernel: [13774.158509] CPU0: Package power limit notification (total events = 16)
Mar 15 19:20:18 ubuntu kernel: [13774.169550] CPU0: Package power limit normal
Mar 15 19:20:18 ubuntu kernel: [13774.169560] CPU2: Package power limit normal
Mar 15 19:20:18 ubuntu kernel: [13774.169571] CPU1: Package power limit normal
Mar 15 19:20:18 ubuntu kernel: [13774.169580] CPU3: Package power limit normal
Mar 15 19:22:09 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:22:09 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:22:09 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:22:09 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:22:09 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:22:09 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:22:09 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:22:09 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/50a73d27b8d24af084d0f1e26325453c
Mar 15 19:22:10 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:25:37 ubuntu kernel: [14093.144492] CPU1: Package power limit notification (total events = 40)
Mar 15 19:25:37 ubuntu kernel: [14093.144496] CPU3: Package power limit notification (total events = 40)
Mar 15 19:25:37 ubuntu kernel: [14093.144500] CPU0: Package power limit notification (total events = 40)
Mar 15 19:25:37 ubuntu kernel: [14093.144503] CPU2: Package power limit notification (total events = 40)
Mar 15 19:25:37 ubuntu kernel: [14093.155520] CPU3: Package power limit normal
Mar 15 19:25:37 ubuntu kernel: [14093.155523] CPU1: Package power limit normal
Mar 15 19:25:37 ubuntu kernel: [14093.155526] CPU2: Package power limit normal
Mar 15 19:25:37 ubuntu kernel: [14093.155529] CPU0: Package power limit normal
Mar 15 19:27:10 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:27:10 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:27:10 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:27:11 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:27:11 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:27:11 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:27:11 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:27:11 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/9d6fd3d57c4b43c6801b7af395a10f7e
Mar 15 19:27:12 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:31:43 ubuntu kernel: [14458.717884] CPU1: Package power limit notification (total events = 90)
Mar 15 19:31:43 ubuntu kernel: [14458.717888] CPU3: Package power limit notification (total events = 90)
Mar 15 19:31:43 ubuntu kernel: [14458.717891] CPU2: Package power limit notification (total events = 90)
Mar 15 19:31:43 ubuntu kernel: [14458.717895] CPU0: Package power limit notification (total events = 90)
Mar 15 19:31:43 ubuntu kernel: [14458.728884] CPU1: Package power limit normal
Mar 15 19:31:43 ubuntu kernel: [14458.728887] CPU3: Package power limit normal
Mar 15 19:31:43 ubuntu kernel: [14458.728890] CPU2: Package power limit normal
Mar 15 19:31:43 ubuntu kernel: [14458.728892] CPU0: Package power limit normal
Mar 15 19:32:12 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:32:12 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:32:12 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:32:13 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:32:13 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:32:13 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:32:13 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:32:13 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/cb0fd24491d043e0a4ad3d64593787eb
Mar 15 19:32:15 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:37:14 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:37:14 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:37:14 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:37:14 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:37:14 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:37:14 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:37:14 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:37:14 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/0c3608ff38a440d49950a43d1317536c
Mar 15 19:37:15 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:38:51 ubuntu kernel: [14885.655144] CPU1: Package power limit notification (total events = 106)
Mar 15 19:38:51 ubuntu kernel: [14885.655149] CPU3: Package power limit notification (total events = 106)
Mar 15 19:38:51 ubuntu kernel: [14885.655153] CPU2: Package power limit notification (total events = 106)
Mar 15 19:38:51 ubuntu kernel: [14885.655156] CPU0: Package power limit notification (total events = 106)
Mar 15 19:38:51 ubuntu kernel: [14885.666165] CPU1: Package power limit normal
Mar 15 19:38:51 ubuntu kernel: [14885.666169] CPU2: Package power limit normal
Mar 15 19:38:51 ubuntu kernel: [14885.666172] CPU3: Package power limit normal
Mar 15 19:38:51 ubuntu kernel: [14885.666174] CPU0: Package power limit normal
Mar 15 19:42:15 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:42:15 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:42:15 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:42:15 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:42:15 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:42:15 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:42:15 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:42:15 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/55d47ebfa9a145698595ee448abf54b9
Mar 15 19:42:16 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:45:34 ubuntu kernel: [15288.062309] CPU3: Package power limit notification (total events = 112)
Mar 15 19:45:34 ubuntu kernel: [15288.062313] CPU1: Package power limit notification (total events = 112)
Mar 15 19:45:34 ubuntu kernel: [15288.062317] CPU2: Package power limit notification (total events = 112)
Mar 15 19:45:34 ubuntu kernel: [15288.062320] CPU0: Package power limit notification (total events = 112)
Mar 15 19:45:34 ubuntu kernel: [15288.073293] CPU1: Package power limit normal
Mar 15 19:45:34 ubuntu kernel: [15288.073305] CPU0: Package power limit normal
Mar 15 19:45:34 ubuntu kernel: [15288.073314] CPU2: Package power limit normal
Mar 15 19:45:34 ubuntu kernel: [15288.073322] CPU3: Package power limit normal
Mar 15 19:47:16 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:47:16 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:47:16 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:47:16 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:47:16 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:47:16 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:47:16 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:47:16 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/773fbee65fad46638bb806a4385937c8
Mar 15 19:47:17 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:50:42 ubuntu kernel: [15596.174840] CPU2: Package power limit notification (total events = 122)
Mar 15 19:50:42 ubuntu kernel: [15596.174845] CPU1: Package power limit notification (total events = 122)
Mar 15 19:50:42 ubuntu kernel: [15596.174849] CPU3: Package power limit notification (total events = 122)
Mar 15 19:50:42 ubuntu kernel: [15596.174852] CPU0: Package power limit notification (total events = 122)
Mar 15 19:50:42 ubuntu kernel: [15596.185844] CPU2: Package power limit normal
Mar 15 19:50:42 ubuntu kernel: [15596.185847] CPU0: Package power limit normal
Mar 15 19:50:42 ubuntu kernel: [15596.185870] CPU1: Package power limit normal
Mar 15 19:50:42 ubuntu kernel: [15596.185873] CPU3: Package power limit normal
Mar 15 19:52:17 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:52:17 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:52:17 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:52:18 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:52:18 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:52:18 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:52:18 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:52:18 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/a62f36a60d064e62a2168d5f3cfd2a45
Mar 15 19:52:18 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 19:55:53 ubuntu kernel: [15905.764488] CPU2: Package power limit notification (total events = 130)
Mar 15 19:55:53 ubuntu kernel: [15905.764492] CPU1: Package power limit notification (total events = 130)
Mar 15 19:55:53 ubuntu kernel: [15905.764496] CPU3: Package power limit notification (total events = 130)
Mar 15 19:55:53 ubuntu kernel: [15905.764499] CPU0: Package power limit notification (total events = 130)
Mar 15 19:55:53 ubuntu kernel: [15905.775484] CPU1: Package power limit normal
Mar 15 19:55:53 ubuntu kernel: [15905.775488] CPU2: Package power limit normal
Mar 15 19:55:53 ubuntu kernel: [15905.775490] CPU3: Package power limit normal
Mar 15 19:55:53 ubuntu kernel: [15905.775493] CPU0: Package power limit normal
Mar 15 19:57:18 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 19:57:18 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 19:57:18 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 19:57:18 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 19:57:18 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 19:57:18 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 19:57:18 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 19:57:18 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/476d3069cc2347ba82a67b8072090428
Mar 15 19:57:19 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:01:40 ubuntu kernel: [16252.932505] CPU0: Package power limit notification (total events = 136)
Mar 15 20:01:40 ubuntu kernel: [16252.932509] CPU2: Package power limit notification (total events = 136)
Mar 15 20:01:40 ubuntu kernel: [16252.932513] CPU3: Package power limit notification (total events = 136)
Mar 15 20:01:40 ubuntu kernel: [16252.932516] CPU1: Package power limit notification (total events = 136)
Mar 15 20:01:40 ubuntu kernel: [16252.943514] CPU2: Package power limit normal
Mar 15 20:01:40 ubuntu kernel: [16252.943517] CPU0: Package power limit normal
Mar 15 20:01:40 ubuntu kernel: [16252.943539] CPU1: Package power limit normal
Mar 15 20:01:40 ubuntu kernel: [16252.943542] CPU3: Package power limit normal
Mar 15 20:02:19 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:02:19 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:02:19 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:02:19 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:02:19 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:02:19 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:02:19 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:02:19 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/8dd372fefa094fbe86d00cf742d06d46
Mar 15 20:02:20 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:04:31 ubuntu kernel: [16423.885186] usb 2-1.2: USB disconnect, device number 3
Mar 15 20:04:31 ubuntu kernel: [16423.942012] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
Mar 15 20:04:31 ubuntu kernel: [16423.942092] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Mar 15 20:04:34 ubuntu ntfs-3g[5285]: Unmounting /dev/sdb1 (Expansion Drive)
Mar 15 20:04:34 ubuntu ntfs-3g[5285]: Failed to sync device /dev/sdb1: Input/output error
Mar 15 20:04:34 ubuntu ntfs-3g[5285]: Failed to fsync device /dev/sdb1: Input/output error
Mar 15 20:04:34 ubuntu ntfs-3g[5285]: Failed to close volume /dev/sdb1: Device or resource busy
Mar 15 20:07:20 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:07:20 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:07:20 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:07:20 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:07:20 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:07:20 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:07:20 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:07:20 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/55b3531f6efc4efb9d551af4fcf428ae
Mar 15 20:07:21 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:08:20 ubuntu kernel: [16652.425380] CPU1: Package power limit notification (total events = 138)
Mar 15 20:08:20 ubuntu kernel: [16652.425385] CPU2: Package power limit notification (total events = 138)
Mar 15 20:08:20 ubuntu kernel: [16652.425388] CPU3: Package power limit notification (total events = 138)
Mar 15 20:08:20 ubuntu kernel: [16652.425391] CPU0: Package power limit notification (total events = 138)
Mar 15 20:08:20 ubuntu kernel: [16652.436373] CPU0: Package power limit normal
Mar 15 20:08:20 ubuntu kernel: [16652.436377] CPU1: Package power limit normal
Mar 15 20:08:20 ubuntu kernel: [16652.436380] CPU3: Package power limit normal
Mar 15 20:08:20 ubuntu kernel: [16652.436382] CPU2: Package power limit normal
Mar 15 20:13:20 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:13:20 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:13:20 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:13:20 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:13:20 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:13:20 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:13:20 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:13:20 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e5d236664a384991855dafca067bda31
Mar 15 20:13:21 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:14:39 ubuntu kernel: [17030.692687] CPU2: Package power limit notification (total events = 139)
Mar 15 20:14:39 ubuntu kernel: [17030.692691] CPU0: Package power limit notification (total events = 139)
Mar 15 20:14:39 ubuntu kernel: [17030.692718] CPU1: Package power limit notification (total events = 139)
Mar 15 20:14:39 ubuntu kernel: [17030.692721] CPU3: Package power limit notification (total events = 139)
Mar 15 20:14:39 ubuntu kernel: [17030.703685] CPU2: Package power limit normal
Mar 15 20:14:39 ubuntu kernel: [17030.703693] CPU0: Package power limit normal
Mar 15 20:14:39 ubuntu kernel: [17030.703723] CPU1: Package power limit normal
Mar 15 20:14:39 ubuntu kernel: [17030.703732] CPU3: Package power limit normal
Mar 15 20:17:04 ubuntu CRON[8151]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 15 20:19:20 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:19:20 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:19:20 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:19:20 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:19:20 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:19:20 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:19:20 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:19:20 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/4c016f08244542aa8d1899c77d0de550
Mar 15 20:19:21 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:24:21 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:24:21 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:24:21 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:24:21 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:24:21 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:24:21 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:24:21 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:24:21 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ad4a9ec426414d818a70d33de5af82fe
Mar 15 20:24:22 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:29:22 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:29:22 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:29:22 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:29:22 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:29:22 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:29:22 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:29:22 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:29:22 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/e1c9fb1965a24b5e9da859e6b0d2ce73
Mar 15 20:29:22 ubuntu kernel: [17912.492051] CPU3: Package power limit notification (total events = 140)
Mar 15 20:29:22 ubuntu kernel: [17912.492054] CPU1: Package power limit notification (total events = 140)
Mar 15 20:29:22 ubuntu kernel: [17912.492058] CPU0: Package power limit notification (total events = 140)
Mar 15 20:29:22 ubuntu kernel: [17912.492061] CPU2: Package power limit notification (total events = 140)
Mar 15 20:29:22 ubuntu kernel: [17912.503049] CPU2: Package power limit normal
Mar 15 20:29:22 ubuntu kernel: [17912.503053] CPU1: Package power limit normal
Mar 15 20:29:22 ubuntu kernel: [17912.503056] CPU3: Package power limit normal
Mar 15 20:29:22 ubuntu kernel: [17912.503058] CPU0: Package power limit normal
Mar 15 20:29:23 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:34:23 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:34:23 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:34:23 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:34:23 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:34:23 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:34:23 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:34:23 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:34:23 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/f272ec0dc99e4c2f9751a35255fb1769
Mar 15 20:34:24 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:36:33 ubuntu kernel: [18343.076484] keyboard: can't emulate rawmode for keycode 240
Mar 15 20:36:33 ubuntu kernel: [18343.076507] keyboard: can't emulate rawmode for keycode 240
Mar 15 20:36:33 ubuntu kernel: [18343.076518] asus_wmi: Unknown key 58 pressed
Mar 15 20:36:34 ubuntu anacron[8323]: Anacron 2.3 started on 2012-03-15
Mar 15 20:36:34 ubuntu anacron[8323]: Normal exit (0 jobs run)
Mar 15 20:36:35 ubuntu kernel: [18344.908365] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
Mar 15 20:38:24 ubuntu ntfs-3g[8379]: Version 2011.4.12AR.4 external FUSE 28
Mar 15 20:38:24 ubuntu ntfs-3g[8379]: Mounted /dev/sda5 (Read-Write, label "DATA", NTFS 3.1)
Mar 15 20:38:24 ubuntu ntfs-3g[8379]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177
Mar 15 20:38:24 ubuntu ntfs-3g[8379]: Mount options: rw,nosuid,nodev,uhelper=udisks,allow_other,nonempty,relatime,fsname=/dev/sda5,blkdev,blksize=4096,default_permissions
Mar 15 20:38:24 ubuntu ntfs-3g[8379]: Global ownership and permissions enforced, configuration type 7
Mar 15 20:39:24 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:39:24 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:39:24 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:39:24 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:39:24 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:39:24 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:39:24 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:39:24 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/b1cb352769c2477ca8456a7b00dd6c79
Mar 15 20:39:25 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:44:25 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:44:25 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:44:25 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:44:25 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:44:25 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:44:25 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:44:25 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:44:25 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/126d02731c6a4c3087671333e0bc5094
Mar 15 20:44:26 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:48:36 ubuntu kernel: [19064.104119] keyboard: can't emulate rawmode for keycode 240
Mar 15 20:48:36 ubuntu kernel: [19064.104126] keyboard: can't emulate rawmode for keycode 240
Mar 15 20:48:36 ubuntu kernel: [19064.104129] asus_wmi: Unknown key 57 pressed
Mar 15 20:48:36 ubuntu kernel: [19064.933147] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=600
Mar 15 20:49:21 ubuntu kernel: [19109.336357] CPU3: Package power limit notification (total events = 141)
Mar 15 20:49:21 ubuntu kernel: [19109.336361] CPU1: Package power limit notification (total events = 141)
Mar 15 20:49:21 ubuntu kernel: [19109.336365] CPU2: Package power limit notification (total events = 141)
Mar 15 20:49:21 ubuntu kernel: [19109.336369] CPU0: Package power limit notification (total events = 141)
Mar 15 20:49:21 ubuntu kernel: [19109.347331] CPU1: Package power limit normal
Mar 15 20:49:21 ubuntu kernel: [19109.347341] CPU3: Package power limit normal
Mar 15 20:49:21 ubuntu kernel: [19109.347351] CPU0: Package power limit normal
Mar 15 20:49:21 ubuntu kernel: [19109.347361] CPU2: Package power limit normal
Mar 15 20:50:25 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:50:25 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:50:25 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:50:25 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:50:25 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:50:25 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:50:25 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:50:25 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/c277137f09e84fe18a984522d7dabddf
Mar 15 20:50:26 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
Mar 15 20:55:26 ubuntu AptDaemon: INFO: Quitting due to inactivity
Mar 15 20:55:26 ubuntu AptDaemon: INFO: Quitting was requested
Mar 15 20:55:26 ubuntu dbus[958]: [system] Activating service name='org.debian.apt' (using servicehelper)
Mar 15 20:55:26 ubuntu AptDaemon: INFO: Initializing daemon
Mar 15 20:55:26 ubuntu dbus[958]: [system] Successfully activated service 'org.debian.apt'
Mar 15 20:55:26 ubuntu AptDaemon: INFO: UpgradeSystem() was called with safe mode: 1
Mar 15 20:55:26 ubuntu AptDaemon.Trans: INFO: Simulate was called
Mar 15 20:55:26 ubuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/baf129791056491b88d6b7ad6fe478cd
Mar 15 20:55:27 ubuntu AptDaemon.Worker: INFO: Upgrade system with safe mode: 1
```

---

### Post by kecsap on 2012-04-24
I have a similar problem, but not all the time. My laptop fails to resume in once out of ~10 attempts.

As much as I understood so far, the problem lies in the missing filesystem syncing (done by the system automatically) before suspend. If my laptop fails to suspend, I have exactly the same error what you have:

rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]

The following lines are missing from my syslog when the suspend/resume fails:

Apr 23 01:18:27 ..... kernel: [112267.138297] PM: Syncing filesystems ... done.
Apr 23 01:18:27 ..... kernel: [112267.458432] PM: Preparing system for mem sleep

The same lines are missing from your syslog as well. I don't know any solution yet, I investigate the situation.

---

### Post by kecsap on 2012-04-26
It seems that adding

acpi_sleep=s3_bios

to the kernel boot parameters in grub2 solves the problem for me.

---

### Post by kecsap on 2012-05-21
Eventually, the acpi_sleep=s3_bios did not work, however, the acpi_sleep=s4_nohwsig seems to work after more than a week without problems.

---

