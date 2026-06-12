---
title: "USB mass storage partially broken in 9.04?"
date: 2010-01-09
forum: General Help
---

### Post by ThaddeusW on 2010-01-09
Hello everyone:

I am having a problem mounting my phone (Motorola ic902) under Ubuntu 9.04 as a mass storage device. Before this problem it mounted up and worked fine under 8.04 and still works fine under Windows XP and Vista. When I upgraded to 9.04 it would not even be recognized as a mass storage device. I thought it might be a USB configuration problem so I tried mounting it on a fresh install of 9.04 on another system. But even on the new system it does not function and I get the same error message in the syslog.

Syslog message:
```

Jan  9 13:45:41 atom kernel: [ 6725.628046] usb 5-1: new full speed USB device using uhci_hcd and address 4
Jan  9 13:45:41 atom kernel: [ 6725.696087] hub 5-0:1.0: unable to enumerate USB device on port 1
Jan  9 13:45:42 atom kernel: [ 6727.144038] usb 5-1: new full speed USB device using uhci_hcd and address 5
Jan  9 13:45:42 atom kernel: [ 6727.307337] usb 5-1: configuration #1 chosen from 1 choice

```

As you can see it cannot enumerate the device. The same exact message appears on both 9.04 systems. And yes I checked to make sure the phone is set to mass storage and it mounts under windows.

Anyone hear of this problem? Other USB mass storage devices including USB keys and USB-ATA/SATA bridges work 100%. I will not upgrade to 9.10 as I have had problems with 9.10. I am waiting for the next LTS version before upgrading.

---

### Post by dcstar on 2010-01-10
> **ThaddeusW said:**
> Hello everyone:

I am having a problem mounting my phone (Motorola ic902) under Ubuntu 9.04 as a mass storage device. Before this problem it mounted up and worked fine under 8.04 and still works fine under Windows XP and Vista. When I upgraded to 9.04 it would not even be recognized as a mass storage device. I thought it might be a USB configuration problem so I tried mounting it on a fresh install of 9.04 on another system. But even on the new system it does not function and I get the same error message in the syslog.

Syslog message:
```

Jan  9 13:45:41 atom kernel: [ 6725.628046] usb 5-1: new full speed USB device using uhci_hcd and address 4
Jan  9 13:45:41 atom kernel: [ 6725.696087] hub 5-0:1.0: unable to enumerate USB device on port 1
Jan  9 13:45:42 atom kernel: [ 6727.144038] usb 5-1: new full speed USB device using uhci_hcd and address 5
Jan  9 13:45:42 atom kernel: [ 6727.307337] usb 5-1: configuration #1 chosen from 1 choice

```

As you can see it cannot enumerate the device. The same exact message appears on both 9.04 systems. And yes I checked to make sure the phone is set to mass storage and it mounts under windows.

Anyone hear of this problem? Other USB mass storage devices including USB keys and USB-ATA/SATA bridges work 100%. I will not upgrade to 9.10 as I have had problems with 9.10. I am waiting for the next LTS version before upgrading.

You can try this, but I don't think it will help much:
```
sudo update-usbids
```

---

