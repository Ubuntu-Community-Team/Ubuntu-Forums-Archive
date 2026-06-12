---
title: "LAN Side (masqueraded) interface doesn't come up."
date: 2011-09-18
forum: General Help
---

### Post by AlexBooton on 2011-09-18
Very odd.

It seems if you don't have a client PC on the LAN side ethernet port at startup; dhcpd fails.

I'm using the isc-dhcp-server 4.1.1-P15ubuntu9.1 package.  Is that the correct/preferred package?

If a client is on the port at startup, it seems to start correctly; but if the port is empty (unused) it fails.

Any way to fix this odd behaviour?

Thanks

---

### Post by dcstar on 2011-09-19
> **AlexBooton said:**
> Very odd.

It seems if you don't have a client PC on the LAN side ethernet port at startup; dhcpd fails.

I'm using the isc-dhcp-server 4.1.1-P15ubuntu9.1 package.  Is that the correct/preferred package?

If a client is on the port at startup, it seems to start correctly; but if the port is empty (unused) it fails.

Any way to fix this odd behaviour?

Thanks

Plug in an Ethernet switch so the port is actually in use. That is the way 99.99% of systems supplying DHCP expect to work.

---

### Post by AlexBooton on 2011-09-19
> **dcstar said:**
> Plug in an Ethernet switch so the port is actually in use. That is the way 99.99% of systems supplying DHCP expect to work.

Thanks,  That what I did eventually; but it was frustrating till I stumbled upon that "solution".

And, to make matters worse, I'll probably forget by the time I need to set up a new system.  ;)

---

