---
title: "Trying to find correct drivers"
date: 2009-12-12
forum: General Help
---

### Post by PaulStat on 2009-12-12
Hi Folks,

I'm very new to linux so bare with me. I've just managed to install ubuntu 9.10 (yay!) and it doesn't seem to have installed any of the drivers.

So the motherboard I'm using is[SIZE=4]
[/SIZE]**[SIZE=4]ZOTAC GeForce® 9300-ITX-WiFi[/SIZE]**

Which uses the nVidia geforce 9300 onboard chipset, it also has an integrated wifi card and ethernet port.

So yeah I need the drivers for these? And perhaps some instructions on how to install them.

Thanks,
Paul

---

### Post by jocko on 2009-12-12
To get graphics drivers, check System --> Administration --> Hardware drivers. It should give you the option to install and enable the nvidia driver.
For wifi and ethernet: Are you sure you need to install any driver? The drivers for most or all ethernet cards are already part of the kernel. Intel wifi cards also usually work with open source drivers that are already in the kernel, but there are cards from some other wifi manufacturers that will require you to install a windows driver through a wrapper.

---

