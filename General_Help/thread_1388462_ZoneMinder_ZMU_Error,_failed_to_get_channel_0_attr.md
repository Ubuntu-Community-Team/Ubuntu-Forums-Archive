---
title: "ZoneMinder ZMU: Error, failed to get channel 0 attributes: Invalid argument"
date: 2010-01-23
forum: General Help
---

### Post by GCoffee on 2010-01-23
Hello,

I have a Sweex USB webcam which I am trying to setup with ZoneMinder, however I cannot find the settings for it, and when I run:

```
$ zmu -d /dev/video0 -q -v
```

I get:

```
Error, failed to get channel 0 attributes: Invalid argument

```

the device shows up as:

```
ID 0ac8:3343 Z-Star Microelectronics Corp. Sirius USB 2.0 Camera

```

in lsusb.

Can someone provide settings, or how to fix ZMU?

Thanks,
GC.

---

### Post by GCoffee on 2010-01-24
bump

Please help with this!

---

### Post by free-martin on 2010-01-25
have the same issue...

---

### Post by dunand on 2010-01-28
i have the same problem 9.10 64

```
zmu -d /dev/video0 -q -v
Error, failed to get channel 0 attributes: Invalid argument
```

lsusb
```
Bus 001 Device 003: ID 0ac8:3420 Z-Star Microelectronics Corp.
```

thanks

---

### Post by jtobe on 2010-02-06
I have the same problem. I picked up a 1.3mp Gear Head webcam.

lsusb:
```

user@ubuntu:~$ lsusb
Bus 001 Device 002: ID 0ac8:3420 Z-Star Microelectronics Corp.

```

The problem is awkward because some apps work fine and others choke. Skype and mplayer read from it in my tests. Camorama and zoneminder cannot.

---

### Post by rabbitear on 2011-08-04
Exactly the same error going on here :(

---

