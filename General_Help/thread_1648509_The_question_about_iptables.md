---
title: "The question about iptables"
date: 2010-12-18
forum: General Help
---

### Post by nhubinh111 on 2010-12-18
[SIZE=3]Hi , everybody .
A mery Chirstmas and a happy New Year to you .
I am new Member about Linux-ubuntu .so that
i have some problem with my firewall . I try config iptables for connect my lan network to Internet . My Lan include :

Clients : IP range 10.0.0.0/24 (GW 10.0.0.3)
FW-Server :
   +private interface  : eth1 IP 10.0.0.3 
   +public interface   : eth0 IP 192.168.1.13 (dynamic IP - GW : IP router 192.168.1.1 )

I try config iptables :

[/SIZE][SIZE=3]iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT


iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

[/SIZE][SIZE=3]iptables -A INPUT -i eth1 -s 10.0.0.0/24 -j ACCEPT
iptables -A OUTPUT -o eth1 -d 10.0.0.0/24 -j ACCEPT


iptables -A OUTPUT -o eth0 -j ACCEPT
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT


iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o eth0 -j SNAT --to 192.168.1.13


I try test connect from my client and Server :

From Server : 
  ping google.com - Success
  ping 192.168.1.1 (router) - Success
From Client :
  ping 192.168.1.1 - Success
  ping google.com - Not Success
Can You help me . Thank so much .[/SIZE]

---

### Post by nhubinh111 on 2010-12-19
Help me !  :(:(:(:(:(:(

---

