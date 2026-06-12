---
title: "Proble with connection -- Linksys WUSB54G"
date: 2011-05-22
forum: General Help
---

### Post by JCM_Pico on 2011-05-22
Hi there,

I've an old PC connected to my wireless network with an USB device -  Linksys WUSB54G...
Everything yours well, I can connect to any connection without problem, BUT, after a couple of hours the connection drops and I have to disconnect  and reconnect the usb device, in order for it to work... 
Isn't a problem during the day, but since I let the PC to make downloads during the nigth it becomes  a really annoying problem.
Have any body experienced this, and knows to fix this? 

[IMG]http://img.epinions.com/images/opti/af/ce/Linksys_WUSB54G_Wireless-G_USB_Network_Adapter-resized200.jpg[/IMG]

---

### Post by SeijiSensei on 2011-05-22
What kernel are you using?  (In a terminal, type "uname -a" if you don't know already.)  I have the same adapter and the performance of the kernel module for this device has gone up and down across releases.  It seemed especially unstable with some 10.04 kernels; I upgraded to 10.10 and the problem went away.  When I upgraded to 11.04, the device became unstable once again.  I'm now back to booting 11.04 with the 10.10 kernel 2.6.35-28-generic.  I suggest upgrading to 10.10 and see it that solves the problem.  (Alternatively, you could try to track down the Maverick kernel in a backports repository, but I wasn't having much luck finding 2.6.35-28.)

---

### Post by lmn. on 2011-05-22
Could well be a signal problem.
You could buy one of _[these]("http://www.dealextreme.com/p/ultra-thin-cat-6-male-to-male-rj45-ethernet-lan-cable-blue-15m-length-48951")_ snazzy lan cables if you want a solid connection overnight..

---

### Post by JCM_Pico on 2011-05-22
> **SeijiSensei said:**
> What kernel are you using?  (In a terminal, type "uname -a" if you don't know already.)  I have the same adapter and the performance of the kernel module for this device has gone up and down across releases.  It seemed especially unstable with some 10.04 kernels; I upgraded to 10.10 and the problem went away.  When I upgraded to 11.04, the device became unstable once again.  I'm now back to booting 11.04 with the 10.10 kernel 2.6.35-28-generic.  I suggest upgrading to 10.10 and see it that solves the problem.  (Alternatively, you could try to track down the Maverick kernel in a backports repository, but I wasn't having much luck finding 2.6.35-28.)

I recently upgraded to 11.04, so i'm experience the same as you. How can I boot 11.04 with 10.10 kernel?


[QUOTE=lmn.]  Could well be a signal problem.
You could buy one of _[these]("http://www.dealextreme.com/p/ultra-thin-cat-6-male-to-male-rj45-ethernet-lan-cable-blue-15m-length-48951")_ snazzy lan cables if you want a solid connection overnight.. 	  [/QUOTE]

The PC is an old laptop (6 yr old) with some issues... the wifi board burned and the wire network board burned too... so it work with some aids :D.. 
So I only can connect to the Internet with this USB adapter that I already had at home

---

### Post by lmn. on 2011-05-22
haha. I guess you would have to leave your laptop next to the router while it downloads.
if it still disconnects then maybe your laptop is buggered..

---

### Post by JCM_Pico on 2011-05-22
> **lmn. said:**
> haha. I guess you would have to leave your laptop next to the router while it downloads.
if it still disconnects then maybe your laptop is buggered..

Indeed, I already toad that hypothesis, but I tryed to use the same adapter I my current day using laptop (that don't have any burned unit so far) and I had the same problem.
So I'm guessing that the option that SeijiSensei gave will solve my problem =) hehe

---

### Post by SeijiSensei on 2011-05-22
Getting the 2.6.35-28 kernel might be a bit tricky if you upgraded from 10.04 to 11.04.  In my case, I upgraded from 10.10 so the 2.6.35 kernel was already in place and preserved during the upgrade.  Which kernels does grub offer during boot?  If you don't see a grub menu, hold down the SHIFT key while booting.

If you have the appropriate kernel, you can edit /boot/grub/grub.cfg manually to force it to be the default kernel.  Before we get into that, let's see what's available.

---

### Post by linuxinstalledfromhdd on 2011-05-22
If your equipment is older than 4 years, which that adapter is also I believe, I would go with a hardwired Ethernet connection to your router.

---

### Post by JCM_Pico on 2011-05-22
> **linuxinstalledfromhdd said:**
> If your equipment is older than 4 years, which that adapter is also I believe, I would go with a hardwired Ethernet connection to your router.

can't make the hardwire to work :( it seems I got problemes with the hardware maybe burned

---

### Post by linuxinstalledfromhdd on 2011-05-22
you might be able to pick up a usb to Ethernet adaptor on ebay

---

