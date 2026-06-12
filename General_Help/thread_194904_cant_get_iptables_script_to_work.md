---
title: "cant get iptables script to work"
date: 2006-06-12
forum: General Help
---

### Post by mrweirdo on 2006-06-12
OK I am runing ubuntu server dapper(aka base install + no gui) but for the life of me I cant figure out why my iptable script will not work. I can still sites online from the box but internaly from other computers on the lan I cant access or ping any external sites.

Basicly what its suposed to do is share an internet conection on the internal lan eth1
external lan is eth0.

```

#!/bin/sh
IPTABLES='/sbin/iptables'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

#------------------------------------------------------------------------------
# Cleanup.
#------------------------------------------------------------------------------

# Delete all rules.
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F

# Delete all (non-builtin) user-defined chains.
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t mangle -X

# Zero all packet and byte counters.
$IPTABLES -Z
$IPTABLES -t nat -Z
$IPTABLES -t mangle -Z

#------------------------------------------------------------------------------
# Filter policies:
#------------------------------------------------------------------------------

# Default policies: drop everything.
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT DROP

# Define Input Rules:
$IPTABLES -A INPUT -i eth1 -j ACCEPT
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -f -j DROP
$IPTABLES -A INPUT -d 127.0.0.0/255.0.0.0 -i eth0 -j DROP

# Define Forward Rules:
$IPTABLES -A FORWARD -i eth1 -o eth0 -m state --state NEW,ESTABLISHED -j ACCEPT

# Define Output Rules:
$IPTABLES -A OUTPUT -o eth1 -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT
$IPTABLES -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -m tcp -m multiport --dports 67,68 -j ACCEPT
$IPTABLES -A OUTPUT -p icmp -j ACCEPT

#------------------------------------------------------------------------------
# Nat policies:
#------------------------------------------------------------------------------

# Default policies: allow everything.
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT

# Define Postrouting Rules:
$IPTABLES -t nat -A POSTROUTING -o eth0 -j MASQUERADE

#------------------------------------------------------------------------------
# Mangle policies: 
#------------------------------------------------------------------------------

# Default policies: allow everything.
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P INPUT ACCEPT
$IPTABLES -t mangle -P FORWARD ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT
$IPTABLES -t mangle -P POSTROUTING ACCEPT

```

Nothing is wrong with the network config but as far as the rest of the setup goes for reference:
**eth1: **
ip:192.168.1.11
subnet: 255.255.255.0
**lan client pc** 
ip: 192.168.1.15
subnet: 255.255.255.0
gateway: 192.168.1.11
dns1: 68.87.76.178
dns2: 68.87.66.196

Does anyone know why the internal lan client cant access the net or ping websites on the net while the ubuntu box can still ping sites on the net? and how I might fix this script?

---

### Post by mrweirdo on 2006-06-12
got it working I had the devices backwords in the forward rule. didnt see it till now eather lol.

---

