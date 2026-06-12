---
title: "Remote control pc behind router"
date: 2010-03-14
forum: General Help
---

### Post by Naatan on 2010-03-14
Hi guys,

I am planning to install Ubuntu at my work to replace my Windows XP installation. However currently I can use RDP to connect to my work computer and the domain will automatically forward my connection seeing as my computer is not "directly" connected to the internet.

Is there any way I can get something similar working on Ubuntu? 

Essentially I want to connect to take remote control of a Ubuntu installation that is behind a router and I do not have access to the router.

Any ideas?

---

### Post by 2hot6ft2 on 2010-03-14
> **Naatan said:**
> However currently I can use RDP to connect to my work computer and the domain will automatically forward my connection seeing as my computer is not "directly" connected to the internet.
Does that mean there is a port forwarded to the pc behind the router?
If it does then you might consider checking out the SSH FreeNX how to in my sig. below.

The DD-WRT part is just about how to do port forwarding with DD-WRT on a router so if you already have a port forward in place it should be just a matter of setting everything up to that port.

There's a screenshot of me using FreeNX to remote desktop and transferring a file at the same time using nautilus at the bottom of the how to.

---

### Post by Naatan on 2010-03-14
No, as said I have no access to the router so I cannot configure a port to be forwarded.

I could probably get it done but I'd prefer not to.

Thanks for the response though :)

---

### Post by dcstar on 2010-03-14
> **Naatan said:**
> Hi guys,

I am planning to install Ubuntu at my work to replace my Windows XP installation. However currently I can use RDP to connect to my work computer and the domain will automatically forward my connection seeing as my computer is not "directly" connected to the internet.

Is there any way I can get something similar working on Ubuntu? 

Essentially I want to connect to take remote control of a Ubuntu installation that is behind a router and I do not have access to the router.

Any ideas?

If the router is only set up to forward RDP then you may be out of luck - especially if there is something else set up to make the connection.

Talk to the people who manage your work network and find out what they can do for you.

---

