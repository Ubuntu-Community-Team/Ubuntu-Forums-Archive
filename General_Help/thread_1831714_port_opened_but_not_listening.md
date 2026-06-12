---
title: "port opened but not listening"
date: 2011-08-23
forum: General Help
---

### Post by jlocke on 2011-08-23
Hello
recently I installed OpenVPN in one Virtual Unbutu Server
I want my firewall  to forward the port 1193 to this Virtual Server 
I already put all the iptables rules to do this but the port is still closed.
When i run the command netstat -plntu | grep 1194 nothing it returns me nothing..  

this are the rules I used: 

/sbin/iptables -A INPUT -s 192.168.3.0/24 -p tcp -m tcp --dport 1194 -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -s 192.168.3.0/24 -d 192.168.3.197 --dport 1194 -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -d 192.168.3.0/24 -s 192.168.3.197 --dport 1194 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -p tcp -i 192.168.3.0/24 --dport 1194 -j DNAT --to 192.168.3.197:1194


192.168.3.0/24 is my WAN interface
192.168.3.197 is my OpenVPN server


sorry for my awful english

---

### Post by allwimb on 2011-08-23
are you sure that port 1194 is working on your server ? I mean before looking at the firewall check that port 1194 is opend in the server if it is then check if the firewall can access it.

You can use telnet to do that.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

