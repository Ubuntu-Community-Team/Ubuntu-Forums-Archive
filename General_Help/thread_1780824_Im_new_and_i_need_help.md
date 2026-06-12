---
title: "Im new and i need help"
date: 2011-06-12
forum: General Help
---

### Post by Fabeskates on 2011-06-12
hello im a very new to ubuntu linux im having trouble with two things, when i try to install a software form the software center on the left side it says in progress for less then a second then disappears. my other problem is connecting to my wifi wireless network i cant seem to connect to any network at all. if anyone can help that would be a great help thank you in advance.

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Fabeskates said:**
> hello im a very new to ubuntu linux im having trouble with two things, when i try to install a software form the software center on the left side it says in progress for less then a second then disappears. my other problem is connecting to my wifi wireless network i cant seem to connect to any network at all. if anyone can help that would be a great help thank you in advance.

First thing you want to do is make sure you are using a guide:

<snip>

Go down the checklist throughly and make sure you have everything you are going to need installed first. There are quite few extra things you need to do first before you can be using Ubuntu to it's fullest. :)

So I can help you figure out your WIFI, what kind of computer are you running? Make model? etc?

---

### Post by Fabeskates on 2011-06-12
i have a dell inspirion 530 with a intel(R) core(TM) Quad CPU and a Nvidia graphic card..which ubuntu do you recommend i should get the 11.04 or the 10.10??

---

### Post by nothingspecial on 2011-06-12
I would suggest posting your wireless info

from a terminal (Ctrl-Alt-T)

```
sudo lshw -C network
```

Post the resulting gobbldygook here.

---

### Post by Fabeskates on 2011-06-12
i try doing the terminal thing and it ask for a password i put the password i use to log in but it says sorry, try again

---

### Post by Blasphemist on 2011-06-12
> **nothingspecial said:**
> I would suggest posting your wireless info

from a terminal (Ctrl-Alt-T)

```
sudo lshw -C network
```

Post the resulting gobbldygook here.

The above is a good request as I think the network issue is keeping you from installing any software. Also, about the Ubuntu version question, in addition to the above please post the results of this:
```
sudo lshw -c Display
```

---

### Post by nothingspecial on 2011-06-12
> **Fabeskates said:**
> i try doing the terminal thing and it ask for a password i put the password i use to log in but it says sorry, try again

That is a symptom of another problem.

However you can try running it without sudo

```
lshw -C network
```

It will complain that you should have run it as a super-user (sudo), but it should return enough info to start troubleshooting your wireless problem.

---

### Post by Fabeskates on 2011-06-12
> **Blasphemist said:**
> The above is a good request as I think the network issue is keeping you from installing any software. Also, about the Ubuntu version question, in addition to the above please post the results of this:
```
sudo lshw -c Display
```

this is what i got 


  *-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f8000000-f9ffffff ioport:cf00(size=128) memory:fb000000-fb01ffff(prefetchable)
fabian@fabian-desktop:~$

---

### Post by Fabeskates on 2011-06-12
> **nothingspecial said:**
> That is a symptom of another problem.

However you can try running it without sudo

```
lshw -C network
```It will complain that you should have run it as a super-user (sudo), but it should return enough info to start troubleshooting your wireless problem.

for this i got

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:80:8c:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.1-2 latency=0 multicast=yes
       resources: irq:25 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:fdefc000-fdefdfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:8c:b2:7b:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
fabian@fabian-desktop:~$




btw i have ubuntu 10.04 installed if tht helps out with anyhting

---

### Post by Fabeskates on 2011-06-12
ive been doing some research and i think im suppose to install the b43 firmware on the computer ive tryed to install it using this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) but i jus cant seem to get it can anyone help? thanks in advance

---

### Post by wildmanne39 on 2011-06-12
> **Fabeskates said:**
> ive been doing some research and i think im suppose to install the b43 firmware on the computer ive tryed to install it using this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) but i jus cant seem to get it can anyone help? thanks in advance
Hi, there might be a driver for your card in additional drivers or it might say restricted drivers not sure which one since I do not know what version of ubuntu you are using look there and if it is there install it, you will have to be one a wired internet connection to do it. See if you can understand this guide a little better, your card is the 4318.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

