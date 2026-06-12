---
title: "Disabling fingerprint reader"
date: 2012-05-25
forum: General Help
---

### Post by toaster2 on 2012-05-25
Hi, I have an Acer Travelmate 8471 and am wondering if it's possible to disable the fingerprint reader.  I don't use it and I  want to optimize my laptop's battery life.  I couldn't find any option in my BIOS to do so.  Is there a kernel module that I can disable/blacklist?  Thanks.

```
michael@COMPUTER:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 002 Device 002: ID 1c7a:0801 LighTuning Technology Inc. Fingerprint Reader
```

---

### Post by toaster2 on 2012-05-26
bump

---

### Post by PhantomTurtle on 2012-05-26
Maybe this might help - [http://basshero.org/blog/62/how-to-disable-devices-in-ubuntu]("http://basshero.org/blog/62/how-to-disable-devices-in-ubuntu"). Also you can only bump a thread every 24 hours.

EDIT: This also means that you have to remove that line from the blacklist.conf file to re-enable it.

---

