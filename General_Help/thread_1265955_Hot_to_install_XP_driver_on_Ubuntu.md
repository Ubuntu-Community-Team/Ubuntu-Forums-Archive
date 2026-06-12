---
title: "Hot to install XP driver on Ubuntu"
date: 2009-09-14
forum: General Help
---

### Post by mr.suchy on 2009-09-14
Hi,

Is there any software to run windows driver on linux ? something like NDISWrapper to network driver ? I want install driver to my Samsung Avila. I need samsung modem driver. Thanks for any help.

Regards!:popcorn:

---

### Post by MelDJ on 2009-09-14
xp drivers are for xp. you dont use the same drivers in ubuntu

---

### Post by foxmulder881 on 2009-09-14
As above, Windows and Linux drivers and are completely different and can not be used between each other.

---

### Post by MelDJ on 2009-09-14
this thread might help:[http://ubuntuforums.org/showthread.php?t=88727](http://ubuntuforums.org/showthread.php?t=88727)
try googling your problem. Google is a friend:)

---

### Post by mr.suchy on 2009-09-14
Thanks for replay. NDISWrapper use windowx driver (I think) to run wifi in Ubuntu. So I want the same with driver to run samsung phone. Anyway, I read this link and check this out. Thanks everybody for help:P

---

### Post by P4man on 2009-09-14
As you said, ndiswrapper works for wifi cards, and wifi cards (/sticks) only. Its the only windows driver wrapper im aware off. To use your phone as modem, I dont think you'll need any drivers though, ubuntu will probably just see it as a USB dialup modem and you should be able to use network manager or gnome-PPP to use it.

---

### Post by mr.suchy on 2009-09-14
I donty speak english very well so once again :) I want connect with my cell phone to upload new date on it, sounds, picture. When I connect with usb Ubuntu not mount it :confused:

---

### Post by P4man on 2009-09-14
> **mr.suchy said:**
> I donty speak english very well so once again :) I want connect with my cell phone to upload new date on it, sounds, picture. When I connect with usb Ubuntu not mount it :confused:

In that case, I have no idea. I dont know the phone... some phones, its enough to browse the internal memory card and copy sounds and pictures to it. 

If you need more than that, I guess you can install windows in virtualbox, install the phone software and use that. You will need the "VirtualBox Personal Use and Evaluation License (PUEL)." version of virtualbox (not the OSE version you can find in add/remove programs, as it doesn't support USB) and a windows installation disk and some patience.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Or contact Samsung and ask if they have linux software for your phone..

---

### Post by theozzlives on 2009-09-14
On my Samsung Delve, I tell the phone to exit Mass Storage mode. I then click on Network Manager and select CDMA. It should work the same on yours if you have a USB cable. I'd check carefully how your wireless provider charges for such services, you could wind up with a high bill.

---

### Post by mr.suchy on 2009-09-14
there is not problem to connect to second memory card on my phone. But i have trouble this memory on cell phone. I try with network menager like U said. Thx

---

