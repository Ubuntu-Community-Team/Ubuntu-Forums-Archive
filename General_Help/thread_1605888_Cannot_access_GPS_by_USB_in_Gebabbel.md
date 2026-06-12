---
title: "Cannot access GPS by USB in Gebabbel"
date: 2010-10-25
forum: General Help
---

### Post by grantk86 on 2010-10-25
I'm trying to connect my Garmin Venture HC via USB and download/upload points thru Gebabbel. When the program tries to connect, I get an error message; "Claim interfaced failed: could not claim interface 0: Operation not permitted".

The GPS shows up when plugged in in dmesg and lsusb, however I cannot access it. It has worked fine in previous versions of Ubuntu.

If I run the program as root I am able to connect and download points, however this is not a suitable solution. Is there a way to give my user account access permissions for the GPS device?

---

### Post by jeremybrown on 2011-07-05
I was able to use gebabbel with my Garmin GPS in Ubuntu 11.04 by invoking it with sudo gebabbel.  Hopefully this will work for you too.

---

