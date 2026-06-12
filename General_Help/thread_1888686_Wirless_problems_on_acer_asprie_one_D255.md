---
title: "Wirless problems on acer asprie one D255"
date: 2011-11-29
forum: General Help
---

### Post by jp17 on 2011-11-29
Hello all 

I understand that this problem has been solved on other acer's but not the d255. I have spent all afternoon search and found little to help me. 

The wireless does work but it drops in and out all the time and is slow most of the time. 
If i reboot the computer then it comes back good for 5 min then goes horrible again. 

I am using Ubuntu 11.2 32bit and only installed it about a week ago via usb 

I have a second machine on Ubuntu and the Internet works fine. I have tried plugging into a wired connection but it is not found. 

Any help would be great. 

thanks in advance.

---

### Post by Penguinnerd on 2011-11-29
First of all, Welcome to the forums! :)

I did some searching myself, and I found something that might work. (Or it might not...)

Based on this article:

[http://www.cnx-software.com/2011/08/21/installing-ubuntu-10-04-lts-in-acer-aspire-one-d255](http://www.cnx-software.com/2011/08/21/installing-ubuntu-10-04-lts-in-acer-aspire-one-d255)

It looks like there are two possible wireless cards in this model. (?) The solution depends on whether you have the Intel or the Broadcom wireless. 

Although that article was written for 10.04, the fixes described might still work for you. (Although I am unsure)

Also, you say that ethernet won't work either. The article describes a possible fix for that as well.

So, which wifi adapter do you have? Intel or Broadcom?


Edit: I had vaguely similar issues the other day then installing on an Acer Aspire One 532H. The issue turned out to be file corruption due to failed updates during the install. A re-install solved the problem. If all else fails, that's all I've got.

---

### Post by jp17 on 2011-11-29
Hi 

Thanks for the fast reply, I have a Intel corporation centrino wireless-iv 1000 card I believe. 

in regards with the install and corrupt updates, I have updated the machine several times since the install so hopefully all the files should be okay.Maybe I should add that I chose to install Ubuntu onto the computer due to a big virus when running windows 7 (plus I hated windows 7 starter rubbish) , since having Ubuntu the computer has ran very well with no freezing ect the only problems in the wifi. the computer is 100% Ubuntu with no added partitions. 


cheers

---

### Post by bluexrider on 2011-11-29
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

this may help

---

### Post by insomniaccanuck on 2011-11-30
if that doesn't help run lspci in the terminal and look for a wireless device in the listing.

Search for advice on how to set up that device.  If this is unclear paste the result of lspci here and people will be able to help you more easily.

cheers

---

### Post by KBD47 on 2011-11-30
> **jp17 said:**
> Hello all 

I understand that this problem has been solved on other acer's but not the d255. I have spent all afternoon search and found little to help me. 

The wireless does work but it drops in and out all the time and is slow most of the time. 
If i reboot the computer then it comes back good for 5 min then goes horrible again. 

I am using Ubuntu 11.2 32bit and only installed it about a week ago via usb 

I have a second machine on Ubuntu and the Internet works fine. I have tried plugging into a wired connection but it is not found. 

Any help would be great. 

thanks in advance.

Yes, been there, done that. Much trouble until the 3x kernel was released. Ubuntu 11.10 and Mint 12 (based on Ubuntu 11.10) have that newer kernel and better wireless support. I had very weak wireless in my D255E AAO with Ubuntu until the 3x kernel. Ubuntu 11.10, or Xubuntu 11.10, or Lubuntu 11.10, or Mint 12 will be your friend with that computer because of better wireless support in the new kernel. That has been my experience.
KBD47
BTW all those I mentioned will run well on the 255, but Lubuntu is lightning fast on it, and Xubuntu is pretty light on it as well.

---

### Post by jp17 on 2011-11-30
Hello all 

Here is the results from the code given: 

james@james-AOD255:~$ 
james@james-AOD255:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
james@james-AOD255:~$ 



On the last post, are you saying I should maybe try a different version on Ubuntu?  

thanks again



PS: just found this and have done the code, hopefully it will work. 

[http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/](http://www.computerandyou.net/2011/05/how-to-solve-no-wireless-network-in-ubuntu-11-04-centrino-wireless-n-1000/)

I will make this as solved after the wifi has worked for a hour or 2. 

thanks to all.

---

### Post by KBD47 on 2011-11-30
I'm saying I've got basically the same computer and the same wireless and the Linux kernel 3x solved my wireless problem. So any distro with that kernel will help you, or alternately you can upgrade to the 3.0 kernel, but I can't advise you there. I know that Lubuntu 11.10, Xubuntu 11.10, Ubuntu 11.10, and Linux Mint 12 all with the newer kernel work well with no wireless problems for me with same system. I can also tell you the lighter Linux the better, faster on your netbook, Xubuntu or Lubuntu are very good.
KBD47

---

### Post by jp17 on 2011-11-30
Okay so the above link i posted did work for around a hour and then drooped out :(. 

To the above post, it may seem like a silly question but is the difference between Ubuntu,Kubuntu and all the other ?buntus. 
what are the  kernel you are suggesting are they packets you add to ubuntu or a new sever all together?  
I am a little lost. 


I have ultimate 2.7 Ubuntu on disk is it worth me trying this, or is it to old as it came out in 2010?. 

 cheers

---

### Post by KBD47 on 2011-11-30
I'm not an expert, I can only tell you that the Linux kernel is the heart of Linux, it has things like wireless drivers. The d255/e is not that old, so it looks like the wireless driver that works best for our machine has just made it into the latest linux kernel. Ubuntu 11.10 and its children (Xubuntu 11.10, Lubuntu 11.10, etc.,) is built on the latest linux kernel. I have found with my netbook that the newest Ubuntu, probably because it has the newest kernel, now supports my wireless very well. But the older Ubuntu gave me the exact same problem you are having. So I'm suggesting you install an Ubuntu 11.10 that has the newest kernel and see if that solves your wireless problem, I'm guessing it will as it did for me with the same situation.
Best wishes.
KBD47

---

### Post by KBD47 on 2011-11-30
PS--if I misunderstood you and you are already running the 11.10 Ubuntu, then I'm thinking you may be having a router or other wireless problem. The centrino 1000 wireless is working well for me in 11.10 and its derivatives.

---

### Post by jp17 on 2011-12-01
Your read my mind, i was just about to say that i only installed this Ubuntu about a week ago.

router problems seem unlucky as my other machine works well.

---

### Post by KBD47 on 2011-12-01
The only other thing I can add is that even when I had wireless trouble on Ubuntu 11.04 with the d255e that I had less problems with wireless on lighter versions of Ubuntu--Lubuntu & Xubuntu. It might be worth trying Lubuntu or Xubuntu 11.10 on a cd or usb stick to see if you have less wireless trouble running a lighter system.

---

