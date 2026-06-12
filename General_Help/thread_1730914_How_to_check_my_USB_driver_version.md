---
title: "How to check my USB driver version?"
date: 2011-04-16
forum: General Help
---

### Post by jiapei100 on 2011-04-16
Hi, all:

I can see my USB devices by ```
lspci
```, 

> 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)


However, the speed I copied from one USB device to anther (both are USB 2.0 ) is around 4.4M/second, which seems to be very slow. I'm wondering if the USB driver is not powerful enough. By the way, I'm using Ubuntu 10.10 .

Can anybody give me a hint?

Best Regards
JIA

---

### Post by Ad@m on 2011-04-16
The speed will also depend on the USB device, if it has slow read/write speeds expect slow speeds.

What are the devices?

---

