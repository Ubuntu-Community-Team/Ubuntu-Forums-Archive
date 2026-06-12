---
title: "External HD (reiserfs) won't automount in Lucid"
date: 2010-09-18
forum: General Help
---

### Post by HangukMiguk on 2010-09-18
My external HD where everything I backed up from my previous install will not mount.  It shows up in lsusb, but when I do dmesg:

```
[20801.408614] usb 1-3: USB disconnect, address 36
[20804.190095] usb 1-3: new high speed USB device using ehci_hcd and address 38
[20804.343675] usb 1-3: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[20804.345100] usb 1-3: configuration #1 chosen from 1 choice

```

Anyone know what is going on?  Need more information.

Also of note, my main filesystem is reiserfs, so there isn't a problem of not having reiser installed.

---

### Post by HangukMiguk on 2010-09-18
Bump.

---

### Post by HangukMiguk on 2010-09-19
bump

---

