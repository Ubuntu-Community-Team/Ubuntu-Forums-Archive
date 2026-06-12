---
title: "Thunderbird / Firestarter / UFW Problems"
date: 2010-12-20
forum: General Help
---

### Post by nogoingback on 2010-12-20
.

---

### Post by QLee on 2010-12-20
You certainly don't want dueling firewall applications. Completely purge Firestarter, get rid of all the rules you manually wrote for iptables and turn off ufw. In other words get back to basics. Thunderbird should work then. After that you could turn on ufw if you need it for some reason. A default install isn't listening for connections on any port so you don't really need to block anything. If you install some services that listen for connections you could then add firewall rules. The ufw GUI, named gufw is recommended.

---

### Post by nogoingback on 2010-12-20
.

---

### Post by nogoingback on 2010-12-21
.

---

### Post by nogoingback on 2010-12-22
.

---

### Post by QLee on 2010-12-22
[QUOTE=nogoingback]Hello, does anybody here have any expertise in these matters?[/QUOTE]

Well, I have over 30 years experience but you are correct, experience does not necessarily translate into expertise.

Our two posts will bring your question back to the top where it will get the attention it deserves.

---

### Post by QLee on 2010-12-22
> **nogoingback said:**
> Hello, does anybody here have any expertise in these matters?

Nogoingback, 

I see that bodhi.zazen is currently active in the forums and he is expert in these matters. There is a good chance your thread will be noticed.

---

### Post by oldos2er on 2010-12-22
> **nogoingback said:**
> Hello, does anybody here have any expertise in these matters?

A better place to discuss firewall issues would be the Security Discussions forum.

---

### Post by nogoingback on 2010-12-23
.

---

