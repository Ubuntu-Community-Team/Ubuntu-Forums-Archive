---
title: "Toshiba Laptop Mute Issue"
date: 2009-08-08
forum: General Help
---

### Post by ku5165 on 2009-08-08
Hey everyone,
I have a slight, but rather large issue at hand. I have a Toshiba U205-S5034, and i was dual booting XP for a long time with Ubuntu, however, i finally decided to make the full jump and get rid of XP all together. I reformatted my harddisk and installed everything nicely as i wanted. Now, when I was dual booting I had a slight issue where if i accidentally shut down XP with my audio muted, i would not get any audio in Ubuntu. Well, before formatting my computer, i accidentally left the audio on mute, or so it seems. 
Basically, my audio has worked previously on Ubuntu, i just think that XP has somehow "hardware locked it" so that i cannot unmute it using Ubuntu. Is there any way to fix this problem without reinstalling XP, unmuting and removing XP once again?
Thanks in advance.
ku

---

### Post by ku5165 on 2009-08-08
Just in case anyone wants, I found the same/similar bug on Launchpad.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160655)
I have attached most of my information there.
If you still need any info let me know.

---

### Post by ku5165 on 2009-08-09
aplay -l output
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



LSPCI OUTPUT
```

lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0003
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at ffd80000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at cff8 [size=8]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Memory at ffd40000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0003
	Flags: fast devsel
	Memory at b2000000 (32-bit, non-prefetchable) [disabled] [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b2080000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: ffc00000-ffcfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b2084000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: ac000000-b1ffffff
	Prefetchable memory behind bridge: 00000000a8000000-00000000abffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at cef0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1040
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	Memory at ffcff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: a8000000-abfff000 (prefetchable)
	Memory window 1: ac000000-affff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at b0006000 (32-bit, non-prefetchable) [size=2K]
	Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at b0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Device 0001
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at b0006800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```
let me know if u need anythign else, thanks again

---

### Post by ku5165 on 2009-08-09
output of sudo lshw -c multimedia
```

  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```
let me know if you guys need anything else

---

