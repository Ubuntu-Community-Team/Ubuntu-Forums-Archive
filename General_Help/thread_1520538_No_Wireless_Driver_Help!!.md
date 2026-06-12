---
title: "No Wireless Driver? Help?!?!?"
date: 2010-06-29
forum: General Help
---

### Post by Kledubunt.u on 2010-06-29
I have ubuntu installed on my HP Pavalian DV4 and there is no wireless driver. It worked in vista but not in ubuntu. I don't know how to find the driver name. But when I go to 
system > administration > Hardware Drivers 
It says and I quote "Downloading package indexes failed, please check your network status. Most drivers will not be available."

Then it says "No proprietary drivers are in use on this system:

help!!!

---

### Post by linux-hack on 2010-06-29
to see the wifi card open a terminal and type : 
```
lspci
```

and put the output of the command in here
you'll may be need to plugin a cable ethernet to install the drivers using the Hardware Drivers installer.

---

### Post by supergrav on 2010-06-29
> **Kledubunt.u said:**
> I have ubuntu installed on my HP Pavalian DV4 and there is no wireless driver. It worked in vista but not in ubuntu. I don't know how to find the driver name. But when I go to 
system > administration > Hardware Drivers 
It says and I quote "Downloading package indexes failed, please check your network status. Most drivers will not be available."

Then it says "No proprietary drivers are in use on this system:

help!!!

Obviously you can't connect to internet without your wireless card. That's why you get the message above, as your system can't download necessary drivers. You can try to connect by cable to a router instead.

---

### Post by Kledubunt.u on 2010-06-29
> **supergrav said:**
> Obviously you can't connect to internet without your wireless card. That's why you get the message above, as your system can't download necessary drivers. You can try to connect by cable to a router instead.

I don't have a cable, I only have wireless.

---

### Post by Kledubunt.u on 2010-06-29
It is a long list and I don't want to type it out so I took a screen shot. Zoom in with the magnifing glass to the top right of the pic.

---

### Post by supergrav on 2010-06-29
Before trying to find manually the appropriate drivers using vista, run lspci in command line to find out if your card is recognised.

---

### Post by Kledubunt.u on 2010-06-29
> **supergrav said:**
> Before trying to find manually the appropriate drivers using vista, run lspci in command line to find out if your card is recognised.

I ran it but I don't understand what it is telling me.

---

### Post by indBcode on 2010-06-29
Apparently I don't see any images so in short .. Broadcom ?

---

### Post by nacho32 on 2010-06-29
since your new to it I would suggest get a cable off one of your friends hard-wire it then download the driver package.

---

### Post by Kledubunt.u on 2010-06-29
Sorry, here is the link to the pic [http://goo.gl/F27A](http://goo.gl/F27A)

---

### Post by Kledubunt.u on 2010-06-29
I have the live cd, I think it has some stuff that might help?

---

### Post by supergrav on 2010-06-29
You may follow this guide [http://jomcode.com/fadhil/jomcode/broadcom-official-linux-driver-bcm4312/]("http://jomcode.com/fadhil/jomcode/broadcom-official-linux-driver-bcm4312/"). You may download the driver from vista and then continue.


There is also this discussion  [http://ubuntuforums.org/showthread.php?t=1520365&page=2]("http://ubuntuforums.org/showthread.php?t=1520365&page=2").

---

