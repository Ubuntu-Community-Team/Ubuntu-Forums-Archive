---
title: "Setting up dual screen with nouveau"
date: 2010-06-13
forum: General Help
---

### Post by Jordanwb on 2010-06-13
Since nouveau seems capable for what I want I'm going to give it a try instead of nvidia's massive drivers. Another user earlier last year had a similar issue: he had two monitors and wanted to use both of them, and he solved it. Using the xorg.conf that worked for him, I modified it for my system. However when Ubuntu starts Xorg cannot because no device is selected.

```
Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "primary screen" 0 0
EndSection

Section "Device"
	Identifier     "nVidia Corporation GT216"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Driver         "nouveau"
	Option         "monitor-LVDS-0" "primary"
	Option         "monitor-VGA-0" "secondary"
EndSection

Section "Monitor"
	Identifier     "primary"
	VendorName     "HP"
	ModelName      "w1707"
	Option         "Position" "0 0"
	Option         "PreferredMode" "1440x900"
EndSection

Section "Monitor"
	Identifier     "secondary"
	VendorName     "HP"
	ModelName      "w1707"
	Option         "PreferredMode" "1440x900"
	Option         "RightOf" "primary"
EndSection

Section "Screen"
	Identifier     "primary screen"
	Device         "nVidia GeForce GT220"
	Monitor        "primary"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Virtual    2880 900
	EndSubSection
EndSection
```

lspci -v

```
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
	Subsystem: eVga.com. Corp. Device 1226
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	Expansion ROM at fea00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
```

Error:

> The following error was encountered. You may need to update your configuration to solve this.

(EE) [drm] failed to open device.
(EE) No devices detected.

---

### Post by Jordanwb on 2010-06-13
Whoa in two hours this thread is bumped to the 5th page?

---

### Post by Despot on 2010-07-11
I encountered the same issue in my Lucid install. De-activating the nvidia binary driver and rebooting seemed to resolve it.

---

