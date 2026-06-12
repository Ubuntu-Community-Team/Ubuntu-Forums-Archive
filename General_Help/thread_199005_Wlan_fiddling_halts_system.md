---
title: "Wlan fiddling halts system"
date: 2006-06-18
forum: General Help
---

### Post by stfu on 2006-06-18
I installed pci wlan card on dapper after I made updates with standard ethernet card. Now I tried to configure the wlan without DHCP to get desired ip for the machine, but something bugged. Now when I start the system it hangs on 'configuring network' and when I press ctrl+c it continues to GDM but won't load gnome after login. 

Command line isn't much better. Sudo hangs system so I cannot really edit anything. When i took out the card the system booted normally. Which file(s) I should edit/remove to get to reconfigure the wlan card?

I don't really feel like installing all the things again. It took me hours and hours not to mention the machine is pretty old.

---

### Post by stfu on 2006-06-18
Anyone? I'd really need help.

---

### Post by stfu on 2006-06-18
Solved it. Edited /etc/network/interfaces file and removed wrong settings. Then I could configure the wlan card again. Thought someone would have known this in 5 seconds :(

---

### Post by stfu on 2006-06-27
Actually it only worked until next boot. Sigh.

---

