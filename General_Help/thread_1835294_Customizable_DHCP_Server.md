---
title: "Customizable DHCP Server"
date: 2011-08-29
forum: General Help
---

### Post by KnevetS on 2011-08-29
I'm looking for a DHCP application for my home network - I'm thinking I might have to code it myself, but maybe there's something out there that already does what I need.

Here's what I'm looking for:

1) Reserved DNS Addresses.  I need some of my machines to have pseudo-static IPs, so for instance, whenever my laptop connects to the network, it's address is always the same.

2) Some machines are configured to route through my local proxy, some aren't.  (I want to keep an eye on my children's internet usage, but I don't want to inadvertently break other things)

3) I'd like to be able to easily see what's connected to the network, and occasionally ban a MAC address that doesn't belong on my network.

Is there an open source DHCP server that does this?  Or should I be looking to code my own?  Ideally, I'd also like it to automatically add dns entries for local network machines, but I think that might just be pie in the sky.

---

### Post by Wayne_V on 2011-08-29
sudo apt-get install dhcp3-server bind9

do you need a proxy server on your ubuntu system too (apt-get install squid3)?

this will do everything you need.   if you are not already well versed in dns/dhcp the configuration is probably not going to be trivial tho.   but there are a lot of examples if you google 'home dns server' or 'home dhcp server'.

---

