---
title: "Problmes getting dhcp3 started"
date: 2006-05-11
forum: General Help
---

### Post by mattiashem on 2006-05-11
Hi !

A cant get my dhcp3 server started.
I have 2 network cards installed eth0 is for the internet and eth2 is for my localnet.
Im telling the dhcp server to use eth2 in the dhcp-server file but when a trying to start the server all a get is this error



May 11 18:13:54 edubuntu dhcpd: No subnet declaration for eth2 (0.0.0.0).
May 11 18:13:54 edubuntu dhcpd: ** Ignoring requests on eth2.  If this is not what
May 11 18:13:54 edubuntu dhcpd:    you want, please write a subnet declaration
May 11 18:13:54 edubuntu dhcpd:    in your dhcpd.conf file for the network segment
May 11 18:13:54 edubuntu dhcpd:    to which interface eth2 is attached. **
May 11 18:13:54 edubuntu dhcpd:
May 11 18:13:54 edubuntu dhcpd:
May 11 18:13:54 edubuntu dhcpd: Not configured to listen on any interfaces!
May 11 18:14:01 edubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
May 11 18:14:08 edubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
May 11 18:14:15 edubuntu dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9


What to do what to do ??


// matte

---

