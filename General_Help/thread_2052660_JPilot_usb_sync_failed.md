---
title: "JPilot usb: sync failed"
date: 2012-09-03
forum: General Help
---

### Post by aspi12 on 2012-09-03
With my old Notebook I synced my palm pilot with jpilot (usb:) under Ubuntu 12.04 succesful. My old notebook crashed and my new notebook have the same configuration  (Ubuntu 12.04, JPilot 1.8 ) but the JPilot becomes no connection to the palm.

This is output of syslog:

```
Sep  2 21:36:07 xian kernel: [  132.693911] usb 2-1.2: USB disconnect, device number 4 Sep  2 21:39:54 xian kernel: [  359.668588] usb 2-1.2: new full-speed USB device number 5 using ehci_hcd Sep  2 21:39:54 xian mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2" Sep  2 21:39:54 xian mtp-probe: bus: 2, device: 5 was not an MTP device
```

Its a usb serial device. Maybe I need additional software for usb to serial drivers?
Have anybody an idea?

---

### Post by aspi12 on 2012-09-10
> **aspi12 said:**
> With my old Notebook I synced my palm pilot with jpilot (usb:) under Ubuntu 12.04 succesful. My old notebook crashed and my new notebook have the same configuration  (Ubuntu 12.04, JPilot 1.8 ) but the JPilot becomes no connection to the palm.

This is output of syslog:

```
Sep  2 21:36:07 xian kernel: [  132.693911] usb 2-1.2: USB disconnect, device number 4 Sep  2 21:39:54 xian kernel: [  359.668588] usb 2-1.2: new full-speed USB device number 5 using ehci_hcd Sep  2 21:39:54 xian mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2" Sep  2 21:39:54 xian mtp-probe: bus: 2, device: 5 was not an MTP device
```Its a usb serial device. Maybe I need additional software for usb to serial drivers?
Have anybody an idea?

solution is: add the own user to group dialup

---

