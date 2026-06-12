---
title: "Help with Ubuntu 9.04/Leopard"
date: 2010-02-05
forum: General Help
---

### Post by LartTyler on 2010-02-05
Ok.

A while back, I installed Ubuntu Jaunty Jackalope onto my older PowerMac G4, and, figuring I would never need the Mac OS again, i completly removed it.

Now, I'm giving the computer to a friend, and he asked if I could put Leopard back onto the machine. I didn't think it would be difficult so I said sure. Apparently, I was wrong. I haven't had any luck, and no tutorial online I've found has been any help regarding completly removing Ubuntu and putting Leopard back on.

Does anyone know how to do this, or can point me to a tutorial that can help? 
Just to be sure, its a PowerMacG4, running Ubuntu Jaunty Jackalope 9.04. And I do have the leopard install disk, just bought it from a nearby apple store the other day.

Thanks in advance.
Tyler

---

### Post by MooPi on 2010-02-05
I'm not certain but you'll need to wipe the drive and then add a file system via the Mac install disk. I did it recently but don't remember the details. I do know that all of the tools for this are located on the Mac OS install disk. The Mac Os won't recognize any other file system other that native mac file format. Boot from a Ubuntu live CD and use gparted to wipe the drive of any file system then reboot with the MAC CD. I think you choose tools in the first phase to format the hard drive. Try this page for info.
[http://www.kenstone.net/fcp_homepage/partitioning_tiger.html](http://www.kenstone.net/fcp_homepage/partitioning_tiger.html)

---

### Post by LartTyler on 2010-02-05
Well how would you remove the ubuntu install? Once I get into the mac side I'll be able to go from there, but ubuntu utterly confuses me when it gets to the more technical side... :|

---

### Post by MooPi on 2010-02-05
Do you have a Live Ubuntu CD ? If so you can boot from it . After it has started press```
 Alt F2
``` This will bring up a run dialog. Type ```
gparted
```Delete all partitions and reboot using the Mac install disk. Use the info from my other post to format the drive to Apples spec.

---

### Post by MooPi on 2010-02-05
I'm sorry I remember my dilemma. The Mac won't boot the Live  CD so I pulled out the hard drive and used another computer to wipe the drive. I then re-installed back to the Mac and proceeded to format via install CD.

---

