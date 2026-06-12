---
title: "Apache2 stopped working :/"
date: 2011-08-25
forum: General Help
---

### Post by hakermania on 2011-08-25
Hello, I had apache2 running on my machine which has a static **local** address 192.168.1.254.
I was running apache2 and I'd tested it from the other local machines and all were OK till the moment I realized that my server is non-responsive from the other local machines :(


I don't know what happened, but I can see the apache2 processes running, also note that restarting the server didn't gave me any solution...

Thanks for any tip.:guitar:

---

### Post by hakermania on 2011-08-26
*bump*

---

### Post by apollothethird on 2011-08-26
> **hakermania said:**
> Hello, I had apache2 running on my machine which has a static **local** address 192.168.1.254.
I was running apache2 and I'd tested it from the other local machines and all were OK till the moment I realized that my server is non-responsive from the other local machines :(


I don't know what happened, but I can see the apache2 processes running, also note that restarting the server didn't gave me any solution...

Thanks for any tip.:guitar:
Can you ping the server machine from the remote machine?

What do you get when you run the browser from the local machine at [http://localhost](http://localhost) ?

What do you get when you telnet to port 80 from the remote machine?

```
 telnet 192.168.1.254 80
```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by hakermania on 2011-08-28
Thanks for the reply, as I mentioned earlier the server is dead remotely(from other machines in the same local network) and works fine if I place localhost in the local PC running the server.
So, my answers are:
1) No, server is unresponsive
2) Normally the page that I have as index.html
3) Unresponsive again

---

### Post by hakermania on 2011-08-29
*bump*

---

### Post by hakermania on 2011-08-30
bump

---

### Post by hakermania on 2011-09-01
bump

---

### Post by AlexDudko on 2011-09-01
If the server is not reachable from other machines it can be firewall that blocks the access.
Try
> iptables -L
to see which ports and protocols are blocked.

---

### Post by hakermania on 2011-09-02
Hi alex, thanks for the answer, I get:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  my.siemens           anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  my.siemens           anywhere            
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

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.254        my.siemens          tcp dpt:domain 
ACCEPT     udp  --  192.168.1.254        my.siemens          udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
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

```

---

### Post by apollothethird on 2011-09-02
> **hakermania said:**
> Thanks for the reply, as I mentioned earlier the server is dead remotely(from other machines in the same local network) and works fine if I place localhost in the local PC running the server.
So, my answers are:
1) No, server is unresponsive
2) Normally the page that I have as index.html
3) Unresponsive again

When you mentioned server dead you didn't specify every port as being dead.  A machine will appear dead remotely depending on the way it's being accessed (port/programs).  Thanks for taking the time for this update.


Try disabling your firewall momentarily, then test the ports.  Then re-enable the firewall.

You can add the paranoid option to the  /etc/hosts.deny file during this interim, while you run this test.  If you find it's your firewall blocking access you'd have to fine-tune your firewall to allow the web access to your local machines.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by hakermania on 2011-09-04
thanks, it was firewall issue after all :)

---

