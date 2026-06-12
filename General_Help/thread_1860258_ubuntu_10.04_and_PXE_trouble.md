---
title: "ubuntu 10.04 and PXE trouble"
date: 2011-10-14
forum: General Help
---

### Post by sergio83 on 2011-10-14
Hi everybody,
I've set up a clonezilla server for 12 PC and encountering some trouble with PXE boot
The client image is dual boot dows WinXP-Ubuntu 10.04 (updated)
The network card is via rhine II
The cloning process is great and successfull unless in a particular condition:
Case 1:When last OS runned on the client was ubuntu, the PXE fails immediatly "PXE-MOF exiting..."...:(
Case 2:When last OS runned is XP, PXE boot works perfectly and clonezilla works!:D
With wireshark on another PC I saw that in case 1, there were no dhcp discover request from the client (just nothing in fact...).
So anyone knows the trouble between ubuntu 10.04 and the pxe settings of the netcard??
thanks
Serge

---

