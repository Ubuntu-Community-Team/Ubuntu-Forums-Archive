---
title: "usb printer connection"
date: 2010-06-16
forum: General Help
---

### Post by okkadiroglu on 2010-06-16
Hi,

I have the very latest version of Ubuntu 10.4 on my AMD-64 desktop computer. A Samsung CLX-2160 is connected to the computer via USB port (/dev/mfp4). A month ago there was no problem with the Printer/scanner. After recent updates computer does not recognize the USB port. /dev/mfp4 says it is unused, lsusb yields *Bus 001 Device 022: ID 04e8:3425 Samsung Electronics Co., Ltd* But the printer says *Internal Error Power Off/On* and *USB_Ctrl EP.c 72 PCNT* I tried the printer/scanner with an up-to-date Ubuntu notebook and it worked with out a problem. I tried various USB port to connect to the device but nothing changed. Other devices, like web cam, usb hard disks operate without any problems.

How can I correct this problem and use the printer?

Also when I reboot my computer it takes a long time and sometimes needs few new tries to start it. After the screen with Ubuntu writing on it disappears it is stuck there. I have to try few times to boot it. It was not like this before the updates.

Any ideas what is happening?

Many thanks for your help.

---

### Post by labinnsw on 2010-06-17
I had a printing problem over the weekend. I reinstalled cups and the problem was gone.

---

### Post by okkadiroglu on 2010-06-19
Hi,

I did it, re installed CUPS but still nothing changed.

---

### Post by labinnsw on 2010-06-19
Check if your printer properties are similar to my third attachment. If not, try adding a new printer. (See attachments 1 and 2)

---

### Post by Chame_Wizard on 2010-06-19
If the printer cannot be added,check if you USB cable is broken.

---

### Post by okkadiroglu on 2010-06-20
Thanks for your reply.

When I use CUPS it does not see a printer attached to the computer so I can not do anything. When I try to add a printer it say that there is no printer!

---

### Post by okkadiroglu on 2010-06-20
Thanks for your reply.

I did checked the cable and there is nothing wrong with it. I used the very same cable and connected the printer to a notebook and it worked without any problem.

---

### Post by okkadiroglu on 2010-06-20
Thanks for your reply.

I reinstalled CUPS and installed the newest version of Samsung Unified Driver Configurator. Still computer does not see the printer as I explained earlier.

---

