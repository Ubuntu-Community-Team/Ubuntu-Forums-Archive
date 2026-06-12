---
title: "&quot;Disabling IRQ #11&quot; loop on boot"
date: 2010-03-07
forum: General Help
---

### Post by LloydM999 on 2010-03-07
I have Ubuntu kernel 2.6.31-20 generic 64-bit. After replacing my mobo, bootup gets stuck in a "[<timestamp>] Disabling IRQ #11" loop. I tried the older kernel versions available in grub, but the same thing happens. The recovery mode kernel bootup also loops. I'm not sure how to get the dmesg log when the system won't boot, so I'm not sure what messages I'm getting from recovery mode.

 If I disconnect all my USB devices, Ubuntu boots OK. When I reconnect everything after boot, lsusb seems to find all my USB devices. When I connect a device to my PCI USB hub card, Ubuntu recognizes it, but dmesg repeats this error:

[ 1332.940138] usb 3-3.4.1: usbfs: USBDEVFS_CONTROL failed cmd lsusb rqt 128 rq 6 len 4 ret -110

lsusb shows the PCI hub card as:
Bus 003 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

 cat /proc/interrupts doesn't show anything for IRQ 11 with everything connected.

Can anyone help me troubleshoot this?

 -Thanks, LloydM999

---

