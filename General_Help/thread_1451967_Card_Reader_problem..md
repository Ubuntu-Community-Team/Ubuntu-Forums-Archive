---
title: "Card Reader problem."
date: 2010-04-11
forum: General Help
---

### Post by Steam. on 2010-04-11
I have this card reader, it works perfectly on Win7, but when i try to put my xD card in it whilst on Linux, it wont read it, nothing shows up in nautilus nor on the desktop.Any help?

If it's any use, it's an external, with a USB cable.

---

### Post by mhgsys on 2010-04-11
attach the usb card reader; 
open up a terminal and post output of

```
lsusb
```

also post the output of; 
```
tail -f /var/log/messages
``` 
when plugging in the usb card reader
 
That way we'll have a little info on the device

---

### Post by Steam. on 2010-04-12
Nevermind, needed to connect the device on bootup, now it works all the time.Sorry for your trouble.

---

