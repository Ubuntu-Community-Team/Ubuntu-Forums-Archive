---
title: "usbserial instead of cdc_acm"
date: 2012-06-14
forum: General Help
---

### Post by Dtag on 2012-06-14
Hi,

In recent Ubuntu Versions I am having trouble communicating with a serial device (connected via usb) which is recognized by the cdc_acm kernel module (it results in /dev/ttyACM0). The device works, but when reconnecting to the port, it sometimes does not respond anymore.

When i use the usbserial module instead, by doing
sudo rmmod cdc_acm
sudo modprobe usbserial vendor=myvendorid product=myproductid

I get a ttyUSB0 device which works fine.

My question is how I can automatically make linux use usbserial instead of cdc_acm. Is that possible using udev rules?

Thanks!

---

