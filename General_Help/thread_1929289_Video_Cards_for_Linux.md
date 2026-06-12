---
title: "Video Cards for Linux"
date: 2012-02-21
forum: General Help
---

### Post by SyntheticShield on 2012-02-21
I want to build my first desktop in eons.  Ive used laptops for so long that I have a desire to have a much larger monitor and something a little more expandable and modifiable.

The problem I having in deciding on which hardware to use is with the Video card.  I really do not want to run anything that uses proprietary drivers.  I have a laptop with a Nvidia card in it and its been nothing but a pain to set up.  In fact Ive never had it fully set up rather relying solely on the integrated Intel graphics.

Im probably going to go with an i5 processor, just because I dont really need the horsepower from an i7 and it will help keep the costs down.  However, I would like to have a decent video card that will work out of the box without having to use proprietary drivers.

What options are out there for use?  I know of Intel HD 3000 cards, but before I committed to that path, I wanted to see what else may be available.

Also, are there any good sound cards that work without the need of proprietary drivers? 

Thanks in advance for the help.

---

### Post by pqwoerituytrueiwoq on 2012-02-21
iirc amd's apu's use open source drivers (if i am wrong someone please correct me)

[http://www.phoronix.com/scan.php?page=news_item&px=OTc4NQ](http://www.phoronix.com/scan.php?page=news_item&px=OTc4NQ)

close to being off topic:
only reason i got a nvidia gpu was adobe was going to use hardware acceleration in flash with geforce 8200+ but they just seem to be screwing up kinda wishing i got a ati gpu now...

edit:
[http://www.phoronix.com/scan.php?page=news_item&px=ODk4OQ](http://www.phoronix.com/scan.php?page=news_item&px=ODk4OQ)

---

### Post by SyntheticShield on 2012-02-21
Hmmmm, so I could get an AMD graphics card and there would be native support for it in Xubuntu without having to download proprietary drivers from something like jokey (I believe thats what it is called)?

---

### Post by 3Miro on 2012-02-21
The only reason why you had issues with your laptop is because there really are no good rivers for the hybrid Optimus video cards (where you have both integrated Intel and dedicated Nvidia and you switch between them). On the desktop, the best video performance can be obtained with Nvidia + proprietary drivers and the desktop proprietary drivers are installed by selecting a check-box. Over the past 5 years I have had Ubuntu on 5 different Nvidia machines and had no issues or whatsoever.

AMD video cards + proprietary drivers come second to Nvidia. The only problem with AMD is that you will have trouble with wine games.

AMD has also good open drivers (they come installed by default). If you want to just run a desktop environment, movies, internet and documents, then the AMD FOSS drivers are good enough. AMD FOSS drivers will fall short on anything involving 3D graphics (Unity 3D is fine, but even native Linux games will suffer). The FOSS drivers are also bad on a laptop for heat and power consumption, but want a desktop.

Intel HD 3000 has great out of the box support, but Intel HD is generally the slowest of them all. Only some of the weakest AMD graphics cards are below Intel HD.

If you want a big monitor, then depending on what you mean by big, an integrated card may not work well enough. I have a System76 laptop with Intel HD on an i7 CPU and I cannot run external monitor on more than 720p. If you want full HD resolution of 1920x1080, you should read the specs carefully. I don't know about AMD APU processors, but mid range AMD and Nvidia cards will have no trouble supporting 1920x1080.

If you are on a budget, then consider AMD CPUs as well. AMD usually packs more power for the dollar, not just for the CPU, but AMD motherboards also tend to be cheaper. 4 of the Nvidia machines that I mentioned had AMD CPUs and I couldn't be happier. Phenom II X6 3.2Ghz is about the same price as the cheapest of the i5 (not counting the even cheaper motherboard) and it stand to my laptop's i7 2.0 Ghz for almost all tasks. The new Bulldozers have mixed reviews and I haven't tested them, but the Phenom II X6 series are a good bargain.

---

### Post by pqwoerituytrueiwoq on 2012-02-21
i just know the proprietary driver for ati is fglrx i tend to instal my drivers from synaptic
i know intel's GPU are open source and i wish nvidia's were i was pretty impressed with the nouveau driver's dual screen support much better than nvidia's
the only ati chip i ever used was a integrated one (ati radeon 3000) and i would really like to try one of those APUs out

---

### Post by SyntheticShield on 2012-02-21
3Miro, your point is well taken.  My thought process went more along the lines of if they are not supporting linux with open drivers then I want to purchase products from vendors that do.  I switched from using AMD processors to Intel for that reason.  I had not bought a single HP printer for many years until I started using Linux and discovered HP has great support in Linux and supports linux with open drivers.  I started buying Dell laptops for the same reason.

And yes I did, shortly after getting the laptop, learn of the lack of support for Optimus and I wish I had known that before I bought the laptop.  I knew Nvidia would be cause for proprietary drivers, and I should have stopped there but lesson learned.

I do not do much if any gaming.  In fact I cannot recall the last time I played any such 3D game.  I hate make the blanket statement that I never will, because having a desktop PC again may change that.  I have not owned a desktop PC for the better part of 10 years now, Ive had nothing but laptops.

I will say I had leanings to using an Intel card, but I dont want to shoot myself in the foot either and be where I cannot do anything 3D if the occasion should arise.

I will check out the AMD CPU's and MB's.  I have shied away from them because I became so intent on sticking with Intel, but maybe its time to revisit that plan.

---

### Post by 3Miro on 2012-02-22
Preference for FOSS drivers is a good thing, totally understandable.

When it comes to AMD and Intel, I don't see one of them as being more dedicated to Linux then the other. ATI used to not care about Linux much, but AMD instantly changed that and while they are still trying to undo ATI's legacy, new AMD products have excellent Linux support. AMD's FOSS drivers are really good (much better than noveau) and they keep getting better.

I guess my advice would be to get and AMD video card (don't get anything before Radeon 4xxx, 6xxx may be better, you should do some research as I am not too familiar with their products). You can use the FOSS driver for work and if you decide to game you can install the proprietary driver. Some people play wine games with AMD graphics, although things are iffy. Note that with the rate at which AMD FOSS drivers are improving, in couple of years you may not even need the prop driver for gaming.

---

### Post by mastablasta on 2012-02-22
> **3Miro said:**
>  
AMD has also good open drivers (they come installed by default). If you want to just run a desktop environment, movies, internet and documents, then the AMD FOSS drivers are good enough. AMD FOSS drivers will fall short on anything involving 3D graphics (Unity 3D is fine, but even native Linux games will suffer). The FOSS drivers are also bad on a laptop for heat and power consumption, but want a desktop.
.
 
i had no issues running linux games or games in winde using opensource driver on ATI card.
 
AMD is one of major Linux supporters.
 
new AMD drivers even support their hybrid graphics on laptops.
 
[QUOTE=SyntheticShield] 
My thought process went more along the lines of if they are not supporting linux with open drivers then I want to purchase products from vendors that do. I switched from using AMD processors to Intel for that reason.
[/QUOTE]
 
What do you mean not supporting linux with open drivers? and why does that even matter so much? would you rather have them opening drivers and their card designs completelly and then have a bunch of fake AMD made in china chips arround?
 
it is completelly understandable that they want to lock in their drivers in order to keep unique things in their chips that gives them an edge on competition secret. 
 
Intel opened up since their GPU chips were rubish at the time anyway... they improved a lot but their performance don't come near to latest from nVidia or AMD.

---

### Post by SyntheticShield on 2012-02-22
3Miro I guess that pretty much settles that then.  If I can get decent video performance and still have the option to do more intensive things video wise, then that is the way I would like to go.  I dont really see the need, but again, having a desktop with a little more horsepower may change that and I want to at least have an option.  I certainly have never played WINE games before.  In fact I try to avoid using WINE as any software I have ever needed to run in it, never has worked properly.  Not bashing on WINE, I just accept that it does what it does and does not usually run what I need run.  Instead, I use VirtualBox for those times I need software that will run only under windows.

mastablasta perhaps I did not define what I meant correctly.  What I should have said is just provide stable drivers that work in linux on par with their window counterparts.  Better yet, just plain out of the box functionallity no matter what OS you use though I do understand there are economics behind that.

I would, however, be highly surprised if their chips are not made 'overseas' already.  But I get the gist of your point, and that was not what I was trying to say and should have stated that a bit better than I did.

---

### Post by 3Miro on 2012-02-22
> **mastablasta said:**
> i had no issues running linux games or games in winde using opensource driver on ATI card.

Did you play actual 3D games? Older games like Diablo II don't require 3D graphics and will run on pretty much any video card, but things like Oblivion and Starcraft II would be more demanding. When I was using FOSS ATI drivers on Radeon 4250 I couldn't even run the Unique engine benchmarks.

>  
AMD is one of major Linux supporters.

Absolutely true.

> 
new AMD drivers even support their hybrid graphics on laptops.

Great news indeed.

@SyntheticShield: glad we could help with the choice.

---

### Post by SyntheticShield on 2012-02-22
Yes, thank you all for the valuable input and guidance.  Now, its on to a good sound card.  I dont think I want to skimp there, I do like to listen to music when Im on the computer.

---

