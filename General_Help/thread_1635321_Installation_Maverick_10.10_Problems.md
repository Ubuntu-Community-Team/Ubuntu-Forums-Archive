---
title: "Installation Maverick 10.10 Problems"
date: 2010-12-01
forum: General Help
---

### Post by Habeouscorpus on 2010-12-01
-My live disk cannot get an internet connection. 

I am using a self-burned Meerkat live CD, and it will not enable networking. Is there some kind of code fu to get this going? I have tried right clicking and selecting "Enable Networking," but it won't take. It still insists the networking is disabled. The reason I need the connection is because I have to install. 

I have a Netgear wireless router with a network, and a wired LAN to connect to.

---

### Post by NCLI on 2010-12-01
> **Habeouscorpus said:**
> -My live disk cannot get an internet connection. 

I am using a self-burned Meerkat live CD, and it will not enable networking. Is there some kind of code fu to get this going? I have tried right clicking and selecting "Enable Networking," but it won't take. It still insists the networking is disabled. The reason I need the connection is because I have to install. 

I have a Netgear wireless router with a network, and a wired LAN to connect to.
Is this both with wireless and wired LAN?

---

### Post by Habeouscorpus on 2010-12-01
Embarrassing... Now it's decided to work. Never mind.

---

### Post by NCLI on 2010-12-01
> **Habeouscorpus said:**
> Embarrassing... Now it's decided to work. Never mind.
If it ever happens again, you can use the comand "sudo ifup eth0" to connect to wired ethernet.

---

### Post by macaz1 on 2010-12-01
Often you have to wait say... 1 minute for the wireless to connect or other network cards to fully establish a connection when using a live CD.

---

