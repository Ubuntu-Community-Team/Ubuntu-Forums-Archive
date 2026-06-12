---
title: "Attempting to change Default Audio Output"
date: 2009-10-31
forum: General Help
---

### Post by giggaflop on 2009-10-31
currently i have just upgraded to 9.10 and have discovered that my sound no longer works.
after much playing and tweaking i have discovered that oss and alsa outputs both work with my sound card, the only one that doesn't in fact is pulse (as it seems for most people too :P) so i am looking for a way to get my entire system to move over to either of the two audio output systems. preferably with as little system hacking as possible. 
Details are kept below:

josh@josh-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


josh@josh-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0
    Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f0904800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0500000-f05fffff
    Prefetchable memory behind bridge: 00000000f0a00000-00000000f0afffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: f0600000-f06fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0904c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
    I/O ports at 1818 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1810 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 18e0 [size=32]
    Memory at f0904000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: medium devsel, IRQ 10
    Memory at be000000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0, IRQ 31
    I/O ports at 4000 [size=256]
    Memory at f0500000 (64-bit, non-prefetchable) [size=4K]
    Memory at f0a00000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0a20000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

09:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0600000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: fast devsel, IRQ 16
    Memory at f0600400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

09:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: CLEVO/KAPOK Computer Device 0805
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0600800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

---

### Post by Sin@Sin-Sacrifice on 2009-10-31
Google brought this up [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) so when you click on it you see a huge post about pulseaudio. Just hit ctrl+f and search the word disable in the page and it will bring you to where it explains how to disable it. Happy linuxing.

---

### Post by TheCheeze on 2009-11-01
I think I found the answer

[http://ubuntuforums.org/showthread.php?p=8217190#post8217190](http://ubuntuforums.org/showthread.php?p=8217190#post8217190)

---

