---
title: "RAM and HDD question :)"
date: 2010-08-28
forum: General Help
---

### Post by M93 on 2010-08-28
hi, could u please tell me how do i know what type of RAM i am using?
what is my limit?(if there is)
and where is RAM and HDD located in the laptop in case i want to change them?
i have a Sony Vaio VGN-FW230J

thank you :)

---

### Post by ShakeyJake on 2010-08-28
The command

```
sudo lshw
```

will tell you all of those things, but then again so will actually opening the case and looking. The memory and hdd are usually pretty accessible, are there and obvious cutouts on the bottom that look like they can be unscrewed? 
[URL="http://repair4laptop.org/contrib/samsung_x10plus/samsung_x10plus_upgrade.html"]
Something like this?[/URL]

---

### Post by M93 on 2010-08-28
*-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM DDR2
             physical id: 0
             slot: SODIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2
             physical id: 1
             slot: SODIMM2
             size: 1GiB
             width: 64 bits


i understood that ive got 2 slots 2GB + 1GB
can i have more slots or if i want to upgrade i have to remove the 1GB and get a new one and what brand would be compatible?
those pictures were helpful i found those cuts.
thank u for ur effort :)

---

### Post by ShakeyJake on 2010-08-30
You're welcome. 

You've probably only got those two slots, so any upgrade will likely need to remove one or both of the RAM sticks. You can check the speed of the RAM by either physically looking and opening up the laptop or by rooting around in the BIOS.

Once you've found the speed, any DDR2 sodimm of a similar (or below, usually) speed will work. If you're on a 32-bit OS then 3GB is really the most you can have. Your laptop itself might top out at 4.

EDIT - 30 seconds on Google found [this]("http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFW230J") page. If you click 'marketing specifications' you can see that your laptop can handle 8GB of PC6400 ram. [Any of these would do.]("http://www.lambda-tek.com/componentshop/index.pl?level3=MEMSTAND&searchString=&mfr_uid=&minprice=&maxprice=&show=stock&itemsperpage=400&keywords=&pFilter0=DDR2&pFilter1=&pFilter2=SODIMM&pFilter3=&pFilter4=&pFilter5=800&ordering=price") Google is your friend.

---

### Post by M93 on 2010-08-30
it says>
Type: DDR2 SDRAM 
Installed: 3GB PC2-6400 (2GBx1 + 1GBx1)
Maximum: 8GB
Speed: 800MHz....is this the speed ur talking about?
what brand do u recommend?

---

### Post by ShakeyJake on 2010-08-30
Well the speed is 800MHz you're right. RAM that has a 800MHz speed is known as 'PC-6400' (for some not-very convincing reasons, but I digress) so any of the ram that I liked to before would do, or any stick of laptop-sized pc-6400 ram for that matter. If it says PC-6400 or 800Mhz you're good to go. 

IMO the brand of the memory probably isn't too important. I would just try and avoid the cheaper no-name brands. They're probably ok too actually, I would just feel safer buying from a well-established name with a good warranty. You might want to check out Corsair, OCZ, Kingston, Geil, Crucial etc.

---

### Post by cascade9 on 2010-08-30
> **ShakeyJake said:**
> Once you've found the speed, any DDR2 sodimm of a similar (or below, usually) speed will work. 

Always go OVER, not under, the rated speed of your current RAM. In a lot of cases, the slower RAM will work, its just going to run slightly slower than it could do. But sometimes running slower RAM can give all sorts of problems..... 

As long as you get decent quality DDR2-800 or higher, there shouldnt be any problems (I'd avoid 'yum cha' cheap RAM, normally its OK but why risk it for a few $$$?).

---

### Post by deserthowler on 2010-08-30
> **cascade9 said:**
> Always go OVER, not under, the rated speed of your current RAM. In a lot of cases, the slower RAM will work, its just going to run slightly slower than it could do. But sometimes running slower RAM can give all sorts of problems..... 

As long as you get decent quality DDR2-800 or higher, there shouldnt be any problems (I'd avoid 'yum cha' cheap RAM, normally its OK but why risk it for a few $$$?).

In my experience, sometimes DDR likes to be matched as to brand and style and sometimes not.  I don't know why but this is the case.

Earl

---

### Post by M93 on 2010-08-30
thanks alot for ur help...now i knw wut i need i'll just go get it :)
just one thing left :) ...hdd? ..i have 250GB 5400rpm, i want to upgrade it wut shall i do? wut do i need to knw about wut im gona get?

---

### Post by ShakeyJake on 2010-08-31
It's pretty much the same situation  as it is with memory. Any matching HDD (in your case a 2.5" sata hard drive) will work just fine. I'm partial to Western Digital myself. I have 6 of their drives from different ranges and all are flawless.

Obviously you'll lose everything, so make sure you have a way of keeping all your files safe during the transfer and a way of reinstalling an OS.

---

### Post by M93 on 2010-08-31
so it has to be a 2.5" and sata

nothing else specific has to be there, the rest is up to me? (brand, size, rpm)

i'll keep WD in mind i've tried a lot of their products n they r good :)
thank u alot :)

---

