---
title: "need a GPU, plz help"
date: 2010-04-12
forum: General Help
---

### Post by spikeofdoom on 2010-04-12
so i have a radeon x1600 xt (512gddr3)
unfortunately that isnt supported anymore, and i rather like having full 3d support in my OS,
so i wana get a new graphics card, so i would love some recommendations
i have a pci express x16 board though, im currently running 10.04, ive looked at these cards

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814500154](http://www.newegg.com/Product/Product.aspx?Item=N82E16814500154)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162022](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162022)

any other recommendations would be great, just looking for something under $100 thats gona have an up to date fully working driver, and that wount be too slow to run visual effects on high.

---

### Post by gradinaruvasile on 2010-04-12
Get a nvidia 220 - it has all: full vdpau video playback, power, and great (small) price. I use a 210 (that is essentially a 220 with 64-bit bus) and it runs wonderfully with the latest nvidia drivers (on Debian Squeeze).

Something like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125295](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125295)

Watch out for these features:
It must have:

128-bit (or more, but i doubt you find in that price range)
DDR3 (256 at least, but i see that for the 200 series 512 MiB is the lowest you can find)

And contrary to some beliefs, higher memory != more speed. 512 MB is more than enough ( i have a 128 MB 7600 GS/DDR3 and it plays games well). But memory speed is very important. It should be AT LEAST DDR3 if you really want to squeeze the juice out of them. Many manufacturers put 1 GiB/512 MiB of DDR2 memory, this leads to speed decrease despite having 128-bit bus. But probably they wont heat up that fast and thus more they might be more stable (just a guess).

I would say Gibabyte or Asus as manufacturer. I have cards from both manufacturers and had no problems with them. But thats me, maybe there are others i dont know and are better...

---

### Post by spikeofdoom on 2010-04-12
one problem i havent found any 220 in pci express x16, (pci express 1.0), i wanted something without having to get a new mobo, cause at that point i'd just get a new laptop and say **** it, this desktop is getting old anyways

---

### Post by gradinaruvasile on 2010-04-12
That is not a problem, the 2.0 PCIExpress  is fully backwards compatible with x16. But you can plug the 2.0 card in the x16 slot and will work at x16 speed.

See the discussion here:

[http://www.tomshardware.co.uk/forum/249006-13-express-motherboard](http://www.tomshardware.co.uk/forum/249006-13-express-motherboard)

So, you can buy any Pciex card, be it x16 or 2.0. It will work.

PS: I too have a x16 mobo with a 2.0 card in it (Optiplex 755 with Nvidia GF 210).

---

### Post by cascade9 on 2010-04-12
I agree, a GT220 would be fine. Its not the only decent choice, but its a god one. 

> **spikeofdoom said:**
> one problem i havent found any 220 in pci express x16, (pci express 1.0), i wanted something without having to get a new mobo, cause at that point i'd just get a new laptop and say **** it, this desktop is getting old anyways

PCIe- 2.0 cards run fine in PCIe 1.0 slots (PCIe 2.0 is backward compatible) 

> **gradinaruvasile said:**
> Get a nvidia 220 - it has all: full vdpau video playback, power, and great (small) price. I use a 210 (that is essentially a 220 with 64-bit bus) and it runs wonderfully with the latest nvidia drivers (on Debian Squeeze).

Something like this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125295](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125295)

Watch out for these features:
It must have:

128-bit (or more, but i doubt you find in that price range)
DDR3 (256 at least, but i see that for the 200 series 512 MiB is the lowest you can find)

And contrary to some beliefs, higher memory != more speed. 512 MB is more than enough ( i have a 128 MB 7600 GS/DDR3 and it plays games well). But memory speed is very important. It should be AT LEAST DDR3 if you really want to squeeze the juice out of them. Many manufacturers put 1 GiB/512 MiB of DDR2 memory, this leads to speed decrease despite having 128-bit bus. But probably they wont heat up that fast and thus more they might be more stable (just a guess).

I would say Gibabyte or Asus as manufacturer. I have cards from both manufacturers and had no problems with them. But thats me, maybe there are others i dont know and are better...

128bit isnt a 'must have'. Sure, its better than 64bit, but just because something is 64bit doesnt make it bad (just 'low end'). 

DDR3 isnt a 'must have' either. As long as the memory runs at the rated speed, that is what matters, not the memory type. More than a few newer cards have DDR2, including some of the GT220s- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814261052](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261052)

BTW, that card isnt running at the standard specification settings for the GT220 ;) Matter of fact, a lot of the DDR2 cards are running under specifiaction (like the GT220 above, it should have 1000Mhz memroy, but its running 800Mhz). DDR2 actually runs hotter than DDR3, so its not for heat lowering, or stability, its just to get id of 'old stock' RAM chips. If they put the proper specification speed DDR2 in them there would be no real difference between the DDR3 and DDR2 cards though (DDR2 might run hotter, but its not by much)

If you want to overclock ('squeeze the juice' LOL) then I agree, but for the average use overlcocking the video card is pointless in a lot of cases, and more complex than needed. 

256bit cards are around in that price range (9600 GT + GSO, 9800s, others) but for desktop you wont notice much, if any, difference between them. Better off with the GT220 for VDPAU which is more likely to be used (9600+9800, feature set 'a', gt220, feature set 'c'- far more video is hardware decoded with the GT220) 

BTW, I can see what you are saying just (sorry for the way this sounds) most people dont have the right brain setup to remember and compare all the facts and figures that go with hardware in general, video cards in particular. I've recently helped out someone who got a shopping list similar to what was above and ended up selecting the wornm card. He got told 'get 1Ghz+ memory, 500Mhz + core, 256bit interface' and managed to find an FX5800 ultra :lolflag:

---

### Post by gradinaruvasile on 2010-04-12
> **cascade9 said:**
> I agree, a GT220 would be fine. Its not the only decent choice, but its a god one. 



PCIe- 2.0 cards run fine in PCIe 1.0 slots (PCIe 2.0 is backward compatible) 



128bit isnt a 'must have'. Sure, its better than 64bit, but just because something is 64bit doesnt make it bad (just 'low end'). 

DDR3 isnt a 'must have' either. As long as the memory runs at the rated speed, that is what matters, not the memory type. More than a few newer cards have DDR2, including some of the GT220s- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814261052](http://www.newegg.com/Product/Product.aspx?Item=N82E16814261052)

BTW, that card isnt running at the standard specification settings for the GT220 ;) Matter of fact, a lot of the DDR2 cards are running under specifiaction (like the GT220 above, it should have 1000Mhz memroy, but its running 800Mhz). DDR2 actually runs hotter than DDR3, so its not for heat lowering, or stability, its just to get id of 'old stock' RAM chips. If they put the proper specification speed DDR2 in them there would be no real difference between the DDR3 and DDR2 cards though (DDR2 might run hotter, but its not by much)

If you want to overclock ('squeeze the juice' LOL) then I agree, but for the average use overlcocking the video card is pointless in a lot of cases, and more complex than needed. 

256bit cards are around in that price range (9600 GT + GSO, 9800s, others) but for desktop you wont notice much, if any, difference between them. Better off with the GT220 for VDPAU which is more likely to be used (9600+9800, feature set 'a', gt220, feature set 'c'- far more video is hardware decoded with the GT220) 

BTW, I can see what you are saying just (sorry for the way this sounds) most people dont have the right brain setup to remember and compare all the facts and figures that go with hardware in general, video cards in particular. I've recently helped out someone who got a shopping list similar to what was above and ended up selecting the wornm card. He got told 'get 1Ghz+ memory, 500Mhz + core, 256bit interface' and managed to find an FX5800 ultra :lolflag:

The 64 vs 128 bit thing IS visible even in Compiz. 
I had that 7600GS/128MB-DDR3/128bit and it runs Compiz in 1920x1200 perfectly without a hint of "slowness". Compared to that, the GF 210/512MB-DDR2/64bit crawls with Compiz (vdpau is fine).
Also, i did some overclocking back in my Windows times and i found that the vid cards memory speed really matters, the clock speed didnt have much impact in 3d performance. Ok, it was an old MX-440 Asus card i was plaing with, but i think the rule applies still. So, thats why i recommended DDR3 - DDR2 runs on lower clock speeds as you have stated.

---

### Post by cascade9 on 2010-04-12
> **gradinaruvasile said:**
> The 64 vs 128 bit thing IS visible even in Compiz. 
I had that 7600GS/128MB-DDR3/128bit and it runs Compiz in 1920x1200 perfectly without a hint of "slowness". Compared to that, the GF 210/512MB-DDR2/64bit crawls with Compiz (vdpau is fine).

I cant really speak for compiz, as I never use it. I dont think that a comparison between a older midrange card and a later *very* low end card is exactly fair. It could be various things causing it, some hardware, some software (nvidia care more about performance on higher end cards, the low end cards 'get what they get and upgrade if your not happy). I dont know if compiz uses the shaders, texture mapping or render output - if it doesn the 7600GS is 5+12 (shaders) 12 (Texture mapping) 8 (render output), GT210 is 16, 8, 4. If compiz uses texture mapping is 50% on the 7600GS and for render output then its got a 100% advatage over the GT210.  

Also, the 7600GS was avaible in 533Mhz @ 128bit memory models- a GT210 @ specification (1Ghz memory @ 64bit) has a very tiny bandwidth difference to some of the 128bit 7600GS cards. 

> **gradinaruvasile said:**
> 
Also, i did some overclocking back in my Windows times and i found that the vid cards memory speed really matters, the clock speed didnt have much impact in 3d performance. Ok, it was an old MX-440 Asus card i was plaing with, but i think the rule applies still. So, thats why i recommended DDR3 - DDR2 runs on lower clock speeds as you have stated.

Memroy speeds do matter...but far more on older cards like the MX440. It only had 400Mhz memory, uping that really helped the memory bandwidth. Core speed did help as well, if you wanted to push it, but it was bandwidth that was the MX440s weak point, and it was a general weak point at the time, check the specs for the Ti4400 vs Ti4600- a mere 25mhz bonus on clock speed (275 vs 300) , but a huge 100Mhz on memory (550 vs 650). 

DDR2 doesnt have to run at lower clock speeds. It tends to, but there are plenty of cards out there running at specifiaction speed with DDR2. Its just that most people dont bother to check things like that, and assume that one XXXX model nvidia card is the same as another. Manufacturers use that to dump cheaper memory on video cards, savign themeselves some money on production. 

Its only at the low end of video cards they do that, its a much harder game to get away with on high level gaming cards.

---

### Post by spikeofdoom on 2010-04-12
well im just saying, atm i have the x1600 which i cant get a driver for, so im really not looking for an upgrade so much as maybe an nivida alternative? does Ubuntu like nivida better? i kinda assumed they did. (by like i mean have better support for)
if 2.0 cards are backwards compatible ill prolly get the 220 cause i can find them very cheap, now the question is, does 10.04 support the 220 with full 3d support? so if i wanted to get ambitious i could easily play urban terror (quake 3 mod), i tryed doing comparisons and they came up with the 220 being way better then i currently have as well, so that would be nice since it's cheap. oh for the record

Amd 4200+ on 939, preventing me from upgrades:(
2 gigs of sd-ddr
160gig 5400rpm laptop drive cause my other is full
ati radeon x1600 xt   (590/900)core/mem if i remember correctly 512Gddr3

i cant wait to buy a new computer :(

---

### Post by cascade9 on 2010-04-12
> **spikeofdoom said:**
> well im just saying, atm i have the x1600 which i cant get a driver for, so im really not looking for an upgrade so much as maybe an nivida alternative? does Ubuntu like nivida better? i kinda assumed they did. (by like i mean have better support for)
if 2.0 cards are backwards compatible ill prolly get the 220 cause i can find them very cheap, now the question is, does 10.04 support the 220 with full 3d support? so if i wanted to get ambitious i could easily play urban terror (quake 3 mod), i tryed doing comparisons and they came up with the 220 being way better then i currently have as well, so that would be nice since it's cheap. oh for the record

Linux generally is has better drivers with nVidia, and (as yet) nVidia keeps making drivers for the older series cards, something that ATI should do as well..but they dont :(  

You should be able to get full 3D with the GT220 on any linux distro. 10.04 should work fine with the GT220. 

Even if you werent after it, the GT220  should be a major upgrade from an x1600. ;) 

As for the PCIe 1.0/1.1/2.0 issues, this is what wiki says about it- 

> PCIe 2.0 motherboard slots are fully backward compatible with PCIe v1.x cards. PCIe 2.0 cards are also generally backward compatible with PCIe 1.x motherboards, using the available bandwidth of PCI Express 1.1. Overall, graphic cards or motherboards designed for v 2.0 will be able to work with the other being v 1.1 or v 1.0.

[http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_2.0](http://en.wikipedia.org/wiki/PCI_Express#PCI_Express_2.0)

I havent heard of any problems with PCIe 2.0 cards in 1.x slots. No doubt some exist, but its not normally a problem. 

> **spikeofdoom said:**
> 
Amd 4200+ on 939, preventing me from upgrades:(
2 gigs of sd-ddr
160gig 5400rpm laptop drive cause my other is full
ati radeon x1600 xt   (590/900)core/mem if i remember correctly 512Gddr3

i cant wait to buy a new computer :(

Socket 939 might well be upgradable, depending on what chips yoru motherboard will take (some support opteron and athlon FX chips) An Opteron 185 (2.6Ghz, 2x1024k cahce) or a FX-60 (same as the opteron) would be a major upgrade ;)

---

### Post by spikeofdoom on 2010-04-12
hmmm, i thought i had one of the best prcessors for my board, (which is a modifiyed HP media center)
 i live in CNY
and there used to be COMPUSA's around, well when they almost went under like 7 years ago is when i got this thing, its a athlon x2, which i like the processor, never had problems with it  2.2ghz each core, i played oblivion (which to this day is still one of the best games ever!) on ultra high settings, 1600x1200 with details and everything on high, ran fine and was getting 40 FPS average, tryed playing boarderlands, HAHAHAHAHA no where near good enough, downloaded L4D2 and hada overclock my GPU for it to run smoothly, but that was in winter when i could pipe my window fan with a vacuum cleaner hose taped to it right at my comp's intake. (comp ran so ****ing smooth when i had that, cept my room was a bit colder)

but you all have been such a great help so thankyou very much. imma get a GT220 and that should be good, and throw another gig stick of ram in, ( i mean it's sd-ddr 3200, i can find that in a gutter these days)

so that will put me to 
athlon x2 4200+ (2.2ghz)
3gb sd-ddr
gt220
160gb 5400rpm

what i'd like is to also find eather a 7200rpm or maybe another 5400 or 2 older 7200 so i can speed it up a bit, run raid 0 if i find a 2nd drive (yes i know they should be identical)

but again thx for all the help

---

### Post by lakerssuperman on 2010-04-12
I used a Geforce GT 220 in a test rig I just built.  I currently have Kubuntu 10.04 running on this machine and it runs very well.

Here is the link to the card I used.  It serves it purpose well, gives excellent performance with desktop effects and can playback HD video with VDPAU.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347&Tpk=geforce%20gt%20220]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121347&Tpk=geforce%20gt%20220")

---

