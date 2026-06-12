---
title: "dhcp problems"
date: 2006-03-18
forum: General Help
---

### Post by JamesNorris on 2006-03-18
I have a dhcp3 server installed to allow my network to access the internet through my comp. I use dapper at the moment, and upgrading from breezy seems to have broken dhcp or something.

When I run firestarter I get this:
```
james@jamie:~$ sudo firestarter
Password:
Firewall started
Failed to start DHCP server

```
And an error message pops up saying
 "an unknown error occured. Please check your netrwork device settings and make sure your internet connection is active"

but when I type 
```
james@jamie:~$ sudo /etc/init.d/dhcp3-server restart
```
I get this
```
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 * Stopping DHCP server                                                  [ ok ]
Internet Systems Consortium DHCP Server V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
 * Starting DHCP server:                                                 [ ok ]
```

This says that there's soemthing wrong, as DHCP is running and the server is working fine. So why does firestarter think dhcp isn't running?

Can anyone help? I enclose my dhcpd.conf below:

```
# Setting DHCPD global parameters
allow unknown-clients;

# Set parameters for the 192.168.0.0/24 subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.255;
default-lease-time 604800;
max-lease-time 604800;
option subnet-mask 255.255.255.0;

option domain-name-servers 158.152.1.58, 158.152.1.43;
option ip-forwarding on;
option routers 192.168.0.1;
}



```

---

### Post by hajk on 2006-03-18
There's no problem with Firestarter off, I gather? The problem may be in that port 53 (the nameserver service) is closed in Firestarter.

---

