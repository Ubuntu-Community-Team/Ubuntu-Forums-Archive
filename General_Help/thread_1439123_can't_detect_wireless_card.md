---
title: "can't detect wireless card"
date: 2010-03-25
forum: General Help
---

### Post by anastasia on 2010-03-25
Hi, i recently downloaded ubuntu 9.10
I have a dell d410 with a built in wireless card. 
it won't detect it, and i have no access to a wired connection for now.
Could anyone help?

---

### Post by waynefoutz on 2010-03-25
Connect the laptop directly to the router with an ethernet cable. Open up synaptic package manager, hit the reload button. Reboot. Then click on System>Administration>Hardware Drivers. You should see "Broadcom STA" on the list. Hit the button down below it, and activate it. It should start downloading the driver. When it's done, reboot again. Should be working now.

---

### Post by gordintoronto on 2010-03-25
If you run Accessories/Terminal and enter the command:
lspci
you should get about 20 lines of output.  Probably near the bottom will be the exact identification of your wireless adapter.

What did you observe that makes you say Ubuntu did not detect your wireless card?

---

### Post by anastasia on 2010-03-26
> **gordintoronto said:**
> If you run Accessories/Terminal and enter the command:
lspci
you should get about 20 lines of output.  Probably near the bottom will be the exact identification of your wireless adapter.

What did you observe that makes you say Ubuntu did not detect your wireless card?


Gordintoronto:
It tells me the identification of my wireless card, however, when i go into the place to select a wireless network, none show up.

---

### Post by efflandt on 2010-03-27
Yes, but you forgot to tell us what lspci says your wireless is so we can help you.  If it is BCM4311 or BCM4312 most commonly used for Dell laptops, it is proprietary and not supported by default modules.  You need the Broadcom STA hardware driver mentioned by waynefoutz.

But if you do not have any other ethernet connection you can use temporarily, you can insert the Ubuntu CD and check the box to add it to the Synaptic repository, refresh the list of packages, and install bcmwl-kernel-source package from the install CD.  Once you have your wireless connection working, you can uncheck the Ubuntu CD from Synaptic repositories and refresh list of packages from internet.

---

### Post by anastasia on 2010-03-27
> **efflandt said:**
> Yes, but you forgot to tell us what lspci says your wireless is so we can help you.  If it is BCM4311 or BCM4312 most commonly used for Dell laptops, it is proprietary and not supported by default modules.  You need the Broadcom STA hardware driver mentioned by waynefoutz.

But if you do not have any other ethernet connection you can use temporarily, you can insert the Ubuntu CD and check the box to add it to the Synaptic repository, refresh the list of packages, and install bcmwl-kernel-source package from the install CD.  Once you have your wireless connection working, you can uncheck the Ubuntu CD from Synaptic repositories and refresh list of packages from internet.

I typed lspci into thew terminal, and if you're looking for the network controller it says: Broadcom corporation BCM4318 [Airforce One 54g] 802. 11g wireless LAN controller (rev 02)
( if that wasn't the correct information i was supposed to give you, let me know)
Also, can i use the Ubuntu boot up/ install disk to install bcmwl-kernel-source?

---

### Post by anastasia on 2010-03-27
> **waynefoutz said:**
> Connect the laptop directly to the router with an ethernet cable. Open up synaptic package manager, hit the reload button. Reboot. Then click on System>Administration>Hardware Drivers. You should see "Broadcom STA" on the list. Hit the button down below it, and activate it. It should start downloading the driver. When it's done, reboot again. Should be working now.
I borrowed an ethernet cable, connected it, and i received internet. I followed all of your steps, but it still will not connect. I checked in the hardware drivers section, and it tells me that there's no proprietary drivers in use on this device.

---

