---
title: "iptables not dropping packets?"
date: 2011-11-13
forum: General Help
---

### Post by bnhrobotics on 2011-11-13
I have a home server, and I just installed fail2ban for added security. It is successfully adding rules to my iptables, but I don't think the packets are actually being dropped. For example, I'll ssh into my work computer and ssh into my server, but type in bogus paswords. Then my work computer shows up in the iptables as shown below. However, even after that rule has been added, I can still ssh into my server. Perhaps I am misunderstanding something, but it seems that the iptables are not actually dropping the packets from my work computer. Any thoughts?

Output of iptables -L:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-apache-proxy  tcp  --  anywhere             anywhere            multiport dports www,https 
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-apache-proxy (1 references)
target     prot opt source               destination         
DROP       all  --  58.218.199.227       anywhere            
DROP       all  --  58.218.199.147       anywhere            
RETURN     all  --  anywhere             anywhere            

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
DROP       all  --  XXXXXX.sp.cs.cmu.edu  anywhere            
RETURN     all  --  anywhere             anywhere  
```

---

### Post by bnhrobotics on 2011-11-14
I still can't figure this out. Any suggestions?

---

### Post by bnhrobotics on 2011-11-15
Ok, so I figured it out with a bit of tinkering. Turns out ssh (keyword used by both fail2ban and iptables) is looked up in /etc/services. The default port is listed as 22. I'm using a non standard port, so iptables was not banning the right port (although, I think it should have been banning every port). Either way, editing my services file got it to drop packets at least on the offending port.

I hope this helps somebody else someday. =)

---

