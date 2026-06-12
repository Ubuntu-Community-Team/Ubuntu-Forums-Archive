---
title: "Windows Driver Firmware?"
date: 2011-06-04
forum: General Help
---

### Post by Alecazam3568 on 2011-06-04
Okay, after installing Ubuntu Natty Narwhal 11.04, I'm experiencing tons and tons of complications with the wireless Internet connection. I have solved most of them. 

Now I have only one thing left. When I hit the drop-down menu for wireless connections, it says "Wireless connection (Firmware missing)" 

I have installed the driver for my wireless card but what is the firmware? I honestly don't know what it is although it's very basic. 

I have a Broadcom 43xx as my wireless card (specifically 4306). How do I get the firmware for it? Do I find it in Windows? 

Also I cannot get b43-fwcutter because I have absolutely to Internet connection on Ubuntu. To post this, I'm using Windows. If you can help me with this I will finally be able to connect through Linux. Thanks in advance! :D

---

### Post by jamesisin on 2011-06-04
Have you tried connecting via wired and while doing so enabling your wireless?  Ubu may need to download something for your card.

---

### Post by Alecazam3568 on 2011-06-04
The thing is that would be a little time consuming because I have a desktop and I have no Ethernet cable and my router is a floor below me...

---

### Post by MattBD on 2011-06-04
I've had that kind of situation before. Normally Ubuntu should pick up on whether your computer needs certain restricted drivers (these are the closed-source ones used for some wireless adapters and graphics cards) and should prompt you to install them. However, this can be rather a difficult situation if the hardware in question is a wireless adapter and that's your only connection to the Internet.

Now you have several options. You can use an alternative device to connect to the Internet (earlier today I did this by tethering my Android phone that was connected to my wi-fi), or you can download the package using another computer or OS, then transfer it across to Ubuntu by whatever means you wish and install it with the following command:
```
sudo dpkg -i packagename.deb
```
The package I believe you're after is at [http://packages.ubuntu.com/natty/b43-fwcutter](http://packages.ubuntu.com/natty/b43-fwcutter) - however I've always done this using the Restricted Drivers tool so I'm not 100% sure of the package name.

---

### Post by jamesisin on 2011-06-04
MattBD is steering you in the correct direction.  I also always do this at bulid-time and connected by wire.  On the bright side, you should only have to do this once.

---

