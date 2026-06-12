---
title: "Sony Vaio VPCEA1S1E - lucid linx 10.10 slow boot"
date: 2010-11-10
forum: General Help
---

### Post by afro22 on 2010-11-10
Hi, I updated my Sony Vaio VPCEA1S1E to Ubuntu 10.10. After that my boot process slow down.

From dmesg log i found 2 causes:

1)
[    1.309549] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.309678] NET: Registered protocol family 1
[B][    3.306525] pci 0000:00:1a.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    5.305851] pci 0000:00:1d.0: EHCI: BIOS handoff failed (BIOS bug?) 01010001[/B]
[    5.305983] pci 0000:01:00.0: Boot video device
[    5.306126] PCI: CLS 64 bytes, default 64

2)
[    6.675479] ata6: SATA link down (SStatus 0 SControl 300)
[B][    7.101340] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   17.627708] Adding 11454460k swap on /dev/sda5.  Priority:-1 extents:1 across:11454460k 
[/B][   18.947566] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.408201] udev[513]: starting version 163

First is old problem, this was on Ubuntu 10.04, too but second problem is new. Do you have idea why is 10 seconds pause between bold lines.

Thanks for any help

---

### Post by benste on 2010-11-12
Hi afro thanks for the dmesg hint, looks like I'm facing the same issues

> 
[    1.812560] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.940237] firewire_core: created device fw0: GUID 08004603022f0dd3, S400
[    7.333540] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   21.100269] udev[435]: starting version 163
[   21.167957] EXT4-fs (dm-1): re-mounted. Opts: errors=remoun


>  29.189033] Bluetooth: RFCOMM TTY layer initialized
[   29.189039] Bluetooth: RFCOMM socket layer initialized
[   29.189042] Bluetooth: RFCOMM ver 1.11
[   31.601556] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.605262] EXT4-fs (dm-0): re-mounted. Opts: commit=0
[   31.666120] EXT4-fs (dm-2): re-mounted. Opts: commit=0
[   31.669845] EXT4-fs (dm-3): re-mounted. Opts: commit=0
[   37.450024] eth0: no IPv6 routers present
[   40.760785] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   45.947772] wlan0: authenticate with 00:19:70:39:33:b0 (try 1)

---

