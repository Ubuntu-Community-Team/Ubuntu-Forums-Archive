---
title: "how to add a new service that's not in Service Settings list"
date: 2006-03-10
forum: General Help
---

### Post by mgreen on 2006-03-10
hi all,

I just installed ubuntu and I'm impressed so far (i gave-up using linux as a desktop os 4 years ago).

I want to add mysqld as a service but it's not available in the list (although it's in /etc/init.d, and I don't see the option to add a new service in Service Settings. Furthermore, the screenshots in Help depict a Service Settings with far more advanced featured than mine (Breezy). What's up with that? Where does Service Settings pull its list of services from? 

Thanks!

---

### Post by Sendervictorius on 2006-03-10
You can do it from the command line, but it is easier to use Boot-Up Manager.  Install bum (Boot-up manager) from synaptic.

Boot-Up Manager is a graphical tool to allow easy configuration
of init services in user and system runlevels, as far as changing
Start/Stop services priority.

---

### Post by mgreen on 2006-03-10
Thanks for your help! BUM does the job.

Anyone know why Service Settings is used in place of the seemingly superior BUM?

---

