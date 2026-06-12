---
title: "iptables - a question"
date: 2011-09-02
forum: General Help
---

### Post by mbuell on 2011-09-02
A few years ago, when I started trying to learn about iptables, all the tutorials/tips/stories talked about 3 main categories. They all still do - but iptables now contains 6 categories of rules. 

For instance, iptables -L shows me an

**INPUT** section

AND, later on, it has an **INBOUND** section!

Ditto **OUTPUT** and **OUTBOUND** - what's the difference?

---

### Post by Habitual on 2011-09-02
good and basic what's up on iptables (by example even)

[http://www.thegeekstuff.com/2011/06/iptables-rules-examples/](http://www.thegeekstuff.com/2011/06/iptables-rules-examples/)

and the man page always should be the first resort.
[http://man.cx/iptables](http://man.cx/iptables)

---

### Post by mbuell on 2011-09-04
While I thank you for your answers, and for the effort, I have to believe the question was not clear to you. The links you have provided do not even touch upon what I have asked to clarify. The man page does not mention the Chain definitions I am asking about. So, obviously, I will have to be more specific. Let me show an example. Of course, it is somewhat truncated, with the names changed, for simplicity. Otherwise, it is an actual iptables ruleset. 

I have highlighted the Chains in question - namely Input/Inbound, and Output/Outbound. 
 
Start with a simple request for the current iptables ruleset:
```
me@myserver:~$ sudo iptables -L
[sudo] password for me: 
```

Result:
```

Chain **[COLOR="Blue"]INPUT[/COLOR]** (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  198.16.0.1           anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  198.16.0.1           anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             198.16.0.255        


Chain FORWARD (policy DROP)
target     prot opt source               destination         
 
Chain **[COLOR="Blue"]OUTPUT[/COLOR]** (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  uthor                198.16.0.1          tcp dpt:domain 
ACCEPT     udp  --  uthor                198.16.0.1          udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            

Chain **[COLOR="Blue"]INBOUND [/COLOR]** (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  198.16.0.0/24        anywhere  

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere     

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain **[COLOR="Blue"]OUTBOUND [/COLOR]** (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere       
 
```

That is pretty much it. Every reference I have found only mentions the INPUT and OUTPUT chains. Nobody mentions the INBOUND and OUTBOUND chains. Or at least not that I have found. If you HAVE seen a reference to them, of course, this is what I am asking for. Why are they there? Why are both used?

---

### Post by Doug S on 2011-09-04
I think the OUTBOUND and INBOUND chains are user defined.
I assume the references are not listed because they are not in the filter area.
Perhaps supply the output for ```
sudo iptables -t nat -n -L -v -x
```(the -v and -x are just options that I always use, you can leave them out if you like)
And/or supply the output for ```
sudo iptables-save -c
```(again the -c option is just something I always use, you can leave it out if you want)

---

### Post by mbuell on 2011-09-05
User-defined - I have been continuing to read stuff in my spare time, and I had come to this conclusion also. I think you are right. 

First - the output you requested:```
Chain PREROUTING (policy ACCEPT 10569 packets, 930235 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 513 packets, 40649 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 545 packets, 42890 bytes)
    pkts      bytes target     prot opt in     out     source               destination  
```

Now, I'm going to repost the results of my iptables -L command, but this time I will have more highlights:
```

Chain [COLOR="Blue"]INPUT[/COLOR] (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  198.16.0.1           anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  198.16.0.1           anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             198.16.0.255        
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
[COLOR="Red"]LSI[/COLOR]        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
[COLOR="Red"]INBOUND[/COLOR]    all  --  anywhere             anywhere            
[COLOR="Red"]LOG_FILTER[/COLOR]  all  --  anywhere             anywhere            
[COLOR="Red"]LOG[/COLOR]        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain [COLOR="Blue"]FORWARD[/COLOR] (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
[COLOR="Red"]LOG_FILTER[/COLOR]  all  --  anywhere             anywhere            
[COLOR="Red"]LOG[/COLOR]        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain [COLOR="Blue"]OUTPUT[/COLOR] (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  uthor                198.16.0.1          tcp dpt:domain 
ACCEPT     udp  --  uthor                198.16.0.1          udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
[COLOR="Red"]OUTBOUND[/COLOR]   all  --  anywhere             anywhere            
[COLOR="Red"]LOG_FILTER[/COLOR]  all  --  anywhere             anywhere            
[COLOR="Red"]LOG[/COLOR]        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain [COLOR="Red"]INBOUND[/COLOR] (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  198.16.0.0/24        anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:nntp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:119 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh 
ACCEPT     tcp  --  198.16.0.0/24        anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  198.16.0.0/24        anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  198.16.0.0/24        anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  198.16.0.0/24        anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  198.16.0.0/24        anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  198.16.0.0/24        anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  198.16.0.0/24        anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  198.16.0.0/24        anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:microsoft-ds 
[COLOR="Red"]LSI[/COLOR]        all  --  anywhere             anywhere            

Chain [COLOR="Red"]LOG_FILTER [/COLOR](5 references)
target     prot opt source               destination         

Chain [COLOR="Red"]LSI[/COLOR] (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain [COLOR="Red"]LSO[/COLOR] (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain [COLOR="Red"]OUTBOUND[/COLOR] (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

```

Once I had the idea that the chain names might be user-defined, I went back and looked in the rules for them - and bingo - you can see for yourself, the ruleset is using these user-defined chain names and passing defined traffic to them. Well, ok then - now that we have figured that out ---

Chapeau for the help folks!
:D

:guitar:

---

### Post by mbuell on 2011-09-05
Oh - and just in case anybody wants to dig deeper - like if you want to know which of those names we were looking at are provided by default in iptables? Also, btw, they are called TARGETS.

[http://www.faqs.org/docs/iptables/targets.html]("http://www.faqs.org/docs/iptables/targets.html")

ACCEPT, DROP, REJECT, LOG, and more are default targets in iptables. But, as we have seen, you can create a target simply by putting the target name in the ruleset in one of the standard areas (which seem to be limited to INPUT, FORWARD, OUTPUT).

---

### Post by Doug S on 2011-09-05
O.K., that makes much more sense now. I guess the first listing was incomplete. Now, all the references add up.

---

