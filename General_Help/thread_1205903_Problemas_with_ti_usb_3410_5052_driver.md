---
title: "Problemas with ti_usb_3410_5052 driver"
date: 2009-07-06
forum: General Help
---

### Post by amoya on 2009-07-06
Hello,

I'm using Ubuntu 9.04 and when i plug the TIUSB3410 on the usb port i get this dmesg:

[COLOR=Blue][ 3909.028057] usb 2-2: new full speed USB device using uhci_hcd and address 5
[ 3909.235941] usb 2-2: configuration #1 chosen from 1 choice
[ 3909.281609] cdc_acm 2-2:1.0: This device cannot do calls on its own. It is no modem.
[ 3909.281636] ti_usb_3410_5052 2-2:1.0: TI USB 3410 1 port adapter converter detected
[ 3909.281651] usb 2-2: firmware: requesting &#65533;&#65533;&#65533;&#65533;
[ 3909.305834] usb 2-2: firmware: requesting ti_3410.fw
[ 3910.317852] usb 2-2: ti_download_firmware - error downloading firmware, -110
[ 3910.317887] ti_usb_3410_5052: probe of 2-2:1.0 failed with error -5
[ 3920.385143] /build/buildd/linux-2.6.28/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[ 3920.385198] generic-usb 0003:0451:F432.0004: timeout initializing reports
[ 3920.389156] generic-usb 0003:0451:F432.0004: hiddev96,hidraw1: USB HID v1.01 Device [Texas Instruments Texas Instruments MSP-FET430UIF] on usb-0000:00:1d.0-2/input1[/COLOR]

[COLOR=Black]there's a fail in download firmware...I have the firmware in /lib/firmware and /lib/firmware/(uname -r) with the name ti_3410.fw. I don't know why is requesting this and don't find the firmware.
Any help in this?
Thank you in advance.

Aldo
[/COLOR]

---

