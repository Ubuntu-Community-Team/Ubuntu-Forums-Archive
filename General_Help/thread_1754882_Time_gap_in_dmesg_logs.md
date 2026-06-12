---
title: "Time gap in dmesg logs"
date: 2011-05-10
forum: General Help
---

### Post by andrope on 2011-05-10
In dmesg output there is a gap after 3d second:

[    2.633399] mmc0: no vmmc regulator found
[    2.634436] Registered led device: mmc0::
[    2.640065] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA
[    2.651379] firewire_ohci 0000:02:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.712159] firewire_ohci: Added fw-ohci device 0000:02:09.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    2.976307] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.212236] firewire_core: created device fw0: GUID 334fc0001040d9a1, S400
[   24.366755] <30>udev[299]: starting version 167
[   24.415607] lp: driver loaded but no devices found
[   24.523840] Adding 9044556k swap on /dev/sda5.  Priority:-1 extents:1 across:9044556k 
[   24.609536] lib80211: common routines for IEEE802.11 drivers
[   24.609540] lib80211_crypt: registered algorithm 'NULL'

Could you please explain this? Is it possible to remove the gap and speed boot up?

---

### Post by lithopsian on 2011-05-10
dmesg doesn't log every single thing that happens.  Mostly it just logs stuff that the kernel does, which means a lot of messages in the first couple of seconds, then hardly anything until the boot is about finished.

---

