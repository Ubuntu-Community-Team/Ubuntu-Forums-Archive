---
title: "Can't connect to network after power failures"
date: 2010-07-14
forum: General Help
---

### Post by zoomiest on 2010-07-14
I had a couple of failures around my Ubuntu Studio box. Now, it won't connect to the Internet, or network. It won't even pick up the gateway router...

I have read a few posts about reconfiguring the IP to be static, rather than dhcp, but that didn't help.

When I restart the network, I now get:
"Don't seem to have all the variables for eth0/net
Failed to bring up eth0"

My network/interfaces file reads:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.111
netmast 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

any thoughts?

---

