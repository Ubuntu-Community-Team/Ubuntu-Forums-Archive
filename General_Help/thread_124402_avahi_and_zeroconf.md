---
title: "avahi and zeroconf"
date: 2006-02-01
forum: General Help
---

### Post by tikal26 on 2006-02-01
Hi I just upgraded to kde 3.5.1 and I noticed that it automtically install avahi, but I remember that J ridell had said that kubuntu was going to have zeroconf now . I am about to intall kubuntu on my computer and was wondering if they are the same thing and how you enable them.
any hlep is apreciated.

---

### Post by geearf on 2006-02-01
interested in the answer.

---

### Post by Sokraates on 2006-02-02
They are **not** the same thing and both will be installed.

AFAI understand, one is for detecting newly connected services or devices, the other for automatically assigning IP-adresses, so that connected devices can communicate with each other.

For further info (and maybe the real answers) take a look at [http://avahi.org](http://avahi.org) and [http://www.zeroconf.org](http://www.zeroconf.org) .

In my case I removed both, after avahi failed to initiallize at startup and zeroconf automatically assigned an IP to my NIC, which has a static IP assigned to connect to the internet.

---

