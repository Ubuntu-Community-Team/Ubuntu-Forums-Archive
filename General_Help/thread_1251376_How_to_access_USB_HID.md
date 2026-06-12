---
title: "How to access USB HID"
date: 2009-08-27
forum: General Help
---

### Post by PeEllAvaj on 2009-08-27
In addition to my normal USB mouse & Keyboard, I am trying to connect a USB IR receiver that is supposed to act as an HID.

Here is what dmesg is reporting:
1377449.692027] usb 2-10: new full speed USB device using ohci_hcd and address 18
[1377449.914369] usb 2-10: configuration #1 chosen from 1 choice
[1377449.929396] generic-usb 0003:04D8:FEB4.000B: hiddev98,hidraw3: USB HID v1.11 Device [Microchip Technology Inc. HID Receiver] on usb-0000:00:02.0-10/input0

I was able to cat some random bytes out of the IR receiver by catting /dev/usb/hiddev2, but I was expecting the input to come through as it would if it were typed in a keyboard.

Anyone know what I'm doing wrong to get it to work like a USB keyboard, or are my assumptions wrong?

Thanks in advance!

---

