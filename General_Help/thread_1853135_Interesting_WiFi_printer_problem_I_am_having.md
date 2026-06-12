---
title: "Interesting WiFi printer problem I am having"
date: 2011-10-01
forum: General Help
---

### Post by cptrohn on 2011-10-01
I have an HP J4680 WiFi All-in-one printer...  I am connecting it to a cradlepoint ctr35 mobile broadband router that is using WPA2 authentication...   DHCP is enabled and it is handing out the right IP addresses to everything else on the network,  I have a few Wireless clients connected (the router can handle up to 14 clients in the documentation) but it is handing out the printers IP address on a seperate network, almost like it is setting it up on a VLAN or something crazy...  SO I can't connect to the printer in Linux, Windows or anything else since it is coming back that it's on a seperate network than my own wireless/wired network....  So in the routers Client list I can see the printers MAC address, some connection information etc... but no hostname or IP address for the client.

Any ideas?  Is there a way I can assign the printer a static IP address in Ubuntu that anybody knows of?

---

### Post by cptrohn on 2011-10-01
I am wondering if the printer can't support AES?  thoughts?

---

### Post by cptrohn on 2011-10-01
Yep, had to assign it a static IP address for it to work.... at least it's working though.. lol

---

