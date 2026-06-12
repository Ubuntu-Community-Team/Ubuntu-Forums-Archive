---
title: "Tor cannot bind to port 9050"
date: 2012-06-03
forum: General Help
---

### Post by MetaX360 on 2012-06-03
when i run tor, it cannot bind to port 9050, (tor is not running, i checked in sys moniter) ive looked at the settings in vidalia and it does not offer a way to change that port as far as i can see, maybe theres a way to change the port by editing the torrc file? btw port 9051 works just fine and vidalia offers to change that port but why not the other? i am running a clean install of ubuntu precise pangolin.

---

### Post by oldos2er on 2012-06-03
Post moved to its own thread.

---

### Post by jim_deadlock on 2012-06-03
All of that stuff on the post you replied to has become redundant since the Tor browser bundle was released. All you need to do is download the bundle and run it, no need to even install. Messing around with ports and config files is a thing of the past.

---

### Post by jenic on 2012-06-03
> **MetaX360 said:**
> when i run tor, it cannot bind to port 9050, (tor is not running, i checked in sys moniter) ive looked at the settings in vidalia and it does not offer a way to change that port as far as i can see, maybe theres a way to change the port by editing the torrc file? btw port 9051 works just fine and vidalia offers to change that port but why not the other? i am running a clean install of ubuntu precise pangolin.
 
Do a 'netstat -ltn' and/or 'lsof -i' to see if something is taking port 9050. Then do a 'man torrc' and search for '9050' which will lead you to your answer:

> [B]
SocksPort[/B] *PORT*[INDENT]Advertise this port to listen for connections from Socks-speaking applications. Set this to 0 if you don't want to allow application connections. (Default: 9050)
[/INDENT]

---

### Post by haqking on 2012-06-03
> **jim_deadlock said:**
> All of that stuff on the post you replied to has become redundant since the Tor browser bundle was released. All you need to do is download the bundle and run it, no need to even install. Messing around with ports and config files is a thing of the past.

Tor is not just used for webbrowsing.

---

