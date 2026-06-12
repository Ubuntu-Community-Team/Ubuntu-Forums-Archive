---
title: "Ubuntu freeing when ethernet network interface not connected"
date: 2011-07-05
forum: General Help
---

### Post by DevinJCan on 2011-07-05
Hello and thanks for reading my thread,

I'm having a problem  here. I did a fresh install of kubuntu, and this computer will only boot  properly (without freezing) when it is plugged into a network via  ethernet cable. It will also freeze when I unplug after a successful  boot. I have had the same problem with Ubuntu... I have done a little  bit of searching to no avail. Any direction will be appriciated. Where  do I start?

Some of this information may help.

Platform Version 4.6.2 (4.6.2)

Grub:
Package: grub
Priority: optional
Section: admin
Installed-Size: 912
Maintainer: Ubuntu Kernel Team <[EMAIL="kernel-team@lists.ubuntu.com"]kernel-team@lists.ubuntu.com[/EMAIL]>
Original-Maintainer: Grub Maintainers <[EMAIL="pkg-grub-devel@lists.alioth.debian.org"]pkg-grub-devel@lists.alioth.debian.org[/EMAIL]>
Architecture: i386
Version: 0.97-29ubuntu61
Provides: linux-boot-loader
Depends:  libc6 (>= 2.12), libncurses5 (>= 5.5-5~), grub-common, udev  (>= 117-5), ucf (>= 3.004-0ubuntu2), debconf (>= 1.5.19) |  cdebconf, util-linux (>= 2.15-1)
Suggests: grub-legacy-doc, mdadm
Conflicts: grub-coreboot, grub-efi-amd64, grub-efi-ia32, grub-ieee1275, grub-pc
Filename: pool/main/g/grub/grub_0.97-29ubuntu61_i386.deb
Size: 284940
MD5sum: 91d35178cf3d6c0d981576767f1c6b56
SHA1: b4eb84699955ef2b1a48de33aed1a6e558a939e3
SHA256: da28dea2a76b1b286500e0de1be391ca07fe5eeccd0b2a3dad2425aa107b65e4
Description: GRand Unified Bootloader (Legacy version)
 GRUB is a GPLed bootloader intended to unify bootloading across x86
 operating systems.  In addition to loading the Linux kernel,
 it implements the Multiboot standard, which allows for flexible loading
 of multiple boot images (needed for modular kernels such as the GNU Hurd).
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 18m

CPU:
Architecture:          i686
CPU op-mode(s):        64-bit
CPU(s):                1
Thread(s) per core:    1
Core(s) per socket:    1
CPU socket(s):         1
Vendor ID:             AuthenticAMD
CPU family:            20
Model:                 1
Stepping:              0
CPU MHz:               750.000
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             32K
L2 cache:              512K

GPU:
00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9803
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

---

