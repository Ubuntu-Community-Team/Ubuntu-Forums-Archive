---
title: "How to temporarily disable a wireless card?"
date: 2011-02-24
forum: General Help
---

### Post by wrybread on 2011-02-24
I need to *temporarily* disable a wifi card and can't figure out how to do it. Googling I can find lots of heavy-handed methods, like adding the driver to the blacklist, but there must be some easy way to disable an internal card for a few hours on those rare occasions that I want to use an external wifi card.

Anyone?

---

### Post by smurphy_it on 2011-02-24
Why not just bring the interface down ?

Do a ifconfig -a to see all of your interfaces.  Then do a ifconfig -a [wifi adapterID] down"


so if for example, your wifi card is called wlan0, you would issue a "sudo ifconfig wlan0 down"

You don't have a "disable function" for your wireless card ?

Another method is to use "lsmod" to see the module running your wifi interface, and then do a "sudo rmmod [module name]" to disable it.  When you are ready to bring it back up, issue a "sudo modprobe [module name]"

---

### Post by mikewhatever on 2011-02-24
Right click the network manager applet in the panel, uncheck 'Enable Wireless'.

---

### Post by wrybread on 2011-02-24
Thanks, ifconfig [id] down is perfect.

---

