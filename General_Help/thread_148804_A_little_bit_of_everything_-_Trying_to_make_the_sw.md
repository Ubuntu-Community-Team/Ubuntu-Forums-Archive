---
title: "A little bit of everything - Trying to make the switch to fulltime linux"
date: 2006-03-22
forum: General Help
---

### Post by rockdr80 on 2006-03-22
Well after much frustration I managed to get ubuntu up and running, and for those who have the problem with their p4p800 series board not recognizing the cdrom drive try switching enhanced mode to s-ata only and not p-ata+s-ata.  So to make a long story short I'm up and running and slowly picking away at at setting up my hardware my system is as follows for reference
Asus p4p800 with a p4 2.6ghz Northwood
1g 3200/400mhz ram (dual channel)
80gig IDE hd (windows xp install)
40gig sata hd (ubuntu install)
lg dvd burner 4081b I believe
Creative Audigy 2zs
Ati All in Wonder x800xt (AGP)
I think that about sums it up.  

I have my x800xt video card 2d and 3d drivers up and running I havent found a free game to test it out with (suggestions welcomed) but the gears test was running at around 7500 fps so I think im good to go. Ive taken a quick search through the forums but havent found answers to some of the hardware software questions I have so if someone has some answers its appreciated.

Outstanding Hardware Issues:
- Theatre chip drivers for my video card , (I think i have a guide for my ati remote wonder 2 but havent bothered till I figure out how to set the tuner up). Ive poked around the gatos sight but havent had any luck finding the answeres I was looking for so I guess my question is do drivers exist for the tuner poriton of the card anwhere and two if so where.

Software Issues:
- I currently do a fair bit of remote sensing and GIS work , what I am wondering is if there is a program out there that will let me run my existing window partition in a window in linux for my GIS / RS work (I also need this funciton for microsoft money, i dont like the money equivialnts in linux). I understand VMWare might do this (it was unclear whether it could use an existing partion or just run a created virtual one) but is there a free version that will accomplish what I need ?


I think those are my two outstanding issues at the moment. Ive gotten most things working other than that and any suggestions or pointing to the right threads would be appriciated.  Also a point to a guide on backing up dvds and dvd post processing would be helpfull as well.

thanks

---

### Post by Jedeye on 2006-03-22
First off I think its awesome that you are working the problems out instead of giving up. I don't have much info for you, but just wanted to throw a word of encouragement out! As far as a free 3d game try out enemy territory if you are into the first person games. and for a money equivalent you could try gnu cash.

---

### Post by rossjman1 on 2006-03-22
Try using Wine([http://www.winehq.org](http://www.winehq.org)) to get MS Money working in Linux.

---

### Post by rockdr80 on 2006-03-22
thanks I forgot i installed wine , i ment to try it out but I got distracted by bbqing  the other day.

---

### Post by rockdr80 on 2006-03-26
Just a few more questions if anyone has a second:

So I tried wine and it doesnt seem to work with ms money 2006 (it could just be my lack of knowledge).  I found a good guide for setting up vmware for linux however when it comes time to choose the setting use existing partition my ide winxp drive doesnt show up. I made sure that I was added to the disk group and it wasnt currently mounted in linux.  that didnt change anything then I changed the disk group to my accound and changed the permission settings also no dice.  My only options for selecting existing partitions are /dev/sdc and sdb I believe neither of which are the ones Im looking for /dev/hda1 is my winxp partition.  Anyone run into this problem before ?

---

