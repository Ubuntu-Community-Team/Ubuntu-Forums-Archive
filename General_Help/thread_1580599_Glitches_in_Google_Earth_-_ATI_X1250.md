---
title: "Glitches in Google Earth - ATI X1250"
date: 2010-09-23
forum: General Help
---

### Post by ahlidap on 2010-09-23
Hi people,

I'm having glitches in Google Earth... 
They started some time ago, and I've waited for updates but none of them solved the problem.


I know that this card is "out of support" by AMD / ATI, but I always used Google Earth without any problem... but now....things seem different..


I'm using 10.04 (64bit) with kernel 2.6.32-24....

An image of the problem is attached below.. This occurs when I zoom (when the entire earth is being displayed I have no problem!

I've tried different color modes, safe mode, and enabling/disabling compiz effects, etc... 


Thanks community!

---

### Post by ahlidap on 2010-09-30
No one?

---

### Post by Mark Phelps on 2010-09-30
Sorry, but you answered your own question when you mentioned that the card is Out of Support...

All you have now is the open-source drivers, and if they aren't working, your only choice is to upgrade to a card which DOES have support.

---

### Post by alliance1975 on 2010-10-01
> **Mark Phelps said:**
> Sorry, but you answered your own question when you mentioned that the card is Out of Support...

All you have now is the open-source drivers, and if they aren't working, your only choice is to upgrade to a card which DOES have support.

Having the same problem, it would seem all I can do is go back to 9.10. Tracking similar bugs in Launchpad indicates nothing is being done about it for either 10.04 and 10.10.

---

### Post by ahlidap on 2011-02-16
I've just fixed the problem!!!!

:D

---

### Post by thefinalfrontier1701 on 2011-02-16
Well, that's ATI for you. Nvidia has much better support for Linux. Unfortunately, I'm running an ATI card and I've had nothing but trouble with games. I should just get a Nvidia card and swap the cards out.

---

### Post by ahlidap on 2011-02-16
> **thefinalfrontier1701 said:**
> Well, that's ATI for you. Nvidia has much better support for Linux. Unfortunately, I'm running an ATI card and I've had nothing but trouble with games. I should just get a Nvidia card and swap the cards out.



Ye I know that NVIDIA is MUCH better than ATI..
I've an NVIDIA fan.. but this is a laptop, and I love AMD cpu.. so, ATI is now part of AMD................ there are laptops with AMD cpus running with NVIDIA cards, but this one was cheap.. and I use it more for work (university) and I love my laptop :P


I can play counter strike, nexuiz, urban terror..etc.. quite well

---

### Post by ahlidap on 2011-02-16
Guys, here's what I did / discover..

First, as now Ubuntu don't use a xorg.conf file, we need to create it!
So, quite X server, stop it and:

```
sudo X -configure
```



This will create a xorg.conf file..
Now, the trick (or the stupid thing) is here...

In the end of the file in the "Section Screen" I have:
```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


We should delete all SubSections, and add a "DefaultDepth 16" line..
So, the screen sections should be like this:

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16
EndSection
```


I've attached a screenshot :p
Google Earth with zoom, and no glitches


NOTE: the "flickering" with the special effects on, stills the same..

---

