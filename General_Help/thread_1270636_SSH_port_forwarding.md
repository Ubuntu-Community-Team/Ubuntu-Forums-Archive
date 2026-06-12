---
title: "SSH port forwarding"
date: 2009-09-19
forum: General Help
---

### Post by carloshiga on 2009-09-19
Hi everyone,

in my university I can download some research articles from Nature magazine, for example, but when I'm at home I need to connect to a server in the university and do some port forwarding with SSH:

```
ssh -L 3128:proxy.university.com:3128 university.com
```

Then I need to configure the Firefox in Edit -> Preferences -> Advanced -> Network -> Connection settings to manual proxy configuration:

HTTP Proxy: localhost
Port: 3128

and i check the "Use this proxy server for all protocols" box. The problem is that this is not working anymore because I think that the network administrator closed the port or something like that. But I have a computer working as a server there and now I'm trying to use it to do the same thing I was doing before:

```
ssh -L 3128:myserver:3128 myserver
```

The connection seems to be ok, but the Firefox shows a blank page for every website and in my terminal I see the message:

```
channel 3: open failed: connect failed: Connection refused
```

I already tried to do something like this in the server:

```
sudo iptables -A INPUT -p tcp --dport 3128 -j ACCEPT
```

but it does not work too. Here is the iptables -L result:

```
user@myserver:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level warning 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I tried some other stuffs that I found Googling but I got no sucess. Any idea?

---

