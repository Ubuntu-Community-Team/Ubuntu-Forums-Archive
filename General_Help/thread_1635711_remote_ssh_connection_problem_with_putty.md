---
title: "remote ssh connection problem with putty"
date: 2010-12-02
forum: General Help
---

### Post by danro on 2010-12-02
Hi all
I have an ubuntu 10.10 virtual box.
I've installed apache etc and can connect to it on the local LAN (home network) with PuTTY from a windows laptop.
The virtual box has it's own IP address on the LAN in the same way the other device do.

I've opened port 22 and 80 on the netgeat router and aimed them at my virtual machine, by IP address.

From the internet (work ;)) I can see the homepage fine but get a 
"PuTTY Fatal Error" message
"Network error:Connection refused"
when I try to connect with ssh

I'm confident the port forwarding is fine (but happy to recheck!)
Is there something in Ubuntu that would be refusing the connection or should I try a different port or something?

Any help advise greatly received.:D

Danny

---

### Post by Zookalicious on 2010-12-02
Make sure to install SSH. I believe it's disabled by default for security. 

```

sudo apt-get install openssh-server

```

---

### Post by efflandt on 2010-12-02
Actually by default the ssh client is installed, but the ssh server is NOT installed.  So the command Zookalicious listed will install the server.

Also make sure that your ~/.ssh directory has 700 permission (drwx------) and files in it have 600 permission (-rw-------), in other words, only your user (and root) should be able to access your .ssh directory and files.

---

