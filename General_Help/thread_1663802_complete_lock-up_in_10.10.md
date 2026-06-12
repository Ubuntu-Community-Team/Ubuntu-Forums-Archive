---
title: "complete lock-up in 10.10"
date: 2011-01-10
forum: General Help
---

### Post by wfedorko on 2011-01-10
Hi,
For several days now my laptop has been locking up. This happens 2-3 times a day and there seems to be no particular pattern in terms of what I am doing at the time. Mostly I am not doing much at the time e.g. browsing the web. The symptom is that my display freezes, I can't switch to terminal (Alt+Ctrl+F1) and CapsLock NumLock keys don't switch the indicator lights.

/var/log/syslog kern.log show nothing from the crash. All I see are entries from way before the crash and than messages from the reeboot. 

Is there a way to enable more detailed logging? The system must have done something when it crashed no?

The laptop is Asus M50VM

lspci -v below

kernels I used are 2.6.35-23 -24 2.6.37-020637 and now I am trying 2.6.36-020636 (all -generic) (this one hasn't crashed yet but I don't have my hopes high)

any help appreciated...
Thanks,
w

 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0a <?>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bc00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b800 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1893
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fdf00000-fdffffff
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe000000-fe9fffff
	Prefetchable memory behind bridge: 00000000f6000000-00000000f8efffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: [40] Express Root Port (Slot-), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 1897
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b480 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b080 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: feb00000-febfffff
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 1897

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 48
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=32]
	Memory at f9fff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1892
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fd000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information: Len=14 <?>
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

03:00.0 Network controller: Intel Corporation WiFi Link 5100
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at fdffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-16-ea-ff-ff-63-56-c0
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. U6V laptop
	Flags: bus master, fast devsel, latency 0, IRQ 47
	I/O ports at e800 [size=256]
	Memory at f8fff000 (64-bit, prefetchable) [size=4K]
	Memory at f8fe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 91-01-69-00-68-4c-e0-00
	Kernel driver in use: r8169
	Kernel modules: r8169

09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: firewire_ohci
	Kernel modules: ohci1394, firewire-ohci

09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at febfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1897
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at febfe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: r852
	Kernel modules: r852

---

### Post by TeoBigusGeekus on 2011-01-10
If you're using the nvidia restricted drivers, try disabling them and switching to nouveau.
You'll lose some eye candy, but at least your system will (probably) be steady...

---

### Post by wfedorko on 2011-01-10
Hi,

the lspci shows:

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1892
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fd000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

So it seems that I am using the nvidia driver (I also get an nVidia splash screen on reeboot) 

Why do you think this is due to nvidia drivers? My system used to be very stable until maybe a week ago when it started occasionally crashing.  I am not sure how to see an update history to check what changed and in particular if nvidia driver was updated...

Thanks,
w

---

### Post by TeoBigusGeekus on 2011-01-10
I have a dual boot system at work (win7/maverick) and I used to experience continuous crashes: after half an hour of operating, the screen would freeze and I couldn't do anything with the mouse/keyboard.
Since I disable the restricted drivers and switched to nouveau it seems to be steady, though it's not my main system, ie. I don't use it quite often.

---

### Post by wfedorko on 2011-01-10
Hi,
Well but that does not show that something is really wrong with the driver on my system- during the crashes you experienced previously - how did you find out that they were brought about by the nvidia driver? 
The nvidia driver seems to be used widely. So I suspect the problem lies somewhere else...
I also run glxgears overnight and system didn't crash.

Before changing drivers etc I would prefer to find out what the problem actually is- and I don't know how to do this. I did a bit of this randomness with the kernels as detailed below but it didn't help. 

Thanks,
Wojtek

---

### Post by TeoBigusGeekus on 2011-01-10
I must have found it somewhere on the internet, can't remember.
There are a number of threads here in the forums about random freezes in maverick, nobody has figured out why it happens.
Try disabling the drivers for an afternoon, you have nothing to lose...
Sorry if I can't be of any more help.

---

### Post by wfedorko on 2011-01-10
Hi,
I post several recent updates from synaptic history. Nothing strikes me as suspicious but maybe you will find what could have gone wrong. Maybe udev? Maybe kernel? But then I experienced a crash with the -23 kernel this morning...

The problem is about a week - 2 weeks old so certainly not the last updates... 

Thanks,
w



Commit Log for Sat Jan  8 16:08:49 2011


Upgraded the following packages:
apparmor (2.5.1-0ubuntu0.10.10.2) to 2.5.1-0ubuntu0.10.10.3
apparmor-utils (2.5.1-0ubuntu0.10.10.2) to 2.5.1-0ubuntu0.10.10.3
cups (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
cups-bsd (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
cups-client (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
cups-common (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
cups-ppdc (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
dpkg (1.15.8.4ubuntu3) to 1.15.8.4ubuntu3.1
dpkg-dev (1.15.8.4ubuntu3) to 1.15.8.4ubuntu3.1
ifupdown (0.6.10ubuntu3) to 0.6.10ubuntu3.1
libapparmor-perl (2.5.1-0ubuntu0.10.10.2) to 2.5.1-0ubuntu0.10.10.3
libapparmor1 (2.5.1-0ubuntu0.10.10.2) to 2.5.1-0ubuntu0.10.10.3
libcups2 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libcupscgi1 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libcupsdriver1 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libcupsimage2 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libcupsmime1 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libcupsppdc1 (1.4.4-6ubuntu2.2) to 1.4.4-6ubuntu2.3
libdpkg-perl (1.15.8.4ubuntu3) to 1.15.8.4ubuntu3.1
libvlc5 (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
libvlccore4 (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
python-django (1.2.3-1ubuntu0.1) to 1.2.3-1ubuntu0.2.10.10.1
vlc (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
vlc-data (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
vlc-nox (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
vlc-plugin-notify (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2
vlc-plugin-pulse (1.1.4-1ubuntu1.1) to 1.1.4-1ubuntu1.2

Installed the following packages:
hardinfo (0.5.1-1.1ubuntu3)



Commit Log for Sun Jan  2 17:04:14 2011


Installed the following packages:
alien (8.81)


Commit Log for Wed Dec 29 17:35:38 2010


Reinstalled the following packages:
qlandkartegt (0.18.3-1)



Commit Log for Thu Dec 23 09:59:09 2010


Upgraded the following packages:
acroread (9.4-1maverick1) to 9.4.1-1maverick1
language-pack-bn (1:10.10+20100930) to 1:10.10+20101204
language-pack-de (1:10.10+20100930) to 1:10.10+20101204
language-pack-en (1:10.10+20100930) to 1:10.10+20101204
language-pack-es (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-bn (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-de (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-en (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-es (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-pt (1:10.10+20100930) to 1:10.10+20101204
language-pack-gnome-xh (1:10.10+20100930) to 1:10.10+20101204
language-pack-pt (1:10.10+20100930) to 1:10.10+20101204
language-pack-xh (1:10.10+20100930) to 1:10.10+20101123
libgudev-1.0-0 (1:162-2.1) to 1:162-2.2
libhdf4g-dev (4.1r4-22) to 4.2r4-10
libudev0 (162-2.1) to 162-2.2
linux-generic (2.6.35.23.25) to 2.6.35.24.28
linux-headers-generic (2.6.35.23.25) to 2.6.35.24.28
linux-image-generic (2.6.35.23.25) to 2.6.35.24.28
linux-libc-dev (2.6.35-1023.41) to 2.6.35-1024.42
udev (162-2.1) to 162-2.2

Installed the following packages:
libhdf4-dev (4.2r4-10)
linux-headers-2.6.35-24 (2.6.35-24.42)
linux-headers-2.6.35-24-generic (2.6.35-24.42)
linux-image-2.6.35-24-generic (2.6.35-24.42)
ps2eps (1.64-6build1)




Commit Log for Wed Dec 15 09:32:37 2010


Upgraded the following packages:
exim4 (4.69-11ubuntu4) to 4.69-11ubuntu4.1
exim4-base (4.69-11ubuntu4) to 4.69-11ubuntu4.1
exim4-config (4.69-11ubuntu4) to 4.69-11ubuntu4.1
exim4-daemon-light (4.69-11ubuntu4) to 4.69-11ubuntu4.1
firefox (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
firefox-3.5 (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
firefox-3.5-branding (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
firefox-3.5-gnome-support (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
firefox-branding (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
firefox-gnome-support (3.6.12+build1+nobinonly-0ubuntu0.9.10.1) to 3.6.13+build3+nobinonly-0ubuntu0.9.10.1
google-chrome-stable (8.0.552.215-r67652) to 8.0.552.224-r68599
krb5-clients (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
krb5-user (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libgssapi-krb5-2 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libgssrpc4 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libk5crypto3 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkadm5clnt6 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkadm5srv6 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkdb5-4 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkrb5-3 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkrb5-dev (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
libkrb5support0 (1.7dfsg~beta3-1ubuntu0.6) to 1.7dfsg~beta3-1ubuntu0.7
nspluginwrapper (1.2.2-0ubuntu6) to 1.2.2-0ubuntu6.9.10.1
xulrunner-1.9.1 (1.9.1.15+build1+nobinonly-0ubuntu0.9.10.1) to 1.9.1.16+build2+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.1-gnome-support (1.9.1.15+build1+nobinonly-0ubuntu0.9.10.1) to 1.9.1.16+build2+nobinonly-0ubuntu0.9.10.1
xulrunner-1.9.2 (1.9.2.12+build1+nobinonly-0ubuntu0.9.10.1) to 1.9.2.13+build3+nobinonly-0ubuntu0.9.10.1

Installed the following packages:
hamster-applet (2.28.0-0ubuntu1.1)
libgtksourceview-common (1.8.5-2)
libgtksourceview1.0-0 (1.8.5-2)
libnautilus-burn4 (2.25.3-0ubuntu3)
python-bugbuddy (2.28.0-0ubuntu1)
python-evince (2.28.0-0ubuntu1)
python-gnome2-desktop (2.28.0-0ubuntu1)
python-gnomedesktop (2.28.0-0ubuntu1)
python-gnomeprint (2.28.0-0ubuntu1)
python-gtksourceview (2.28.0-0ubuntu1)
python-gtop (2.28.0-0ubuntu1)
python-mediaprofiles (2.28.0-0ubuntu1)
python-metacity (2.28.0-0ubuntu1)
python-nautilusburn (2.28.0-0ubuntu1)
python-totem-plparser (2.28.0-0ubuntu1)


Commit Log for Tue Dec 14 09:40:11 2010


Installed the following packages:
gnotime (2.3.1~snapshot20090531-1ubuntu2)
libgnomecups1.0-1 (0.2.3-3build1)
libgnomeprint2.2-0 (2.18.6-1build1)
libgnomeprint2.2-data (2.18.6-1build1)
libgnomeprintui2.2-0 (2.18.4-1)
libgnomeprintui2.2-common (2.18.4-1)
libgtkhtml3.8-15 (1:3.13.5-1ubuntu3)
libqof2 (0.8.1-1)
libqof2-backend-qsf (0.8.1-1)
qof-data (0.8.1-1)

---

### Post by wfedorko on 2011-01-10
Hi Teo
-ok will try that... will see what happens...
w

---

### Post by wfedorko on 2011-01-10
Well ok I installed nvidia driver 260.19.29 using the nvidia installer. And using it with kernel 2.6.35-23-generic (x86-64)
driver used previously had a rather lower version number (but didn't note it down before installing this one)...
Will see what happens.

But would still appreciate information on how to diagnose reason for system lock-up...

Thanks,
w

---

### Post by wfedorko on 2011-01-10
That didn't help - crashed again. This time a sound was playing and it entered a 'broken record' loop - of about 1sec duration. 
Again nothing in the logs from the time of the crash.

Please help...
thanks,
w

---

### Post by Trapper on 2011-01-10
Everyone is quick to blame the nvidia 3rd party drivers. It may not have anything to do with this. I have nvidia video but do not uses nvidia's drivers.  There is something seriously wrong with 10.10. If you do not believe it, try copying and pasting several gigs of files from your home folder to another mounted partition you have rights to or to a USB drive, etc. Chances are you'll freeze up before a gig of files is transferred. That ain't nvidia.

---

### Post by TeoBigusGeekus on 2011-01-10
> **wfedorko said:**
> Well ok I installed nvidia driver 260.19.29 using the nvidia installer. And using it with kernel 2.6.35-23-generic (x86-64)
driver used previously had a rather lower version number (but didn't note it down before installing this one)...
Will see what happens.

But would still appreciate information on how to diagnose reason for system lock-up...

Thanks,
w

As I've told you, try disabling the restricted nvidia drivers completely.
...Or even better, as Trapper suggested, switch to lucid.

---

### Post by wfedorko on 2011-01-14
Hi,
Ok - I may have gotten somewhere. 
As suspected nothing to do with nvidia.

2 days without a crash - by booting with

acpi=off

added to the kernel options.
This naturally makes laptop rather inconvenient to use - suspending to ram doesn't work (hibernate to disk does work though). Unable to change brightness or use the special keys. Battery state is also not accessible.

Can anyone help me debug this further so that I can use acpi again?? Bug must be somewhere there but I can not further diagnose this...

Thanks,
w

---

### Post by Trapper on 2011-01-14
> **wfedorko said:**
> Hi,
Ok - I may have gotten somewhere. 
As suspected nothing to do with nvidia.

2 days without a crash - by booting with

acpi=off

added to the kernel options.
This naturally makes laptop rather inconvenient to use - suspending to ram doesn't work (hibernate to disk does work though). Unable to change brightness or use the special keys. Battery state is also not accessible.


I just tried this with a 10.10 install that I kept around. I never got to any comprehensive testing with it but my initial testing failed when utilizing acpi=off. My biggest headache has been nautilus freezing when transferring large amounts of information to/from other partitions, usb drives, etc. After about 300-600 MB of info the entire system would freeze up. This was most prominent when transferring "from". After including acpi=off in the boot parameters I experienced the same lock ups. I did not test any further to determine what else does or does not lock up the system now.

---

### Post by wfedorko on 2011-01-14
Hi,


Thanks Trapper- 
As I mentioned before - the lock-ups are seemingly unrelated to the load on the system including disk usage (occurred for instance with almost idle system). In one of my tests I have run bonnie++ for several hours and also copied a lot of data between different partitions and no lock-up. So I think the mechanism is different here from the lock-up you are experiencing.


So could anyone give me any hints on how to narrow down the acpi problem?


Thanks,
Wojtek

---

### Post by wfedorko on 2011-01-18
Hi,
Ok investigated further a bit.
Compiled the kernel with acpi debugging support and cpufreq debugging support. (based on 2.6.35-23-generic kernel adding just those two options)

run the system with additional kernel parameters:
cpi.debug_layer=0xffffffff acpi.debug_level=0xf8160407 cpufreq.debug=7

Now of course there is a lot of junk in the /var/log/messages
about every second there is a printout detailing temperature measurement.

Here is a section where the system crashed and then new boot from .../messages:

Jan 18 12:07:34 tachyon kernel: [ 5956.978898] utdelete-0409 [593] ut_update_ref_count   : Obj ffff88013b26a5a0 Refs=0, [Decremented]
Jan 18 12:07:34 tachyon kernel: [ 5956.978902] utdelete-0317 [594] ut_delete_int
ernal_obj: Deleting Object ffff88013b26a5a0 [Integer]
Jan 18 12:07:34 tachyon kernel: [ 5956.978905] nsobject-0241 [591] ns_detach_object      : Node ffff880131cf8d88 [__L1] Object ffff88013b26a5e8
Jan 18 12:07:34 tachyon kernel: [ 5956.978909] utdelete-0695 [592] ut_remove_reference   : Obj ffff88013b26a5e8 Current Refs=1 [To Be Decremented]
Jan 18 12:07:34 tachyon kernel: [ 5956.978913] utdelete-0409 [593] ut_update_ref_count   : Obj ffff88013b26a5e8 Refs=0, [Decremented]
Jan 18 12:07:34 tachyon kernel: [ 5956.978917] utdelete-0317 [594] ut_delete_internal_obj: Deleting Object ffff88013b26a5e8 [Integer]
Jan 18 12:07:34 tachyon kernel: [ 5956.978956]   nseval-0277 [586] ns_evaluate           : *** Completed evaluation of object _TMP ***
Jan 18 12:07:34 tachyon kernel: [ 5956.978960] utdelete-0695 [586] ut_remove_reference   : Obj ffff88013b26a3f0 Current Refs=1 [To Be Decremented]
Jan 18 12:07:34 tachyon kernel: [ 5956.978963] utdelete-0409 [587] ut_update_ref_count   : Obj ffff88013b26a3f0 Refs=0, [Decremented]
Jan 18 12:07:34 tachyon kernel: [ 5956.978967] utdelete-0317 [588] ut_delete_internal_obj: Deleting Object ffff88013b26a3f0 [Integer]
Jan 18 12:07:34 tachyon kernel: [ 5956.978971]    utils-0286 [584] evaluate_integer      : Return value [3262]
Jan 18 12:07:34 tachyon kernel: [ 5956.978974]  thermal-0266 [584] thermal_get_temperatur: Temperature is 3262 dK
Jan 18 12:13:15 tachyon kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 18 12:13:15 tachyon rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1143" x-info="http://www.rsyslog.com"] (re)start
Jan 18 12:13:15 tachyon rsyslogd: rsyslogd's groupid changed to 102
Jan 18 12:13:15 tachyon rsyslogd: rsyslogd's userid changed to 101
Jan 18 12:13:15 tachyon kernel: 0, Enable=00
Jan 18 12:13:15 tachyon kernel: [   25.500672] utdelete-0695    evgpe-0276 [4294967284] ut_remove_reference   : [4294967284] ut_remove_reference   : Read GPE Register at GPE28: Status100, Enable=00
Jan 18 12:13:15 tachyon kernel: [   25.500673] Read GPE Register at GPE28: Status100, Enable=00
Jan 18 12:13:15 tachyon kernel: [   25.500678] utdelete-0409 [4294967286] ut_update_ref_count   :    evgpe-801381ebc18 Refs=0, [Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500678]    evgpe-0276 utdelete-0317 utdelete-0317 Read GPE Regiut_delete_i30: Status=00, Enable=00
Jan 18 12:13:15 tachyon kernel: [   25.500682] Read GPE Regiut_delete_i30: Status=00, Enable=00
Jan 18 12:13:15 tachyon kernel: [   25.500687] Deleting Object ffff8801381ebc18 [Integer]
Jan 18 12:13:15 tachyon kernel: [   25.500689] utdelete-0652 [  evgpe-0276 [4294967284] ut_add_reference      : [4294967284] ev_gpe_detect         : [4294967284] ev_gpe_detect         : utdelete-0393 utdelete-0393 [4294967285] ut_update_ref_count   : Obj ffff8801381eb948 Refs=2, [Incremented]
Jan 18 12:13:15 tachyon kernel: [   25.500700] utobject-0401 [4294967284] ut_allocate_object_des: ffff8801381ebc18 Size 48
Jan 18 12:13:15 tachyon kernel: [   25.500705] utobject-0401 [4294967283] ut_allocate_object_des: ffff8801381eb9d8 Size 48
Jan 18 12:13:15 tachyon kernel: [   25.500709] utdelete-0695 [4294967282] ut_remove_reference   : Obj ffff8801381eb948 Current Refs=2 [To Be Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500713] utdelete-0409 [4294967283] ut_update_ref_count   : Obj ffff8801381eb948 Refs=1, [Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500716] utdelete-0695 [4294967282] ut_remove_reference   : Obj ffff8801381ebc18 Current Refs=1 [To Be Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500720] utdelete-0409 [4294967283] ut_update_ref_count   : Obj ffff8801381ebc18 Refs=0, [Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500724] utdelete-0317 [4294967284] ut_delete_internal_obj: Deleting Object ffff8801381ebc18 [Integer]
Jan 18 12:13:15 tachyon kernel: [   25.500728] utdelete-0695 [4294967282] ut_remove_reference   : Obj ffff8801381eb948 Current Refs=1 [To Be Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500732] utdelete-0409 [4294967283] ut_update_ref_count   : Obj ffff8801381eb948 Refs=0, [Decremented]
Jan 18 12:13:15 tachyon kernel: [   25.500736] utdelete-0317 [4294967284] ut_delete_internal_obj: Deleting Object ffff8801381eb948 [Integer]
Jan 18 12:13:15 tachyon kernel: [   25.500740] utdelete-0652 [4294967282] ut_add_reference      : Obj ffff8801381eb9d8 Current Refs=1 [To Be Incremented]
Jan 18 12:13:15 tachyon kernel: [   25.500744] utdelete-0393 [4294967283] ut_update_ref_count   : Obj ffff8801381eb9d8 Refs=2, [Incremented]


The thing is that the system crashed at 12:10 and yet there is nothing past 12:07 so it seems there was no logging for 3 minutes before the system crash...


Can anyone help me with this?

Thanks,
w

---

### Post by wfedorko on 2011-01-18
Ok another crash...

This time it occurred apparently as the log was being written to...
Notice that the first message after the reboot appears at the unfinished line from the previous boot.


Jan 18 16:22:53 tachyon kernel: [14054.161807] utdelete-0409 [4294964567] ut_update_ref_count   : Obj ffff880137280000 Refs=1, [Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161812] nsobject-0241 [4294964566] ns_detach_object      : Node ffff88006aa45968 [__L0] Object ffff880137280120
Jan 18 16:22:53 tachyon kernel: [14054.161815] utdelete-0695 [4294964567] ut_remove_reference   : Obj ffff880137280120 Current Refs=1 [To Be Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161819] utdelete-0409 [4294964568] ut_update_ref_count   : Obj ffff880137280120 Refs=0, [Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161823] utdelete-0317 [4294964569] ut_delete_internal_obj: Deleting Object ffff880137280120 [Integer]
Jan 18 16:22:53 tachyon kernel: [14054.161827] nsobject-0241 [4294964566] ns_detach_object      : Node ffff88006aa45988 [__L1] Object ffff880137280000
Jan 18 16:22:53 tachyon kernel: [14054.161831] utdelete-0695 [4294964567] ut_remove_reference   : Obj ffff880137280000 Current Refs=1 [To Be Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161835] utdelete-0409 [4294964568] ut_update_ref_count   : Obj ffff880137280000 Refs=0, [Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161838] utdelete-0317 [4294964569] ut_delete_internal_obj: Deleting Object ffff880137280000 [Integer]
Jan 18 16:22:53 tachyon kernel: [14054.161878]   nseval-0277 [4294964561] ns_evaluate           : *** Completed evaluation of object _TMP ***
Jan 18 16:22:53 tachyon kernel: [14054.161882] utdelete-0695 [4294964561] ut_remove_reference   : Obj ffff8801386c5f30 Current Refs=1 [To Be Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161886] utdelete-0409 [4294964562] ut_update_ref_count   : Obj ffff8801386c5f30 Refs=0, [Decremented]
Jan 18 16:22:53 tachyon kernel: [14054.161890] utdelete-0317 [4294964563] ut_delete_internal_obj: Deleting Object ffff8801386c5f30 [Integer]
Jan 18 16:22:53 tachyon kernel: [14054.161894]    utils-0286 [4294964559] evaluate_integer      : Return value [3252]
Jan 18 16:22:53 tachyon kernel: [14054.161898]  thermal-0266 [4294964559] thermal_get_temperatur: Temperature is 3252 dK
Jan 18 16:22:54 tachyon kernel: [14055.162538] cpufreq_debug_printk: 755 callbacks suppressed
Jan 18 16:22:55 tachyon kernel: [14056.139142] nsaccess-0399 [4294964566] ns_lookup             : Searching relative to prefix scope [THRM] (ffff88013b63a520)
Jan 18 16:22:55 tachyon kernel: [14056.139159] nsaccess-0511 [4294964566] ns_lookup             : Simple Pathname (1 segment, Flags=2)
Jan 18 16:22:55 tachyon kernel: [14056.139171]   nsdump-0087 [4294964566] ns_print_pathname     : [_TMP]
Jan 18 16:22:55 tachyon kernel: [14056.139204] nssearch-0114 [4294964568] ns_search_one_scope   : Searching \_TZ_.THRM (ffff88013b63a520) For [_TMP] (Untyped)
Jan 18 16:22:55 tachyon kernel: [14056.139219] nssearch-0149 [4294964568] ns_search_one_scope   : Name [_TMP] (Method) ffff88013b63a560 found in scope [THRM] ffff88013b63a520
Jan 18 16:22:55 tachyon kernel: [14056.139236]   nseval-0127 [4294964564] ns_evaluate           : _TMP [ffff88013b63a560] Value ffff88013b63b2d0
Jan 18 16:22:55 tachyon kernel: [14056.139255] ACPI: Execute Method [\_TZ_.THRM._TMP] (Node ffff88013b63a560)
Jan 18 16:22:55 tachyon kernel: [14056.139280] utobject-0401 [4294964568] ut_allocate_object_des: ffff8800a9a89318 Size 48
Jan 18 16:22:55 tachyon kernel: [14056.139311] utobject-0401 [4294964572] ut_allocate_object_des: ffff8800a9a893a8 Size 48
Jan 18 16:22:55 tachyon kernel: [14056.139324] utobject-0401 [4294964572] ut_allocate_object_des: ffff8800a9a89f78 Size 48
Jan 18 16:22:55 tachyon kernel: [14056.139343] utdelete-0652 [4294964573] ut_add_reference      : Obj ffff8800a9a89f78 Current Refs=1 [To Be Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139357] utdelete-0393 [4294964574] ut_update_ref_count   : Obj ffff8800a9a89f78 Refs=2, [Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139371] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8800a9a893a8 Current Refs=1 [To Be Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139384] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8800a9a893a8 Refs=0, [Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139396] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff8800a9a893a8 [Reference]
Jan 18 16:22:55 tachyon kernel: [14056.139411] utdelete-0695 [4294964571] ut_remove_reference   : Obj ffff8800a9a89318 Current Refs=1 [To Be Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139424] utdelete-0409 [4294964572] ut_update_ref_count   : Obj ffff8800a9a89318 Refs=0, [Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139436] utdelete-0317 [4294964573] ut_delete_internal_obj: Deleting Object ffff8800a9a89318 [Integer]
Jan 18 16:22:55 tachyon kernel: [14056.139448] utdelete-0652 [4294964571] ut_add_reference      : Obj ffff8800a9a89f78 Current Refs=2 [To Be Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139460] utdelete-0393 [4294964572] ut_update_ref_count   : Obj ffff8800a9a89f78 Refs=3, [Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139473] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8800a9a89f78 Current Refs=3 [To Be Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139486] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8800a9a89f78 Refs=2, [Decremented]
Jan 18 16:22:55 tachyon kernel: [14056.139507] utobject-0401 [4294964572] ut_allocate_object_des: ffff8800a9a89318 Size 48
Jan 18 16:22:55 tachyon kernel: [14056.139519] utdelete-0652 [4294964573] ut_add_reference      : Obj ffff8800a9a89f78 Current Refs=2 [To Be Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139532] utdelete-0393 [4294964574] ut_update_ref_count   : Obj ffff8800a9a89f78 Refs=3, [Incremented]
Jan 18 16:22:55 tachyon kernel: [14056.139544] utdelete-0695 [4294964572] ut_remove_reference   : Obj ffff8800a9a89318Jan 18 16:25:37 tachyon kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 18 16:25:37 tachyon rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1116" x-info="http://www.rsyslog.com"] (re)start
Jan 18 16:25:37 tachyon rsyslogd: rsyslogd's groupid changed to 102
Jan 18 16:25:37 tachyon rsyslogd: rsyslogd's userid changed to 101
Jan 18 16:25:37 tachyon kernel: [4294967289] ev_gpe_detect         : Read GPE Register at GPE10: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746892]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE18: Status=08, Enable=0C
Jan 18 16:25:37 tachyon kernel: [   23.746911]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE20: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746918]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE28: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746926]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE30: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746933]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE38: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746943] utdelete-0695 [4294967283] ut_remove_reference   : Obj ffff88013723c3a8 Current Refs=1 [To Be Decremented]
Jan 18 16:25:37 tachyon kernel: [   23.746947] utdelete-0409 [4294967284] ut_update_ref_count   : Obj ffff88013723c3a8 Refs=0, [Decremented]
Jan 18 16:25:37 tachyon kernel: [   23.746950] utdelete-0317 [4294967285] ut_delete_internal_obj: Deleting Object ffff88013723c3a8 [Integer]
Jan 18 16:25:37 tachyon kernel: [   23.746954] utdelete-0652 [4294967283] ut_add_reference      : Obj ffff88013723c3f0 Current Refs=1 [To Be Incremented]
Jan 18 16:25:37 tachyon kernel: [   23.746958] utdelete-0393 [4294967284] ut_update_ref_count   : Obj ffff88013723c3f0 Refs=2, [Incremented]
Jan 18 16:25:37 tachyon kernel: [   23.746964] utobject-0401 [4294967284] ut_allocate_object_des: ffff88013723c3a8 Size 48



Is there really no expert out there who could help?

Thanks,
w

---

### Post by wfedorko on 2011-01-18
Hi,
actually /var/log/kern.log seems to have more messages just prior to the crash here:
Jan 18 16:22:59 tachyon kernel: [14060.152919] utdelete-0695 [4294964569] ut_remove_reference   : Obj ffff8801381ebe58 Current Refs=2 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152924] utdelete-0409 [4294964570] ut_update_ref_count   : Obj ffff8801381ebe58 Refs=1, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152930] nsobject-0241 [4294964569] ns_detach_object      : Node ffff88006aa44d68 [__L0] Object ffff8801381ebc18
Jan 18 16:22:59 tachyon kernel: [14060.152934] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8801381ebc18 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152938] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8801381ebc18 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152941] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff8801381ebc18 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.152945] nsobject-0241 [4294964569] ns_detach_object      : Node ffff88006aa44d88 [__L1] Object ffff8801381ebe58
Jan 18 16:22:59 tachyon kernel: [14060.152949] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8801381ebe58 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152953] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8801381ebe58 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152957] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff8801381ebe58 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.152996]   nseval-0277 [4294964564] ns_evaluate           : *** Completed evaluation of object _TMP ***
Jan 18 16:22:59 tachyon kernel: [14060.153001] utdelete-0695 [4294964564] ut_remove_reference   : Obj ffff880137280120 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.153005] utdelete-0409 [4294964565] ut_update_ref_count   : Obj ffff880137280120 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.153008] utdelete-0317 [4294964566] ut_delete_internal_obj: Deleting Object ffff880137280120 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.153012]    utils-0286 [4294964562] evaluate_integer      : Return value [3262]
Jan 18 16:22:59 tachyon kernel: [14060.153016]  thermal-0266 [4294964562] thermal_get_temperatur: Temperature is 3262 dK
Jan 18 16:22:59 tachyon kernel: [14060.170193] cpufreq_debug_printk: 1623 callbacks suppressed
Jan 18 16:22:59 tachyon kernel: [14060.170197] cpufreq-core: target for CPU 0: 800000 kHz, relation 0
Jan 18 16:22:59 tachyon kernel: [14060.170199] acpi-cpufreq: acpi_cpufreq_target 800000 (0)
Jan 18 16:22:59 tachyon kernel: [14060.170202] freq-table: request for target 800000 kHz (relation: 0) for cpu 0
Jan 18 16:22:59 tachyon kernel: [14060.170205] freq-table: target is 3 (800000 kHz, 3)
Jan 18 16:22:59 tachyon kernel: [14060.170207] cpufreq-core: notification 0 of frequency transition to 800000 kHz
Jan 18 16:22:59 tachyon kernel: [14060.170210] cpufreq-core: notification 1 of frequency transition to 800000 kHz
Jan 18 16:22:59 tachyon kernel: [14060.180042] cpufreq-core: target for CPU 0: 2534000 kHz, relation 1
Jan 18 16:22:59 tachyon kernel: [14060.180044] acpi-cpufreq: acpi_cpufreq_target 2534000 (0)
Jan 18 16:22:59 tachyon kernel: [14060.180046] freq-table: request for target 2534000 kHz (relation: 1) for cpu 0
Jan 18 16:22:59 tachyon kernel: [14060.180049] freq-table: target is 0 (2534000 kHz, 0)
Jan 18 16:23:01 tachyon kernel: [14062.139219] nsaccess-0399 [4294964566] ns_lookup             : Searching relative to prefix scope [THRM] (ffff88013b63a520)
Jan 18 16:23:01 tachyon kernel: [14062.139225] nsaccess-0511 [4294964566] ns_lookup             : Simple Pathname (1 segment, Flags=2)
Jan 18 16:23:01 tachyon kernel: [14062.139228]   nsdump-0087 [4294964566] ns_print_pathname     : [_TMP]
Jan 18 16:23:01 tachyon kernel: [14062.139241] nssearch-0114 [4294964568] ns_search_one_scope   : Searching \_TZ_.THRM (ffff88013b63a520) For [_TMP] (Untyped)
Jan 18 16:23:01 tachyon kernel: [14062.139246] nssearch-0149 [4294964568] ns_search_one_scope   : Name [_TMP] (Method) ffff88013b63a560 found in scope [THRM] ffff88013b63a520
Jan 18 16:23:01 tachyon kernel: [14062.139252]   nseval-0127 [4294964564] ns_evaluate           : _TMP [ffff88013b63a560] Value ffff88013b63b2d0
Jan 18 16:23:01 tachyon kernel: [14062.139258] ACPI: Execute Method [\_TZ_.THRM._TMP] (Node ffff88013b63a560)
Jan 18 16:23:01 tachyon kernel: [14062.139269] utobject-0401 [4294964568] ut_allocate_object_des: ffff880137280c18 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139282] utobject-0401 [4294964572] ut_allocate_object_des: ffff880137280000 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139286] utobject-0401 [4294964572] ut_allocate_object_des: ffff880137280dc8 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139293] utdelete-0652 [4294964573] ut_add_reference      : Obj ffff880137280dc8 Current Refs=1 [To Be Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139298] utdelete-0393 [4294964574] ut_update_ref_count   : Obj ffff880137280dc8 Refs=2, [Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139302] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff880137280000 Current Refs=1 [To Be Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139306] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff880137280000 Refs=0, [Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139310] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff880137280000 [Reference]
Jan 18 16:23:01 tachyon kernel: [14062.139315] utdelete-0695 [4294964571] ut_remove_reference   : Obj ffff880137280c18 Current Refs=1 [To Be Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139319] utdelete-0409 [4294964572] ut_update_ref_count   : Obj ffff880137280c18 Refs=0, [Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139323] utdelete-0317 [4294964573] ut_delete_internal_obj: Deleting Object ffff880137280c18 [Integer]
Jan 18 16:23:01 tachyon kernel: [14062.139327] utdelete-0652 [4294964571] ut_add_reference      : Obj ffff880137280dc8 Current Refs=2 [To Be Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139331] utdelete-0393 [4294964572] ut_update_Jan 18 16:25:37 tachyon kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 18 16:25:37 tachyon kernel: [4294967289] ev_gpe_detect         : Read GPE Register at GPE10: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746892]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE18: Status=08, Enable=0C



It seems that I am not catching the actual moment of the crash.
Can I somehow force that the kern.log is always written in real time without buffering?

Thanks,
w

---

### Post by wfedorko on 2011-01-18
Hi,
actually /var/log/kern.log seems to have more messages just prior to the crash here:
Jan 18 16:22:59 tachyon kernel: [14060.152919] utdelete-0695 [4294964569] ut_remove_reference   : Obj ffff8801381ebe58 Current Refs=2 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152924] utdelete-0409 [4294964570] ut_update_ref_count   : Obj ffff8801381ebe58 Refs=1, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152930] nsobject-0241 [4294964569] ns_detach_object      : Node ffff88006aa44d68 [__L0] Object ffff8801381ebc18
Jan 18 16:22:59 tachyon kernel: [14060.152934] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8801381ebc18 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152938] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8801381ebc18 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152941] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff8801381ebc18 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.152945] nsobject-0241 [4294964569] ns_detach_object      : Node ffff88006aa44d88 [__L1] Object ffff8801381ebe58
Jan 18 16:22:59 tachyon kernel: [14060.152949] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff8801381ebe58 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152953] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff8801381ebe58 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.152957] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff8801381ebe58 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.152996]   nseval-0277 [4294964564] ns_evaluate           : *** Completed evaluation of object _TMP ***
Jan 18 16:22:59 tachyon kernel: [14060.153001] utdelete-0695 [4294964564] ut_remove_reference   : Obj ffff880137280120 Current Refs=1 [To Be Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.153005] utdelete-0409 [4294964565] ut_update_ref_count   : Obj ffff880137280120 Refs=0, [Decremented]
Jan 18 16:22:59 tachyon kernel: [14060.153008] utdelete-0317 [4294964566] ut_delete_internal_obj: Deleting Object ffff880137280120 [Integer]
Jan 18 16:22:59 tachyon kernel: [14060.153012]    utils-0286 [4294964562] evaluate_integer      : Return value [3262]
Jan 18 16:22:59 tachyon kernel: [14060.153016]  thermal-0266 [4294964562] thermal_get_temperatur: Temperature is 3262 dK
Jan 18 16:22:59 tachyon kernel: [14060.170193] cpufreq_debug_printk: 1623 callbacks suppressed
Jan 18 16:22:59 tachyon kernel: [14060.170197] cpufreq-core: target for CPU 0: 800000 kHz, relation 0
Jan 18 16:22:59 tachyon kernel: [14060.170199] acpi-cpufreq: acpi_cpufreq_target 800000 (0)
Jan 18 16:22:59 tachyon kernel: [14060.170202] freq-table: request for target 800000 kHz (relation: 0) for cpu 0
Jan 18 16:22:59 tachyon kernel: [14060.170205] freq-table: target is 3 (800000 kHz, 3)
Jan 18 16:22:59 tachyon kernel: [14060.170207] cpufreq-core: notification 0 of frequency transition to 800000 kHz
Jan 18 16:22:59 tachyon kernel: [14060.170210] cpufreq-core: notification 1 of frequency transition to 800000 kHz
Jan 18 16:22:59 tachyon kernel: [14060.180042] cpufreq-core: target for CPU 0: 2534000 kHz, relation 1
Jan 18 16:22:59 tachyon kernel: [14060.180044] acpi-cpufreq: acpi_cpufreq_target 2534000 (0)
Jan 18 16:22:59 tachyon kernel: [14060.180046] freq-table: request for target 2534000 kHz (relation: 1) for cpu 0
Jan 18 16:22:59 tachyon kernel: [14060.180049] freq-table: target is 0 (2534000 kHz, 0)
Jan 18 16:23:01 tachyon kernel: [14062.139219] nsaccess-0399 [4294964566] ns_lookup             : Searching relative to prefix scope [THRM] (ffff88013b63a520)
Jan 18 16:23:01 tachyon kernel: [14062.139225] nsaccess-0511 [4294964566] ns_lookup             : Simple Pathname (1 segment, Flags=2)
Jan 18 16:23:01 tachyon kernel: [14062.139228]   nsdump-0087 [4294964566] ns_print_pathname     : [_TMP]
Jan 18 16:23:01 tachyon kernel: [14062.139241] nssearch-0114 [4294964568] ns_search_one_scope   : Searching \_TZ_.THRM (ffff88013b63a520) For [_TMP] (Untyped)
Jan 18 16:23:01 tachyon kernel: [14062.139246] nssearch-0149 [4294964568] ns_search_one_scope   : Name [_TMP] (Method) ffff88013b63a560 found in scope [THRM] ffff88013b63a520
Jan 18 16:23:01 tachyon kernel: [14062.139252]   nseval-0127 [4294964564] ns_evaluate           : _TMP [ffff88013b63a560] Value ffff88013b63b2d0
Jan 18 16:23:01 tachyon kernel: [14062.139258] ACPI: Execute Method [\_TZ_.THRM._TMP] (Node ffff88013b63a560)
Jan 18 16:23:01 tachyon kernel: [14062.139269] utobject-0401 [4294964568] ut_allocate_object_des: ffff880137280c18 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139282] utobject-0401 [4294964572] ut_allocate_object_des: ffff880137280000 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139286] utobject-0401 [4294964572] ut_allocate_object_des: ffff880137280dc8 Size 48
Jan 18 16:23:01 tachyon kernel: [14062.139293] utdelete-0652 [4294964573] ut_add_reference      : Obj ffff880137280dc8 Current Refs=1 [To Be Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139298] utdelete-0393 [4294964574] ut_update_ref_count   : Obj ffff880137280dc8 Refs=2, [Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139302] utdelete-0695 [4294964570] ut_remove_reference   : Obj ffff880137280000 Current Refs=1 [To Be Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139306] utdelete-0409 [4294964571] ut_update_ref_count   : Obj ffff880137280000 Refs=0, [Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139310] utdelete-0317 [4294964572] ut_delete_internal_obj: Deleting Object ffff880137280000 [Reference]
Jan 18 16:23:01 tachyon kernel: [14062.139315] utdelete-0695 [4294964571] ut_remove_reference   : Obj ffff880137280c18 Current Refs=1 [To Be Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139319] utdelete-0409 [4294964572] ut_update_ref_count   : Obj ffff880137280c18 Refs=0, [Decremented]
Jan 18 16:23:01 tachyon kernel: [14062.139323] utdelete-0317 [4294964573] ut_delete_internal_obj: Deleting Object ffff880137280c18 [Integer]
Jan 18 16:23:01 tachyon kernel: [14062.139327] utdelete-0652 [4294964571] ut_add_reference      : Obj ffff880137280dc8 Current Refs=2 [To Be Incremented]
Jan 18 16:23:01 tachyon kernel: [14062.139331] utdelete-0393 [4294964572] ut_update_Jan 18 16:25:37 tachyon kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 18 16:25:37 tachyon kernel: [4294967289] ev_gpe_detect         : Read GPE Register at GPE10: Status=00, Enable=00
Jan 18 16:25:37 tachyon kernel: [   23.746892]    evgpe-0276 [4294967289] ev_gpe_detect         : Read GPE Register at GPE18: Status=08, Enable=0C



It seems that I am not catching the actual moment of the crash.
Can I somehow force that the kern.log is always written in real time without buffering?

Thanks,
w

---

### Post by ccordoba12 on 2011-01-23
Hi,

I had random lock ups very similar to what you're describing: out of no where the system just freezed, sometimes ten minutes after booting, sometimes after 3 or 5 days of using it.

I solved the problem switching back to 2.6.35-**22**. Hope this helps.

Carlos

---

### Post by wfedorko on 2011-01-26
Hello Carlos,

I installed 2.6.35-22-generic (x86-64)
but it didn't help - just had a crash again...

Aside from yours and 2 other user's advice I am really surprised at lack of support on this forum. I have narrowed down the problem significantly, (it is related to acpi as with boot option acpi=off system is stable) and I have tried to debug further by compiling kernel with acpi debugging on and posting kern logs from around the the crash (which to me while cryptic seem to miss the actual crash moment).

I am really at a loss as to how I can investigate further and need acpi expert support.

thanks,
Wojtek

---

