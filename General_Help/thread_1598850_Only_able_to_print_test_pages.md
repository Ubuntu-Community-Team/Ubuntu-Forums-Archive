---
title: "Only able to print test pages"
date: 2010-10-17
forum: General Help
---

### Post by Caffinator on 2010-10-17
Hello everyone, I'm having a rather interesting problem and I was wondering if anybody here knew a fix for it. Oh, and yes; I am relatively new to Linux.

Concise version:

I'm trying to print from my Windows 7 machine to a printer connected to an older laptop running Ubuntu. Test pages print successfully, but nothing else does.

Long-winded version:

Basically, I'm trying to set up my old laptop (which due to its age, currently serves no real purpose) to act something like a print server. I installed samba and on my Windows machine, the printer/print driver. When everything is said and done, test pages print successfully. Actual documents do not. 

I've tried various document types, and it's all the same. The print queue on the windows machine shows nothing, though if I watch it as I click print, I will see "1" pop up for a split second, then it reverts to 0. I've checked the ports tab under printer properties, everything is grayed out and unchecked. I can not adjust any values on this tab.

Currently, the laptop is running 9.04 (I've had the CD sitting around, and finally decided to get my feet wet!)

The printer is an HP D4160.

Both computers are connected via. cat-5 to the router. (not sure if this is relevant)

Any help would be **greatly** appreciated. I am excited about Linux, and hope to overcome this hurdle! :)

---

### Post by TeoBigusGeekus on 2010-10-17
The last time I encountered something like this (but not on a samba server) was because I had forgotten to change the default print size (Letter) to A4, which is what my printer was loaded with. The system tried to print but nothing happened.

---

