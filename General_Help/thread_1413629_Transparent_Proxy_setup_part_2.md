---
title: "Transparent Proxy setup part 2"
date: 2010-02-22
forum: General Help
---

### Post by viper3two on 2010-02-22
Hi
I posted a help question regarding setting up a transparent proxy. I now have success with that. I am running ubuntu 9.10 desktop, Squid and Dansguardian. I am able to put the proxy box's ip into a client computer and then it blocks websites perfectly. 
Now I want to make this transparent where I wont have to change all my clients. 
The box has one nic, at 10.0.167.99. Dansguardian is on port 8080 and squid is on port 3128. 
At our DMark where the internet comes in, I have a switch that connects the router and the internal network. I have free ports on that switch if needed. 
Do I install a 2nd nic on this box or should I just be able to plug it into that switch and do the IP table reroute requests for port 80 to port 8080 (dans)? 
If I can just plug it into that switch that the lan and router is on, is there any configuration I need to change? 
And...lastly, if I need to install a 2nd nic on the box, how do I configure that in squid and dansguardian. 
Thanks for the help

---

### Post by viper3two on 2010-02-23
Anyone?

---

### Post by bodhi.zazen on 2010-02-23
You do this with iptables:

[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html)

[http://www.linuxforums.org/forum/linux-networking/18065-iptables-transparent-proxy.html](http://www.linuxforums.org/forum/linux-networking/18065-iptables-transparent-proxy.html)

The exact rule syntax is dependent on your network configuration.

---

### Post by viper3two on 2010-02-23
Thank you! 
So using those rules in iptables, I can just config it to my network and plug it into the switch that the lan is on, in other words, a single nic proxy? Thanks again, I am really stupid on this proxy stuff, all new to me.

---

### Post by bodhi.zazen on 2010-02-23
Yes, but if you have problems, ask for help. Be sure to include more specific details of you network architecture.

---

### Post by viper3two on 2010-02-23
Thanks so much, appreciate it alot. Going to work on this thing and hopefully get it going. Thanks again.

---

### Post by viper3two on 2010-02-24
Still couldn't get this to work. Here is my exact config maybe this will help:
ubuntu 9.10 loaded with iptables, squid, dansguardian, sarg
squid configured to http_port 3128 transparent, otherwise left alone.
dansguardian configured to remove # from unconfigured. 
Nic one eth0 = 10.0.167.99, 255.255.252.0, gate 10.0.164.200 (our router), dns 10.0.164.250 (our dns server)
Nic two eth1= 10.0.167.101, 255.255.252.0, gate 10.0.164.200 (our router), dns 10.0.164.250 (our dns server)
(our network is 10.0.16x.xxx, with all subnet 255.255.252.0. Also we have 4 networks that are 192.168.1 through 4.xxx.

webmin installed with dansguardian module. 
Proxy box is plugged into network switch with eth0 only, eth1 is unplugged. 
The switch that I am plugging into has the dns server on it, the 10.0.164.250

*all is good at this point, but I want this transparent so I dont have to change user browser settings. If it goes down then I have to change 350 clients.

I could move the proxy box to the side of the building that the dmark is at. The dmark has our router, an asa firewall and then a switch that connects the main lan connection for internet. I tried actually taking the proxy box and plugging the lan connection into eth0, and eth1 going to the switch that has the fiewall router on. Still no dice.....

I tried also doing this: following this guide, [http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)
I tried the line: sudo iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080

Then tried surfing on a few client pc's. Able to surf wide open. This is with the box having the lan main connection in eth0 and the switch that holds the firewall and router into eth1. 

Then tried: iptables -t nat -A PREROUTING -p tcp -i eth0 -d xxx.xxx.xxx.xxx --dport 80 -j DNAT --to xxx.xxx.xxx.xxx:8080
Using my IP's>>>eth0 -d 10.0.167.99 --dport 80 -j DNAT --to 10.0.167.101:8080
No dice there either....

Then tried: iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j DNAT --to xxx.xxx.xxx.xxx:8080
iptables -A INPUT -p tcp -m state --state NEW --dport 8080 -i eth1 -j ACCEPT
Using my IP's>>>>DNT --to 10.0.167.99:8080
No dice there either....

I finally wound up doing sudo iptables -x and rebooting. Then went into webmin and reset the firewall to clear it out. 

So basically I don't know what the heck I am doing. I am close because I know the proxy works when I put the proxy ip and port 10.0.167.99:8080 in the client browser. But for the life of me I can't figure out this transparent mode. 

I need to know how to wire this and how to set up eth0 and eth1 in this case. If you could help, I would appreciate it. I know I can do it, I just need some help. Thanks again.

---

