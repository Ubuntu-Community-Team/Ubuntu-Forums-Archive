---
title: "Another WoW Question - Need help installing."
date: 2011-05-04
forum: General Help
---

### Post by bobsaget24 on 2011-05-04
I recently just installed Ubuntu 11.04 64-bit edition.

After reading 20+ tutorials, 100+ message boards, watching 3+ youtube videos, and reinstalling Ubuntu for the 3rd time. I have decided I really need some direct help. 

What I want to do is simple. I want play World of Warcraft using Ubuntu 11.04. I want it to be done the right way, and in the most efficient way, and most of all; I want it to WORK. 

All of the tutorials and message boards I have read so far simply CONFUSE the issue so belligerently that I have had to reinstall Ubuntu multiple times just to fix what I had broke. Apparently not a single Ubuntu user has ever completed that "explain how to make a peanut butter and jelly and sandwich to someone who doesn't know what a sandwich is" assignment back in 6th grade. They seem to presume every user knows the fundamentals of Terminal and Linux without even looking back. 

1) I am using an ATI X1950 GT. I need the appropriate drivers installed.
2)I Don't have the WoW DVD's I am installing the full WoW client from the Battlenet Website. 
3)I believe wine 1.2..... is installed. I just did an upgrade (11.04 to 11.04). Idk how to check the version using Unity (or whatever). 
4) I am starting from scratch, this is my first time using Ubuntu, I have no clue what I am doing. Keep that in mind.

I would greatly appreciate it if someone could give me an idiots guide for installing the appropriate drivers and WoW on Ubuntu 11.04. Again, pretend I have no knowledge of what I am doing. For example: Don't tell me to go to the ATI website and install the drivers for my card. Give me an exact link (Ps. I have already tried this and I have no clue how to make it work). 

I am also willing to CHAT in aim or whatever if that helps. 

Thanks in advanced.

---

### Post by clhsharky on 2011-05-04
bobsaget24


Welcome to Ubuntu forums.

I'm afraid your legacy hardware with open source radeon drivers using window apps in wine on 11.04 will be disappointing.

I recommend duel booting Windows/Ubuntu.

Wine sub-forum for ubuntu users is here
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)



Sharky

---

### Post by bobsaget24 on 2011-05-04
> **clhsharky said:**
> bobsaget24


Welcome to Ubuntu forums.

I'm afraid your legacy hardware with open source radeon drivers using window apps in wine on 11.04 will be disappointing.

I recommend duel booting Windows/Ubuntu.

Wine sub-forum for ubuntu users is here
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)



Sharky

Even if I will experience reduced performance I would still prefer to install WoW on Ubuntu instead of dual booting Vista.

Are you suggesting that I move my thread to the wine-sub forum?

thanks.

---

### Post by clhsharky on 2011-05-05
bobsaget24


> Even if I will experience reduced performance I would still prefer to install WoW on Ubuntu instead of dual booting Vista.
OK
> Are you suggesting that I move my thread to the wine-sub forum?
No. But you may find more helpful info and Wine users that are maybe more familiar with your needs.

There is no FGLRX driver for your card in 11.04, don't try it will bork your X video.


Sharky

---

### Post by bobsaget24 on 2011-05-05
> **clhsharky said:**
> 

There is no FGLRX driver for your card in 11.04, don't try it will bork your X video.


Sharky

Okay to be entirely clear, there are no FGLRX drivers for my card in Ubuntu 11.04. Does this mean that the preinstalled drivers are the BEST ones I can use? Or is there some other option?

According the the AMD-ATI website, they stopped supporting Ubuntu OS' released after February 2009. According to Wikipedia the last released version prior to Feb 09 was Ubuntu 8.10 (Intrepid Ibex. Would it be worth my while to install this older version? Would I see better game performance?

Thanks.

---

### Post by expl0dingz on 2011-05-05
My personal experience with 11.04 and a Sapphire 5750:
copied the entire wow folder from my windows partition into ubuntu user folder. right click wow.exe -> properties -> went to tick "run as executable"
ran it with wine.

40fps in silvermoon
14fps in dalaran
vsync off, 1280x720, everything low except for spell detail (max) and view distance (somewhere in the middle)

i would recommend windows.
dual booting windows 7 would be much better..

---

### Post by skyline-racer on 2011-05-05
Im running Kubuntu Natty Narwhal. I also copyed my wow folder from my windows drive (Before i formatted it to ext3 muahha!) And i can play it in 1280x1024 high detail at around 40 FPS steady (Apart from in orgrimmar then it drops to about 20 FPS) 

This is just using Wine + Latest ATI Drivers installed from the Restricted Drivers.


Really impressed with how Ubuntu / Kubuntu is coming along. Its now my main (And only!) OS :D

---

### Post by skyline-racer on 2011-05-05
> **expl0dingz said:**
> My personal experience with 11.04 and a Sapphire 5750:
copied the entire wow folder from my windows partition into ubuntu user folder. right click wow.exe -> properties -> went to tick "run as executable"
ran it with wine.

40fps in silvermoon
14fps in dalaran
vsync off, 1280x720, everything low except for spell detail (max) and view distance (somewhere in the middle)

i would recommend windows.
dual booting windows 7 would be much better..



Who goes to Dalaran these days :P

---

