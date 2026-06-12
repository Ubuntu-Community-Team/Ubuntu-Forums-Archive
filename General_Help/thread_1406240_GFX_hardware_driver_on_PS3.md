---
title: "GFX hardware driver on PS3"
date: 2010-02-13
forum: General Help
---

### Post by kokkus on 2010-02-13
Hey.
I need to know what graphic card I have so i can find the right driver.
and yes i've tried "hardware" under system>admin.

please help.

---

### Post by kokkus on 2010-02-13
oh, and it's version 8.10.
help me plz. thanks in advance.

---

### Post by lidex on 2010-02-13
Enter this in a terminal:
```
lspci -nn | grep VGA
```

---

### Post by 3rdalbum on 2010-02-13
Sony doesn't allow graphics acceleration on Linux on the PS3, so there's no driver you can install. Or, more correctly, the default graphics driver is the only one that will work.

---

### Post by lidex on 2010-02-13
> **3rdalbum said:**
> Sony doesn't allow graphics acceleration on Linux on the PS3, so there's no driver you can install. Or, more correctly, the default graphics driver is the only one that will work.

Hmm. Guess I should have read more closely...Doh!

---

### Post by kokkus on 2010-02-14
ok i typed in the command and nothing happend, so what do I do now.
And what's the default graphic driver, so I can activate the desktop effects?

---

### Post by TheOnlyMrK on 2010-02-14
> **kokkus said:**
> ok i typed in the command and nothing happend, so what do I do now.
And what's the default graphic driver, so I can activate the desktop effects?

You can't activate desktop effects. When running a second OS on a PS3 you are limited to two CPU cores running at 500Mhz, 256MiB RAM, and no direct access to the video card. Basically it's about as powerful as a desktop from the 90's with a graphics card from the 80's.

---

### Post by TheOnlyMrK on 2010-02-14
Also this website/link was useful to me when I installed Ubuntu on my PS3. [http://psubuntu.com/speed-up-psubuntu/](http://psubuntu.com/speed-up-psubuntu/) After using Ubuntu on my PS3 for a few minutes I found out it's rather useless to an average user and stopped using it, but left it installed as something to use in-case something ever happened to my desktop. Honestly if they wanted to limit the PS3's second OS capabilities to prevent pirating why didn't they just disable the blu-ray drive (make it look like just a CD drive) to the second OS instead of limit the entire second OS to the point it's hard to simply browse the internet.

---

### Post by kokkus on 2010-02-14
Great :( so why do ppl instaall a 2nd OS on their ps3 then?

---

### Post by TheOnlyMrK on 2010-02-14
> **kokkus said:**
> Great :( so why do ppl instaall a 2nd OS on their ps3 then?
The most popular use I've heard of is to emulate old game systems like Super Nintendo (they had 16bit 3.58Mhz CPU's so that's still easy for the PS3 to emulate) or just to be able to use Firefox since the PS3's built in web browser is so slow.

---

### Post by mcduck on 2010-02-14
> **TheOnlyMrK said:**
> You can't activate desktop effects. When running a second OS on a PS3 you are limited to two CPU cores running at 500Mhz, 256MiB RAM, and no direct access to the video card. Basically it's about as powerful as a desktop from the 90's with a graphics card from the 80's.

Actually that would be one CPU core at 3,2 GHz. And the SPUs are also accessible, but since none of the programs you use are designed to use Cell architecture the SPU's don't really do anyhting unless you start progrmming with them yourself..

I'm not quite sure where you got the 500MHz thing, I suppose you confused Cell with the EE from PS2, running at 300MHz...

True about the RAM, amyway, and that's the main reason why PS3 isn't something you'd like to use as desktop computer.

---

### Post by TheOnlyMrK on 2010-02-14
> **mcduck said:**
> Actually that would be one CPU core at 3,2 GHz. And the SPUs are also accessible, but since none of the programs you use are designed to use Cell architecture the SPU's don't really do anyhting unless you start progrmming with them yourself..

I'm not quite sure where you got the 500MHz thing, I suppose you confused Cell with the EE from PS2, running at 300MHz...

True about the RAM, amyway, and that's the main reason why PS3 isn't something you'd like to use as desktop computer.
I had read it on a website that went into a lot of in depth detail on the PS3. Guess I should of mentioned I hadn't proved it myself, I was just sure that's what it was since everything else on the website was correct. Do wish I hadn't of lost that link because it had everything you could imagine on PS3s.

---

### Post by kokkus on 2010-02-14
Well, I guess it's ok though.
I can still use it to play gba, snes, sega and dos games.
HURRA!
I wish I could chip the console or something so that the OS would read the built in graphic card the PS3 uses. It must be possible somehow.
Maybe it could work with a portable USB graphic card?

---

### Post by TheOnlyMrK on 2010-02-14
> **kokkus said:**
> Well, I guess it's ok though.
I can still use it to play gba, snes, sega and dos games.
HURRA!
I wish I could chip the console or something so that the OS would read the built in graphic card the PS3 uses. It must be possible somehow.
I haven't heard of anyone being able to do it yet. But I do know many people are hard at work trying to make it happen. But honestly the PS3's video card is outdated compaired to todays market, it's just a remodeled Nvidia GeForce 7800 that they named "The Reality Synthesizer". And no that doesn't mean you can download the GeForce 7 drivers and it'll work. :P I wish it did.

---

### Post by mcduck on 2010-02-14
> **TheOnlyMrK said:**
> I had read it on a website that went into a lot of in depth detail on the PS3. Guess I should of mentioned I hadn't proved it myself, I was just sure that's what it was since everything else on the website was correct. Do wish I hadn't of lost that link because it had everything you could imagine on PS3s.

Ok. Sounds like you found some false information, Cell dosn't even *have* two general-pupose cores.. Only one PowerPC-based one, and seven SPUs (on the version used in PS3, the ones IBM uses have eight). And all those run at 3,2GHz.

(Although I wonder where thay might have got the two cores -thing. EmotionEngine used in PS2 didn't have two general-purpose cores either, it had one MIPS R10000-based core and two VPUs, all running at 299MHz.)

---

