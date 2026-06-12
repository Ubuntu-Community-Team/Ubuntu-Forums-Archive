---
title: "Where does the jumper need to be for it to be slave? And how to blank a HD using..."
date: 2010-10-20
forum: General Help
---

### Post by princerameses on 2010-10-20
..Windows? I know there's a way to re-format a hard disk using windows XP. But I don't remember how... Anyone know? 

I also need to know where to put the jumper on the HD I'm going to put in. 

And, I'm looking for a small-ish distro that is compatible with old video cards. Like from 2002... (with my LCD monitor) I've found AntiX, Puppy, and Damn Small Linux give me 1024 x 768. Everything else I've tried give me 800 x 600 or something.. D:

Thanks.

---

### Post by wojox on 2010-10-21
[How to Format a Hard Drive With Windows XP]("http://www.ehow.com/how_6026_format-hard-drive.html")

---

### Post by trikster_x on 2010-10-21
I'm not sure how to reformat a drive in windows, but that is mostly because any of my formatting gets done with a gparted live disk.  I don't remember ever seeing a specific tool for it, so maybe the right click menu on the drive's main diretory?  

jumpers are manufacturer specific, even down to model specific, so more info is needed for help there.

the distros you mentioned are most of the smallish ones.  Unfortunately there aren't a whole lot of options when disk space is at a premium, but if you just need it to be compatible with an older vid card, I would suggest trying to find a .iso torrent of the ubuntu 8.04, since I had luck getting that to work with some fairly old and underpowered video cards.  Unfortunately, it isn't exactly smallish.  It is, however, one of the best versions of Ubuntu by far.  I haven't had any problems getting hardware to work correctly with that release.  

If you could be just a bit more specific about what you need the distro to do, it would make it much easier to help you.  Like what vid card, the resolution you want, how much disk space you have, etc.

---

### Post by princerameses on 2010-10-21
Unfortunately, I've tried ubuntu. :( (8.04) The resolution was not correct. 

1024 x 768 is fine. It's not the resolution needed for my monitor, but I know my computer won't support the one I need. Not even windows does.

Compaq Presario, S4020WM Is the model.

And I'm wanting it for web browsing mostly.

---

### Post by mastablasta on 2010-10-21
is this the computer you have?: [http://www.dealtime.com/Compaq-Presario-s4020wm-XP2400/prices](http://www.dealtime.com/Compaq-Presario-s4020wm-XP2400/prices)
 
If so what graphics card do you have? How much ram you have? Because if this is your configuration then processor is quite powerfull for ubuntu.
 
You could try Lubuntu (use the 10.10 version) or Linux Mint LXDE edition (use version 9) or Ubuntu minimal instal and build form there an LXDE system or Peppermint OS (kind of web based). 
by the way why did you try old version of Ubuntu?
 
Unless you have some crappy graphics card, what you need to actually do is to set your resolution. Another option would be to buy a cheap graphics card (for about 30 USD). or a used one maybe. I have a really really old card with 32MB ram and works fine with 1600x1050 resolution. so i really wonder what you have there. because most graphics cards with more than 1MB ram will support resolution higher than 800x600.

---

### Post by trikster_x on 2010-10-21
If it is the graphics card listed on the stock specs for your model, I believe that is an unsupported graphics card for ubuntu.  I remember having problems with one similar to it on one of my old machines.  It absolutely does not like to play nice with linux, so that may be your biggest limitation finding a good distro.  I have a machine with specs close to yours though, and if I had your sound device, I would be running 10.10 on it right now. 

An AGP vid card is cheap on ebay now, even in the 128 MB range.  But if you want a really minimal installation that still has some decent features and support, maybe try the xubuntu variant.  It is supposed to be designed mainly to just get you up and running on a small spec system.

P.S.:  The biggest crutch to you finding a distro is going to be the amount of ram you have.  At 128 MB ram, you will basically have to choose between using a less than stellar distro and getting some hardware upgrades for your comp, unfortunately.  I think with most any distro, 256 MB is about the lower limit for ram.  Below that and things get iffy whether it will perform right or not.  Especially with how much web browsers have to use now thanks to flash based crap.

---

### Post by princerameses on 2010-10-21
Yes, that's the computer. I've just tried linux mint, no go. :(

I tried an old version because I made the disk when that version came out. ;) I also tried the current version.

It's the monitor I'm sure.. :x I might see if I can trade with my aunt.. She has one that I'm sure would probably be more compatible. And this one, I think, would work just fine for her.

It's an e-machines LCD monitor from another computer I have. I get the res I need when I hook it up to my OLDER emachines, too. (I think it's from 2005)

---

### Post by mastablasta on 2010-10-21
iot's not the monitor its the grapchip card. monitor just displays what graphics card tells them too. 
 
15" monitors monitors even back in 1995 supported 1024x768 a long as you had propper graphics card.
 
I would suggest trying to get a better graphics card. maybe you can get a used one somewhere for free.
 
so how much RAM you have? how much HDD you have?
 
i was refering to LXDE edition. hope you tried that one because normal one is quite more demanding. this one: [http://www.linuxmint.com/edition.php?id=60](http://www.linuxmint.com/edition.php?id=60)
 
If you have only 128MB RAM then you are indeed very limited. Lubuntu will work, Puppy also (but to me this one is strange). you could buy a 1Gb stick ( i see up to 1Gb is supported) and replace the current one. or maybe a 512MB stick and add it to current one. both will make the computer blazing fast and give you more choice on the distribution. and get a propper AGP card. 
because with these two relatively small investments (providing motherboard is still holding well...) you will extend computers life a lot. you oculd also try to get used ones. sometimes people upgrade and try to sell the old stuff at very low price. yet there is nothing wrong with it.

---

### Post by princerameses on 2010-10-21
352 MB RAM. 50 GB HD. 

And I get 1024 x 768 on a regular monitor. I think.

---

### Post by InphekD on 2010-10-21
each hdd has a jumper map. look closely

---

### Post by Mr_VeRiTy on 2010-10-21
I cant help with the monitor problem, but as for the HD jumpers; most HDs I've seen don't use a jumper for slave i.e. if there is no jumper, then the drive is a slave. Hope that helps.

---

### Post by mastablasta on 2010-10-21
> **princerameses said:**
> 352 MB RAM. 50 GB HD. 
 
And I get 1024 x 768 on a regular monitor. I think.
 
graphics card (which takes 32MB off your ram) should be strong enough ot easilly go with even more than 1024x768, but may have poor driver support in linux or in general.
 
352 MB ram will be enough to run Ubuntu, you also have enough disk space. 
 
i think the only real issue here is graphics card.
 
you could increase ram by 512 MB (replace the 128MB stick with a 512MB) to get everything work faster. 
 
but still i use normal Ubuntu instal on a 256MB notebook with 1,2Ghz procesor. it works (good enough for internet and some light office stuff), but i know it would work much faster if i ocudl upgrade ram (only i can't and it's not worth). i could have used Lubuntu or Mint LXDE and make it all run even faster, but i decided to go Ubuntu since i already have it on another older computer.
 
 
so basically if you could get some AGP card even old one (something like 32MB or 64MB)you would be fine for internet browsing and such.

---

