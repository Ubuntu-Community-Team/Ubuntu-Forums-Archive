---
title: "Mobloquer block Thunderbird/Evolution after reboot"
date: 2011-01-19
forum: General Help
---

### Post by runeh76 on 2011-01-19
Hi guys :smile:

I have problems with Mobloquer and Thunderbird or Evolution email. (Email is Gmail.)
When i log in Ubuntu and open mail, mobloquer block connection "Google Inc". 

Okey  then i click "Stop blocking this IP"..everything is working, BUT  when i  reboot, same thing and just DIFFERENT "Google Inc" IP to block.

I tried to reinstall Mobloguer and Blockcontrol  (sudo apt-get purge mobloquer) (sudo apt-get purge blockcontrol) but situation was same.
I did remove Mobloguer and everything worked, but i wanna use mobloguer sometimes and get this solved.

What i miss?

runeh

edit:

Got it solved with this:  gksu gedit /etc/blockcontrol/blockcontrol.conf
IP_REMOVE="Google Inc"

---

