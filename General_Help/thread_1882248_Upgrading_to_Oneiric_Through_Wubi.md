---
title: "Upgrading to Oneiric Through Wubi"
date: 2011-11-17
forum: General Help
---

### Post by AlexSV on 2011-11-17
Hey,
I tried the update function initially to upgrade from 11.04 to 11.10 but it failed and the system would not load. I had a dual install running so used windows as a fallback throughout examination period.

However coming back to ubuntu I installed 11.10 through wubi and now to log in my computer goes through Grub (v1.99) in which I have to select Windows, then launches the Windows boot loader from which I select Ubuntu landing me to my working 11.10 version.

How can I wipe the prior install of ubuntu from my hard drive and either remove Grub (as much as I love it) and the previous Ubuntu install, or just remove the previous Ubuntu install and connect this working one to Grub.

Thanks!
Alex

---

### Post by raja.genupula on 2011-11-17
so you dont want that old ubuntu and wanna use new ubuntu .
but you're system is booting from old ubuntu grub and you wanna remove that . 
 
use this link to restore your windows boot loader 
[http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)
 
But personally i wanna give an avice to you that , dont run Ubuntu from WUBI somtimes we have to fight with serious issues. so install ubuntu on a separate partition for better functionality and usage.
 
All the best man,:)

---

### Post by Mark Phelps on 2011-11-17
That link presumes you have a Windows disk -- and I'm betting you do NOT, otherwise, you would have mentioned it.

So, instead of doing that, go to the link below, download and burn the boot CD, boot from that, and use that to restore the Windows MBR:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

I will tell you though, that Wubi is designed for short-term use and often does not survive version upgrades.  So, if you're going to be using Ubuntu long enough to upgrade from version to version, you really need to consider a traditional dual-boot install with Ubuntu to its own partitions.

---

### Post by AlexSV on 2011-11-18
Mark you are right in the fact that I don't have a windows install disk.

I've downloaded and burnt the iso to a disk. I've tried restarting the ASUS laptop with the cd inside however it loads straight to GRUB from the ASUS screen and I cannot find the option to switch the initial boot from hard drive to cd (or usb).

Could someone tell me how I can boot into the repair iso from GRUB or better yet change the booting options.

I can post more details on request.

---

### Post by Rubi1200 on 2011-11-19
Please post the make and model as well as specifications for the laptop.

---

### Post by AlexSV on 2011-11-19
OS:             Microsoft Windows 7 Home Premium
Version:        6.1.7601 Service Pack 1 Build 7601
System Manufacturer ASUSTeK COmputer Inc.
System Model:   K52JU
System Type:    x64-based PC
Processor:      Intel(R) Core(TM) i3 CPU M 350 @ 2.27 GHz, 2266 Mhz, 2 Cores, 4 Logical processors 
BIOS Version:   American Megatrends Inc. K52JU.204, 1 Dec 2010
SMBIOS Version: 2.6 
...
Boot Device:    \Device\HarddiskVOlume2
Locale:         Australia
...
Physical Memory RAM: 8.00 GB

The laptop came with Windows 7 preinstalled, upon which I installed Ubuntu 11.04 on a different partition through USB installer. Problems already existed with the system wake function from hibernation, I figure this broke Ubuntu when I was trying to use the built in feature to upgrade to 11.10.
The laptop boots into Grub fine, however selecting Ubuntu (reads as version 11.04) it fails to load and the screen flickers on and off repeatedly.
From here I ignored the problem for a while and just booted in Windows, recently I was re-examining the problem and couldn't figure out how to get the system to change the boot order (to boot from cd or usb, it seems more difficult than when I installed 11.04). So now I have Ubuntu currently installed through wubi, and am looking to get a successful install of Ubuntu 11.10 on a separate partition and remove the old versions.

---

### Post by Rubi1200 on 2011-11-19
How do you normally enter BIOS after the POST screen, with Del or Ins?

Go in there and tell us what the current boot priority is set to please.

---

### Post by AlexSV on 2011-11-19
I think that more accurately describes my problem I can't get to the BIOS screen.

After pressing the power button an ASUS screen comes up straight away (with an intel inside logo in the bottom corner) and then grub comes straight up.

I've tried hitting DEL from start up until Grub comes up, and INS and it doesn't change.

---

### Post by Rubi1200 on 2011-11-19
Is the laptop still under warranty?

Are you by chance using a USB keyboard or mouse?

---

### Post by Mark Phelps on 2011-11-19
You need to look in your Manual that came with the laptop to see what key combination is used to get into the BIOS settings.

If you don't have that Manual, you can use another PC to go to the site below and download the Manual:

[http://www.asus.com/Notebooks/Versatile_Performance/K52JU/#download]("http://www.asus.com/Notebooks/Versatile_Performance/K52JU/#download")

---

