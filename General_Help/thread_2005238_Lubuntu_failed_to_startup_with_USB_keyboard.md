---
title: "Lubuntu failed to startup with USB keyboard"
date: 2012-06-17
forum: General Help
---

### Post by barnettgs on 2012-06-17
Hi  I am not sure if this is new.  I have already searched for it but could not find anything.

I installed Lubuntu 12.04 with PS2 keyboard so all is good.  And I plugged in USB keyboard and it is working fine.

But when I rebooted with USB keyboard attached, it does not able to start up. Unless PS2 keyboard is plugged in.

Something needs to be configured for USB keyboard at the bootup, right?

---

### Post by Ropetin on 2012-06-17
As far as I know, nothing special is required for USB keyboard support, at least on a software level.  When you start up with the USB keyboard attached, what error do you get?

---

### Post by barnettgs on 2012-06-17
The machine is around 11 years old but the BIOS supports USB Legacy and it is enabled.

USB keyboard works fine in BIOS but after the BIOS screen, it just stopped loading Lubuntu.  However, if Lubuntu is loaded with PS2 keyboard attached and then I put in USB keyboard, it works fine.  

Also it booted up fine with both USB and PS2 keyboards attached.  I think boot loader is looking for PS2 keyboard, could you help?

Regards

---

### Post by codemaniac on 2012-06-17
Please note that if you have a boot device priority list in the BIOS, make sure your internal hard drive has greater priority than any of the USB entries.

---

### Post by barnettgs on 2012-06-17
No error shows up, just black screen after BIOS and few blips of HDD activity before stopping. 

Did a bit of experimenting.  Both keyboard and mouse are USB so I tried booting with PS2 mouse and USB keyboard, it was fine!

HDD is only selected for bootup.  IBM keyboard has 2 USB ports, some buttons such as volume control and its for use with IBM PC.

---

### Post by barnettgs on 2012-06-17
Now marked it as solved.  PC seems to be booted up fine with both mouse and keyboard attached!  I guess IBM machine is getting old... :p

---

### Post by amjjawad on 2012-06-17
> **barnettgs said:**
> Now marked it as solved.  PC seems to be booted up fine with both mouse and keyboard attached!  I guess IBM machine is getting old... :p

Hello and Welcome to Ubuntu Forum :)

Thanks for choosing and using Lubuntu!

I'm interested to find out what is going on and I suspect the machine not the system but please, keep us updated :)

Thanks!

---

### Post by barnettgs on 2012-06-17
Thanks.  

It is actually a 12 years old all-in-one IBM Netvista PC with 14"? 1024x768 TFT.  Pentium III 800mhz and 512mb PC133 ram :p

It is my mate's computer but just for the sake of experiment & experience, I spent countless of hours this week trying out many lightweight distros including Lubuntu 10.04 and 11.04/11.10.  Also did a few full system installations as well.

Many distros failed to get past the booting including Lubuntu 10/11 but 12.04 went through fine.  In the end, I settled for Lubuntu 12.04 and installed Firefox 13 & Libreoffice, so it is all good.  It boots up and shuts down quickly which is impressive.

---

### Post by amjjawad on 2012-06-18
> **barnettgs said:**
> Thanks.  

It is actually a 12 years old all-in-one IBM Netvista PC with 14"? 1024x768 TFT.  Pentium III 800mhz and 512mb PC133 ram :p

It is my mate's computer but just for the sake of experiment & experience, I spent countless of hours this week trying out many lightweight distros including Lubuntu 10.04 and 11.04/11.10.  Also did a few full system installations as well.

Many distros failed to get past the booting including Lubuntu 10/11 but 12.04 went through fine.  In the end, I settled for Lubuntu 12.04 and installed Firefox 13 & Libreoffice, so it is all good.  It boots up and shuts down quickly which is impressive.

Hi,

I have spent more than a month maybe to make this work: [http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)

And last time I played with it, was in April this year when I installed Lubuntu 11.10 because at that first time, it never worked and it was back then Lubuntu 10.04.

Lubuntu is great OS, not because I'm a member of its team but it's really great and it proved that all by itself.

If the machine is very old like that then my guess seems to be correct.

Your machine is much better than the one on that link ;)

---

### Post by barnettgs on 2012-06-20
> **amjjawad said:**
> Hi,And last time I played with it, was in April this year when I installed Lubuntu 11.10 because at that first time, it never worked and it was back then Lubuntu 10.04.Impressive!  Just had a full read and like you, I was so focused on trying out 'super-lightweight' distros that I had left out 'better' distro thinking that they can not run when they actually do!

10.04 and 11.10 did 'booted up' (both install & live cd) but they took longggg time and in the end, I got login screen which I cannot log in so they were un-usable.

At first, I left out 12.04 mainly because of some information on Lubuntu download page, saying if you have older hardware, 10.04 might be better option so I thought 12.04 would not run well on it.  However after trying so many distros, I decided to give 12.04 a try (Alternative install) and once installed, I was surprised when I saw how low CPU idling (1-2%) on older machines like yours and best of all, no cheesy theme and easy to use file manager! :)

> ...I'm a member of its team but it's really great and it proved that all by itself.Glad to know that and keep up the good work!

---

