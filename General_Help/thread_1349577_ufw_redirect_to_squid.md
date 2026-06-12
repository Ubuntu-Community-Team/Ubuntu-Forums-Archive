---
title: "ufw redirect to squid"
date: 2009-12-08
forum: General Help
---

### Post by klashniv on 2009-12-08
Hullo all,

Apologies if I posted in the wrong forum or made some other posting mistake.

Am trying to get ufw to forward all http traffic to squid except for http traffic to one particular site. Am using ubuntu-server 9.10 with all updates installed.

I need to know whether this is the way to do it:

here is my /etc/ufw/before.rules (x.x.x.x is the site I don't want going through squid)

#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Redirect to Squid Proxy
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -d ! x.x.x.x -j DNAT --to-destination 192.168.0.1:3128

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines

# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -i lo -j ACCEPT

# connection tracking rules
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets
# uncomment to log INVALID packets
#-A ufw-before-input -m conntrack --ctstate INVALID -j LOG --log-prefix "[UFW BLOCK INVALID]: "
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP

# connection tracking for outbound
-A ufw-before-output -p tcp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK NOT-TO-ME]: "

# all other non-local packets are dropped
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT

#Don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

Thanks in advance, Joseph

---

