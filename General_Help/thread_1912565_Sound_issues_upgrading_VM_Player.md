---
title: "Sound issues upgrading VM Player"
date: 2012-01-20
forum: General Help
---

### Post by stevennlv on 2012-01-20
I'm having sound issues upgrading from VM Player 3.1.4 build-385536 to 4.0.?-???

It's been maybe 2-3 months since I tried this, so maybe it's been fixed already?
 
Host OS: Win7x64U on a dell box w/ all drivers and updates current.
Guest OS: UB11.04
 
I  have ~8 different use specific VM appliances that I have created. I've  done some basic customizing to the guest OS on each. (Not much though,  I'm new to a lot of this and still learning.)
 
When  I tried this it had been a few months since I had done a "hardcore"  update (all drivers, software, etc.). So I updated everything else  first, then tried upgrading to whatever version of VM Player 4.0 was around a few  months ago.
 
Everything  appeared to work properly until I opened the VM that I use just for  music. The Banshee GUI interface worked correctly.
 
But  all of my music sounded like alvin and the chipmunks on high octane  meth. Everything sounded like it was running at about 20x speed.
 
I  tried updating VMWare tools from inside the guest OS (11.04). The update ran  fine, but that did not fix the problem. So I reverted to VM Player 3.1.4 build  385536 (which is the original version that I built my all of my  appliances on) and that fixed the problem.
 
It's  been a couple of months and I figured it's time to update everything  again. I'd like to figure out how to fix this so that I have all of the  latest / most security stuff on my system.
 
Do  I need to upgrade to 11.10? And if so is that going to cause me any  headaches? Will I lose the customizations that I've done to the guest  OS?
 
BTW,  I'm not sure if maybe it's those tweaks causing this. It was pretty  superficial stuff like installing apparmor with the generic profiles and  checking for errors on every boot. (I know, everybody says there is no  need to check on every boot, but I did some testing and it really did  seem to make my VMs run a lot faster.)
 
Any suggestions would be greatly appreciated.
 
Thanks.

---

