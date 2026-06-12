---
title: "Internet(LAN) port not activating/broken"
date: 2010-10-06
forum: General Help
---

### Post by -gabe-noob- on 2010-10-06
Hey guys, major problem. I installed Ubuntu about a week ago; but I think this error is totally unrelated, just posting here to double check. 

Today while my brother was browsing the web on my windows partition he had a blue screen pop up, one of the soft/hardware error ones, not a true BSOD, anyways, ever since my lan port on the computer seems to not be activiating as no wired connection is recognized. The lan port/card is directly attached to the Mother Board, it's a gigabyte motherboard in a self-build computer. I'm just wondering if there's anything I can do to troubleshoot this and see if it is truly a hardware problem or if its something else. 

Thanks 

-nooby-gabey-

---

### Post by polki@mac.com on 2010-10-07
You can start by checking if it works with your ubuntu partition or with a live cd.

---

### Post by soldier1st on 2010-10-07
does ubuntu have any drivers in the kernel for your wired connection as without drivers that piece of hardware will not function?
open terminal and type lsmod to list all your pci hardware 
 
open terminal and type lspci to list all the kernel modules(drivers) being used in your pc

---

