---
title: "PCI serial card installation"
date: 2012-01-04
forum: General Help
---

### Post by razing32 on 2012-01-04
Hi,

I;m having some issue with a PCI card I bought with serial adapters.
It is produced by Delock , but they did not have any info on how to install on Linux.
The manual pointed me to moschip website but that didn't help either.
I barely found a solution at ASIX website but problem is I don't quite understand it.

Here is the link :
[http://www.asix.com.tw/FrootAttach/driver/MCS98xx_Linux_Default_Driver_Installation_Guide.pdf](http://www.asix.com.tw/FrootAttach/driver/MCS98xx_Linux_Default_Driver_Installation_Guide.pdf)

I'm a beginner in using Linux so I don't quite understand how to choose ports , IRQ channels etc.

If anyone can make heads or tails of the guide (first part -serial) please let me know.

Also , the chip model is 9845 , if it helps.

---

### Post by xc3RnbFO8P on 2012-01-04
As it says:

Step 1

open Terninal window and write:
> lspci -v
(and press ENTER)

can you post output of that?

---

### Post by razing32 on 2012-01-05
> **Ringi said:**
> As it says:

Step 1

open Terninal window and write:

(and press ENTER)

can you post output of that?

Sure , here you go :

alin@alin-mambo:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, 66MHz, medium devsel, latency 32
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdffffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: Giga-byte Technology GA-MA770-DS3rev2.0 Motherboard
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Gigabyte GA-MA69G-S3H Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series] (prog-if 00 [VGA controller])
    Subsystem: Giga-byte Technology Device d001
    Flags: bus master, fast devsel, latency 32, IRQ 18
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at ee00 [size=256]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Subsystem: Giga-byte Technology Device 7919
    Flags: bus master, fast devsel, latency 32, IRQ 19
    Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:06.0 Serial controller: NetMos Technology PCI 9845 Multi-I/O Controller (rev 01) (prog-if 02 [16550])
    Subsystem: LSI Logic / Symbios Logic 0P6S (6 port 16550a serial card)
    Flags: medium devsel, IRQ 20
    I/O ports at df00 [size=8]
    I/O ports at de00 [size=8]
    I/O ports at dd00 [size=8]
    I/O ports at dc00 [size=8]
    I/O ports at db00 [size=8]
    I/O ports at da00 [size=16]
    Kernel driver in use: serial
    Kernel modules: parport_serial

02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
    Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
    Subsystem: Giga-byte Technology GA-MA69G-S3H Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
    I/O ports at d800 [size=256]
    Memory at fddfe000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

alin@alin-mambo:~$

---

### Post by imachavel on 2012-01-05
that is better then mine, which says:

lspci-v
lspci-v: command not found
sudo lspci-v
[sudo] password for *****: 
sudo: lspci-v: command not found

I've never heard of needing to program an irq with linux, it's possible though. My guess is what you want is a restricted driver option. You should list two things please

exact model and version of expansion card you are trying to install on mobo. exact name and model of mobo that you are trying to install this on. Also the manufacturer the card you are trying to install in an expansion slot. Now, if we can figure that out, I'll direct you to the web site of the manufacturer of your product, there you should download newest driver. Then there is something called 'restricted drivers' that you should look into. If you know all this, then it's a bit redundant.

I'm not sure why else it wouldn't work, but it would help to have some information about hardware specifications, also, what type of hard disk drive, is it sata? ide? how many rpms? scratch that last question, just answer the first few questions please! thanks

---

### Post by imachavel on 2012-01-05
> **razing32 said:**
> Sure , here you go :

alin@alin-mambo:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
    Subsystem: Giga-byte Technology Device 5000
    Flags: bus master, 66MHz, medium devsel, latency 32
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fde00000-fdffffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
    Subsystem: Giga-byte Technology Device b002
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
    I/O ports at ff00 [size=8]
    I/O ports at fe00 [size=4]
    I/O ports at fd00 [size=8]
    I/O ports at fc00 [size=4]
    I/O ports at fb00 [size=16]
    Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
    Subsystem: Giga-byte Technology Device 5004
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
    Subsystem: Giga-byte Technology GA-MA770-DS3rev2.0 Motherboard
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: Giga-byte Technology Gigabyte GA-MA69G-S3H Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f900 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: Giga-byte Technology Device 5001
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series] (prog-if 00 [VGA controller])
    Subsystem: Giga-byte Technology Device d001
    Flags: bus master, fast devsel, latency 32, IRQ 18
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at ee00 [size=256]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
    Subsystem: Giga-byte Technology Device 7919
    Flags: bus master, fast devsel, latency 32, IRQ 19
    Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:06.0 Serial controller: NetMos Technology PCI 9845 Multi-I/O Controller (rev 01) (prog-if 02 [16550])
    Subsystem: LSI Logic / Symbios Logic 0P6S (6 port 16550a serial card)
    Flags: medium devsel, IRQ 20
    I/O ports at df00 [size=8]
    I/O ports at de00 [size=8]
    I/O ports at dd00 [size=8]
    I/O ports at dc00 [size=8]
    I/O ports at db00 [size=8]
    I/O ports at da00 [size=16]
    Kernel driver in use: serial
    Kernel modules: parport_serial

02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
    Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
    Subsystem: Giga-byte Technology GA-MA69G-S3H Motherboard
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
    I/O ports at d800 [size=256]
    Memory at fddfe000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

alin@alin-mambo:~$

wow what a read out. Can't tell what is onboard and what is already installed. Did you install a gigabit network interface adapter? One question, did you install this in a network connected to another pc with a gigabit network interface adapter routed through a router that can do max 1000 mbps? if not, and you are just using the card for standard connection improvement over your dsl line, then it might not be the right choice. If it's onboard already, I apologize. Sorry I'm not familiar with huge long read outs from the linux terminal line. That thing read out every chip on your mainboard, which is good. Which of those devices did you currently install?? thanks :popcorn:

---

### Post by Frogs Hair on 2012-01-05
razing32 , My NetMos I/O card had a driver included with the kernel and I see the card listed in the output . The card may be packaged Deadlock and made by NetMos . That is why the pdf has a different name .

I think this is the card. ```
02:06.0 Serial controller: NetMos Technology PCI 9845 Multi-I/O Controller (rev 01) (prog-if 02 [16550])
 Subsystem: LSI Logic / Symbios Logic 0P6S (6 port 16550a serial card)
 Flags: medium devsel, IRQ 20
 I/O ports at df00 [size=8]
 I/O ports at de00 [size=8]
 I/O ports at dd00 [size=8]
 I/O ports at dc00 [size=8]
 I/O ports at db00 [size=8]
 I/O ports at da00 [size=16]
 Kernel driver in use: serial
 Kernel modules: parport_serial
``` 

Add the device to see if it works . I think you're good to go .

---

### Post by Frogs Hair on 2012-01-05
imachavel ,

I think you are missing a space between i and - in the command , try the following .```
lspci -v
```

---

### Post by razing32 on 2012-01-05
> **Frogs Hair said:**
> razing32 , My NetMos I/O card had a driver included with the kernel and I see the card listed in the output . The card may be packaged Deadlock and made by NetMos . That is why the pdf has a different name .Add the device to see if it works . I think you're good to go .

Yes , you were right , drivers were already in the kernel.
I feel like an idiot now.:(

Just had to setup minicom and everything is fine.
Thanks.

---

### Post by imachavel on 2012-01-05
> **Frogs Hair said:**
> imachavel ,

I think you are missing a space between i and - in the command , try the following .```
lspci -v
```

here we are:

lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
    Subsystem: Dell Device 0181
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dfd00000-dfefffff
    Prefetchable memory behind bridge: c0000000-cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dfc00000-dfcfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: dfb00000-dfbfffff
    Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ec00 [size=256]
    I/O ports at e8c0 [size=64]
    Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
    Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 0181
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fea0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: medium devsel, IRQ 5
    I/O ports at e8a0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2009
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dfdf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at dc00 [size=256]
    Expansion ROM at dfe00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
    Subsystem: Hightech Information System Ltd. Device aa38
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at dfdec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04) (prog-if 00 [Generic])
    Subsystem: Dell Device 1000
    Flags: bus master, stepping, medium devsel, latency 64, IRQ 17
    Memory at dfbfe000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at cc00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
    Subsystem: Dell Device 0181
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at dfbff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at c8c0 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100



wow that's painful. My drivers work. A lot of games don't, but I figured that is more of a codec, or directx video signal code format problem then a driver problem. My gpu added in should be listed there:

VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]

oh well. it's linux

---

### Post by Frogs Hair on 2012-01-05
No problem , if you were looking for Deadlock you wouldn't have found it . I have a similar card , so when I opened the pdf I just looked for NetMos . ;)

---

