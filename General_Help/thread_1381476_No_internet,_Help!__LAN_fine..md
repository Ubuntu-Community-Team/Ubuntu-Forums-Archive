---
title: "No internet, Help!  LAN fine."
date: 2010-01-14
forum: General Help
---

### Post by ssefick on 2010-01-14
OS: Ubuntu 9.10 64 bit intel quad core processor
Kernel:2.6.31-17-generic

lspci | grep Ethernet
0:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection


I have lost internet conectivity recently after updating the kernel from 2.6.31-16-generic to 2.6.31-17-generic. I also installed samba to try and share a folder containing music on the LAN (auburn university). I have since uninstalled all of samba and booted into the old kernel to see if this would solve the problem. It did not. I can ssh into the machine from within the LAN but have no ability the ssh from outside of the LAN. Also, I do not have any internet conectivity. Below are places that I have looiked and compared with a server that I am administering to see if there were any differences between the two (The server has internet conectivity). Any help would be greatly appreciated, and if there are any other pieces of information necessary then please don't hessitate to ask.

/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iptables -L
Chain INPUT (policy ACCEPT)
target prot opt source destination 

Chain FORWARD (policy ACCEPT)
target prot opt source destination 

Chain OUTPUT (policy ACCEPT)
target prot opt source destination 

route -n

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
131.204.120.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 131.204.120.1 0.0.0.0 UG 100 0 0 eth0

I have checked /etc/resolv.conf
and they are the correct servers in the correct order- same as the server

131.204.120.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 131.204.120.1 0.0.0.0 UG 100 0 0 eth0

I am not able to ping the internet with an IP address.

Thanks,

Stephen

---

