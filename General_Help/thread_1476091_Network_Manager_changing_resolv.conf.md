---
title: "Network Manager changing resolv.conf"
date: 2010-05-07
forum: General Help
---

### Post by viralmeme on 2010-05-07
The local DNS server is slow, so I added the openDNS servers to  /etc/dhcp3/dhclient.conf. But Network manager keeps appending the local DNS server to resolv.conf. I need to pick up a DHCP address but how to stop it changing DNS servers?

---

### Post by Iowan on 2010-05-07
You should be able to edit */etc/dhcp3/dhclient.conf* and either remove "domain-name-servers" from the "request" line, or use "supercede" to install the DNS of your choosing.

---

### Post by jbrown96 on 2010-05-07
OpenDNS is terrible. It hijacks bad DNS requests, and it's not fast. There's no reason to use it.

If you still want to, then you need to configure it for your connections in NetworkManager. If you edit the connection, go to IPv4 settings and change the it to "dhcp (addresses only)," then you can add the dns server options.

---

