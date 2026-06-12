---
title: "Save data from laptop with broken graphical chip"
date: 2011-08-19
forum: General Help
---

### Post by DeMus on 2011-08-19
Hi,
I have here a Fujitsu-Siemens laptop with Windows Vista on it. The graphical chip of this laptop is damaged in such a way that during boot I can see texts but once the GUI starts it is over. No more picture. This happens with Vista, but also when I boot a live-cd from Ubuntu.

The owner of this laptop, not me, wants to buy a new one but would like all data to be saved.

I have downloaded the server version of Ubuntu 10.04 (so I stay in text mode) and with the CD I can boot into restore mode. There it is possible to mount the internal hard-disk, after which I can see the data.

But... how do I get it from the disc? How do I setup the network, which I believe is running already, to make the laptop a part of my home network? Now from other computers I can't see this laptop, and I have no idea how to see my computers from this laptop.
Or is it possible to burn a CD/DVD in Restore mode. If so how do I do that?

Who can help me fix this problem?

---

### Post by spiky001 on 2011-08-19
If you have ssh server installed on another machine you should be able to copy back with ssh client

---

### Post by snoopo71 on 2011-08-19
Do it like spiky001 said or plug the laptop's hdd off and connect it to a desktop computer (if you have the same interface type), boot with linux, mount the laptop's hdd and copy all that you need to your desktop computer.

---

### Post by jerrrys on 2011-08-19
another possibility would be [clonezilla]("http://clonezilla.org/").  it can be ran in text mode and can be used on a network.

i use clonezilla, but never used it in text (terminal) mode, so don't know how user friendly this will be.  but thought it worth mentioning.  goodluck

---

### Post by Duncan Williams on 2011-08-19
or borrow and plug a usb hard-drive into the laptop and copy the main drive data onto a folder on the usb drive.

---

### Post by DeMus on 2011-08-19
Guys, thank you very much for your answers. I did like Duncan said and it worked. When I wrote the question here I never ever thought about my back-up external hard-disk. Later I saw the thing and I said to myself: you idiot. How can you be so stupid?

Well, anyway, it all worked. I have all the data so my friend will be happy.

Thanks again for your help.

---

