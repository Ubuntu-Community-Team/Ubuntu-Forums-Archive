---
title: "USB Harddrive unreliable, required cold boot to work"
date: 2010-09-19
forum: General Help
---

### Post by RoboJ1M on 2010-09-19
Hi,

I'm rebuilding an old Fedora box as Ubuntu for a friend's parents.

I've put a new disk in and moved the old disk into a USB caddy.

The drive only works on the front USB port or the rear when not connected through, or even next to, a USB hub.

It also works WITH the hub but ONLY IF you cold boot the machine with the disk switched on.

And even then, it disconnects after a while.

This is the error in dmesg:

```
[ 1454.673887] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1455.088825] usb 1-1: device descriptor read/64, error -84
[ 1455.512226] usb 1-1: device descriptor read/64, error -71
[ 1455.728123] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1456.040277] usb 1-1: device descriptor read/64, error -71
[ 1456.476258] usb 1-1: device descriptor read/64, error -71
[ 1456.692309] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1456.920271] usb 1-1: device descriptor read/8, error -71
[ 1457.368240] usb 1-1: device descriptor read/8, error -84
[ 1457.584189] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[ 1457.960263] usb 1-1: device descriptor read/8, error -84
[ 1458.467834] usb 1-1: device descriptor read/8, error -84
[ 1458.568288] usb 1-1: USB disconnect, address 2

```

I've tried 

```
echo -1 > /sys/module/usbcore/parameters/autosuspend
```

and

```
echo Y > /sys/module/usbcore/parameters/old_scheme_first
```

I needed to add noapictimer and irqpoll to the boot params to get the usb mouse usable.

The results are quite random, after switching the device off and on, now I get:

```
[ 2036.984278] usb 1-1: new full speed USB device using uhci_hcd and address 11
[ 2037.204260] usb 1-1: device descriptor read/64, error -71
[ 2037.776142] usb 1-1: device descriptor read/64, error -84
[ 2037.992227] usb 1-1: new full speed USB device using uhci_hcd and address 12
[ 2038.536307] usb 1-1: device descriptor read/64, error -84
[ 2039.104227] usb 1-1: device descriptor read/64, error -84
```

It's not always the same!

It's a pre-2000 BIOS I think, Asus A7V with BIOS ver 1006.

Does anybody have any ideas?

Thanks,

J1M.

---

### Post by Budoc on 2010-09-23
There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349767") documented on launchpad concerning random disconnections of usb harddrives. Perhaps your problem is related to it? Other than that, I've no idea, sorry.

---

