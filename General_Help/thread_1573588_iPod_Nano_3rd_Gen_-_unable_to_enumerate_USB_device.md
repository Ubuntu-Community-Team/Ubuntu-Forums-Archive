---
title: "iPod Nano 3rd Gen - unable to enumerate USB device"
date: 2010-09-12
forum: General Help
---

### Post by element on 2010-09-12
I have a iPod Nano 3rd Generation and cant seem to mount it.  I am getting these messages.  Anyone seen this or know of a fix?
Im using 9.10.
Thanks


```
element@element:~$ dmesg | tail
[46509.208295] usb 6-2: device descriptor read/64, error -71
[46509.432118] usb 6-2: device descriptor read/64, error -71
[46509.648176] usb 6-2: new full speed USB device using uhci_hcd and address 15
[46509.768305] usb 6-2: device descriptor read/64, error -71
[46509.993278] usb 6-2: device descriptor read/64, error -71
[46510.209303] usb 6-2: new full speed USB device using uhci_hcd and address 16
[46510.624291] usb 6-2: device not accepting address 16, error -71
[46510.736307] usb 6-2: new full speed USB device using uhci_hcd and address 17
[46511.145105] usb 6-2: device not accepting address 17, error -71
[46511.145143] hub 6-0:1.0: unable to enumerate USB device on port 2

```

---

