---
title: "Ubuntu 10.04 graphic card problem"
date: 2011-07-22
forum: General Help
---

### Post by Sephir0h on 2011-07-22
[FONT=Arial]Hi i installed today Ubuntu 10.04 but i have some troubles with my graphic card.
It seems that ubuntu doesn't recognise my Nvidia Geforce 8400 gs DD3.

In "driver hardware" no drivers are found. And my pc has froozen alreay two times [/FONT] [FONT=Arial]:(

Here are the results of the command:[/FONT] [FONT=Arial]

lspci -vnn[/FONT] 

#00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d3]
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 4 Series Chipset PCI Express Root Port [8086:2e21] (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fd000000-fe9fffff
    Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device [1043:82d3]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at b800 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at b880 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at bc00 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fcfffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] Vendor Specific Information <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82fe]
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fcff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0000000-c03fffff
    Prefetchable memory behind bridge: 00000000fbf00000-00000000fbffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b080 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b400 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at b480 [size=32]
    Capabilities: [50] Vendor Specific Information <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a] (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fcfff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] Vendor Specific Information <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIB (ICH10) LPC Interface Controller [8086:3a18]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4  port SATA IDE Controller #1 [8086:3a20] (prog-if 8f [Master SecP SecO  PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at a000 [size=8]
    I/O ports at 9c00 [size=4]
    I/O ports at 9880 [size=8]
    I/O ports at 9800 [size=4]
    I/O ports at 9480 [size=16]
    I/O ports at 9400 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information <?>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: medium devsel, IRQ 15
    Memory at fcfff400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2  port SATA IDE Controller #2 [8086:3a26] (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:82d4]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at b000 [size=8]
    I/O ports at ac00 [size=4]
    I/O ports at a880 [size=8]
    I/O ports at a800 [size=4]
    I/O ports at a480 [size=16]
    I/O ports at a400 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information <?>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:10c3] (rev a2)
    Subsystem: Device [1acc:8521]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    Expansion ROM at fe900000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Subsystem: Device [1acc:8521]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe9fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101  single-port PATA133 interface [11ab:6101] (rev b2) (prog-if 8f [Master  SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device [1043:82e0]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Memory at feaffc00 (32-bit, non-prefetchable) [size=512]
    Capabilities: [48] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel driver in use: pata_marvell
    Kernel modules: pata_marvell

04:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at e800 [size=256]
    Memory at febffc00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp#

---

### Post by pqwoerituytrueiwoq on 2011-07-22
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get install nvidia-current
```you may need to add *nomodeset* to your kernel's boot line

---

### Post by Sephir0h on 2011-07-22
Ok in this way i was able to install the nvidia drivers. 
Anyway i have a question in the line:

[FONT=Georgia]01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:10c3] (rev a2)
    Subsystem: Device [1acc:8521]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fe900000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouvea[/FONT]

Why it doesn't specify that my card is an Geforce 8400?
Is it using my graphic card?

---

### Post by Sephir0h on 2011-07-22
VGA compatible controller        : nVidia Corporation Device 10c3 (rev a2) 
 
I assume that this is the onboard Nvidia graphics. But why it isn't using my graphic card :confused:

---

### Post by pqwoerituytrueiwoq on 2011-07-22
my GeForce GT 430 does the same thing you can view the model with this command
```
glxinfo | grep OpenGL
```if it is using the onboard one you need to plug the monitor cable into the actual gpu card

---

### Post by Sephir0h on 2011-07-22
Ok with that command i see:

> OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400GS/PCI/SSE2
OpenGL version string: 3.3.0 NVIDIA 275.19
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler

So it is working, right?

---

### Post by pqwoerituytrueiwoq on 2011-07-22
looks like it
NVIDIA 275.19 driver is running GeForce 8400GS/PCI/SSE2
you have OpenGL 3.3 if you are curious

---

### Post by Sephir0h on 2011-07-22
Ok then, you are my hero :D
Thank you!

---

