---
title: "ATI driver problem."
date: 2011-03-24
forum: General Help
---

### Post by Dakobah on 2011-03-24
Everything was running great until I bought a Radeon HD 6950 and installed it. There was a whole slew of problems that followed(at one point I couldn't even boot into Ubuntu after replacing my original card). Anyhow, I managed to trudge through all of that and now I can boot up into Ubuntu using my ATI with the fglrx drivers installed.

Here's my problem:

Everytime I log in I have to manually set gpu scaling because there are black borders around my window...so I do that...everything looks fine...BUT when I try to play a game in Wine it goes back to having the black borders and places a huge red number 1 in the corner(Catalyst indicating my display). And then it just stops working all together.

Any ideas guys?

---

### Post by Claus7 on 2011-03-24
Hello,

the only thing I can tell you from what you provide is that you should have wiped out every single bit of drivers and packages installed with your previous graphics card.

After that, try to create a stable machine with your new card, installing and enabling what is required and then try to play any games.

Recent experience shows that you should be really aware on not messing things, even with the same card (while you are trying to configure it). Every single time you make an attempt, you have to erase anything that existed before.

Good luck,
Regards!

---

### Post by Dakobah on 2011-03-24
> **Claus7 said:**
> Hello,

the only thing I can tell you from what you provide is that you should have wiped out every single bit of drivers and packages installed with your previous graphics card.

After that, try to create a stable machine with your new card, installing and enabling what is required and then try to play any games.

Recent experience shows that you should be really aware on not messing things, even with the same card (while you are trying to configure it). Every single time you make an attempt, you have to erase anything that existed before.

Good luck,
Regards!

Oh but I did remove every trace of the previous drivers Claus. Its clean, I've uninstalled and reinstalled these drivers a ton of times, purged old existing drivers, even had to manually remove some old entries. Still no dice, I have no idea why its doing this.

---

### Post by Dakobah on 2011-03-24
Update: It seems that Wine is the culprit and that's why I can't play games. I ran glmark2 and the graphics processing is fine. It even got a high score. So I guess my next question is....Whats up with Wine?

---

### Post by Dakobah on 2011-03-24
I seriously need some help(mental help as well as Ubuntu). Wine 1.2 will only run games until it has to render 3d and Wine 1.3 won't run any programs at all.


Thanks Wyld Stallions!

---

### Post by Claus7 on 2011-03-25
Hello,

unfortunately I won't be able to provide you any help. I did drop by, just to say the clean install thing, because you mentioned about some weird lines appearing during boot, so I thought that you might have messed a little your installation.

About wine, you might have to drop a line to their forum. If you do use 1.3, which I think is a major update to 1.2, you will notice that still is under preparation, so bugs are still there.

I do not know (sorry about that) the game you are interested in, yet the newer the game, the less probability to be supported by wine.

Good luck,
Regards!

edit: wine 1.3 is working, the problem is which programs you have on your mind. I use wine 1.3 and is working with some problems though...

---

### Post by bp787 on 2011-03-25
with respect to performing a clean video driver in Ubuntu, are there any directions on how to do this?  I am a Fedora user primarily and that may be "different" than I'm used to.
 
I have lines at startup and then locks, so I figured I'd give that a chance.
 
Thanks for any help!

---

### Post by Claus7 on 2011-03-25
Hello,

> **bp787 said:**
> with respect to performing a clean video driver in Ubuntu, are there any directions on how to do this?  I am a Fedora user primarily and that may be "different" than I'm used to.
 
I have lines at startup and then locks, so I figured I'd give that a chance.
 
Thanks for any help!

first of I saw, that you have not made any new thread on this, which would be ideal since the OP faces another problem as suggested.

I do not know the differences you will face with fedora. I would gladly give you what I made with ubuntu maverick, with the ati card I had.

Hope in general this to be some help:
[http://ubuntuforums.org/showpost.php?p=9901012&postcount=13](http://ubuntuforums.org/showpost.php?p=9901012&postcount=13)

remove any xorg.conf file under /etc/X11 and every package listed in the link I provided. Afterwards install the packages listed in that link. In case you have installed a driver from amd's website, you have to get rid of these packages installed as well.

I would strongly suggest you to open a new thread in case this problem continues to bother you, as the OP has a different problem.

Regards!

---

### Post by bp787 on 2011-03-30
> **Claus7 said:**
> Hello,
 
 
 
first of I saw, that you have not made any new thread on this, which would be ideal since the OP faces another problem as suggested.
 
I do not know the differences you will face with fedora. I would gladly give you what I made with ubuntu maverick, with the ati card I had.
 
Hope in general this to be some help:
[http://ubuntuforums.org/showpost.php?p=9901012&postcount=13](http://ubuntuforums.org/showpost.php?p=9901012&postcount=13)
 
remove any xorg.conf file under /etc/X11 and every package listed in the link I provided. Afterwards install the packages listed in that link. In case you have installed a driver from amd's website, you have to get rid of these packages installed as well.
 
I would strongly suggest you to open a new thread in case this problem continues to bother you, as the OP has a different problem.
 
Regards!
 
Thanks for the info. I understood that the OP had a different issue, but he was directed to do a clean video driver install which I did not see any directions on how to do so in ubuntu.  I spent another day or so and found enough to properly clean everything out and start fresh, which fixed all problems.
 
Thanks!

---

