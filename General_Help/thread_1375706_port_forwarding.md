---
title: "port forwarding"
date: 2010-01-08
forum: General Help
---

### Post by cucuru on 2010-01-08
hello, I'm trying to configure a port forwarding in my computer, I want all the traffic incoming in one port is forward to other computer and port, but I can't, I have no idea how could I do that. Would it be something like that?

> 

sudo iptables -A FORWARD -s localhost -d xx.x.x.x --dport yyyy -j ACCEPT



Thank you for your help.

Regards

---

### Post by cdenley on 2010-01-08
Use rinetd. I don't think you can accomplish this with iptables unless you are using your linux system as a router.

---

### Post by cucuru on 2010-01-11
Hello, rinetd likes very interesting, but I have a problem with it. I want redirect all my ssh traffic to another port, but rinetd can't be used in a port which is already used, how can I solved this problem?

Thank you!

Regards

---

### Post by cdenley on 2010-01-11
> **cucuru said:**
> Hello, rinetd likes very interesting, but I have a problem with it. I want redirect all my ssh traffic to another port, but rinetd can't be used in a port which is already used, how can I solved this problem?

Thank you!

Regards

You can't. How is your computer supposed to know what traffic is supposed to be redirected and what traffic should be handled locally? It is all going to the same port and the same IP. There is no way to differentiate unless you have the traffic going to seperate ports and/or IP's.

---

