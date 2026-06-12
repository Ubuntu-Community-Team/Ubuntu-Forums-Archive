---
title: "Reverse Proxy"
date: 2011-02-24
forum: General Help
---

### Post by couper on 2011-02-24
Hi,
I'm new in ubuntu.
I have three different computer.
2 Ubuntu Server with desktop
1 Win 2008 server
They are both in same network. And I have one static ip which is open to the web. (like 88.88.88.88)
In the network ips are like: 192.168.2.4, 192.168.2.5, 192.168.2.6
 
I have silverlight website in win server 2008, its address is 192.168.2.4:8888
and one other website in ubuntu 192.168.2.5:8090
I want to use reverse proxy
 
ProxyPass /site1 [http://192.168.2.4:8888](http://192.168.2.4:8888)
ProxyPassReverse /site1 [http://192.168.2.4:8888](http://192.168.2.4:8888)
 
 
ProxyPass /site2 [http://192.168.2.5:8090](http://192.168.2.5:8090)
ProxyPassReverse /site2 [http://192.168.2.5:8090](http://192.168.2.5:8090)
 
How can I do that?

---

### Post by An Sanct on 2011-02-24
I don't think this post is clear enough, but I would guess you want to have port forwarding? 

IE:, HTTP - port 80 gets response from server1 and some other port gets the other one...

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

Correct me if I misunderstood your question :)

PS. Also if you use a router, setting port forwarding there is simple, just follow the manual...

---

