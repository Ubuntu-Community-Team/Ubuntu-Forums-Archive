---
title: "SSH Woes"
date: 2011-10-02
forum: General Help
---

### Post by koaxle on 2011-10-02
I have a fresh install of 11.04 server on a new server, it has 2 NICS eth0 192.168.1.157 and eth1 192.168.1.254

I am able to SSH to both interfaces from inside the local network with no issues, but when I try and connect from outside the connection times out after about 15 seconds. I know the forwarding rules work because the server this is replacing used to listen to ssh on 192.168.1.157 and I took a capture on that interface and I see 4 SSH SYN packets come in from outside but there is no response.

I checked hosts.allow and hosts.deny and my iptables and everything is bare. What else can I look in to that would cause the box to not respond to outside SSH?

---

### Post by Doug S on 2011-10-02
Isn't two NICS on the same subnet a no no?
see: [http://ubuntuforums.org/showthread.php?t=1405144](http://ubuntuforums.org/showthread.php?t=1405144) 
what are the results of "route -n"?

---

### Post by koaxle on 2011-10-02
> **Doug S said:**
> Isn't two NICS on the same subnet a no no?
see: [http://ubuntuforums.org/showthread.php?t=1405144](http://ubuntuforums.org/showthread.php?t=1405144) 
what are the results of "route -n"?

One of them is not configured with a default route. I tried without eth1 in and still experienced the same issues.

---

### Post by prodigy_ on 2011-10-02
Try to telnet to SSH port from outside. If you'll get timeout, there are 3 possible reasons:
1) Port isn't actually forwarded or sshd isn't bound to it. Re-check configs.
2) Broken routing. Try to telnet to some other open port.
3) A firewall somewhere between the client and the server is dropping packets.

---

### Post by jamesisin on 2011-10-02
I was having a similar problem trying to ssh back here from work.  I knew I had my server and router correct (after much digging and head scratching).  It was our firewall at work not allowing the outgoing connection.

---

### Post by Miqi on 2011-10-02
I'm pretty new to the forums, but I've been SSHing for a few years andin case of a firewall I found that dynamic port forwarding worked for me.

---

### Post by koaxle on 2011-11-08
Got it working, after packet captures at 3 different points I narrowed it down to a config issue on the box itself.

It helps to make sure you have a default route out to the internet :)

---

### Post by markbl on 2011-11-09
> **jamesisin said:**
> (after much digging and head scratching).  It was our firewall at work not allowing the outgoing connection.
This is common. I configure my home modem/router to listen on port 443 (https) and forward that to port 22 (ssh) on my internal linux server. Then you can "ssh -p443 [email]home@somewhere.com[/email]" or equivalent from your work and it is likely not to be blocked.

---

