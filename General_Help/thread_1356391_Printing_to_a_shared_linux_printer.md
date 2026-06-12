---
title: "Printing to a shared linux printer"
date: 2009-12-16
forum: General Help
---

### Post by Chris H on 2009-12-16
Desktop running Ubuntu, laptop running Zenwalk, both connecting wirelessly to the same router.

Ubuntu on desktop has a printer connected via usb which is set to shared as per the cups admin page.

Laptop can autodiscover printer using the cups admin page but it can't print to it.

Doing a 'print test page' from cups gives this error.


> Unable to connect 

Firefox can't establish a connection to the server at 192.168.1.5:631.

* The site could be temporarily unavailable or too busy. Try again in a few moments.
* If you are unable to load any pages, check your computer's network connection.
* If your computer or network is protected by a firewall or proxy, make sure that Iceweasel is permitted to access the Web.


I can ping from the laptop to the desktop as well, no problems there.

Any ideas?

Ta.

---

### Post by Chris H on 2009-12-16
Some more information.

Desktop Ubuntu ip 192.168.1.5

Laptop Zenwalk ip 192.168.1.4

I can access the cups gui on the laptop by putting [http://192.168.1.4:631](http://192.168.1.4:631) into the browser from the destop.

However, if I try and access the cups gui from the laptop by putting [http://192.168.1.5:631](http://192.168.1.5:631) then I get no connection.

Any ideas?

---

