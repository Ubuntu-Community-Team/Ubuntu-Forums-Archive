---
title: "Firewall/firestarter question"
date: 2006-02-11
forum: General Help
---

### Post by gibson on 2006-02-11
Hi there.

I have recently set up firestarter on my pc and all has been working fine.

I decided to share my content over samba to my mediacenter, however it can not resolve my hostname until i take down the firewall. I have tried to access the pc from my laptop and i can "ping *hostname*" or "ping 192.168.1.100" when the firewall is off, but only ping and access the ip address when it is on.

I have tried opening the following ports in a trial and error attempt, hoever error is all i seem to get back :(

42, 101, 53  (read around and these seemed relevant to the problem)

I am configuring firestarter through the gui in gnome if that makes any difference.

Thanks in advance

G

---

### Post by kaamos on 2006-02-11
Try setting to allow all connections from "192.168.1.1/24"
(That translates as 192.168.1.1-192.168.1.254)

---

### Post by gibson on 2006-02-11
Hi kaamos, thanks for the fast reply

I currentley had it set on "anyone" for the ports in question, will specifying the mask make a difference in this case?

Which ports should i be applying this to?

by the way, i am doing all of this in the "Inbound Traffic Policy"
outbound is currently set to "permissive by default"

thanks 

gib

---

### Post by gibson on 2006-02-11
Hi there, 

OK, i have tried atking out my samba rules and checking i loose the ability to share, which i do. 

Then i set to allow all connections from 192.168.1.1/24 and checked my media center could read the shares, which it could so the new rule should be working niceley, however i can still not reach this pc via the hostname, only the ipaddress (when the firewall is running)


here is the output from iptables -L

ps: sorry for the larce volume of stuff in this quote but i am not sure which parts are relevant to my problem.

Hope i can get this sorted.

Thanks again

> 
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.1.0/24       anywhere
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:6881:6889
ACCEPT     udp  --  anywhere             anywhere            udp dpts:6881:6889
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.1.1          anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.1.255
DROP       all  --  base-address.mcast.net/8  anywhere
DROP       all  --  anywhere             base-address.mcast.net/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.100        192.168.1.1         tcp dpt:domain
ACCEPT     udp  --  192.168.1.100        192.168.1.1         udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  base-address.mcast.net/8  anywhere
DROP       all  --  anywhere             base-address.mcast.net/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

---

### Post by gibson on 2006-02-15
Does anybody have any ideas on this? have been tring for a few days now still to no avail....

thanks again

---

### Post by gibson on 2006-02-16
no ideas.... anyone..... :cry: 

sorry to keep bumping this one but i would really like to get this sorted... any ideas/suggestions will do - i can do most of the research myself from there but i am completley stupmed and need a push in the right direction.

all the best

gib-untu (hehe - sorry that was really bad.... even for me *slaps self*)

---

### Post by chusome on 2006-03-13
I too have been looking for a solution to this problem

Neither the default samba policy, nor adding machines to your white list allows for samba access via name, only ip address.

---

### Post by chusome on 2006-03-13
Ok, here's the closest thing to a solution that I've found
FROM:
[http://www.ubuntuforums.org/showthread.php?t=33741&](http://www.ubuntuforums.org/showthread.php?t=33741&)
[COLOR="Blue"]
In Samba, nmblookup is useful to find the current IP address of a Windows machine but it fails when the firewall is enabled.

The problematic packet is the NetBIOS Name Service answer from the Windows machine which comes back with the protocol UDP with source port 137 and a variable destination port(actually the port that was opened by nmblookup).

The way I fixed this was to add the following rule:

Code:

iptables -I INPUT -p udp --sport 137 -s <my local network IP/mask> -j ACCEPT


Maybe there is a way to tighten the rule with the --dport switch but I don't know the possible range. I've seen packets coming back at ports around 32828 as well as 1023.

I hope this will be useful to someone.

Please post any better rule.[/COLOR]

This is going in the opposite direction but you get the idea

---

### Post by DarthMandeep on 2006-03-13
A Google search for "samba firestarter" shows this as the first hit:
[http://www.fedoraforum.org/forum/archive/index.php/t-47624.html](http://www.fedoraforum.org/forum/archive/index.php/t-47624.html)

To quote the last entry:

"nevermind, i figured it out. to use the names, turn off "Block broadcasts from external network".
this is located in Firestarter under:
Edit --> Preferences --> Firewall --> Advanced Options"

This fixed the problem for me when I ran up against it many months ago.

---

### Post by chusome on 2006-03-13
Thanks Darth

This still defeats the purpose of a white list though....
Firestarter developer's take note

---

