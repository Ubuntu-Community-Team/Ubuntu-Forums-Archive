---
title: "What tty my USB device is on"
date: 2011-09-08
forum: General Help
---

### Post by mrmoreland on 2011-09-08
Hi There,
 
Wondering if some one can help me....
 
I am trying to find out what tty my usb device is detected on so I can configure it to be used as a modem.
 
I dont believe by device is on ttyUSB0
 
I have searched how to do this but to no avail...
 
Many thanks,
 
Ian

---

### Post by Beacon11 on 2011-09-08
Right after you plug your device in, run the following command:

```
dmesg
```

Near the bottom of the output you should see some messages saying something along the lines of "Oh look, a new USB device was plugged in. I'm loading it as /dev/ttyUSB0."

---

