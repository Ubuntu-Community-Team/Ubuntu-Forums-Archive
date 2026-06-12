---
title: "PCI-Express Device Error"
date: 2010-06-09
forum: General Help
---

### Post by cherva on 2010-06-09
My dmesg is full of this messages:
```
[   31.571682] +------ PCI-Express Device Error ------+
[   31.571684] Error Severity		: Uncorrected (Non-Fatal)
[   31.571686] PCIE Bus Error type	: Transaction Layer
[   31.571688] Flow Control Protocol 	: First
[   31.571689] Receiver ID		: 0010
[   31.571692] VendorID=1106h, DeviceID=a238h, Bus=00h, Device=02h, Function=00h
[   31.571694] pcieport-driver 0000:00:02.0: broadcast error_detected message
[   31.571696] pcieport-driver 0000:00:02.0: broadcast mmio_enabled message
[   31.571699] pcieport-driver 0000:00:02.0: broadcast resume message
[   31.571705] pcieport-driver 0000:00:02.0: AER driver successfully recovered
```
Can someone explain this to me :confused:

---

### Post by dino99 on 2010-06-09
you may have more than ones, some conflicts somewhere

sudo update-pciids && update-usbids

i've seen these kind of error (AER) on my system with kernel 32 family, if you cant work with these errors, install kernel 34

---

### Post by cherva on 2010-06-09
Hmmm...
```
cherva@mitosoft:~/Desktop$ sudo update-pciids && update-usbids
[sudo] password for cherva: 
Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

```

---

