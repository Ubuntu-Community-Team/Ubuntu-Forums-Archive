---
title: "software for usb capture card"
date: 2011-11-27
forum: General Help
---

### Post by WinterMadness on 2011-11-27
Kino does not seem to recognize usb capture cards from my research, any other suggestions?

---

### Post by WinterMadness on 2011-11-27
anyone

---

### Post by oldos2er on 2011-11-27
What make/model is it? Does **lsusb** see it?

---

### Post by WinterMadness on 2011-12-04
honestech VHS to DVD&#8482; 5.0 Deluxe 

its marketed towards vhs to dvd conversion, but its really just a piece of hardware that takes in RCA cables and lets you record it on your pc.

I did lsusb and it does show up:
(the second lsusb is to see what doesnt show up after disconnecting it)
```
joe@joe-U46:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 
Bus 002 Device 003: ID eb1a:5006 eMPIA Technology, Inc. 
joe@joe-U46:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 

```

---

### Post by WinterMadness on 2011-12-05
anyone

---

