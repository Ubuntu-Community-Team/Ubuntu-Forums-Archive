---
title: "Samba ports"
date: 2010-04-07
forum: General Help
---

### Post by derek71 on 2010-04-07
I have Samba 3 installed and running under 8.04 server edition.  I am setting up a firewall for the server and have opened the regular Samba ports: 137, 138, 445.

I would like to leave share browsing operational on my Windows XP machine, though it seems to require a range of ports to be open on the server side.

Is there a way to restrict or specify the necessary ports used by Samba for share browsing, or is a function of the Windows client?

---

### Post by 3rdalbum on 2010-04-07
What are you running on the server that listens to incoming ports AND you don't want computers on your network to access it? Do you really need the firewall on the Ubuntu server? If Samba is the only service installed, then it's the only thing listening, and you don't need a firewall.

---

### Post by derek71 on 2010-04-07
The server is behind a router with some firewall capability, I wanted to add some additional protection since it will be running 24/7.  I did not want to leave the extra ports open if I did not need them to.

---

