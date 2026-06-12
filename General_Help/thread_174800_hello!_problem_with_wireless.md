---
title: "hello! problem with wireless"
date: 2006-05-12
forum: General Help
---

### Post by Ercole on 2006-05-12
hi to everyone I'm a new member. 
I've just installed ubuntu for the first time. 
very nice :) 
everythigs is working except for my my wireless lan card PCI   ](*,)  .
it's a sparklan wireless card wl-660. 
anyone know how to configure it or where I can find the driver?

thanks a lot.

bye 

Ercole

---

### Post by ltmon on 2006-05-12
Hi There,

See if you can find out about your wireless card by following the instructions at: [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards).  It might give you some starting hints for getting it up and running.  Also see: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide). 

I suspect you will have to use "ndiswrapper" to get it working.  ndiswrapper is a special driver which "wraps" your ordinary windows drivers for use on Linux.  You can find information about it on the wiki, here in the forums and on the ndiswrapper website.

Good luck, and post back again if you get stuck,

L.

---

