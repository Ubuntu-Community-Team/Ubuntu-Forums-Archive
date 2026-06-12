---
title: "Looking for routing/bridging suggestions"
date: 2006-06-06
forum: General Help
---

### Post by mooch on 2006-06-06
I just broke down and bought an xbox360 and I would like to hook it up to my network. Unfortunately, I am waaaaay too cheap to buy the wireless adaptor for $100, so I am looking to use my bedroom ubuntu machine to route the ethernet connection from the xbox onto my wireless network.

Ubuntu box has 2 interfaces, wlan0 and eth0. Now, I know I could always just NAT the ethernet interface to the wireless, but I would like to avoid this, as I already have a NAT on the network and I would like to avoid double NATting the xbox, as I'm not sure what kind of port requirements exist for its games.

That said, I am looking for opinions/ideas on the best way to deal with this. I was thinking I could either bridge the two interfaces or set up some routing between them. I was also wondering if anyone knew of some voodoo to perhaps create a wlan:0 with the same ip as assigned to the xbox that would just forward the xbox packets onto the wireless network.

Any thoughts or suggestions are appreciated!

---

