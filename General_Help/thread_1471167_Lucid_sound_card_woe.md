---
title: "Lucid sound card woe"
date: 2010-05-03
forum: General Help
---

### Post by mental_122 on 2010-05-03
Hi, probably heavily talked about but I can't for the life (and patience) in me get my SB audigy to show up/work/make sound!?

I've exhausted google looking for help and run every guide I can find.

I've used alot of ubuntu bulds and never had a problem until now with Lucid :cry:


It knows I have a creative card in there but it's just not using it or ignoring it.
```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
    Flags: bus master, medium devsel, latency 0
    Kernel modules: via-agp

00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 8199
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f9f00000-fbffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
    Subsystem: Creative Labs Device 0051
    Flags: medium devsel, IRQ 17
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel modules: snd-emu10k1

00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
    Subsystem: Creative Labs Device 0040
    Flags: bus master, medium devsel, latency 64
    I/O ports at d880 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10)
    Subsystem: Creative Labs Device 0010
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f9eff800 (32-bit, non-prefetchable) [size=2K]
    Memory at f9ef8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:0d.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80ee
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
    Memory at f9ec0000 (32-bit, non-prefetchable) [size=128K]
    I/O ports at d800 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e1000
    Kernel modules: e1000

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device 80e9
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at d480 [size=8]
    I/O ports at d400 [size=4]
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=16]
    I/O ports at c800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80e9
    Flags: bus master, medium devsel, latency 32, IRQ 255
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at c480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at c400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at c080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at c000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f9eff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
    Subsystem: nVidia Corporation Device 033d
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at f9fe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nvidiafb, nouveau

```

I've disabled the onboard chip too. All works fine on my xp dual boot, I'm at a loss here

HALP!!

---

### Post by kostkon on 2010-05-03
What Ubutnu version and what's your problem exactly.

Also, please paste the output of the
```
aplay -l
```
command here.

---

### Post by Elfy on 2010-05-03
A possibility is that it is using the digital rather than analog - I found that with mine anyway.

Open a terminal and run alsamixer 

go across the channels to the Audigy Analog/Digital Output Jack - it should have MM underneath it - if not use m to toggle it.

Hope it is as simple as that.

---

### Post by mental_122 on 2010-05-03
> **kostkon said:**
> What Ubutnu version and what's your problem exactly.

Also, please paste the output of the
```
aplay -l
```command here.

can't get any sound at all, using lucid lynx 10.4

```
aplay: device_list:223: no soundcards found...
izz@ubuntu:~$ 

```


@forestpiskie - whenever i try that command it says bad file/directory etc?? ive tried re-installing alsa too :(

---

