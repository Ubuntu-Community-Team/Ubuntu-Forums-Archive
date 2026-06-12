---
title: "Sound does not come out of headphones, no digital output"
date: 2010-09-29
forum: General Help
---

### Post by flamefury on 2010-09-29
The thread title.

Sound comes out of my laptop speakers, but only when hardware is selected as "Analog Stereo". "Digital Stereo" does not function at all. I don't think this is a priority though.

More importantly, my headphones do not have sound unless it is only partway plugged into the headphone jack. However, this does not help as sound is still coming out of my speakers. The instant I plug it all the way in, the sound disappears from both speakers and headphones. I have not tested this with multiple headphones (no access), but these ones work just fine in Windows 7 plugged in all the way.

I have tried an amazing number of things back in '09 when I was running 9.10, but gave up as no one could provide the answer. The threads that are related are:
[http://ubuntuforums.org/showthread.php?t=1273802](http://ubuntuforums.org/showthread.php?t=1273802) (Don't worry about read-only file stuff, that is all resolved)
[http://ubuntuforums.org/showthread.php?t=1286489](http://ubuntuforums.org/showthread.php?t=1286489)

I am now on a FRESH install of 10.04 Lucid Lynx, so any changes I made in attempt to fix it is gone.

Looking into alsamixer, I found that there is a headphones column, but no bar. It just says it's on. So headphones don't seem to have their own level of volume that's set too low.

Here are some outputs:
**lcat /proc/asound/card0/codec#* | grep Codec**:
```
Codec: Realtek ALC663
Codec: Nvidia MCP78 HDMI
```**aplay -l**:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```**lspci -v**:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fa000000-fdefffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 19a7
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at bc00 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at b880 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b800 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a3
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 19a7
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fdf00000-fdffffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 19a7
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe000000-fe9fffff
    Prefetchable memory behind bridge: 00000000f6000000-00000000f8efffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 19a7
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 19a7
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b480 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b400 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at b080 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    Memory behind bridge: feb00000-febfffff
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 19a7

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 30
    I/O ports at b000 [size=8]
    I/O ports at ac00 [size=4]
    I/O ports at a880 [size=8]
    I/O ports at a800 [size=4]
    I/O ports at a480 [size=32]
    Memory at f9fff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA <?>
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ahci
    Kernel modules: ahci

01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GS] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 1992
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fd000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information <?>
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidiafb, nouveau

03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1201
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at fdffe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number 04-17-c2-ff-ff-5d-21-00
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 16d5
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at e800 [size=256]
    Memory at f8fff000 (64-bit, prefetchable) [size=4K]
    Memory at f8fe0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at feaf0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [d0] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number ff-ff-ff-ff-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at febff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

07:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at febff000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

07:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device 19a7
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at febfec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
```I would greatly appreciate any insight that can be given on the matter.

EDIT: Here's my ALSA information, if you want to take a look at it.
[http://www.alsa-project.org/db/?f=05ddb3af3545efce06f4ef187af5011a1401f952](http://www.alsa-project.org/db/?f=05ddb3af3545efce06f4ef187af5011a1401f952)

---

### Post by flamefury on 2010-09-29
After one year of toiling at this, I managed to find the answer online.
[http://forums.opensuse.org/english/get-help-here/hardware/410618-only-getting-sound-headphones-when-inserted-halfway.html](http://forums.opensuse.org/english/get-help-here/hardware/410618-only-getting-sound-headphones-when-inserted-halfway.html)

For those that don't want to read all the way through, you'll need to add some settings to alsa-base.conf
Open up terminal and type:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

Then add these lines to alsa-base.conf:
```
# Headphone fix                       
options snd-hda-intel model=m51va position_fix=0
options snd slots=snd-hda-intel
# u1Nb.Xk_oFFgpZED:82801I (ICH9 Family) HD Audio Controller
alias snd-card-0 snd-hda-intel
```This not only gets sound coming out after the headphones are fully plugged in, it properly mutes the laptop speakers as well.

Make sure most of your sound card settings match mine before trying this.

---

