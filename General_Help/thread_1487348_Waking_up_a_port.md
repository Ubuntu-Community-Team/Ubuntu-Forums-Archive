---
title: "Waking up a port"
date: 2010-05-18
forum: General Help
---

### Post by ozark_hillbilly on 2010-05-18
Is there a way to "wake up" a port after logging on. I have a USB port falling asleep and I'm trying to avoid physically reconnecting the USB plug which does reactivate it.

Ed

---

### Post by tgalati4 on 2010-05-18
Open a terminal:

sudo apt-get install acpitool
acpitool -w

Make note of the port number that USB is assigned to:

sudo acpitool -W 10

This will enable S3 waking for the device #10

sudo acpitool -W 10

Disables the waking for device #10 (it acts as a toggle each time you use it.)

---

### Post by ozark_hillbilly on 2010-05-18
Is the ten in your post just an example of a port number?

I think I can determine the port number with the help of a Linux manual i have.

Thanks Alot,

Ed

P.S.

 This is the Hardware Address: 00:50:B6:07:29:69 and Interface: Ethernet (eth4) from "Connection Information." Can i use the hardware address to look up the port assignment?

---

### Post by tgalati4 on 2010-05-19
The 10 is a placeholder for the index number that:

acpitool -w

gives you.

It is not the pci port number given by lspci.

---

