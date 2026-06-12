---
title: "ssh port 22 connection refused with Ubuntu 11.04"
date: 2011-06-27
forum: General Help
---

### Post by ldt on 2011-06-27
In one form or another,this question has been asked here and elsewhere many times but I haven't found any of them that solve my problem. I have two Ubuntu computers running on my LAN. They both are running apache web servers and bazaar version control. I need them to be able to communicate with one another with both http and ssh (and sftp). This all worked fine until I recently upgraded one of the machines to 11.04.   

 Ubuntu 9.04: host name arden
/etc/hosts
 127.0.0.1 localhost
 127.0.1.1 arden
 192.168.1.103 natty (this is the correct IP address)
 
 Ubuntu 11.04: host name natty
/etc/hosts
 127.0.0.1 localhost
 127.0.1.1 natty
 192.168.1.109 arden (this is the correct IP address)
 
 from Ubuntu 11.04:
 in the browser [http://arden](http://arden) and [http://natty]("http://natty/") work as expected
 ssh arden works as expected
 ssh natty returns “connect to host natty port 22: connection refused
 
 from Ubuntu 9.04:
 in the browser [http://arden]("http://arden/") works as expected  
   but [http://natty]("http://natty/") and [http://192.168.1.103]("http://192.168.1.103/") hangs and never connects.
 ssh arden works as expected
 ssh -v natty returns:
 connecting to natty [192.168.1.103] port 22
 and then hangs until I kill it with ctrl+c.
 
 ping from either machine to the other and itself works OK. What am I missing?

---

### Post by electrojustin on 2011-06-27
Make sure you don't have a firewall installed on Natty, or if you do, it allows port 22. Also check port forwarding settings to see if your router still has an ssh server listed at 192.168.1.103.

---

### Post by ldt on 2011-06-27
I don't think any firewall is running. I recently installed Firestarter. I don't know much about it yet, but when I ran it the first message was firewall started. I then stopped it and it reported firewall stopped. And I exited Firestarter. So if it was running it isn't now. Still have the problem.

I have a Linksys Wireless-N router that serves as the DHCP server. It lists the client names and corresponding IP addresses that I have listed above in its client table. It is allowing Internet access to all with no blocking of any applications.

A port scan from 9.04 for arden shows 21, 22 and 80 open.
A port scan from 9.04 for natty shows only 80 open.
A port scan from a web page on the other side of the router shows nothing for any of these ports (stealth according to ShieldsUp).

1) how do I open port 22 on the 11.04 natty?
2) I can't find any port scan utility on 11.04 similar to the handy one on 9.04 (and 9.10). Is there one somewhere that I just haven't found yet?
3) would tis solve the problem?

---

### Post by ldt on 2011-06-27
I found the problem. I didn't have openssh-server installed on natty. Installing it solved both the http and ssh problems from both machines. And port 22 on natty is now open.

Thanks for your help.

---

### Post by iclestu on 2011-06-27
> **ldt said:**
> 
1) how do I open port 22 on the 11.04 natty?
2) I can't find any port scan utility on 11.04 similar to the handy one on 9.04 (and 9.10). Is there one somewhere that I just haven't found yet?
3) would tis solve the problem?

1) running openSSH server (or any equivalent) should do this automatically
2)nmap from command line works for me
3)....... try and see :-)

---

### Post by ldt on 2011-06-27
Many thanks. nmap works for me too.

---

