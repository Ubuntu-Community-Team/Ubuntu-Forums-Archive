---
title: "Broadcom 4313 doesn't work"
date: 2011-09-14
forum: General Help
---

### Post by c_raethke on 2011-09-14
Hi, I have recently installed ubuntu 11.04 and Gnome shell 3.0 on an Inspiron n7010 laptop. It has a broadcom wireless mini card..
```
raethkc@ubuntu:~$ lspci -vvnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```The internet doesn't work 3/4 of the time, it doesn't detect any networks (when it does work can easily detect and connect to about 10 of them). Sometimes when I turn on my computer it works, other times it doesn't. I am running it under Wubi in Windows 7. I have the broadcom STA drivers installed right now. 

Can anyone help me figure out how to fix the connection problem? When it doesn't connect, the Ethernet connection also doesn't work, although I haven't tested it when the wifi WAS working (no need to..) but I do have a flash drive to copy files over if I need to.

---

### Post by blade4 on 2011-09-14
This might be a driver problem . Did you install the drivers yourself or did they come with the OS ?

---

### Post by coffeecat on 2011-09-14
@c_raethke, I have 11.04 running on a netbook with the BCM4313 card and wireless is quite stable. In fact I have two instances of 11.04 on that machine. The first is a conventional install in its own partition in which I have installed the STA driver. The second is a wubi install and I've left it with the default open source brcm80211 driver. In both installations the wireless connection is stable, the only difference being I get a slightly faster connection between the netbook and the router with the STA driver. Or rather it's reported as being faster. Ordinary use shows no appreciable difference.

I was struck by one thing in your post.

> When it doesn't connect, the Ethernet connection also doesn't work

That suggests a problem with your router. I suggest you look at your modem-router and also consider the possibility of wireless congestion in your area. This can cause a significant and intermittent degradation of your wireless connection.

Do you have any problems in Windows?

---

### Post by c_raethke on 2011-09-14
It is definitely not a router problem.. my phone (android) connects to the router just fine.. I haven't tested the Ethernet connection to work at all, I just thought I would mention that because when I don't have wifi, I don't have any way to connect to the internet. Windows 7 works perfectly 100% of the time. The wifi card picks up maybe 5 different routers it can connect to in Windows 7 and when ubuntu is working correctly, but if it decides not to work, it can't see any of them, or connect to the saved one. I'm fairly new to ubuntu, have only been using it a couple days, I've messed around with it before on a different computer but also couldn't get the internet to work properly (that was at my house, with a USB wireless receiver and a linksys router).

---

### Post by coffeecat on 2011-09-14
OK. That's all useful information. Clearly the problem is with Ubuntu only.

As I don't have problems with this card, I'm not going to be of much use, except for one thing. I have come across threads where the OP has described really weird and way-out interactions between the wireless driver and some aspect of the hardware. One was where if the OP changed the screen brightness with the FN key combinations, the wireless disconnected. I did say weird, didn't I? All I can think is that there are obscure interactions between some manufacturer's acpi and/or dsdt and the wireless. My netbook is a HP. Your laptop is a Dell. Different acpi, etc. All I can suggest is to see if anything is going on when the wireless disconnects. Anything, however off-the-wall.

Sorry I can't be of more help.

---

### Post by c_raethke on 2011-09-14
Thanks for the reply.. yeah I believe it's specific to my setup, I haven't found any info on the internet or forums about this specific problem.. I read somewhere (can't find the page now) that this card on this port requires a specific driver, but I don't think I have enough experience to just mess with stuff myself, as it works somewhat now, just not well..

Anyone else have an idea?

---

