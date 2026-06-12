---
title: "Does host system firewall get used with VirtualBox?"
date: 2010-03-03
forum: General Help
---

### Post by KayakJim on 2010-03-03
I have an Ubuntu 9.04 system with a firewall configured to only allow access from certain IP's.

I would like to install VirtualBox to run multiple OS's for testing.

I would like to know if incoming connections for the virtualized sessions still pass through the firewall from the base OS or not.

---

### Post by bodhi.zazen on 2010-03-03
> **KayakJim said:**
> I have an Ubuntu 9.04 system with a firewall configured to only allow access from certain IP's.

I would like to install VirtualBox to run multiple OS's for testing.

I would like to know if incoming connections for the virtualized sessions still pass through the firewall from the base OS or not.

In general no.

To be more specific, it depends on how you set up Networking, there are 3 options, NAT, bridged, and host only.

See these links :

[http://www.virtualbox.org/wiki/Advanced_Networking_Linux](http://www.virtualbox.org/wiki/Advanced_Networking_Linux)

[http://www.brighthub.com/computing/windows-platform/articles/29787.aspx](http://www.brighthub.com/computing/windows-platform/articles/29787.aspx)

You certainly may configure your host to firewall your guests. The easiest option is to use NAT.

If you need more then NAT for your guests, you have several options, configure your router (depends on your router), configure NAT on your host, and configure a firewall on your guest.

---

