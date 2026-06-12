---
title: "have problem with iptables in the part of ssh"
date: 2011-06-01
forum: General Help
---

### Post by mlmanlookman on 2011-06-01
I have blocked all connection with iptables and allowed only the loopback:
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

next I want to allow only ssh connections, and also I want to record the IP address of each attempt to access port 22 using the recent module.then I want to to see if that IP address has attempted to connect 2 or more times within the last 60 seconds, and if not then the packet is accepted:
iptables -A INPUT -p tcp --dport 22 -m recent --set --name ssh --rsource
iptables -A INPUT -p tcp --dport 22 -m recent ! --rcheck --seconds 60 --hitcount 2 --name ssh --rsource -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT 
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT 
iptables -A INPUT -p tcp --sport 22 -j ACCEPT 
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP

the problem that probably didn't write it right so can someone show me whhat is my problem

---

