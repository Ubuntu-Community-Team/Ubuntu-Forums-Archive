---
title: "UnicastOnly on option in RADVD"
date: 2011-08-14
forum: General Help
---

### Post by spikersinc on 2011-08-14
Hi,

 I am trying to get my radvd server in ubuntu to send unicast only Router advertisements.I have a client which is sending a Router solicit to the radvd server and in the radvd.conf file i have enabled the "unicastonly on" option.

Without this option I am able to get it send a multicast RA. But when I turn on the unicastonly flag, it doesnt respond to any RS

Please Help!!!

here is the radvd.conf file:

---

