---
title: "Two weeks and still not wifi 11.10"
date: 2011-10-27
forum: General Help
---

### Post by ernestj on 2011-10-27
After upgrading to 11.10, then doing clean install, I still do not have wifi on my ASUS U56. Can anyone help me????

Thanks,
Ernie

---

### Post by fdrake on 2011-10-28
post results of this commands:
```

ifconfig
iwconfig
rfkill list all
lshw

```

---

### Post by ernestj on 2011-10-28
ernest@ernest-U56E:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 14:da:e9:25:6c:d0  
          inet addr:24.125.19.99  Bcast:24.125.19.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:fe25:6cd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8554 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:9640233 (9.6 MB)  TX bytes:1273043 (1.2 MB)
          Interrupt:53 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48268 (48.2 KB)  TX bytes:48268 (48.2 KB)

wlan0     Link encap:Ethernet  HWaddr 40:25:c2:3f:46:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ernest@ernest-U56E:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on



0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wimax: WiMAX
	Soft blocked: yes
	Hard blocked: no

rfkill list all

 description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5887MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2301MHz
          capacity: 2301MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
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
             resources: irq:51 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
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
             resources: irq:52 memory:dfc00000-dfc03fff
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
                product: Centrino Wireless-N + WiMAX 6150
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 67
                serial: 40:25:c2:3f:46:d4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=41.28.5.1 build 33926 latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:50 memory:de800000-de801fff
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
                serial: 14:da:e9:25:6c:d0
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=24.125.19.99 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:53 memory:dd400000-dd43ffff ioport:a000(size=128)
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



Thanks,
Ernie

---

### Post by fdrake on 2011-10-28
can you try first this:
```

sudo rfkill unblock 2

```

---

### Post by ernestj on 2011-10-30
Still nothing. Going crazy, having to hard-wire or Windows 7. Anyone? This bug should have been identified already. Was surfin just fine in Natty.

Thanks, Ernie

---

### Post by garvinrick4 on 2011-10-30
Post 42 in this Thread:
Have to use 2.6.38 kernel for now. Install as stated and boot from it.

[http://ubuntuforums.org/showthread.php?t=1862484&page=5](http://ubuntuforums.org/showthread.php?t=1862484&page=5)

---

### Post by ernestj on 2011-10-30
OK, Great!
Worked for me. 

When the bug is fixed, will I just need to remove the files that were installed or leave them alone and log in 3.0? 
Did loose two finger scroll. :(
But, got my drag and drop back!!! :D

Thanks,
Ernie

---

### Post by garvinrick4 on 2011-10-31
> OK, Great!
Worked for me. 
When the bug is fixed, will I just need to remove the files that were installed or leave them alone and log in 3.0? When ever you want to remove the kernel just go into synapatics and type in search
window.
2.6.38 
and will show you the kernel image and headers just remove them. Glad you are running
enjoy you Ubuntu ernestj. Mark as Solved in Thread tools in upper right so others with same can benefit also.

---

### Post by nuevaburra on 2011-11-22
Hi, I am new and in the same boat. Tried installing old kernel and booting from that but got a big black page of errors and no boot ( "saned disabled; edit /etc/default/saned , starting anac(h)ronistic " etc etc and a bunch of numbers) . 

Tried a lot of other commands to get my WiMax to work- I know that on Windows 7 disabling N mode fixed it, but can't figure out how to do it on Ubuntu.

How do I get the old kernel to work with 11.10 so that my wireless will work? It's more or less just a big paperweight without wireless.

---

### Post by ernestj on 2011-11-23
I installed the old kernel and I have to boot into the older versions of Ubuntu to use it. I do not think anyone has gotten wiMax to work on Ubuntu. If they did, I am sure that it was not easy. Try to google wimax on Ubuntu. I still have had not other fix than the older kernel. I have been working with Ubuntu directly trying to fix the bug. My wimax never worked with Ubuntu by the way.

---

