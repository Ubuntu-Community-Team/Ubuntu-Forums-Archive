---
title: "udev rules: Change permissions for a usb device"
date: 2012-04-30
forum: General Help
---

### Post by ufuser01 on 2012-04-30
Hi,

I have a usb device, with the file attributes 0664, and I intend to change the permissions of this device to 0777 whenever it is inserted. Could someone point me out the right way to do this using udev rules?

I tried this:


```
BUS="usb", ATTRS{idVendor}=="26da" , ATTRS{idProduct}=="000b", MODE="0777"
```

```
SYSFS{idVendor}=="26da" , SYSFS{idProduct}=="000b", MODE="0777"
```Any suggestions?

Thanks.

---

