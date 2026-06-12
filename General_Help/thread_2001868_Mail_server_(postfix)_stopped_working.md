---
title: "Mail server (postfix) stopped working"
date: 2012-06-11
forum: General Help
---

### Post by grizdog on 2012-06-11
Hello all

I am running Ubuntu 10.04, postfix I don't know the version, but I installed it when I brought up the original system.

A few days ago, the mail server I run on my home machine just stopped receiving mail.  I can still send mail from it.  The attempts to get in just get the generic
```
The recipient server did not accept our requests to connect
```and they time out.  I run iptables, but I made no changes to it and it still seems properly configured, smtp is still open.  The only two things that happened about the time everything stopped were:

1. My computer was down for a few days, and by the time I brought it back up, my ISP had assigned me a new IP address, so I had to go to my registrar to tell the nameservers.  The MX record they have looks fine - it is an A record, as it should be, and does not seem to have changed, as it references the name and not the number.

2. There was some sort of kerfluffle with ipv6.  I don't know what it was, I have been avoiding dealing with ipv6 as a matter of principle, but I changed the line in the postfix configuration file from inet_protocols all to inet_protocols ipv4, ipv6 and it had no affect.

There is nothing that looks interesting in any of the mail log files - mail.err, mail.info, mail.log, and mail.warn.  It feels like some sort of secure connection problem, but why would it just happen with no changes?

Thanks for any insight

---

### Post by grizdog on 2012-06-12
OK, after more testing, it seems like the problem is in iptables - I didn't change anything in iptables, or anything else for that matter, what could it be?  here is the output from iptables:

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:ssh state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:imaps state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN limit: avg 3/min burst 3 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  192.168.1.0/24       anywhere            ctstate NEW 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere     
```Thanks for any help

---

### Post by dcstar on 2012-06-13
> **grizdog said:**
> Hello all

I am running Ubuntu 10.04, postfix I don't know the version, but I installed it when I brought up the original system.

A few days ago, the mail server I run on my home machine just stopped receiving mail.
..........
1. My computer was down for a few days, and by the time I brought it back up, **my ISP had assigned me a new IP address**, so I had to go to my registrar to tell the nameservers.  The MX record they have looks fine - it is an A record, as it should be, and does not seem to have changed, as it references the name and not the number.
.........

From another site:

```
telnet *mailserver.dns.address* 25
telnet *new.ip.address* 25
```

You should check that the DNS is actually correct.

---

### Post by grizdog on 2012-06-18
Yes, you were right.  In fact, what happened was that my ISP changed my ip address twice in quick succession.  It usually takes months, this time it only took a day - odd.  But now it works.

Thanks.

---

