---
title: "Setting for Iptables"
date: 2011-12-05
forum: General Help
---

### Post by sil3nthunt3r on 2011-12-05
Hi,

I have search regarding this, but unable to find the solution. Hope to get support from expert here.

I want to set rule for iptables which will limit the HTTP connection (to the server) per IP to only 9. I try to put below command, but failed.

```
iptables -A INPUT -p tcp –syn –dport 80 -m connlimit –connlimit-above 9 -j REJECT –reject-with tcp-reset
```

and it give me error as below:

```
iptables v1.4.4: -c packet counter not numeric
Try `iptables -h' or 'iptables --help' for more information.
```

Hope someone can help me correct the mistake. 

My setup is Ubuntu Server 10.04

---

### Post by collisionystm on 2011-12-05
iptables -A INPUT -p tcp --dport 80 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

change eth1 to whatever adapter is answering the requests

---

### Post by phidia on 2011-12-05
I'm not an expert though I do admin a server. I think you will want to reference the ubuntu guide [here]("https://help.ubuntu.com/community/IptablesHowTo").

Also provide the thread with the output of > sudo iptables -L
I'm just getting the ball rolling.

---

### Post by sil3nthunt3r on 2011-12-05
This is the output from iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I have tried refer to the [guide]("https://help.ubuntu.com/community/IptablesHowTo") but failed to understand.
Also, the server is VPS server and the iptables is not installed by default. So I have to manually install the iptables (apt-get install iptables)

---

### Post by collisionystm on 2011-12-05
> **sil3nthunt3r said:**
> This is the output from iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```I have tried refer to the [guide]("https://help.ubuntu.com/community/IptablesHowTo") but failed to understand.
Also, the server is VPS server and the iptables is not installed by default. So I have to manually install the iptables (apt-get install iptables)


Did you see what I wrote? :confused:

This works


iptables -A INPUT -p tcp --dport 80 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

---

### Post by sil3nthunt3r on 2011-12-05
> **collisionystm said:**
> Did you see what I wrote? :confused:

This works

iptables -A INPUT -p tcp --dport 80 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

Done tried. But I still can get 12 HTTP connection when downloading via HTTP.

This is the output from iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www limit: avg 1/min burst 10

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by collisionystm on 2011-12-05
Oh you are downloading?

You do not place the rule in input. This for incoming connections only

you want it in the forward chain

---

### Post by collisionystm on 2011-12-05
iptables -A FORWARD -p tcp --dport 80 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

---

### Post by sil3nthunt3r on 2011-12-05
> **collisionystm said:**
> iptables -A FORWARD -p tcp --dport 80 -i eth1 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

Ok. Already flush the previous rule, and put the above rule. I change eth1 to eth0

iptables -A FORWARD -p tcp --dport 80 -i eth0 -m limit --limit 1/minute --limit-burst 10 -j ACCEPT

Still can get 16 HTTP connection while downloading..

change the eth0 to eth1, can get 12 HTTP connection while downloading. :confused::confused:

Basically, I want to limit 8 connection while downloading without interrupt the user to browse the same site.

---

### Post by collisionystm on 2011-12-05
iptables -A FORWARD -p tcp --syn --dport 80 -m connlimit --connlimit-above 12 -j REJECT --reject-with tcp-reset

I was reading this 

[http://www.cyberciti.biz/faq/iptables-connection-limits-howto/](http://www.cyberciti.biz/faq/iptables-connection-limits-howto/)

Hope it works

---

### Post by collisionystm on 2011-12-05
> **collisionystm said:**
> iptables -A FORWARD -p tcp --syn --dport 80 -m connlimit --connlimit-above 12 -j REJECT --reject-with tcp-reset

I was reading this 

[http://www.cyberciti.biz/faq/iptables-connection-limits-howto/](http://www.cyberciti.biz/faq/iptables-connection-limits-howto/)

Hope it works


nevermind. its a clone of your OP.

sorry about that

---

### Post by sil3nthunt3r on 2011-12-05
> **collisionystm said:**
> nevermind. its a clone of your OP.

sorry about that

Haha..if only that command works for me.

iptables -A INPUT -p tcp --dport 80 -i eth0 -m limit --limit 1/minute --limit-burst 9 -j ACCEPT

For above command, basically it works, but user will have difficulties to browse the same site using http, where the site will not load.

---

### Post by collisionystm on 2011-12-05
I guess that's the problem with Downloads and HTTP traffic going through the same port

---

### Post by collisionystm on 2011-12-05
maybe just limit how much bandwidth a user can have at any given time?

---

### Post by sil3nthunt3r on 2011-12-05
> **collisionystm said:**
> maybe just limit how much bandwidth a user can have at any given time?

Bandwidth is not a problem since the VPS is unmetered.
Right now, I've increased the MaxKeepAliveRequests from httpd.conf from 100 to 300 and implement the command below:

iptables -A INPUT -p tcp --dport 80 -i eth0 -m limit --limit 1/minute --limit-burst 9 -j ACCEPT

---

### Post by sil3nthunt3r on 2011-12-06
Some update:

```
iptables -p tcp --syn --dport 80 -m connlimit --connlimit-above 16 --connlimit-mask 24 -j REJECT
```

Why when I put above command, it give me error as below: 

***iptables: No chain/target/match by that name.***

Ubuntu Server 10.04

---

### Post by Doug S on 2011-12-06
> **sil3nthunt3r said:**
> Some update:
 
```
iptables -p tcp --syn --dport 80 -m connlimit --connlimit-above 16 --connlimit-mask 24 -j REJECT
```
 
Why when I put above command, it give me error as below: 
 
***iptables: No chain/target/match by that name.***
 
Ubuntu Server 10.04
I do not get the same error with your exact code as above. Anyway, you didn't specify a chain. I don't know if you wanted the INPUT chain or elsewhere, but this worked for me (meaning executed without error):
```
 
sudo iptables -A INPUT -p tcp --syn --dport 80 -m connlimit --connlimit-above 16 --connlimit-mask 24 -j REJECT 

```

---

### Post by sil3nthunt3r on 2011-12-06
> **Doug S said:**
> I do not get the same error with your exact code as above. Anyway, you didn't specify a chain. I don't know if you wanted the INPUT chain or elsewhere, but this worked for me (meaning executed without error):
```
 
sudo iptables -A INPUT -p tcp --syn --dport 80 -m connlimit --connlimit-above 16 --connlimit-mask 24 -j REJECT 

```

Still got same error with the code you given above.

Is there any issue with my Ubuntu because the VPS is installed with Ubuntu 10.04, without iptables installed by default. Have to manually installed it.

---

