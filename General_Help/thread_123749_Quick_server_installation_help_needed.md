---
title: "Quick server installation help needed"
date: 2006-01-30
forum: General Help
---

### Post by mykrob on 2006-01-30
Hello-
i just installed a server installation of Ubuntu 5.10 on a laptop. It has a belkin wireless network card installed, and it works fine when Gnome on a full blown ubuntu distribution. ra0 is its interface name. 

How do i configure/activate this card in server mode? I triend sudo ifup ra0, and it complains that the card is not configured, so how do i configure it? I have several packages i need to add thru apt, but i need the network up and running.

Thanks,
-myk

---

### Post by mykrob on 2006-01-30
nevermind, found it

dhclient ra0

---

