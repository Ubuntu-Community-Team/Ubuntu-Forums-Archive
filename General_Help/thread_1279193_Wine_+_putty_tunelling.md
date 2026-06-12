---
title: "Wine + putty tunelling"
date: 2009-09-30
forum: General Help
---

### Post by JigglyWiggly_ on 2009-09-30
Ok so the network I am on blocks all traffic except on port 8080, 80, 25, 443. So I connect to my ssh server on port 8080, then I tunnel my traffic through putty by going to the tunnels options and create a dynamics socks proxy of 7070. Then I go to the proxy manager and put a manual proxy and set it to manual, and socks 127.0.0.1 on port 7070. It works, chrome connects my wanip is my house's. However I try to play Jedi Outcast(in wine), and it can't see any servers... and I can't connect by ip either making me think it's not using the gnome proxy settings.

Anyone got any idea? Also pidgin isn't seeming to connect either :? (Also I have switched my dns serves on this network to cisco's public one, since the dns here uses opendns and blocks sites)

Oddly enoguh it was working at one point.(Pidgin that is)

---

### Post by JigglyWiggly_ on 2009-09-30
Anyone...?

---

### Post by orange-wedge on 2009-09-30
i doubt wine would use the proxy server settings from gnome.  do you know what ports jedi outcast uses to play online?  it may be easier to purchase a router that has port forwarding than setting up several ssh tunnels.

---

### Post by JigglyWiggly_ on 2009-10-01
> **orange-wedge said:**
> i doubt wine would use the proxy server settings from gnome.  do you know what ports jedi outcast uses to play online?  it may be easier to purchase a router that has port forwarding than setting up several ssh tunnels.

Thing is I'm not admin here. Just a person who loves to use the internet for other purposes :P I guess I guss I can just boot into win 7 if I need to play it. Kind of inconvenient(Also outbound is blocked, as well as inbound, so it doesnn't have to do with port forwarding)

---

