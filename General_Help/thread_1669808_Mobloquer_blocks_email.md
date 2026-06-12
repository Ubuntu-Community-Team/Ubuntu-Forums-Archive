---
title: "Mobloquer blocks email"
date: 2011-01-18
forum: General Help
---

### Post by runeh76 on 2011-01-18
Hi guys :)

I have problems with Mobloquer and Thunderbird or Evolution email. (Email is Gmail.)
When i log in Ubuntu and open mail, mobloquer block "Google Inc". 

Okey  then i click "Stop blocking this IP"..everything is working BUT when i  reboot, same thing and just DIFFERENT "Google Inc" IP to block.

What i miss?

runeh

edit... I have UBUNTU 10.10

---

### Post by runeh76 on 2011-01-18
Okey SOLVED!


edit:

Got it solved with this: gksu gedit /etc/blockcontrol/blockcontrol.conf
IP_REMOVE="Google Inc"


runeh

---

### Post by jre on 2011-01-19
There is certainly no conflict between mobloquer and moblock.

Google's mail server have several IPs. As soon as you have whitehlisted about 5-20 of them you will normally have no more problems.

Your solution that you posted in another thread (IP_REMOVE="google") is one way to solve the problem. Alternatively you may open the whole eMail (IMAP or POP) port (easy, but security risk), or you may choose less blocklists.

---

### Post by jre on 2011-01-19
[deleted double post]

---

