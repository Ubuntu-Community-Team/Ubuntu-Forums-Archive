---
title: "Mounting mp3 player in Ubuntu"
date: 2011-08-08
forum: General Help
---

### Post by Donnie Love on 2011-08-08
I'm trying to mount an Ematic mp3 player through USB to Ubuntu 11.04, but it's not showing up. Any suggestions?

---

### Post by TeoBigusGeekus on 2011-08-08
Is the device recognised at all?
Post us the output of
```
lsusb
```
before and after you plug it in.

---

### Post by Donnie Love on 2011-08-08
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 12d1:1035 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It's plugged in now

---

### Post by TeoBigusGeekus on 2011-08-08
Post us the output when you take it out as well.

---

### Post by Donnie Love on 2011-08-08
Same with it unplugged.

---

### Post by TeoBigusGeekus on 2011-08-08
It seems that the device isn't recognised at all at the specific usb port.
Try with another usb port; if you still get the same output, then there's nothing much you can do.

---

### Post by Donnie Love on 2011-08-08
That sucks.
Thanks anyway.

---

### Post by sinbowden on 2011-08-08
not sure if this will help but its worth a shot. 

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

also try booting to recovery mode wait for boot then look for somthing like repair missing or broken files. worked for me.

---

