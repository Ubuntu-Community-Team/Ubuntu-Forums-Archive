---
title: "network broken after updates"
date: 2011-03-04
forum: General Help
---

### Post by mlg3 on 2011-03-04
There's a problem with the latest updates.

First I allowed the 32-bit version to update under VirtualBox, and now cannot boot with the new kernel. The old kernel works, so it's not really a problem. BUT:

Then, I allowed update on the real desktop, and now the network disappeared.

sudo /etc/init.d/networking restart

shows a very short message about eth0=eth0 and does nothing.
(I cannot copy&paste, because the network is not working under Ubuntu. Now I'm under Windows, the network works (I can post).)

Atheros L1 Gigabit Ethernet 10/100/1000Base-T Controller PCI bus 2, dev 0, func 0

Heeeelp!!!!!!! :confused:

---

### Post by mlg3 on 2011-03-04
I have searched for occurrences of eth0 and found that
/etc/network/interfaces reads:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp

I uncommented the last line to be:

iface eth0 inet dhcp

and did:

sudo /etc/init.d/networking restart

There is definitely something wrong:
never before did dhcp discovery take so much time!

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                              Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:1b:fc:ba:89:de
Sending on   LPF/eth0/00:1b:fc:ba:89:de
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.2
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.10.77.2
DHCPNAK from 10.10.77.3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 10.10.79.218 from 10.10.77.3
DHCPREQUEST of 10.10.79.218 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.10.79.218 from 10.10.77.2
bound to 10.10.79.218 -- renewal in 259705 seconds.

For now it sort of works, but... c'est pas vrai!
It should not be like this! And only a short while before, it was not!

---

