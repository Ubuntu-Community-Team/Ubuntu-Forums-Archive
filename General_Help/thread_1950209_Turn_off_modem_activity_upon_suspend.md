---
title: "Turn off modem activity upon suspend?"
date: 2012-03-31
forum: General Help
---

### Post by donsy on 2012-03-31
When I suspend my laptop, the modem PC-Activity light stays on as if I were still connected. The last version of Ubuntu on which it turned off was 8.04. Is there some fix for this so that upon suspend, when the computer is disconnected from the Internet, the activity light turns itself off indicating that the PC is indeed inactive?

---

### Post by gordintoronto on 2012-03-31
Brand and model of laptop? I don't understand what you mean when you say "modem PC-Activity light." Can you describe this further, please?

---

### Post by HiImTye on 2012-04-01
modem or ethernet port? there's no reason the modem will stay on but the ethernet port will stay on if your system supports magic packets (Wake-on-LAN or WAL)

---

### Post by donsy on 2012-04-01
> **gordintoronto said:**
> Brand and model of laptop? I don't understand what you mean when you say "modem PC-Activity light." Can you describe this further, please?

Dell Inspriron 17R. The PC-Activity light is on when an ethernet connection is active between the PC and the modem. It does not appear related to "Send, Receive, and Online" for upstream/downstream communications between the modem and the cable company (COX).

> **HiImTye said:**
> modem or ethernet port? there's no reason the modem will stay on but the ethernet port will stay on if your system supports magic packets (Wake-on-LAN or WAL)

Mororola SB5101U with ethernet direct connection and no router. I think you're on to something with the Wake-on-LAN issue because I notice that when I suspend and the connection disconnects, the light goes off momentarily but starts up again after the suspension.

---

### Post by donsy on 2012-04-01
Confirmed, it's WOL.

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

