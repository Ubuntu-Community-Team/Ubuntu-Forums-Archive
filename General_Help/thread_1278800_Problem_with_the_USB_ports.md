---
title: "Problem with the USB ports"
date: 2009-09-30
forum: General Help
---

### Post by theskiziado on 2009-09-30
hi everyone

i have a problem with my usb ports
turns out that when i start my laptop it has no problems at all, but when i try to conncet any usb device, like my mouse or pendrive it doesn't happen anything, it doesn't mount my pendrive or the mouse works
but the weird part is that when i turn on my laptop with any usb device connected it recognize it right away
needless to say the inconvenience of this situation

so if anyone can help me with this problem
i would really appreciate it

---

### Post by KeyserSoze93 on 2009-09-30
you could try restarting udev (after having plugged your device in):
```
sudo /etc/init.d/udev restart
```

This might make it re-evaluate the devices connected to the system and make the proper entries for them.

Could you also post the output of:
```
lsusb
```

---

### Post by Giblet5 on 2009-09-30
It could also be the HAL daemon not running...

```
ps -ef | grep hald
```

should show (at least) /usr/sbin/hald as running.

If not, ```
sudo /etc/init.d/hal restart
``` should start it. Then, we'll need to figure out why it isn't starting to begin with...

---

