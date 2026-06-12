---
title: "stupid kworld pvr 7130 tv tuner card."
date: 2006-04-16
forum: General Help
---

### Post by bdmp on 2006-04-16
check it out...
I am trying to install a kworld pvr 7130 tv tuner card. I got 2 pages helpful webpages, one with info about my card and another with someone talking about installing it in kubuntu. I did what he said but something is wrong

Here is the card info page [http://paste.ubuntu-nl.org/12376](http://paste.ubuntu-nl.org/12376) the real page is sooooo hugely long so i made this. The only thing that is different is that the card has a check in the box for NTSC not BG+DK like this discription

Here is the page for the dude who installed it on kubuntu [http://www.flexbeta.net/forums/lofiv...php/t7604.html](http://www.flexbeta.net/forums/lofiv...php/t7604.html)

burepe he said do # sudo modprobe saa7134 card=cardnumber tuner=tunernumber so I changed cardnumber to 3 and tunernumber to 5 but it didn't work. I am not sure not what the numbers should be. I thought those were the numbers he used so I tried to do what he did.

Many kworld cards are bttv but I do not think this card is bttv. I am not sure though.

Also if I load # sudo modprobe saa7134 card=3 tuner=5 do I have to unload it before I try loading another one?

Please help.

---

### Post by darkteckno on 2006-11-07
> **bdmp said:**
> check it out...
I am trying to install a kworld pvr 7130 tv tuner card. I got 2 pages helpful webpages, one with info about my card and another with someone talking about installing it in kubuntu. I did what he said but something is wrong

Here is the card info page [http://paste.ubuntu-nl.org/12376](http://paste.ubuntu-nl.org/12376) the real page is sooooo hugely long so i made this. The only thing that is different is that the card has a check in the box for NTSC not BG+DK like this discription

Here is the page for the dude who installed it on kubuntu [http://www.flexbeta.net/forums/lofiv...php/t7604.html](http://www.flexbeta.net/forums/lofiv...php/t7604.html)

burepe he said do # sudo modprobe saa7134 card=cardnumber tuner=tunernumber so I changed cardnumber to 3 and tunernumber to 5 but it didn't work. I am not sure not what the numbers should be. I thought those were the numbers he used so I tried to do what he did.

Many kworld cards are bttv but I do not think this card is bttv. I am not sure though.

Also if I load # sudo modprobe saa7134 card=3 tuner=5 do I have to unload it before I try loading another one?

Please help.

May be worth asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

