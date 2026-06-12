---
title: "Switching bluetooth modes HID to HCI"
date: 2009-11-11
forum: General Help
---

### Post by |Porsche on 2009-11-11
Hello,
Does anybody know how to switch from HID mode to HCI mode? 
This is the output of my lsusb command:
```
Bus 002 Device 008: ID 046d:c70a Logitech, Inc. MX5000 Cordless Desktop
Bus 002 Device 007: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth Laser Mouse
Bus 002 Device 006: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 003: ID 04b4:120f Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Any ideas? Oh, and BTW when I do a hcitool dev it does not recognize it.

Thanks

---

### Post by niteshifter on 2009-11-11
Hi,

See if post 7 on [this page]("http://forums.logitech.com/t5/Keyboards-Bluetooth/How-to-use-a-Logitech-BT-Mini-Receiver-as-a-BT-dongle/m-p/768") (forums.logitech.com) works.

---

### Post by |Porsche on 2009-11-11
> **niteshifter said:**
> Hi,

See if post 7 on [this page]("http://forums.logitech.com/t5/Keyboards-Bluetooth/How-to-use-a-Logitech-BT-Mini-Receiver-as-a-BT-dongle/m-p/768") (forums.logitech.com) works.

GENIUS!! Thanks a lot. Sure enough it worked. You have to:
1. Remove dongle.
2. Press red dot.
3. Insert dongle while the red dot is pressed and hold it down for a few seconds.

lsusb output:
```
Bus 002 Device 028: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 002 Device 027: ID 046d:0b02 Logitech, Inc. BT Mini-Receiver (HID proxy mode)
Bus 002 Device 003: ID 04b4:120f Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

