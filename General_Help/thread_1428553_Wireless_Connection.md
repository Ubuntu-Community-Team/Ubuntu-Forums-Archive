---
title: "Wireless Connection"
date: 2010-03-12
forum: General Help
---

### Post by georgetu12 on 2010-03-12
Hi all,
  I am very new to Ubuntu, I thought I'd give it a try rather than staying with windows all the time.

Anyway, I have a problem about my wireless connection and ubuntu.

My problem is that ubuntu cannot connect to my internet wirelessly, and I have absolutely no clue how to.  The only way I can get internet while using ubuntu at the same time is if I plug the ethernet cable in directly.
My router is the
**[B]Linksys Home Wireless N  Router (WRT160N).**[/B]

If it helps to know:  I am using an HP 64 bit computer, with AMD Athlon processor and windows 7.

P.S. - I have searched for a solution on google, and I see there have been many  problems about wireless connections, however I can't find the answer to my question.

---

### Post by PRC09 on 2010-03-12
You can check under System > Admin > Hardware Drivers and see if it is there,if so activate and you should be ready to go.If not you need to post back with the specs for your network card.In a terminal window enter
 > lshw -C network  and that will give you what network cards you have and then you can go from there...

---

### Post by georgetu12 on 2010-03-12
> **PRC09 said:**
> You can check under System > Admin > Hardware Drivers and see if it is there,if so activate and you should be ready to go.If not you need to post back with the specs for your network card.In a terminal window enter
  and that will give you what network cards you have and then you can go from there...

Thanks I shall give it try a bit later, and post the result.

---

### Post by georgetu12 on 2010-03-13
OK, so I looked under Hardware Drivers and found nothing was there, so I ran the terminal and got this result:

  	 	 	 	 	 	  [COLOR=Navy]WARNING: you should run this program as super-user.  [/COLOR]
 [COLOR=Navy]  *-network                [/COLOR]
 [COLOR=Navy]       description: Network controller  [/COLOR]
 [COLOR=Navy]       product: BCM4322 802.11a/b/g/n Wireless LAN Controller  [/COLOR]
 [COLOR=Navy]       vendor: Broadcom Corporation  [/COLOR]
 [COLOR=Navy]       physical id: 0  [/COLOR]
 [COLOR=Navy]       bus info: pci@0000:02:00.0  [/COLOR]
 [COLOR=Navy]       version: 01  [/COLOR]
 [COLOR=Navy]       width: 64 bits  [/COLOR]
 [COLOR=Navy]       clock: 33MHz  [/COLOR]
 [COLOR=Navy]       capabilities: bus_master cap_list  [/COLOR]
 [COLOR=Navy]       configuration: driver=b43-pci-bridge latency=0  [/COLOR]
 [COLOR=Navy]       resources: irq:18 memory:f0200000-f0203fff  [/COLOR]
 [COLOR=Navy]  *-network  [/COLOR]
 [COLOR=Navy]       description: Ethernet interface  [/COLOR]
 [COLOR=Navy]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  [/COLOR]
 [COLOR=Navy]       vendor: Realtek Semiconductor Co., Ltd.  [/COLOR]
 [COLOR=Navy]       physical id: 0  [/COLOR]
 [COLOR=Navy]       bus info: pci@0000:08:00.0  [/COLOR]
 [COLOR=Navy]       logical name: eth0  [/COLOR]
 [COLOR=Navy]       version: 02  [/COLOR]
 [COLOR=Navy]       serial: 00:21:cc:38:91:d5  [/COLOR]
 [COLOR=Navy]       width: 64 bits  [/COLOR]
 [COLOR=Navy]       clock: 33MHz  [/COLOR]
 [COLOR=Navy]       capabilities: bus_master cap_list rom ethernet physical  [/COLOR]
 [COLOR=Navy]       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes  [/COLOR]
 [COLOR=Navy]       resources: irq:27 ioport:a000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)  [/COLOR]

---

### Post by claracc on 2010-03-13
I think you have to install WICD to control wireless instead of network-manager-gnome. You go to synaptic ad thick WICD to install, it automatically uninstall network-manager-gnome and network-manager-common.

It works in my laptop (hp compacq 6720s), ubuntu karmic koala.

---

### Post by 2hot6ft2 on 2010-03-13
WICD has issues as well, don't turn 1 issue into 2.

Here's a guide for your wifi chipset which is the **BCM4322**
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

I installed WICD a while back and NONE of my 3 wifi adapters would connect. Ran without a network manager of any kind for a while and I'm using network-manager again right now.

---

### Post by trideceth12 on 2010-03-13
> **georgetu12 said:**
> 
  My problem is that ubuntu cannot connect to my internet wirelessly.

Can you connect to your wireless network at all?

---

### Post by asmoore82 on 2010-03-13
I think you just need to install the broadcom firmware for your wireless device.

check the output of this to confirm: ```
dmesg | grep -i firmware
```

If that looks to be the issue, just install the "b43-fwcutter" package:
```
sudo apt-get install b43-fwcutter
```-OR- via Synaptic of course.

---

### Post by georgetu12 on 2010-03-13
> **trideceth12 said:**
> Can you connect to your wireless network at all?
Yes, I can connect wirelessly using windows 7.
At the moment I am trying [2hot6ft2]("http://ubuntuforums.org/member.php?u=568708")s solution.

---

### Post by georgetu12 on 2010-03-13
Thank you 2hot6ft2!  I have now established the wireless connection, huzzah!
Thank you to everyone else for your input, I appreciate it.

---

### Post by 2hot6ft2 on 2010-03-13
> **georgetu12 said:**
> Thank you 2hot6ft2!  I have now established the wireless connection, huzzah!
Thank you to everyone else for your input, I appreciate it.
You're welcome. Glad to hear it. Please mark your thread as solved using the Thread Tools at the top of the thread.

---

