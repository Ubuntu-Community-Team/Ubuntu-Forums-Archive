---
title: "NetworkManager not falling back to IPv4LL"
date: 2010-11-06
forum: General Help
---

### Post by btindie on 2010-11-06
My laptop is running a clean install of Maverick.

I'm having problems getting NetworkManager to automatically assign an IP address to eth0 when a DHCP server isn't available. I've got a connection profile named 'Auto eth0' and under the IPv4 settings the Method is set to 'Automatic (DHCP)'. When I connect it directly to my NAS, where no DHCP is available, NetworkManager fails to fallback to assigning an IPv4LL address via avahi-autoipd. I'm pretty sure this was the behaviour in the past. If I manually run "avahi-autoipd -wD eth0", eth0 gets assigned an IPv4 address and I can connect to my NAS.

Has something been changed in the behaviour of NetworkManager or is this **another** Maverick 'feature'?

How do I get NetworkManager to fallback to using IPv4LL (Link-Local) if no DHCP server is available?

---

