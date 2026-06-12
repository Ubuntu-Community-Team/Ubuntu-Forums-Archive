---
title: "usb pendrive"
date: 2010-10-09
forum: General Help
---

### Post by haafmaad on 2010-10-09
recently when my gremeen phone modem was not working i solved that problem with this code

SUBSYSTEM=="usb",
ATTRS{idProduct}=="1446",
ATTRS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x$attr{idVendor} --product 0x$attr{idProduct} --type option-zerocd"

after that my modem is working but i cannot find my pendrive in the list

---

