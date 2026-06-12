---
title: "I broke Ubuntu"
date: 2006-03-15
forum: General Help
---

### Post by SHodges on 2006-03-15
Ubuntu was working fine last night, online and everything, speedy responses, etc.  Then I used synaptic to download some stuff Ajunta needed, the C and C++ and Java preprocessors or some such.  Anyways, internet still worked after this.  Then I shut down.  Then I tried turning it on again, but now it hangs during bootup on "waiting for network interface to come up" and won't log onto the internet, despite the fact that I've made sure no settings have changed.  It isn't my router/connection, because my living room PC running windowsXP has the exact same settings/numbers with DNS addresses and all that, so what happened?

---

### Post by Jawbreaker4Fs on 2006-03-15
trying doing CTRL+C on boot when it gets to that spot to cancel waiting for the network interface... when you get into Ubuntu try configuring it manually.

---

### Post by rab on 2006-03-15
This happened to me a few days ago, after about 5 restarts it worked :/

---

### Post by dpaint4 on 2006-03-15
When that waiting message comes up, it just means it's waiting through a loooooong timeout for the network it expects. It's not frozen, but can take longer than 5 minutes in my experience. I use a laptop and it's very very frustrating. I just hit ctrl+C like that other guy said and bring the network up myself after the OS boots. 

Hopefully in a future Ubuntu they'll make the timeout a lot shorter by default and additionally won't thrust some doomsday failure message at the user. Networks come and go when you live in laptop land. No biggie.

---

