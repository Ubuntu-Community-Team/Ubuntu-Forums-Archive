---
title: "No DHCP after update"
date: 2006-03-17
forum: General Help
---

### Post by dystrust on 2006-03-17
I updated Breezy yesterday and now eth0 is no longer able to obtain an IP address.  This seems to be related to dhcp3-client and dhcp3-common being updated.  Is there any way to roll these back to the previous version?

---

### Post by dystrust on 2006-03-17
I have also tried to assign my own IP address, and while I can ping other computers on the network, Internet still does not work.

---

### Post by dystrust on 2006-03-17
Figured it out.  The DHCP utilities updated in the wrong order, so the client didn't configure.

---

