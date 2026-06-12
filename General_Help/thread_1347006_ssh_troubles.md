---
title: "ssh troubles"
date: 2009-12-05
forum: General Help
---

### Post by ubudog on 2009-12-05
Hi, I have a desktop and a laptop.  I need to be able to ssh into the desktop from my laptop.  It appears that my router has given my laptop and desktop the same ip address.  Any ideas?

---

### Post by whitethorn on 2009-12-05
have you tried setting a static IP on your desktop?

---

### Post by The Cog on 2009-12-05
That shouldn't happen. Try running this command on both machines:
**sudo dhclient**
and see if they get allocated different addresses this time.

If you are going to be using ssh between them on a regular basis, it would be better if they always had the same address. Either configure static addresses on the machines, or most routers can be configured to always allocate a particular IP address to a particular MAC address (which always stays with the same machine).

---

