---
title: "dhcpd wont start"
date: 2009-12-08
forum: General Help
---

### Post by jdelidc on 2009-12-08
ive got 2 nics on my machine. one of them is only there in case the other one breaks so it aint plugged in. the primary (eth0) is on 192.168.1.117 (old ip address from my router) and the bckup (eth1) is 192.168.1.253 but its unplugged. also, this is with fedora 12. i had it working fine in fedora 11 but it was so maintenance free i dont remember what i did. and i completely nuked the hard drive when i upgraded

dhcp.conf file

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.116;
  option domain-name-servers 192.168.1.117;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.1.255;
}


the error i come up with:

no subnet declaration for eth0 (192.168.1.117)
**ignoring requiests on eth0. if this is not what
  you want, please write a subnet delaration
  in your dhcpd.conf file for the network segment
  to which interface eth0 is attached. **

Not configured to listen on any interfaces!

---

