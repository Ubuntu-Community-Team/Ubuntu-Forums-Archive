---
title: "Help debugging ethernet"
date: 2009-10-02
forum: General Help
---

### Post by stair314 on 2009-10-02
If someone could help me debug my ethernet connection, I'd greatly appreciate it.

I have a cable modem, connected to a switch. On the switch, I also have a MacBook running OS X and a desktop computer running Hardy. The MacBook connected to the internet with no intervention on my part, but Hardy is not able to do so.

From my MacBook, I can ping the desktop by it's IP. I can also ping it by calling it pygmalion.local (pygmalion is its hostname). From the desktop, I can ping the MacBook, but only using its IP, not using its hostname.

One thing that is weird is that the MacBook's IP and the desktop's IP don't have any fields in common. I thought they should have all but the last field in common. My MacBook does have the same first three fields of its IP the same as the router, as I would expect. The desktop doesn't report a router IP but if I ping the IP of the router reported by the MacBook, I can't reach it. Also, I can't ping any internet hosts like google, either by URL or IP.

If I run sudo /etc/init.d/network restart, the desktop sends out several DHCPDISCOVERs but never gets a DHCPOFFER. Switching to a static IP doesn't fix anything though.

Any ideas?

---

### Post by stair314 on 2009-10-02
Sorry, fixed by rebooting my cable modem. Now I feel stupid.

---

