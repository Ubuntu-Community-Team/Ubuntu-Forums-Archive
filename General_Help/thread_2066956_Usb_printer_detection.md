---
title: "Usb printer detection"
date: 2012-10-05
forum: General Help
---

### Post by gregorg on 2012-10-05
Hi!
I have an Ubuntu 12.04 64bit fresh install from minimal instalation disk without any desktop (I am using it as a server).
I am trying to install my HP G55 OfficeJet printer, or rather to make it work.
I've cups instaled and hplip 3.12.9
The printer does not work. It fails with "/usr/lib/cups/backend/hp failed"
Something weird is happening though. If I run 
```
lsusb
``` 
I can see the printer

```
Bus 003 Device 006: ID 03f0:0011 Hewlett-Packard OfficeJet G55
```

However if I run 

```
hp-probe -busb
```

this is what I get

```
warning: No devices found on the 'usb' bus. If this isn't the result you are expecting, 
warning: check to make sure your devices are properly connected and powered on.
```

Any idea on how to debug this? I've been googling for two days bud got nothing usefull.
Thanks for any reply!

---

### Post by Optimus72 on 2013-03-17
I'm having exactly the same problem. No help from anyone?

---

### Post by gifford on 2013-03-17
I don't use a HP printer but found the following regarding this particular one.
[https://answers.launchpad.net/hplip/+question/209551](https://answers.launchpad.net/hplip/+question/209551)

Hope it solves the problem.

---

