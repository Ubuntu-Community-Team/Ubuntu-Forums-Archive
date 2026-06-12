---
title: "Lost wireless and sound"
date: 2006-03-02
forum: General Help
---

### Post by ked on 2006-03-02
Dear all!

I'm totally lost here. I tried posting the same problem a while ago but did not get any help.

I've totally lost contact with sound and wireless devices on my laptop.
'ifup eth1' returns "Ignoring unknown interface eth1=eth1" but eth0 works fine.

I suspect this has something to do with the hotplug subsystem since it takes ages for the laptop to perform the "mapping hotplug subsystem" while booting.

Earlier I red something about certain modules could prevent other modules to be loaded and cause loss of sound, wireless etc. 

I know this happened when I tried to run an installation script (which failed) as root, and ever since I've been without wireless, sound and DVD/RW devices.

I don't have a clue how to find out what config files could have been changed around that critical date/time my problem appeared. A lot of the config files seem to be edited upon every boot, making my hunt on the right ones even more difficult

Could someone maybe suggest an apprach to diagnose my problem?

Ked

---

### Post by john_markh on 2006-03-04
Well, I really can't help!
I have the same problem over here. It worked fine under original kernel. When I upgraded kernel, it stop working.
I tried to install updated ipw2200 driver and it didn't help.
I have noticed that button that activates wirelss card is not working. Looking in the event log, I saw that there is no mapping for this button. 
Anyone ?

---

