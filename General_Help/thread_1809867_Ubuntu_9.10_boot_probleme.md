---
title: "Ubuntu 9.10 boot probleme"
date: 2011-07-22
forum: General Help
---

### Post by Sephir0h on 2011-07-22
Hi i'm using ubuntu 9.10 and i have a Geforce 8400 gs. Yesterday i installed nvidia drivers 195. Now my boot loks like that:

[IMG]http://img36.imageshack.us/img36/3143/ubuntu910karmickoala1.jpg[/IMG]

How can i change it?
Are the drivers wrong for my video card?
If yes which should i use?

---

### Post by westie457 on 2011-07-22
Hello and welcome to the forums.

You might not be aware that 9.10 has reached end of life and is no longer supported for security and other updates. Your best option now is to download 10.04 LTS - which has very nearly all the bugs ironed out - and try the LiveCD to check what works. Then do clean install.

If you need help with this just ask anytime. These forums are 24/7 and there is always someone to help.

---

### Post by Sephir0h on 2011-07-22
Ok i upgraded to 10.04! :)
Now the resolution is fine even without the video card drivers...
But i think i need the nvidia drivers...right?
Anyway i don't know which are the correct ones for my card: Geforce 8400 gs DD3.

---

### Post by westie457 on 2011-07-22
> **Sephir0h said:**
> Ok i upgraded to 10.04! :)
Now the resolution is fine even without the video card drivers...
But i think i need the nvidia drivers...right?
Anyway i don't know which are the correct ones for my card: Geforce 8400 gs DD3.

open a terminal and run ```
lspci -vnn
```
Copy the output and in a new reply click # and paste between the ```
 
``` brackets.
This will identify the graphics card and ultimately the correct driver if you need to install it/them.

---

### Post by Sephir0h on 2011-07-22
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

00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20] (prog-if 8f [Master SecP SecO PriP PriO])
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

00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26] (prog-if 85 [Master SecO PriO])
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

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface [11ab:6101] (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
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

### Post by Quackers on 2011-07-22
I believe nvidia-current (recommended) should appear in the Hardware Drivers window. This is the correct driver for your card.

---

### Post by Sephir0h on 2011-07-22
I tried that one, but it says there are no drivers...

---

### Post by Quackers on 2011-07-22
In Hardware Drivers?

---

### Post by Sephir0h on 2011-07-22
Yes. It says "**No proprietary drivers are in use on this system"**.

---

### Post by Quackers on 2011-07-22
That's odd.
I notice from the output of lspci that you posted this line regarding your graphics card ```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:10c3] (rev a2)
Subsystem: Device [1acc:8521]
``` No graphics card name or details are given.
For comparison, here is my own line from lspci ```
01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600M GT] [10de:0407] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Device [104d:9016]

```
I am aware that there was a problem some time ago with the Nvidia 8400 GS and the Natty kernel. I do not know whether that problem was solved or not.

If you are having no video problems at the moment it may be prudent to ignore the Nvidia driver for the moment, or at least find out if that problem was solved. Google maybe.

---

### Post by Sephir0h on 2011-07-22
I googled for a while and found nothing relevant. I'm new in ubuntu and i don't know what to do right now. I read that my video card could work with nvidia 173 drivers, but i don't know what that means :(

---

### Post by Quackers on 2011-07-22
Do you have integrated graphics on your motherboard, as well as the Nvidia card?

---

### Post by Quackers on 2011-07-22
I'm not sure whether your Nvidia card is being properly recognised by Ubuntu. This might explain why no video drivers are available to you.
Sadly I have no idea what to do about that, if it is the case :-(

---

### Post by Sephir0h on 2011-07-22
:(

None can help?
Should i reput windows again?

---

### Post by Quackers on 2011-07-22
As Ubuntu 9.10 is now no longer supported you may be better off installing a later version. 10.04 is a Long Term Support release that you may have better luck with :-)
You could backup whatever data you have in your current installation and install it to the new installation.
Alternatively you could wait for further input regarding your current problems.

---

### Post by Sephir0h on 2011-07-22
I'm already using 10.04 and have the same problem as on 9.10.
I'm sure the problem is, as you said, that ubuntu isn't recognising my video card.
And that is a big problem...

---

### Post by Quackers on 2011-07-22
???
Given the thread title and this being the first line of your first post

"Hi i'm using ubuntu 9.10 and i have a Geforce 8400 gs"

I think I can be forgiven for thinking you were on 9.10 :-)

If I were you I would wait for further input - hopefully :-)

---

### Post by Sephir0h on 2011-07-22
My second post was:

>                                                    Ok i upgraded to 10.04! :)
Now the resolution is fine even without the video card drivers...
But i think i need the nvidia drivers...right?
Anyway i don't know which are the correct ones for my card: Geforce 8400 gs DD3.
Ok i will wait. I hope i can fix that cause i really like ubuntu and don't want to go back to windows xp :(

---

### Post by Quackers on 2011-07-22
Ah, my mistake :-)
Many people run Ubuntu without the proprietary drivers. The default nouveau driver is really quite good now.

---

### Post by Sephir0h on 2011-07-22
So i don't need the drivers? :confused:

PS: should i open a new topic since the title is wrong?

---

### Post by Quackers on 2011-07-22
Sorry for the delay.
No, many people don't use the proprietary drivers at all.
A new topic with a different title may be better for getting advice.

This may give more information.
During booting at the grub menu (and if you don't see a grub menu tap the shift key or the Esc key during boot) and when your normal Ubuntu entry is highlighted, press the "e" key.
On the new screen using the arrow keys navigate to the end of the line which currently ends with "quiet splash".
Using the backspace key, delete the words quiet splash then press ctrl + x to boot.
Lots of text lines will scroll past. When booting stops, the text may display information in the lasy couple of lines to explain why it has stopped booting.
Please copy that and put it into your next post (or in the new thread).

---

