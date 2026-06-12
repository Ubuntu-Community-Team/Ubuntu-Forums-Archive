---
title: "no sound on ubuntu 9.10 creative x-fi"
date: 2009-10-04
forum: General Help
---

### Post by mvl30 on 2009-10-04
hello everybody I download ubuntu 9.10 (Karmic Koala) but  my soud card does not make any sound (creative labs x-fi pci-e ) can you guys help me i do not have much experince on this this is my

 lspci-v


00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [94] HyperTransport: #1a
    Capabilities: [60] HyperTransport: Retry Mode
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [d0] HyperTransport: #1c

00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 2900 [size=64]
    I/O ports at 2d00 [size=64]
    I/O ports at 2e00 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at fde80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fde7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fde7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fde7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fde7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: 66MHz, fast devsel, IRQ 21
    Memory at fde78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fdf00000-fdffffff
    Capabilities: [b8] Subsystem: Micro-Star International Co., Ltd. Device 7375
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. Device 7375
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
    I/O ports at a080 [size=8]
    I/O ports at a000 [size=4]
    I/O ports at 9c00 [size=8]
    I/O ports at 9880 [size=4]
    I/O ports at 9800 [size=16]
    Memory at fde76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Capabilities: [8c] SATA HBA <?>
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
    Capabilities: [ec] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
    Subsystem: Micro-Star International Co., Ltd. Device 375c
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 30
    Memory at fde7c000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 9480 [size=8]
    Memory at fde7e400 (32-bit, non-prefetchable) [size=256]
    Memory at fde7e000 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/4 Enable+
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7375
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot-), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Prefetchable memory behind bridge: 00000000fcf00000-00000000fcffffff
    Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7375
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7375
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=09, sec-latency=0
    Memory behind bridge: feb00000-febfffff
    Capabilities: [40] Subsystem: Micro-Star International Co., Ltd. Device 7375
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) (prog-if 10)
    Subsystem: Micro-Star International Co., Ltd. Device 375d
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fdfff800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at bc00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=02, secondary=03, subordinate=05, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [40] Power Management version 3
    Capabilities: [60] Express Upstream Port, MSI 00
    Capabilities: [a0] Subsystem: nVidia Corporation Device cb19
    Kernel modules: shpchp

03:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=03, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [40] Power Management version 3
    Capabilities: [60] Express Downstream Port (Slot+), MSI 00
    Kernel modules: shpchp

03:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=03, secondary=05, subordinate=05, sec-latency=0
    Capabilities: [40] Power Management version 3
    Capabilities: [60] Express Downstream Port (Slot+), MSI 00
    Kernel modules: shpchp

04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
    Subsystem: XFX Pine Group Inc. Device 2445
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe8f0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at c000 [size=256]
    Expansion ROM at fe8c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
    Subsystem: XFX Pine Group Inc. Device aa30
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8ec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 375c
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at d800 [size=256]
    Memory at fe9ff000 (64-bit, non-prefetchable) [size=4K]
    Memory at fcff0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
    Capabilities: [d0] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 03-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

07:00.0 SATA controller: JMicron Technology Corp. 20360/20363 Serial ATA Controller (rev 03) (prog-if 01)
    Subsystem: JMicron Technology Corp. 20360/20363 Serial ATA Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at feafe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: ahci

07:00.1 IDE interface: JMicron Technology Corp. 20360/20363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: JMicron Technology Corp. 20360/20363 Serial ATA Controller
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    Capabilities: [68] Power Management version 2
    Kernel driver in use: pata_jmicron

08:00.0 PCI bridge: Creative Labs Device 7006
    Flags: bus master, fast devsel, latency 0
    Bus: primary=08, secondary=09, subordinate=09, sec-latency=64
    Memory behind bridge: feb00000-febfffff
    Capabilities: [50] Power Management version 3
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/4 Enable-
    Capabilities: [80] Subsystem: Creative Labs Device 0010
    Capabilities: [90] Express PCI/PCI-X Bridge, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel modules: shpchp

09:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0018
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [dc] Power Management version 3
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

can you tell me what is wrong?  looks like is using the wrong drivers for my sound card
any help would be aprecciated :confused:

---

### Post by twipley on 2009-10-10
Haven't installed v9.04 specifically because of that issue; seems like it hasn't yet been fixed.

P.S.: that issue included the lack of that *quite needed *creative audio console.

---

### Post by TheCarl on 2009-10-27
I got 9.04 and SB X-Fi and it works fine with creative's linux drivers.
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

---

### Post by P4man on 2009-10-27
The OP has 2 soundcards. If he is still reading this: try blacklisting the snd-hda-intel onboard sound.

---

### Post by twipley on 2009-10-29
Are those drivers by default included in Ubuntu? And if not, why not? But if yes, then *hurray *from here!

Furthermore, can you guys confirm access to the Creative Audio Console (a.k.a. the Audio Control Panel)?

---

### Post by halfsane on 2009-10-29
I thought that the X-fi drivers were included in Karmic also.

Can anyone confirm X-fi cards work out of the box for them?

---

### Post by fcuk112 on 2009-10-29
i have a creative x-fi fatal1ity pro, it works out of the box.  i have set it to analog stereo output as i am using 2.1 speaker setup.  plug the cable into the second hole from the top on the card.

use alsamixer in terminal to set volumes.
you can also use pulseaudio volume control (more flexible).

HTH.

---

### Post by twipley on 2009-10-29
> **fcuk112 said:**
> i have a creative x-fi fatal1ity pro, it works out of the box.
Yeah, but do you have access to the Audio Console like one has under Windows?

[http://www.codinghorror.com/blog/images/creative-audio-console.png](http://www.codinghorror.com/blog/images/creative-audio-console.png)
[http://aphnetworks.com/review/auzentech_x_fi_prelude/ss0.png](http://aphnetworks.com/review/auzentech_x_fi_prelude/ss0.png)
[http://img339.imageshack.us/img339/6541/xfivolumenw1.gif](http://img339.imageshack.us/img339/6541/xfivolumenw1.gif)

---

### Post by whoop on 2009-11-03
It works out of the box for me although surround sounds sounds very pitchy. I only get good sound with analog stereo...

---

### Post by Zoot7 on 2009-11-03
You might want to upgrade to Alsa 1.0.21 which has the stable X-Fi driver contained within.
I have it installed under Hardy and had it installed under Jaunty, and the sound was perfect in both cases.
There's a great upgrade script posted here:
[http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810")

---

### Post by twipley on 2009-11-21
yeah but there is no mention of the console yet which makes me believe that this quite important piece of control software (i.e. permitting you to switch from the default game mode to the entertainment mode) is absent.

---

### Post by twipley on 2010-04-30
Hello. Sorry for the bump, everyone.

Is there any update on console capabilities on 10.04?

---

