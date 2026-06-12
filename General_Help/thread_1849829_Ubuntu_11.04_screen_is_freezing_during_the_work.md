---
title: "Ubuntu 11.04 screen is freezing during the work"
date: 2011-09-25
forum: General Help
---

### Post by Mutatos on 2011-09-25
Hi, I bought me a new PC. I have looked that the Grafic carg is an ATI, because the support is better! But maybe I don't have luck with PC's I have work 2 days to run the ubuntu on this grafic card. It is an AMD Radeon 6850 HD . 

I have run it when I select only the Ubuntu classic without effects. Everything others is not running or is freezing after the login screen.

To make the card running I have installed the ATI driver downloadet from the AMD site for this grafic card.

Here is the xorg.conf


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

----------
uname -a:

Linux germanpc 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686 i686 i386 GNU/Linux


So the big problem now is, that from time to time the screen is freezing and this is very bad! Nothing is working only freeze screen. I need to press the shutdown button.

I have install for testing the game OpenArena and teh PC is freezing on the first screen as well every time.

Where can I see what causes this error and how to solve it? DO you need other info from my system?

Really I am so unlucky with every PC and Laptop. I have never seen, that the ubuntu is running from the beginning perfect :-(

Cheers
Nik

---

### Post by LinuxFan999 on 2011-09-25
Do you have the latest drivers and updates?

---

### Post by Mutatos on 2011-09-25
Yes! I have update, upgrade everything.

Update:

I have found a place where the ubuntu is freezing every time. I am using eclipse. When I install new software, then on one place there is an error coming, that the software can not be istalled and a error promt is coming with an option "OK". When I click on OK then the screen is freezing every time. Can this info help?

And as well when I start the game Open Arena.

---

### Post by Mutatos on 2011-09-25
Hi, is there really no one, who can help me? It is not possible that I am so unlucky man! I have installed 11.10 beta2, 10.10, 9.10 and 10 times 11.04 but every time the same stuff. When I install the API drivers by this tutorial [http://ubuntuforums.org/showthread.php?t=1697185&page=3](http://ubuntuforums.org/showthread.php?t=1697185&page=3) - last post, then everything is running fine, until randomly the screen is freezing! For example when the driver on 10.10 was not installed, then there was no one freeze, but when I install the driver from the website, then it begun to freeze - especially when I select some stuff from the menu for example setting or other menu.

This is impossible that this card is so awful! Man I tought ATI is better then gForce but by gforce I have never take 1 day to prepare the grafic card :-(

Please some one to help me it is very importand for me, I can not work ... I have deadlines :-(

Thanks
Nik

---

### Post by LinuxFan999 on 2011-09-25
Open up your computer and check for dust. If there is a lot of dust, clean it out, then close up your computer and boot it up again.

---

### Post by Mutatos on 2011-09-26
Haha, well the PC complete new!

Please give another reason!


Where can I see in the error logs, from what the PC is freezing?

Cheers
Nik

---

