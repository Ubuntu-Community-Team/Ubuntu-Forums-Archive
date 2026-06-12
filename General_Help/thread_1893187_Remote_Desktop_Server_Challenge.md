---
title: "Remote Desktop Server Challenge"
date: 2011-12-09
forum: General Help
---

### Post by ZeroCool2u on 2011-12-09
A few staff in my Office need remote desktop (RDP) access into the system used at another office across town.

This machine must be separate from the existing on site systems, so that ONLY the software the staff in my office needs access to will be available on this machine.

This machine must be as secure as possible, including firewall rules that allow RDP connections only from our VPN. It should drop all packets that are not inbound from known subnets.  Outbound connections should be restricted to hosts or subnets needed for things like automatic updates and network time server(s).

I need an Ubuntu box that will:

•	Have a tightly controlled firewall, both in- and out-bound
•	Accept inbound RDP connections only from a specific subnet.
•	Forward inbound RDP traffic to the existing Windows 2000 machine

Any suggestions? I think I can deal with the firewall rules, but I'm not entirely sure how to deal with the RDP forwarding.

---

### Post by dcstar on 2011-12-10
> **ZeroCool2u said:**
> A few staff in my Office need remote desktop (RDP) access into the system used at another office across town.
........
I need an Ubuntu box that will:

•	Have a tightly controlled firewall, both in- and out-bound
•	Accept inbound RDP connections only from a specific subnet.
•	Forward inbound RDP traffic to the existing Windows 2000 machine

Any suggestions? I think I can deal with the firewall rules, but I'm not entirely sure how to deal with the RDP forwarding.

Totally pointless using a Ubuntu system for this, most decent firewalls have all these functions.

---

