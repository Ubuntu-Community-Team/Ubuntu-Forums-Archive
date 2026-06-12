---
title: "lcdproc v0.5.3 - ConnectionType=ftdi not being recognized"
date: 2010-10-20
forum: General Help
---

### Post by MacUsers on 2010-10-20
Hi there,

I just apt-get installed lcdproc, which essentially installed v0.5.3 but if I use 
***ConnectionType=ftdi*** for **hd44780**, I get unknown connection error:
```
Server running in foreground
Listening for queries on 127.0.0.1:13666
screenlist_init()
driver_load(name="hd44780", filename="/usr/lib/lcdproc/hd44780.so")
hd44780: unknown ConnectionType: ftdi
Driver [hd44780] init failed, return code -1
Module /usr/lib/lcdproc/hd44780.so could not be loaded
Could not load driver hd44780
There is no output driver
Critical error while initializing, abort.
```Does any one know what am I missing? Thanks in advance for your help. Cheers!!

---

