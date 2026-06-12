---
title: "missing Cisco vpn connection type"
date: 2011-09-16
forum: General Help
---

### Post by hamiltzp on 2011-09-16
Hello,

This is my first post, so hopefully I am posting this correctly.  I have a vpnc issue that I haven't seen in the other forum posts.

I have two laptops, one with Ubuntu 10.10 and the other with Ubuntu 11.04.  I have my 10.10 laptop configured to connect to my Cisco VPN at work.  I am having difficulty configuring my 11.04 laptop.

From the "Network Connections" screen, I select the VPN tab.  Then I click Add.  On my 10.10 laptop, I have the options "Cisco Compatible VPN (vpnc)" and "Point-to-Point Tunneling Protocol (PPTP).  The choice is obvious.

On my 11.04 laptop, I have installed vpnc/kvpnc, but for some reason I only have the PPTP option.  Did something change?  What am I missing?

Thanks for any help anyone can offer.

---

### Post by dcstar on 2011-09-17
> **hamiltzp said:**
> Hello,

This is my first post, so hopefully I am posting this correctly.  I have a vpnc issue that I haven't seen in the other forum posts.

I have two laptops, one with Ubuntu 10.10 and the other with Ubuntu 11.04.  I have my 10.10 laptop configured to connect to my Cisco VPN at work.  I am having difficulty configuring my 11.04 laptop.

From the "Network Connections" screen, I select the VPN tab.  Then I click Add.  On my 10.10 laptop, I have the options "Cisco Compatible VPN (vpnc)" and "Point-to-Point Tunneling Protocol (PPTP).  The choice is obvious.

On my 11.04 laptop, I have installed vpnc/kvpnc, but for some reason I only have the PPTP option.  Did something change?  What am I missing?

Thanks for any help anyone can offer.

Install the **network-manager-vpnc** package. kvpnc is for the KDE system not Gnome.

---

