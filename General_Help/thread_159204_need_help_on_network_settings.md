---
title: "need help on network settings"
date: 2006-04-12
forum: General Help
---

### Post by leftyman on 2006-04-12
hello,


I have a broadband adsl modem/router with IP 192.168.1.1
My ubuntu computer with IP 192.168.1.2
My Windows Laptop 192.168.1.3

I tried to install samba with no luck, and investigating I found this.


from the laptop when I ping ubuntu computer (192.168.1.2) there are no problems


from the ubuntu computer when I ping the laptop (192.168.1.3) I get no answer.


maybe I have a problem with iptables or a firewall, I dont know.


thanks in advance for the help

---

### Post by Ramses de Norre on 2006-04-12
I think it's a firewall on the laptop then, because by default outgoing pings certainly aren't dropped.
Is there some kind of a firewall running on it?

---

### Post by apjone on 2006-04-12
open a terminal on the linux maching
type 'sudo -s'
now type 'vi /etc/resolv.conf'
enter the following.

nameserver 158.152.1.58 
domain MSHOME # or what ever you called your network
nameserver 158.152.1.43
nameserver 192.168.1.1

you can replace the name server ip's with any dns you wish
Does your linux pc have a static ip?

---

### Post by Robor on 2006-04-12
I would suspect it's Windows Firewall (enabled by default) that's dropping your pings.  You can turn it off in the advanced network properties or just disable the service.

---

### Post by Ramses de Norre on 2006-04-12
On win: Network connections, right click the connection, select properties > advanced tab > first button (don't know what's it called in english, something like settings I think) > advanced > select network connection and click settings (or whatever it's called) again and then you can select whether or not to accept pings in the ICMP tab.
In the services tab you can allow samba by adding a service for it, but I'm not sure how to configure it.

---

