---
title: "Wireless network problem"
date: 2011-06-25
forum: General Help
---

### Post by fatteralbert on 2011-06-25
I'm an absolute newbe on ubuntu och linux. I've just this morning switched from Windows to Ubuntu, so please be gentle. 

So the problem is that I can't get the wireless connection to work. I followed a guide on how to install the ndiswrapper to use a windows driver for the ethernet card. ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))

But it doesn't work, so I need your help. And when you talk to me, pretend that you're talking to a baby or an idiot. Or most preferable an idiot baby. 

Thanks!

---

### Post by gandaran on 2011-06-25
> **fatteralbert said:**
> I'm an absolute newbe on ubuntu och linux. I've just this morning switched from Windows to Ubuntu, so please be gentle. 

So the problem is that I can't get the wireless connection to work. I followed a guide on how to install the ndiswrapper to use a windows driver for the ethernet card. ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))

But it doesn't work, so I need your help. And when you talk to me, pretend that you're talking to a baby or an idiot. Or most preferable an idiot baby. 

Thanks!
post the output of typing in terminal
```
lspci
```
this shows the wireless card chipset, nearly all wireless devices have linux drivers no need to use ndiswrapper

---

### Post by fatteralbert on 2011-06-25
Thanks for your reply. Here come the output: 

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by gandaran on 2011-06-25
> 02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
can you connect with wired internet and update software package list
```
sudo apt-get update
```
then look in additional drivers to activate the broadcom driver,
this should get your wireless card working.

edit:
remove every trace of the ndiswrapper driver to avoid any conflict
if you don't find any broadcom drivers in additional drivers you can install them using synaptic package manager, see this thread to help you choose which one to install
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by fatteralbert on 2011-06-25
It works. I followed the steps in the link you posted and it did the trick. Hopefully I've learned something too. 

Thanks! I'm sure I will be back here soon with another problem.

---

### Post by gandaran on 2011-06-25
> **fatteralbert said:**
> It works. I followed the steps in the link you posted and it did the trick. Hopefully I've learned something too. 

Thanks! I'm sure I will be back here soon with another problem.
please mark the thread solved (click the thread tools)

---

