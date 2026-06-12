---
title: "help needed! iptables"
date: 2006-05-04
forum: General Help
---

### Post by soongwoo on 2006-05-04
I have two machines which has different iptables rules.
One is connected via xdmcp and the other is not.
I can not identify the problem.
Can anyone point out why the first one is not working?

Thanks
soongwoo

Can not connect:
```
# set default parameters
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

iptables -A TRUSTED -m udp -p udp --dport 177 -j ACCEPT

```

Can connect:
```
# set default parameters
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW -m udp -p udp --dport 177 -j ACCEPT

```

---

