---
title: "How to skip grub boot menue"
date: 2010-03-05
forum: General Help
---

### Post by Aaron Durant on 2010-03-05
Hi,

Having installed Ubuntu about a week ago, i am very pleased with it, however i have 1 problem. Every time i boot the computer, i get the grub menu, which slows the boot time by about 10 seconds. Is there a way i can make it boot ubuntu straight away with the grub menu as i have no other OSs installed, and so don't need the menu.

Please help,

Thanx,

Aaron

---

### Post by Intrepid Ibex on 2010-03-05
You can edit menu.lst (if you are using grub-legacy) or grub.cfg (if you are using grub2) in /boot/grub.

If you want to do this graphically you can install a program called startupmanager. You can get it with apt or synaptic, which ever you feel more comfortable with. Then launch it and on the first tab (Boot options) change the timeout from 10 to 1.

Closer look: this is done with (I dunno if grub2 (the one in karmic) is even supported by startupmanager but you probably won't use it anyway as it will notice if there's no other OS).

You can also just edit the file with:
```
sudo gedit /boot/grub/menu.lst
```
and find the line timeout=10 (in seconds) which you would then change to e.g. 1 (when it will just flash).

**E:** forgot karmic uses grub2 by default.

---

### Post by wilee-nilee on 2010-03-05
The above is for grub legacy, grub2 is different. The easiest way change the grub timeout is by installing startup manager in synaptic it has other uses as well depending on the distro your running.

This time out is indicative of a dual boot eh don't leave out anything that might be helpful.

---

