---
title: "No Wireless Access"
date: 2006-05-12
forum: General Help
---

### Post by michalng on 2006-05-12
I had just installed Ubuntu (dual boot) onto a PC. The connection to internet is via wireless network using a USB Wireless Adapter (D-link DWL-G122). 

The problem is when I boot into Ubuntu the USB Wireless Adapter isn't detected thus I have no internet access when in Ubuntu. All the apt-get thing therefore is not applicable to me :-? 

I had for the pass hours browse through the forum hoping to self help but isn't getting anywhere.

[COLOR="Blue"]**Anyone kind enough to give a simple howto.**[/COLOR]

---

### Post by Titus A Duxass on 2006-05-12
A simple search for GWL-G122 gives four (4) pages of results that are relevant to your equipment.  One of those is a howto for just about any card.

Suggest you do a bit more reading.

---

### Post by michalng on 2006-05-12
[QUOTE=Titus A Duxass]A simple search for GWL-G122 gives four (4) pages of results that are relevant to your equipment.  One of those is a howto for just about any card.

Suggest you do a bit more reading.[/QUOTE]


Thanks for being so helpful  ](*,)  


Seems that you had a high regard for most newbie :-D

---

### Post by Durito on 2006-05-12
Run a search for "wireless setup", "wireless howto", "wireless connection", "usb wireless", in this forum. There's a lot of stuff on here. First though, run a search for wireless at wiki.ubuntu.com. A few howto's will come up. Basically, you're going to need to:

1. Find out what your chipset is. Check the lists on the Wiki, or google the brand and model of your card and the word "chipset". 

2. If Linux doesn't have native support, you'll need to download the Windows XP drivers and the program ndiswrapper. There's a howto and links on the Wiki for ndiswrapper, but run a search for it in the forums as well. If Linux has a driver for your card's chipset, but it's just not working right, you may have to dispose of the old driver for ndiswrapper to work properly. 

3. Follow the instructions you'll find to set up your network card.

Also, you should check out [http://hplabs.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://hplabs.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html). He's the one who wrote the wireless tools for Linux, and there's a lot of good info on that site. Good luck. Don't give up.

---

### Post by michalng on 2006-05-12
[QUOTE=Durito]Run a search for "wireless setup", "wireless howto", "wireless connection", "usb wireless", in this forum. There's a lot of stuff on here. First though, run a search for wireless at wiki.ubuntu.com. A few howto's will come up. Basically, you're going to need to:

1. Find out what your chipset is. Check the lists on the Wiki, or google the brand and model of your card and the word "chipset". 

2. If Linux doesn't have native support, you'll need to download the Windows XP drivers and the program ndiswrapper. There's a howto and links on the Wiki for ndiswrapper, but run a search for it in the forums as well. If Linux has a driver for your card's chipset, but it's just not working right, you may have to dispose of the old driver for ndiswrapper to work properly. 

3. Follow the instructions you'll find to set up your network card.

Also, you should check out [http://hplabs.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://hplabs.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html). He's the one who wrote the wireless tools for Linux, and there's a lot of good info on that site. Good luck. Don't give up.[/QUOTE]


Durito, thanks for the info.

I had did searches for "ndiswrapper" "wireless" etc. and had come to several pages of info 
Just that I am overwhelmed by the amount of info and my inability to truely understand each and everyone. :( 

Did tried installing the g++, ndis from the CD and did something like:
ndiswrapper -i /path/name_of_driver.inf
ndiswrapper -m
ndiswrapper -l (that's where I have to wait forever) to check the driver is loaded properly etc.

Well, somehow ndiswrapper doesn't work.

Anyway, many thanks for the link. Will read it and hopefully get things working 

Cheers :-D

---

