---
title: "iptables question"
date: 2010-08-15
forum: General Help
---

### Post by titanicmusic14 on 2010-08-15
I would like to know how to approach doing some IPtables. I am using a dd-wrt router. which has iptables in it.    My interface is wl0.1 I want to redirect all http traffic on it to my webserver which is 192.168.1.100 so that a page can be viewed. I tried the routers nocatsplash and I tried http redirection and they don't seem to work. THANKS

I saw these online for a proxy , might these work?
iptables -t nat -A PREROUTING -i br0 -s $LAN_NET -d $LAN_NET -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -i br0 -s ! $PROXY_IP -p tcp --dport 80 -j DNAT --to $PROXY_IP:$PROXY_PORT
iptables -t nat -I POSTROUTING -o br0 -s $LAN_NET -d $PROXY_IP -p tcp -j SNAT --to $LAN_IP
iptables -I FORWARD -i br0 -o br0 -s $LAN_NET -d $PROXY_IP -p tcp --dport $PROXY_PORT -j ACCEPT

---

