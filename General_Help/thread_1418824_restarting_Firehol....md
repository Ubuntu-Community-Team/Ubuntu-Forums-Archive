---
title: "restarting Firehol..."
date: 2010-03-01
forum: General Help
---

### Post by karthick87 on 2010-03-01
When i restart firehol,it shows the following message..What it mean???

karthick@Learners-desktop:~$ sudo /etc/init.d/tinyproxy restart
Restarting tinyproxy: tinyproxy.
karthick@Learners-desktop:~$ sudo /etc/init.d/firehol restart
 * Firewall disabled via /etc/default/firehol

---

### Post by karthick87 on 2010-03-03
Bump...

---

### Post by QLee on 2010-03-03
> **getyourkarthick said:**
> When i restart firehol,it shows the following message..What it mean???

karthick@Learners-desktop:~$ sudo /etc/init.d/tinyproxy restart
Restarting tinyproxy: tinyproxy.
karthick@Learners-desktop:~$ sudo /etc/init.d/firehol restart
 * Firewall disabled via /etc/default/firehol

It means what it says, * Firewall disabled via /etc/default/firehol. Did you have a look at that file to see if it explains anything? I'm not familiar with firehol, is the ufw that comes with Ubuntu not sufficient for your needs? Most people here use the one that comes with the system and could help more with that. Probably why not many replies.

---

