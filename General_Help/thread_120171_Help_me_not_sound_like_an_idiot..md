---
title: "Help me not sound like an idiot."
date: 2006-01-20
forum: General Help
---

### Post by frost_ad on 2006-01-20
Ok I want to connect wirelessly on my campus. I've been trying to learn about vpnc but I'm at a loss. When I ran windows I used a cisco VPN client that just required my username and password. Now when I ran vpnc it asked for ipsec, groupname or something and then username and password. What is ipsec? Basically what information can I ask for from the technology help desk so I can use vpnc? Hopefull I made some sense out of my problem here. Thanks for any help you can give.

(If you have any links to threads or articles that explain what I don't get that'd be great too)

---

### Post by hajk on 2006-01-21
You need to make a conf-file in /etc/vpnc/ directory, for example 
"campus.conf", with the following information:

IPSec gateway <campus.access.address>
IPSec ID <groupID>
IPSec secret <groupSecret>
XAuth username <yourID>
XAuth password <yourPassword>

Bracketed <items> should be replaced with the information specific to your situation (without the brackets). You should ask the IT people about the first three items, the last two items you should already know. 

Then start the connection with "sudo vpnc campus", and stop it with 
"sudo vpnc-disconnect". 

Are you running the Firestarter firewall? In that case you need to apply some special rules in /etc/firestarter/user-pre&#65535;

iptables -A INPUT -j ACCEPT -s <campus.access.adres> -p esp
iptables -A INPUT -j ACCEPT -s <campus.access.address> -p udp -m multiport --sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d <campus.access.address> -p esp 
iptables -A OUTPUT -j ACCEPT -d <campus.access.address> -p udp -m multiport --dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+

Again, replace the bracketed items with your own info, see earlier. This worked for me...

---

### Post by frost_ad on 2006-01-22
Thanks so much for your help. I'll have to get that info tomorrow and try it out on campus.
Just out of curiousity why do you not need this information when you use a windows cisco vpn client?

---

