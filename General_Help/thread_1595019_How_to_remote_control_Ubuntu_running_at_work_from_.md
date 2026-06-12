---
title: "How to remote control Ubuntu running at work from my home PC?"
date: 2010-10-12
forum: General Help
---

### Post by geek2330 on 2010-10-12
I have an Ubuntu 10.10 running on a pc at work.
On my Windows pc I can use a free utility called Teamviewer which you run on the pc (no install needed) and then you connect without any need to VPN into my work network.

So, what would be the best way to connect from home and remotely connect to my Ubuntu system at work?

---

### Post by geek2330 on 2010-10-13
bump.......

---

### Post by Refalm on 2010-10-13
[TeamViewer for Linux]("http://www.teamviewer.com/download/") ;)

---

### Post by lukeiamyourfather on 2010-10-13
I'd use VNC or SSH with X tunneling (e.g. ssh -X user@host). There are various VNC clients and servers, some better than others.

---

### Post by geek2330 on 2010-10-13
> **Refalm said:**
> [TeamViewer for Linux]("http://www.teamviewer.com/download/") ;)

man, i had checked their site and they didn't have it available back then, should've checked again before asking the question here.....:)

Thanks.

---

### Post by efflandt on 2010-10-13
I was wondering about this too, because last time I looked, Logmein only had a 32-bit "client" for Linux.  TeamViewer has a 64-bit .deb, and it looks like you can connect "to" Linux instead of only using it to connect "from" Linux.

---

