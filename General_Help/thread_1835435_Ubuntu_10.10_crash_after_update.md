---
title: "Ubuntu 10.10 crash after update"
date: 2011-08-29
forum: General Help
---

### Post by pascal.schwartz on 2011-08-29
my ubunto would't start the GUI after update of the Ubuntu (from the application-update gui) it show only flickering white rectangle but not the GUI desktop.
i think that is the nvidia driver besuase when i purge the nvidia driver (apt-get purge nvidia*) the gui tries to start bu is stuck with the ubuntu logo with out any procgress.
 
when i try to reinstall the driver the orginal problem comes back ...
any advice 
Thanks

---

### Post by deserthowler on 2011-08-29
Is there a copy of xorg.conf installed with the driver that causes the system to attempt to start the driver?

I haven't had this problem myself but remember finding this on a friend's machine.  Just a thought.

Earl

---

