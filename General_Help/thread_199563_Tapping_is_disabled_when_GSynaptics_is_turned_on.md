---
title: "Tapping is disabled when GSynaptics is turned on"
date: 2006-06-19
forum: General Help
---

### Post by sheilnaik on 2006-06-19
I am running Dapper Drake on a Dell 700m, which uses the Synaptics Touchpad driver.  I installed GSynaptics today, and was very pleased with how the program worked.  However, I noticed that after I restarted my computer, tapping no longer worked when GSynaptics was turned on.  What I mean by "turned on" is that as long as the Option "SHMConfig" was turned "on" in my xorg.conf, the laptop did not register a tap as a click.  However, edge scrolling was on SHMConfig was turned "on", meaning that GSynaptics must have been on.

Any ideas anyone on why tapping suddenly stopped working?

---

### Post by jazzgossen on 2006-06-19
I don't know, but maybe it could be something with MaxTapTime? 

[http://kerneltrap.org/node/1582/](http://kerneltrap.org/node/1582/)

(Please note that I'm just guessing here)

---

