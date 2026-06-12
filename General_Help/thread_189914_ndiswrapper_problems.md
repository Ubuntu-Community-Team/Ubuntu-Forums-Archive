---
title: "ndiswrapper problems"
date: 2006-06-05
forum: General Help
---

### Post by GhandiBurger on 2006-06-05
I am using a Netgear WG311v3 wireless card. I installed ndswrapper from Synaptic and also installed ndisgtk. I found the drivers on the CD and then ran ndisgtk. I had to use the terminal to open it.

sudo /usr/bin/ndisgtk
modprobe config already contains alias directive

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

Can someone show me how to install these drivers?

---

### Post by ????? on 2006-06-05
Try downloading the .inf and .sys files off the net instead.. sometimes the CD drivers dont work well

---

### Post by hackmeister on 2006-07-15
Remove the ndiswrapper packages you installed from the repositories. They're outdated and didn't work for me. You'll need to compile them yourself. Follow this how-to:
[http://www.ubuntuforums.org/showthread.php?t=104539](http://www.ubuntuforums.org/showthread.php?t=104539)

---

