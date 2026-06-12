---
title: "SD Card Reader on DELL Inspiron 700m"
date: 2006-04-24
forum: General Help
---

### Post by wizzkid on 2006-04-24
Hi. I am using DELL Inspiron 700m and running Kubuntu 5.10 Breezy.

I want my SD Card reader functional as I need that to have my files transfered to my SD Card, files include audio, photo and video.

I tried to plugged my sd card on the sd card reader built-in on my dell inspiron 700m, but it doesnt work. 

does anybody tried this thing or anybody has a solution on this?

Any thoughts, help and suggestion is appreciated.

Thanks.

---

### Post by jstueve on 2006-04-24
nope.  

the controller has no linux driver, and as far as I know, there isn't any under development (I have the same laptop)

I bought a USB-key than I can put a SD-card into to use to transer files onto my 700m.

it sux...

---

### Post by wizzkid on 2006-04-25
I see,, that problem was, I have to use SD Card since, I used SD Card for my Treo 650 phone, I cant find software that browse the content of SD Card, 

I have windows xp in duel partition, but it was messed up by a virus, thats sux ah!

Do you think the USB SD card reader will help? :)

Thanks.

---

### Post by tribaal on 2006-04-25
Yeah the USB SD card reader makes your SD card look like a flash memory USB drive, which is really really supported :)

It should just pop on your desktop when you plug it in.

Enjoy :)

- trib'

---

### Post by BryanL0911 on 2006-04-25
[QUOTE=jstueve]nope.  

the controller has no linux driver, and as far as I know, there isn't any under development (I have the same laptop)

I bought a USB-key than I can put a SD-card into to use to transer files onto my 700m.

it sux...[/QUOTE]


It has been a while since this was posted. Is this still an outstanding problem? I've loaded Daper and Breezy and neither recognize the SD card on my 700m. I also dual boot XP and Daper now. Is their a way to utilize XP from Daper to load the hardware drivers?

---

### Post by jive_dude on 2006-05-13
I've had breezy on my 700m for a while, that card reader is whats keeping me from getting rid of XP. I know i could just buy a USB card reader, but I'm cheep, so if anyone knows how to get the integrated card reader working on any dell laptop it would be greatly appretiated by everyone I'm sure.](*,)

---

### Post by GeneralZod on 2006-05-13
[QUOTE=jive_dude]I've had breezy on my 700m for a while, that card reader is whats keeping me from getting rid of XP. I know i could just buy a USB card reader, but I'm cheep, so if anyone knows how to get the integrated card reader working on any dell laptop it would be greatly appretiated by everyone I'm sure.](*,)[/QUOTE]

Every source I've seen says that no Linux drivers exist for the 700m SD reader, so there's no way of  getting it working, I'm afraid.  Unless you want to complain to Dell until they release a driver, or pay a developer to reverse-engineer the SD card reader and write a driver, of course :)

---

### Post by openback on 2006-05-27
[QUOTE=jive_dude]I've had breezy on my 700m for a while, that card reader is whats keeping me from getting rid of XP. I know i could just buy a USB card reader, but I'm cheep, so if anyone knows how to get the integrated card reader working on any dell laptop it would be greatly appretiated by everyone I'm sure.](*,)[/QUOTE]

You could try this: [http://www.compusa.com/products/product_info.asp?product_code=50741261&pfp=BROWSE](http://www.compusa.com/products/product_info.asp?product_code=50741261&pfp=BROWSE)
It's what I use and it works great.

---

### Post by CitizenKane on 2006-05-28
As far as I can tell, the Dell Insipron 700m has a Texas Instruments chipset for that card reader.  I have an HP6120 notebook that also has a Texas Insturments chipset for the card reader (I am pretty sure) and the card reader mostly works properly.  I am using Kubuntu 6.06 with latest updates at the time of this post.  The sdhci driver (for secure digital card readers in linux).  There is data at this at the [MMC wiki]("http://mmc.drzeus.cx/wiki/Controllers/SDHCI"), and it seems that most TI ones work.  It is possible that upgrading to dapper might work, or it is also possible that the chipset the 700m uses does not follow the common standard.

---

### Post by twrock on 2007-10-29
(Reviving an old thread.)

Seems that Gusty somehow has a driver that supports the 700m's internal SD card slot ... sort of. Inserting a SD card will result in recognition and even an initial read of the card. However, at least on my machine, almost any subsequent read of the card, particularly attempting to read any folder with more than a few files in it, results in the card being "unsafely removed" and then immediately remounted. I haven't experimented with any card writes for fear of trashing my SD card. Anyone else having better luck? Anyone know who developed this driver and if it can be made more stable?

---

### Post by boeing777 on 2007-11-01
same problem here, so any fix?? using Dell Inspiron 6400

---

### Post by twrock on 2007-11-04
This "bug" (faulty disconnect, no automounting, etc.) is showing up all over the place with somewhat different symptoms. Hopefully the bugs are being worked on. At this point I can't seem to get any external memory device to function properly without disconnecting. I might have to revert to Feisty if nothing happens soon.

---

### Post by carlthewinner on 2008-01-29
I have the Dell Inspiron 700m.  I am in the same boat as many of you.  I have the SD card slot and was thrilled when I saw it notice even my 4GB high capacity card.  but to no avail, when I try to do much of anything with it it just randomly says that I have ejected it.  I am trying to move completely to LInux, and be done with windows.  (I am sick of all the windows problems.)  I have been happier with everything in linux until this.  I have to have it because that is the only way that I can syncronize files with my pocket pc!  I sure hope that someone can get a fix to this.  

I even plugged in my external card reader, and encountered the same problems!  I cannot successfully read/write to my SD card at all!  Do you guys think that if I buy a new SD card reader it might work?

---

### Post by PhaedrusXY on 2008-07-06
I had the same problem Carl, but it does work with our external card reader.

---

