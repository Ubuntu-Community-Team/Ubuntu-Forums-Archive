---
title: "Wubi install question."
date: 2009-08-17
forum: General Help
---

### Post by BrandonArchangel on 2009-08-17
I have a desktop computer that is very old and I want to upgrade it to Ubuntu but want to try it out first. The computer runs on a wireless network which requires a USB adapter so that it can communicate with the router for internet access. I am unsure to whether when I finish installing wubi and boot Ubuntu that it will not recognize the adapter or have the Netgear WG111v2 wizard installed. In that case I would not have internet access since my windows network manager doesn't work. So what I am asking is will I have internet access without the netgear smart wizard installed? Or will it work without it because i am pretty sure it won't auto install and i am pretty sure it can't anyway because of wubi only being a file inside windows.

---

### Post by michy99 on 2009-08-17
Ubuntu will not use the Windows wizard. It has its own network drivers. Even though Wubi installs it inside the windows partition, when Ubuntu is running, Windows is not.

If you can burn an Ubuntu installation disk, you can run it from the disk without installing to see how it will work on your system.

---

### Post by BrandonArchangel on 2009-08-17
Thanks. But I am not using windows network drivers, I am using a Netgear wizard which manages my connection. Will Ubuntu detect the adapter and allow me internet access?

---

### Post by michy99 on 2009-08-17
The Netgear Wizard is a Windows program. (I'm pretty sure.) As to whether Ubuntu will detect your adapter automatically, or you will have to install special software to get it to work depends on the adapter.

---

