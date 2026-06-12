---
title: "New Network Card"
date: 2006-03-25
forum: General Help
---

### Post by Ignite_nz on 2006-03-25
I'm having a bit of an issue, my Father and I just got his PC working from its down state, and the network card wouldnt detect in Windows XP SP2. I took the network card out of my Ubuntu server machine and put it into his machine and it worked. With that I took the other network card out of his machine and put it into my Ubuntu server.

I now have a problem that I cant get the ethernet card to work - I dont know what to do with Ubuntu when adding hardware - I've only ever installed it with new hardware and it does it all for me. 

I know the network card words as the light is on the back when I plug it in, and when I type *lspci* I see the following:```
0000:00:08.0 Ethernet controller: Realtek Semiconducter Co., LTD.: Unknown Devoce 0139 (rev 10)
``` I think its a case of installing the drivers for it, but I dont know how to it or where to get them from. 

Anyones help would be greatly appreciated.

---

### Post by soce_32 on 2006-03-25
Do any lspci -vv and see if you can get the chipset info.

There are two realtek drivers in the default kernel that you can load by doing:

'modprobe -v 8139TOO' for the RTL8139/older RTL-8129/8130 chips

or 'modprobe -v 8139CP' for the RTL8139C+ chips, but this is marked as experimental

---

