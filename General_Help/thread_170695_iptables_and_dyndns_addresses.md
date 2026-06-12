---
title: "iptables and dyndns addresses?"
date: 2006-05-05
forum: General Help
---

### Post by CyberAngel on 2006-05-05
Hi, I am trying to setup my iptables but I realized a small problem with dyndns remote addresses....
I will reffer to my following example.
When I setup my rules, iptables will resolve the ip at the time I am passing the rule, and it will add it to my INPUT chain (as IP). But if the remote host`s ip change then the rules I have already added are useless. I am not letting the people I want to ping me, and someone else that I don`t know has taken this IP can (Something that I don`t want to). 

e.g. I want to cut all pings from outside to inside except of 2-3 hosts that they are using dyndns.
So I am using the following commands:

```

IPTABLES=/sbin/iptables

$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A INPUT -p icmp -s xxx.dyndns.org -j ACCEPT
$IPTABLES -A INPUT -p icmp -s xxx.kicks-***.net -j ACCEPT
$IPTABLES -A INPUT -p icmp -s xxx.ath.cx -j ACCEPT
$IPTABLES -A INPUT -p icmp -j DROP

```

At the time I am passing the rule xxx.dyndns.org might have 150.120.140.10 as IP, but tomorrow he might have 150.120.140.20. So Tomorrow xxx.dyndns.org cannot ping me but 150.120.140.10 that is someone else and I don`t know him can.

Any solutions?

---

### Post by foxystoatyweasely on 2007-03-23
Bumped - same problem here. Thanks in advance if anyone can help?

How do I set up an iptables rule which will listen for any changes to my ISP-allocated IP address and update itself so as to continue to allow access from DynDNS?

---

### Post by moore.bryan on 2007-03-23
[I]perhaps [this link]("http://www.ubuntuforums.org/showthread.php?t=111972") will help.
[/I]

---

### Post by CyberAngel on 2007-03-23
I haven`t found a solution yet :(
But the truth is that I have not search it thoroughly again from when I posted this question (Almost a year now) :)

---

### Post by moore.bryan on 2007-03-23
> **CyberAngel said:**
> I haven`t found a solution yet :(
*did you check the thread i reposted above?*

---

### Post by CyberAngel on 2007-03-23
> **moore.bryan said:**
> *did you check the thread i reposted above?*

Not yet cause I haven`t free time now....
I just answered to foxystoatyweasely :)

I will check it maybe tomorrow and I will post again if it fits to me :)
Thanks anyway!!

---

### Post by moore.bryan on 2007-03-23
*good deal... hope it works for you!*

---

### Post by foxystoatyweasely on 2007-04-01
Thank you everyone for all the assistance received. I've also found a rather eloquent solution to this problem at the following site:

[http://dave.thehorners.com/](http://dave.thehorners.com/)

I also emailed the guy who was very helpful and he's provided some great stuff on his site too.

Many thanks Dave!! :)

---

