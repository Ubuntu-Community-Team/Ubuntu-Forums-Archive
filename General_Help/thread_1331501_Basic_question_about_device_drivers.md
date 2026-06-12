---
title: "Basic question about device drivers"
date: 2009-11-19
forum: General Help
---

### Post by balteo on 2009-11-19
Hello,
 
I am tempted to write a device driver and I would like to better understand how these work before embarking on this adventure. 
 
I recently purchased a usb tv tuner card i.e. a nova hauppage and followed the instructions given on linuxtv website and finally got a working tv on my Ubuntu box.
 
What I don't understand is:
 
-How many layers/drivers are there between the kernel and my hauppage tuner card? Just one or several? 
-How do modules relate to each other?
-How would you define what the firmware is?
 
I also have a logitec webcam that was picked up automatically on installation by Ubuntu.
-Where is the driver for that specific webcam located on the hard drive?
-Can a given driver server several devices?
 
Any reply, albeit partial is welcome.
 
Thanks in advance,
 
Julien.

---

### Post by fluffman86 on 2009-11-19
Linux drivers are built into the kernel, either directly or as a module.  As far as layers between your kernel and your card, well, there's your card, which talks to the PCI ports, so there's code or hooks for that, and then I'd image your PCI port would talk to the kernel.

---

### Post by balteo on 2009-11-19
Hi,
I shoud have mentionned my card is a usb card. what I am trying to figure out is how a single module can handle all different models of all different vendors of devices. Is there something about modularization that I am missing?
J.

---

### Post by balteo on 2009-11-19
...how can I obtain the sources for the device drivers? I am looking for the sources of usb-storage and on my ubuntu distrib the following folder:
/usr/src/linux-headers-2.6.28-16-generic/drivers/usb/storage 
does not contain any .c files...
Any idea?
J.

---

