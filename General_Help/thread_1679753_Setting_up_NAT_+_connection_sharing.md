---
title: "Setting up NAT + connection sharing"
date: 2011-02-01
forum: General Help
---

### Post by alxlabs on 2011-02-01
I need to share internet connection eth0->eth1 and VPN server and NAT. Firestarter is good but unfortunatelly it kills vpn... Suggested fix (from firestarter website) did not work. So, I want to do it manually thru iptables. I found this example
```

#!/bin/sh 
# 
# internet connection sharing wlan0 is the gate way 
# eth0 is the lan port this might use a straight ethernet cable to a router wan port or a switch or a single PC
# 192.168.2.2 is the port that is being used by the lan for access I changed it to 192.168.2.254 and set fixed addresses for the wan and router
#
# change wlan0 to ppp0 and you can use this for mobile broadband connection sharing
#
ifconfig eth0 up"
ifconfig eth0 192.168.2.1
echo “1” > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.2
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p udp -m multiport --dports 88,3074 -j ACCEPT

```

Question: do those two lines

iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.2
iptables -A FORWARD -i wlan0 -d 192.168.2.2 -p tcp --dport 3074 -j ACCEPT

mean that port 3074 tcp will be forwarded to 192.168.2.2? I.e. if I have a web server at 192.168.2.3 then i should add

iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 80 -j DNAT --to-destination 192.168.2.3
iptables -A FORWARD -i wlan0 -d 192.168.2.3 -p tcp --dport 80 -j ACCEPT

Is my understanding correct?

---

