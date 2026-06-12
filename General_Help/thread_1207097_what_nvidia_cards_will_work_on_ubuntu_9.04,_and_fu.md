---
title: "what nvidia cards will work on ubuntu 9.04, and future versions?"
date: 2009-07-07
forum: General Help
---

### Post by Dustin2128 on 2009-07-07
I've found some great deals on nvidia cards under 75$ new on amazon. I was wondering what the cutoff point for cards is on the new kernel. I am currently running ubuntu 8.04 with an nvidia geforce4 that has worked well over the years with compiz and many games. one card I was looking at was the nvidia 8600GT. How long can I expect this card to be supported by the linux kernel? and what kind of performance can I get on it? I only have 75$ and it is VERY important to get the right card. also, there must be support from other distros, like slack, arch, ect.

---

### Post by Dustin2128 on 2009-07-07
bump

---

### Post by Washer on 2009-07-07
i have the 8600gt & it works perfect with the proprietary drivers. I've never heard of a nvidia card not working.

---

### Post by Dustin2128 on 2009-07-07
well, one thing that it must be able to do: play an mmo called regnum online (free to play and native linux client) with terrain multitexturing, realistic water, and terrain detail with minimal lag (20-30 at least, 30-40 optimal)for the fastest view of the water, particle effects, terrain detail, and terrain multitexturing, go to the alsius initiation zone. it's the port you start out in so you get a fast view of all 4. Also, post process if possible. and do you know if the card will be supported in the next few years? I want to keep it in my computer for a good few years. 3-5.

---

### Post by Krupski on 2009-07-07
> **Dustin2128 said:**
> I've found some great deals on nvidia cards under 75$ new on amazon. I was wondering what the cutoff point for cards is on the new kernel. I am currently running ubuntu 8.04 with an nvidia geforce4 that has worked well over the years with compiz and many games. one card I was looking at was the nvidia 8600GT. How long can I expect this card to be supported by the linux kernel? and what kind of performance can I get on it? I only have 75$ and it is VERY important to get the right card. also, there must be support from other distros, like slack, arch, ect.

I can tell you the ones I have that DO work:

* 7300
* 7600
* 7950
* 250 GTS

The 7300 is several years old, and NVidia uses a unified driver structure, and the Linux NVidia drivers are quite new (v180.xx as on now) so I would guess almost any card will work.

-- Roger

---

### Post by bobjr777 on 2009-07-07
There are no nvidia cards that will not work as long as you are using the drivers from nvidia. I have an evga gtx 285 and it works perfectly.

---

### Post by Dustin2128 on 2009-07-07
no nvidia cards that will not work? than why do I get the message that my rather old geforce 4 will not work if I upgrade to intrepid or jaunty? probably older than what you're thinking of cards though.

---

### Post by Dustin2128 on 2009-07-07
also, I was wondering about one thing: I'm torn about some other cards. One that was rather seductive to me was the geforce 9400. However, I heard something about power supply. I have an out of the box power supply. Would I have problems with a 350 watt card?

---

### Post by Dustin2128 on 2009-07-07
bump

---

### Post by t4thfavor on 2009-07-07
I have a 9600GT on a 350 Watt PSU. Its only an athalon x64 3500+ w/4GB ram though, so no monster quad core.

On my desktop I have a 500 Watt PSU with dual 9600GT's and 8GB ram with a Q6600 and I have no issues whatsoever. I dig the 9600GT as it was relatively cheap, and performs very well while keeping the heat/noise to a minimum. 

You should be fine as long as your card is on the Nvidia driver list you will have Ubuntu support.

EDIT: 
I got 2x EVGA 9600GT's for 95USD, and 1x BFG 9600GT for 55USD (Refurb) Out of the three cards I like the bfg as it appears to perform better, and it looks cooler :)

---

### Post by MadAGu on 2009-07-08
i have a 8600 GT and it works perfectly...

---

### Post by Dustin2128 on 2009-07-11
ok, another prerequisite: it must fit in the slot occupied by an nvidia geforce 4

---

### Post by Vakman on 2009-07-11
> **Dustin2128 said:**
> ok, another prerequisite: it must fit in the slot occupied by an nvidia geforce 4
So the AGP slot? Geforce 4 also released a card that has PCI-Express so I am not sure which slot you have then again that was later on so I am going to say it is an AGP slot. That could be harder. So it has to be AGP... you could get a 7600 GS or a 7300 GT. If you have a spare PCI-Express slot though, you could get far better cards. Those two would be your best bet if you have to use AGP. Also on a 350W PSU, you wouldn't be able to have many higher cards anyway I suppose.

---

### Post by Gizenshya on 2009-07-11
1.  The 8600 is significantly better than the 9400.

2.  have a link to the geforce4 you have?  There are many different models in that series.

I think most of the geforce4's are AGP.  and if you have an AGP board, you probably have a CPU that wouldn't come close to being able to handle any of the cards mentioned so far (even if they were AGP).  But they are PCI-Express,  You're very limited in choices.  If you are set on upgrading the graphics card on your current system, then ok.  But if not, I would recommend not sinking money into that system.  I'd wait and upgrade.

---

### Post by jonobr on 2009-07-11
I have a 9400 GT which I am quite happy with although I had problems originally until I figured the 176 drivers in synaptic work better then the later ones (183 I think?)

Im not a hugely serious gamer, so maybe IM not seeing things others would see and Gizenshya's recommendation that the 8 series is better sounds like a good piece of info

---

### Post by fragos on 2009-07-12
I had an FX5200 AGP which worked fine until it fried a chip. I replaced it with an FX6200 AGP. Any newer Nvidia card should work well for you. Nvidia is IMHO the best supported GPU in Linux even though the driver is proprietary.

---

