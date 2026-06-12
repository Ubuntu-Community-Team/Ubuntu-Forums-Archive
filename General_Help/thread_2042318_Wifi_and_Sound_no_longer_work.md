---
title: "Wifi and Sound no longer work"
date: 2012-08-14
forum: General Help
---

### Post by jmoney47 on 2012-08-14
Hello guys, 

I am running Ubuntu 12.04 dual-booted with Windows 7 on my 64-bit laptop.  Recently, I booted into Ubuntu, but I could no longer connect to the internet wirelessly.  I have an ethernet port, but it is a Killer Gaming Network special port thing and the manufacturer has no drivers for linux.  The computer has been able to connect wirelessly in the past and was doing so consitently and on different networks.  Also, the same time that I lost wireless abilities, sound and the touchpad stopped working.  Any idea what could have happened?  I was thinking an update gone wrong so I ran update-manager and it said I needed to do a partial upgrade?  I am running it now, but I am not sure what will happen.  Anyone have any ideas what could have went on?

---

### Post by Vakman on 2012-08-14
For your killer network card, I believe this is the one you are referring to: [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332)
That should help with getting that working.

Now, what are you using for wireless, this is a desktop, so is it another card or USB device, either way, what is it?

---

### Post by jmoney47 on 2012-08-14
This is not a desktop, it is a laptop.  This one to be specific [http://bit.ly/K9d77s](http://bit.ly/K9d77s)  
It has a built-in wireless card

---

### Post by Vakman on 2012-08-15
> **jmoney47 said:**
> This is not a desktop, it is a laptop.  This one to be specific [http://bit.ly/K9d77s](http://bit.ly/K9d77s)  
It has a built-in wireless card

Ah, sorry, I read that network card and had assumed.

Please post the output of:
```
lspci -v
```
Or if you know what the wireless card is already just let us know what it is.

---

### Post by jmoney47 on 2012-08-15
Alright so after I did that update thing, everything started working again, which was kinda strange because I only finished the part where it said "preparing" and I had to take away my phone from which I was tethering 3g.  After rebooting, it worked.  The second post about getting the ethernet port to work worked as well so thank you for that.  I guess this is solved now, but I have no idea what made the wireless and sound work again...

Here is the output of that if you are still curious:

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f4000000-f60fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000ebffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 10cb
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, medium devsel, latency 0, IRQ 42
	Memory at f7400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f741b000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f7418000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f7410000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7300000-f73fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f7200000-f72fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f6800000-f71fffff
	Prefetchable memory behind bridge: 00000000ec100000-00000000ecafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7417000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at f0b0 [size=8]
	I/O ports at f0a0 [size=4]
	I/O ports at f090 [size=8]
	I/O ports at f080 [size=4]
	I/O ports at f060 [size=32]
	Memory at f7416000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: medium devsel, IRQ 3
	Memory at f7415000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1212 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 10cb
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=32M]
	Memory at e0000000 (64-bit, prefetchable) [size=128M]
	Memory at e8000000 (64-bit, prefetchable) [size=64M]
	I/O ports at e000 [size=128]
	Expansion ROM at f6000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb

02:00.0 Ethernet controller: Atheros Communications Inc. Device e091 (rev 13)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f7300000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: alx
	Kernel modules: alx

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
	Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f7200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6801000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor

04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 10be
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6800000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

---

