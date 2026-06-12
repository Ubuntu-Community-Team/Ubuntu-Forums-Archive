---
title: "iptables help"
date: 2010-06-29
forum: General Help
---

### Post by McDoodleson on 2010-06-29
Hello, I am new to Ubuntu and new to the forums, so forgive me if this thread is in the wrong place.
 
I have a little issue with my iptables, I have done some research but seem to be screwed. I am very very new to this stuff so please be kind, I know that its probably something that is really easy to fix.
 
 I have two MS 2003 servers, one of them is my domain controller with other services running (10.0.0.3) and the other one is working as my Exchange server with other services running (10.0.6.4) I also have an XP workstation and a Ubuntu desktop 9.10 acting as the firewall/default gateway (10.0.6.1) 
 
The iptable rules I have set up so far work for allowing services like my external FTP and HTTP, VPN and internet traffic through. 
 
What I can't do though is access a webserver on 172.25.104:93 to see if the external emails I sent were let through the firewall, so I can't tell if those rules worked either.
 
I have edited these rules a few times now and nothing seems to work.
 
I still do not fully understand the iptables stuff.
 
Again, please be gentle and any help is muchly appreciated.
 
sudo iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
 
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
 
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 8081 -j ACCEPT
 
sudo iptables -A INPUT -p tcp --dport 90 -j ACCEPT  [COLOR=red]<-- updated rule[/COLOR]
sudo iptables -A INPUT -p tcp --dport 25 -j ACCEPT  [COLOR=#ff0000]<-- updated rule[/COLOR]
sudo iptables -A OUTPUT -p tcp --dport 90 -j ACCEPT [COLOR=#ff0000]<-- updated rule[/COLOR]
sudo iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT [COLOR=#ff0000]<-- updated rule[/COLOR]
&#12288;
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 443 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 21 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1723 -j DNAT --to-destination 10.0.6.3
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 90 -j DNAT --to-destination 10.0.6.4 
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 90 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 25 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 25 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 93 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 93 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 110 -j DNAT --to-destination 10.0.6.4
sudo iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 110 -j DNAT --to-destination 10.0.6.4
 
:confused:

---

### Post by yeleek on 2010-06-29
172.25.x.y is a private address range, so must be an internal address i.e. thats not the address its on the internet with.

So have you got a rule to allow connectivity to that?  Would help if we could see your current iptables config.

type

```
sudo iptables -L
```

and post the results.

Also whats the OUTPUT policy, if DROP for example you need to specify which rules you want and at the moment you only seem to have

sudo iptables -A OUTPUT -p tcp --dport 90 -j ACCEPT <-- updated rule
sudo iptables -A OUTPUT -p tcp --dport 25 -j ACCEPT <-- updated rule

i.e. port 25 + 90.

---

### Post by dino99 on 2010-06-29
ipblock and his whitelist is an easy way to play with. by the way the security forum is a better place.

---

