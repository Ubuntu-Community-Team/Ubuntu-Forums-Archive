---
title: "Can you configure udev to use different port?"
date: 2011-03-01
forum: General Help
---

### Post by steviefordi on 2011-03-01
I have a 3g modem that is functioning ok but not perfectly. Udev sets up 3 devive nodes: /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2.

According to dmesg, all three of these are modem ports - however the driver - for whatever reason - uses /dev/ttyUSB2 as the modem.

Is it possible to configure udev and/or the "option" driver to try out the other two ports and see if this fixes my problems?

---

