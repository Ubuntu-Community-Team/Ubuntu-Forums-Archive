---
title: "Is there a way to have Firestarter Autolaunch after via dialup"
date: 2005-02-05
forum: General Help
---

### Post by Nexxus6 on 2005-02-05
I would like to have firestarter automaticly launch after I initiate a dialup connection.  I use modem lights to connect and it does a pon command.  This is not even a problem for most people but I am stuck on dialup and the manual of firestarter says to start the firewall after you connect on dialup. Otherwise I get a nice error message when firestarters starts that says ppp0 is not ready. The manual says to use the kppp dialer.  Is this necessary or can I accomplish this another way?  Is there some script file I can edit to launch firestarter once a connection is made?  I am a Linux NEWBIE so be easy on me.

---

### Post by az on 2005-02-05
Look in 
/etc/ppp/ip-up.d.  Whatever is there is executed after the ppp conection is up.


do
man pppd



kppp is krappp.

---

