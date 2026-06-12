---
title: "Why don't my router show up in Network?"
date: 2009-11-05
forum: General Help
---

### Post by dixie460 on 2009-11-05
When I go to Places > Network > Windows Network > Workgroup, it shows all other computers on my LAN (all are running some variant of windows), but not my Linksys WRT54GL running Tomato firmware. I can connect thru and http into the router just fine, it just isn't visible. If I look at my network infrastructure from windows my router is shown along with the other windows machines. I would've though that my Linux based router would be visible to a Linux-based machine more so than a windows machine...any thoughts on why it don't show up? Just to be clear about this, I am having absolutely no issues whatsoever with the router or my network connection from karmic, this is more of a "I wonder why...?" type question.

Thanks!

Andy

---

### Post by Iowan on 2009-11-05
> **dixie460 said:**
> When I go to Places > Network > [COLOR="Red"]Windows Network[/COLOR] > Workgroup, it shows all other computers on my LAN (all are running some variant of windows), but not my Linksys WRT54GL running Tomato firmware. ...I would've though that my Linux based router would be visible to a Linux-based machine more so than a windows machine...Perhaps if the router had a Windows share...
I suspect other linux-based machines (without Samba) would also be invisible to a Linux machine  checking a Windows network.

---

### Post by undecim on 2009-11-05
Your router is going to report itself as a member of a workgroup. The router's job is to take all the different computers and let them share a single internet connection, not share files.

It is part of the network infrastructure, and you can see it in linux. If you look at your network connection information (by right clicking on the network manager) you will see that the "Default Gateway" address is your router's IP address.

There is also the traceroute, which traces a connection from one router to another (useful for determining the structure of a network)

---

### Post by dixie460 on 2009-11-06
Ah ok, it makes sense now. Thanks!!

Andy

---

