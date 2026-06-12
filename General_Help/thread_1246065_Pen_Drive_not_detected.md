---
title: "Pen Drive not detected"
date: 2009-08-21
forum: General Help
---

### Post by ashwinhgtx on 2009-08-21
A 2GB pendrive of a friend is not being detected in Jaunty. It doesn't even show up in GParted.
Here's the dmesg|tail output:
```
ashwin@TWINTURBOV8Mint7 ~ $ dmesg|tail
[316654.944094] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316655.321064] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316655.696118] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316656.080036] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316656.452088] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316656.828104] usb 1-2: reset high speed USB device using ehci_hcd and address 14
[316656.960878] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[316656.960889] end_request: I/O error, dev sdb, sector 0
[316656.960898] Buffer I/O error on device sdb, logical block 0
[316783.407666] [drm:i915_getparam] *ERROR* Unknown parameter 6

```

Is this a hardware problem? Or is due to some error in Jaunty?

---

