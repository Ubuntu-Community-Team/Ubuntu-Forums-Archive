---
title: "Enable SSH, rlogin etc."
date: 2006-03-27
forum: General Help
---

### Post by riwa on 2006-03-27
I have the program but whenever I try to connect somewhere I get a:
Connection refused error. I've read somewhere that ssh is disabled by default. How do I enable it?

Also how do I enable rlogin, telnet and talk. Thay also seem 'disconnected'.

Regards
Richard

---

### Post by dragonfyre13 on 2006-03-27
At least with SSH, you need to install it with Synaptic, or Apt-get. Grab the ssh server, and away you go. Also, make sure to open that port in any firewall you have.

---

### Post by riwa on 2006-03-29
Well I have the programs and everything but they don't seem to be operateble. I ALWAYS get connection refused on everything. ftp, telnet, rlogin, ssh etc. So it must have something to do with some setting that doesn't allow connecting to external hosts or something. 

Any ideas?

---

### Post by Ian Maxwell on 2006-03-29
Look under System -> Administration -> Services. Somewhere on the list of services that pops up should be ssh, rlogin, etc. If they are not there, they must be installed; if they are there and unchecked, they must be checked.

If this does not work, make sure you are not behind a router that blocks most incoming traffic. If you are, you will have to set up port forwarding--how to do this depends on your router.

---

### Post by riwa on 2006-03-29
The only thing there (that matters) is ssh and it's checked. So it's my router then? I guess nobody can help then ;/.

Thanks anyway..

++
I found something about the /etc/hosts.allow file and maybie it's the bandit. Don't really know how to configure it? Is it like: $HOST=$IP or what??

---

### Post by haircut on 2006-03-29
Your router is the right place to look.

Try opening/forwarding port 22 and see.

I also get other srange problems accessing my Linux box from "outside", even when I set it to DMZ. It has something to do with the other Windose box on the network, If I boot the machines in a particular order things work OK.

---

### Post by riwa on 2006-03-29
I honestly don't know what forwarding/open port 22 means much less how to do it. But if I found out how I will. 

It's another *nix machine I'm trying to connect to.

---

