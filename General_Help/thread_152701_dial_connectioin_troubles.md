---
title: "dial connectioin troubles"
date: 2006-03-30
forum: General Help
---

### Post by Vole on 2006-03-30
Hi, I'm fairly new to linux and  I recently installed ubuntu 5.10, it recognized my modem with no problems, I configured my connection with no problems, everything should be smooth sailing I'm thinking, but the connection drops at random intervals. It seems to hold longer when I'm only using firefox, when I try to use synaptic or upgrade packages with apt-get in a terminal it drops the connection in a matter of seconds.
The modem and isp presented no problems at all when I ran winxp or fedore core 3. 
Any thoughts or suggestions for a solution would be greatly appreciated, I'm completely stumped. 

Cheers

---

### Post by hajk on 2006-03-30
Most of us reading your message will also be completely stumped, because you're not giving much information, just some symptoms...

So, what is the make of your modem? Which driver is loaded for it? How is the setup of your connection (using wvdial? using Gnome networking manager? What does the config file for it in /etc/ppp/peers look like? Are there entries for the interface (ppp0?) in /etc/network/interfaces? 

We really do need that information in order to be able to help you.

---

