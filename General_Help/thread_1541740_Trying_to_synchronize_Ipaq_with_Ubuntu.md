---
title: "Trying to synchronize Ipaq with Ubuntu"
date: 2010-07-29
forum: General Help
---

### Post by arashiko28 on 2010-07-29
OOK... I know support is almost nule, but I have ran the mile with this and I'm getting closer to it.

Before I could not even get to identify the Ipaq on the usb port. Now, after blacklisting ipaq I got this:

> ~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 006 Device 002: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC[/COLOR]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b105 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


But still can't see it on the computer nor in media folder, what goes next?
I also installed activesync trhough wine, but still no success on actively detecting the device.

---

### Post by Joe of loath on 2010-07-29
You'll need to install synce. The best guides are on their website.

---

