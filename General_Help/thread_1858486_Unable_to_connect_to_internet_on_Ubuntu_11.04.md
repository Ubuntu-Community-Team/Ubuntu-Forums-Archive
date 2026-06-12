---
title: "Unable to connect to internet on Ubuntu 11.04"
date: 2011-10-12
forum: General Help
---

### Post by DrArroganto on 2011-10-12
[FONT=Arial]When I press the Network button on the top it says that firmware is missing.
Here's my device and drivers specs. (I have a HP 550 notebook)[/FONT]

                                                   [SIZE=1]atte@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:3a:f2:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:e4600000-e4620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

atte@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
atte@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub (rev 0c)
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at e4400000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, fast devsel, latency 0
    Memory at e4500000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d8
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e4600000 (32-bit, non-prefetchable) [size=128K]
    Memory at e4620000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4020 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 4040 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at e4621000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at e4624000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: e4000000-e40fffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=28, subordinate=28, sec-latency=0
    I/O behind bridge: 00002000-00003fff
    Memory behind bridge: e0000000-e3ffffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 4060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 4080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 40a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at e4628000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 40c0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 3618
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 13f0 [size=8]
    I/O ports at 15f4 [size=4]
    I/O ports at 1370 [size=8]
    I/O ports at 1574 [size=4]
    I/O ports at 4100 [SIZE=32]
    [SIZE=1]Memory at e4629000 (32-bit, non-prefetchable) [,size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at e4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
[/SIZE]
[/SIZE]

---

### Post by searchfgold6789 on 2011-10-12
Hrm... I *think* these drivers should be installed by default in linux. I would double-check the connection and the equipment. The drivers may be found [here]("http://downloadmirror.intel.com/9180/eng/e1000-8.0.30.tar.gz") if they are not installed.

---

