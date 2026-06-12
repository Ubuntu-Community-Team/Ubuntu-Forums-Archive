---
title: "usbserial hangs on modprobe"
date: 2010-11-04
forum: General Help
---

### Post by torrent99 on 2010-11-04
Hi,

I recently upgraded my nvidia driver, and now the usbserial module won't install.

A modprobe usbserial just hangs and can't be exited.

modprobe usbserial debug=1 

gives the following in dmesg:

usbcore: registered new interface driver usbserial
[  109.761360] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the open usb serial operation with the generic one.
[  109.761369] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the write usb serial operation with the generic one.
[  109.761377] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the close usb serial operation with the generic one.
[  109.761386] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the write_room usb serial operation with the generic one.
[  109.761395] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the chars_in_buffer usb serial operation with the generic one.
[  109.761403] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the read_bulk_callback usb serial operation with the generic one.
[  109.761412] /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c: Had to override the write_bulk_callback usb serial operation with the generic one.
[  109.763765] USB Serial support registered for generic


This is on Lucid with the default kernel (32 bit)

Can anyone help me debug this please?

Cheers

Steve

---

