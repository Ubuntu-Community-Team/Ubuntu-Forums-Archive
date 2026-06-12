---
title: "advice wanted- ssl vpn , router to router"
date: 2010-07-07
forum: General Help
---

### Post by glen99 on 2010-07-07
hello 
ive a couple of draytek 2910s linked to eached other - providing an ipsec vpn link, i chose this option because they were relativly cheap, and my knowledge of linux being limited, quite easy to configure
they work fine here in london, but installing one abroad recently it doesnt work, and almost thinking it may be an isp issue.
going down the ssl vpn 443 route is an option im considering, 
again id like a tunnel which is reliable, and can send voip over to the other router , out of that and onto a sip phone/asterisk box .
on my draytek setup- the vpn is always on, which is a facility id like with the ssl tunnel.
can someone advise me if installing a router to router ssl vpn using wrt-dd is both pratical and relaible..or besides using sonicwall routers, can anyone advise of a router that offers the facilities of the draytec vpn- but using ssl instead?

---

### Post by btindie on 2010-07-07
What's the problem with the Draytek router when it's used abroad? Does it get an internet connection? Does it get a public routable IP address? Which way is the ipsec connection initiated? London -> abroad or the other way around??
If the ipsec vpn doesn't work then chances are that the ssl vpn may not work.

---

