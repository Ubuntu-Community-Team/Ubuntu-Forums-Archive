---
title: "Lucid + UPS + nut = Operation not permitted"
date: 2010-04-29
forum: General Help
---

### Post by ilna on 2010-04-29
After upgrading to Lucid I have:

```
$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.4.3
Network UPS Tools - Generic HID driver 0.34 (2.4.3)
USB communication driver 0.31
Using subdriver: CyberPower HID 0.3
libusb_get_report: error sending control message: Operation not permitted
Can't initialize data from HID UPS
Driver failed to start (exit status=1)
```

Where to dig in?

---

### Post by ilna on 2010-04-30
Ok, [https://bugs.launchpad.net/ubuntu/+source/nut/+bug/572262](https://bugs.launchpad.net/ubuntu/+source/nut/+bug/572262) is reported

---

