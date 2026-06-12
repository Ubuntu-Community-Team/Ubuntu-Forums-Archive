---
title: "Mobloquer blocks email, after every boot."
date: 2011-01-18
forum: General Help
---

### Post by runeh76 on 2011-01-18
Hi guys :)

I have problems with Mobloquer and Thunderbird or Evolution email. (Email is Gmail.)
When i log in Ubuntu and open mail, mobloquer block "Google Inc". 

Okey then i click "Stop blocking this IP"..everything is working BUT when i reboot, same thing and just DIFFERENT "Google Inc" IP to block.

What i miss?

runeh

edit:

got it solved with this:  gksu gedit /etc/blockcontrol/blockcontrol.conf
IP_REMOVE="Google Inc"

---

### Post by howefield on 2011-01-18
Moved to General Help.

---

