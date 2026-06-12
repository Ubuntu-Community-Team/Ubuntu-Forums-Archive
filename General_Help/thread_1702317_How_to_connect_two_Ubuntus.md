---
title: "How to connect two Ubuntus?"
date: 2011-03-07
forum: General Help
---

### Post by rva1945 on 2011-03-07
I set a domain name in the U 9.10 PC. It has Samba 4 installed because I  needed to connect it to a W7. Do I need Samba to connect to another  Ubuntu now?

How do I set a domain in U 10.10?

Thanks

---

### Post by YesWeCan on 2011-03-07
I always use ssh and Nautilus to browse between Ubuntu PCs. It is very simple and fast.

---

### Post by rva1945 on 2011-03-07
> **YesWeCan said:**
> I always use ssh and Nautilus to browse between Ubuntu PCs. It is very simple and fast.

Ok I go to Places-Network, the other ubuntu PC is on, but in network I see a Windows Network, no idea what it is, there's no Windows running.

I think I should set this U 10.10 to be in the same domain. How?

---

### Post by YesWeCan on 2011-03-07
You need to make each PC an ssh server, so it can accept ssh connection requests. See [https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)

You can install 'ssh' from the Software Center. Don't worry about configuring it to begin with, just try it out. It uses port 22 so if you have a firewall you must allow this port.

You use the Places/connect to server menu and you have to put in the IP address of the PC you wish to connec to, your username and password. It will connect and then give you a file browser. You can then open remote files and directories and copy to and from.

You can also connect to an ssh server from the command line, eg:
ssh charlie@192.168.1.2

ssh replaced ftp. It is the most commonly used means to make connctions between linux PCs. It has the added advantage of encrypting all data so it can be used across unsecure networks and the www.

---

