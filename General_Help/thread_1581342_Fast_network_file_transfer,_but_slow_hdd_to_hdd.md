---
title: "Fast network file transfer, but slow hdd to hdd"
date: 2010-09-24
forum: General Help
---

### Post by piine on 2010-09-24
Hi, I'm not sure if this is the proper thread to post in or not, however, I have a strange problem. Whenever I hookup a drive to my computer, whether IDE, SATA (via PCI sata controller) or USB IDE/SATA adapter, data transfers extremely slowly, however, when I transfer VIA network (SMB or SSH) and downloading from the net, the transfer speed is between 5 and 15x's the rate of a drive directly connected to the computer. 

In this particular computer, I have both an IDE drive connected to the motherboards IDE controller and a SATA drive connected to a PCI Sata Controller. I am using 10.04 and the computer is a Dell 8400, 1.7 GHZ, 640 RAM (Rambus). I get the same results when transferring to either drive. Please help...

---

### Post by pricetech on 2010-09-24
Couple of things come to mind;

If the USB is version 1, it's not going to be very fast.

An IDE controller passes data at the rate of the slowest device so if you have an optical drive on the chain, it could be slowing your hard drive down.

Nothing comes to mind concerning the SATA drive though, except for the speed of the other two.

---

### Post by piine on 2010-09-24
Each device is on it's own controller, CD/DVD Rom is on IDE2, Hard Drive 1 (40 GB) is on IDE1 and the Sata Drive is on a PCI SATA/IDE Controller and I have USB2.0 card installed for the USB IDE/SATA...

---

### Post by piine on 2010-10-01
Anybody there? No one has any insight on the situation???

---

### Post by piine on 2010-10-07
I am really disappointed. Only one person replied, with no info... Is this really how we do???

---

