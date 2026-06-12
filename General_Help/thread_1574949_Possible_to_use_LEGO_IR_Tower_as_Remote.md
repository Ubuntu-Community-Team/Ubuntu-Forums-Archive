---
title: "Possible to use LEGO IR Tower as Remote?"
date: 2010-09-15
forum: General Help
---

### Post by xXxBlender3DxXx on 2010-09-15
I've been browsing around the internet, and have found no useful information. I want to be able to send commands to control my TV/DVD Player via my LEGO IR Tower (it is the same frequency that most TVs use).

I have only gotten it to broadcast messages via NQC, but only formatted as RCX packets:
```
nqc -remote 748B 1
```.

I have tried using LIRC, but to no avail. It is exactly what I need, but I can't get irsend to work:
```
sudo irsend -d /dev/usb/lego0 SEND_ONCE 0x748B
irsend: could not connect to socket
irsend: Connection refused
```

I am quite confused. Anybody have a similar project that worked?

Thanks!

---

