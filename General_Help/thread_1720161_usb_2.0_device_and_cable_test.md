---
title: "usb 2.0 device and cable test?"
date: 2011-04-02
forum: General Help
---

### Post by sdowney717 on 2011-04-02
I would like to know as you see in windows, when you plug in a device it tells you some thing whether it is 2.0 or not.

Is there a way to tell if the usb extension cable is 2.0 compatible?
How about the usb device itself?

---

### Post by dragonfly41 on 2011-04-03
I've started using the commands

```
sudo lsusb
```

and

```
sudo dmesg | tail -n 20
```

which I picked up from here ..

[http://www.linux-usb.org](http://www.linux-usb.org)

---

