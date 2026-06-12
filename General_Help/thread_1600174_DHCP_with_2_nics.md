---
title: "DHCP with 2 nics"
date: 2010-10-18
forum: General Help
---

### Post by mkirkland on 2010-10-18
Ok, im sure this is a newb question but here it goes:
 
I have ubuntu 10.04 loaded and i have 2 nics.
eth0 is static to my router with internet acces. 
eth0: 192.168.0.114/255.255.255.0
GWay: 192.168.0.1
DNS&DHCP 192.168.0.2
 
eth1 is my dhcp card setup as 192.168.1.1/255.255.255.0
eth1 will send dhcp lease to a laptop that i have on the network and assign DHCP addresses accordingly. But i cannot get the internet access to be accessed by the DHCP client from eth1. If i have both nics enabled then internet access on the Ubuntu server dies. I also have a Proxy running on the server. I cannot use the proxy or internet with both nics running. It will only work when eth0 is active and eth1 is disabled.
 
This is what i want to do. PC1 is ububtu running DHCP server, Firestarter Firewall and Squid 2.7 stable2.7
 
PC2 is a windows client that i want to get DHCP and proxy/Firewall access from PC1
 
Right now i can get the DHCP working with no problems but no internet access to it. I think my /etc/networm/interfaces file needs to be setup accordingly but im newb at this. Right now the only thing listed in interfaces is:
auto lo
iface lo inet loopback
 
Need some help QUICK...Halp!:(

---

### Post by mkirkland on 2010-10-19
Bump

---

### Post by SeijiSensei on 2010-10-19
There are a number of issues you need to review.  First, is IP forwarding enabled?  Check the line for net.ipv4.ip_forward in /etc/sysctl.conf and make sure it's set to one.  You can check the current status of this switch with the command "sudo cat /proc/sys/net/ipv4/ip_forward".  If it returns zero, you can't forward traffic between interfaces.

Next check the firewalling rules and make sure traffic from eth1 to the internet is "masqueraded".

You should have only one default gateway, presumably through eth0.  If the DHCP server gives out an gateway for the eth1 interface, disable it on the DHCP server.

If you're still having trouble, post the results of the commands "ifconfig" and "route -n" and maybe the results of "sudo iptables -L -nv" as well.

---

### Post by mkirkland on 2010-10-19
[COLOR=black][FONT=Arial][SIZE=3]I uncommented the ip_forward line so that its set to 1[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Arial][SIZE=3][/SIZE][/FONT][/COLOR] 
[COLOR=black][FONT=Arial][SIZE=3]eth0      Link encap:Ethernet  HWaddr 00:0c:f1:87:4d:74  
          inet addr:192.168.0.114  Bcast:192.168.0.255   Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe87:4d74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:48586571 (48.5 MB)  TX bytes:4217981 (4.2 MB)

eth1      Link encap:Ethernet  HWaddr 00:0e:0c:58:c0:1e  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe58:c01e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:251350 (251.3 KB)  TX bytes:517024 (517.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2870913 (2.8 MB)  TX bytes:2870913 (2.8 MB)



# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1[/SIZE][/FONT][/COLOR]

---

### Post by mkirkland on 2010-10-27
Anyone? Bump

---

