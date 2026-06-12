---
title: "Need udev to run a script every time a flash drive is connected"
date: 2009-08-18
forum: General Help
---

### Post by OEP on 2009-08-18
Hello!

I'm trying to get udev to scan flash drives for viruses (via a script I wrote) each time one is plugged in. The script just takes a mountpoint as an argument and it does the rest.

The big thing is how to I use either udev to look at every device that gets plugged in and mounted so it can scan them?

Udev may be the wrong approach and it might could be done through FUSE. But I guess that is why I'm asking here. :)

Any ideas on this one?

---

### Post by werru on 2009-09-01
try pmount
write rules and script... similar like this [http://muhas.ru/?p=94](http://muhas.ru/?p=94)

---

