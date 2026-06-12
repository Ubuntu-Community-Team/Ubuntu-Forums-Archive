---
title: "Using UFW to configure iptables"
date: 2010-03-12
forum: General Help
---

### Post by risingsun on 2010-03-12
Hi,

I've got a machine on my network that's just running default Ubuntu 9.10, but I was considering setting up a network dhcp service on it to manage my machines. As such I was just wondering about configuring the iptables for it.

Reading about, I believe all incoming connections are dropped by default in a standard installation of Ubuntu anyway. If so, is it simply a case of enabling UFW and using it to allow the appropriate port for the dhcpd service and not touching anything else and everything should remain secure?

Many thanks.

---

### Post by diesch on 2010-03-13
By default Ubuntu doesn't set up any network package filters neither it installs any programs listening for incoming network connections. Just configuring your DHCP daemon to only listen to the query you want should be secure.

---

