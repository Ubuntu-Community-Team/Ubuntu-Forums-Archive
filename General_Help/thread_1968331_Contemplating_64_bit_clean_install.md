---
title: "Contemplating 64 bit clean install"
date: 2012-04-28
forum: General Help
---

### Post by MainframeGuy on 2012-04-28
Despite a happy upgrade experience generally it broke my dual head :(

I am struggling to fix that (thread elsewhere) but have progressed to the point it seems the ATI drivers are 64 bit.... and I have made a 32 bit install (old habits die hard, it was the right thing for me at one time, even though this hardware supports 64 bit I wanted stability etc etc

Now I am thinking if it is time to review that decision.

Perhaps, I thought, it is worht having a thread for people to share their experiences or thoughts on the subject.

The main thing holding me back is that I have a horrible feeling I might go all around the houses of a fresh install, losing other aspects of my migrated system - only to discover the old ATI card still does not do dual head! (I'm NOT going to attempt to hack this system into 64 bit, that offends the coder in me!).

Apart from the general decision to go 64 bit (or not) someone with the right technical experience may well be able to answer that question for me also I hope....

Look forward to hearing experiences on this subject - or links to threads that cover what must be a recurring theme.

---

### Post by 3Miro on 2012-04-28
AFIK AMD/ATI have both 32 and 64-bit drivers. Regardless of which architecture you use, you should get the same functionality. 

If you have broken your system, a clean install may work and if your hardware supports it, you may go for 64-bit.

---

### Post by MainframeGuy on 2012-04-29
Thanks 3miro, that is pretty much what I expected, and I suspect my dual head experience with 64 bit COULD be better....

I am still interested in a general discussion on the merits/demerits of going for 64 bit....in the past I definitely thought it would help with older drivers and things - has this problem with the 64 bit system largely disappeared than?  Will I notice an improvement (especially with the DASH, which is broken for me at the moment!)?  Does the "clean install" tidy up a lot of stuff on a Linux system that's been around the update/migrate path from 11.04 to 12.04?

These are the sort of trade offs I was thinking about - hope that clarifies

---

### Post by xyzzyman on 2012-04-29
The only downsides left to someone using 64bit is processes on average tend to use 10-25% more RAM. Unless you are using all of your RAM, the performance increase of 64bit is worth it. Drivers aren't an issue anymore, especially in Linux with so many things baked into the kernel. 

If you've only got 1GB of RAM or less would be the only real reason to stick with 32bit. As far as fixing problems it's all the same source code, so if something doesn't work on 32 probably won't work on 64.

---

### Post by MainframeGuy on 2012-04-30
> **xyzzyman said:**
> ... Drivers aren't an issue anymore, especially in Linux with so many things baked into the kernel.....

Quick status update - dropped back the old 32-bit Natty that upgraded and then became compromised to a resized sda1 and made a fresh Precise install to the remaining space - which I am now using in single head mode.

So far so good - but I shall be awaiting the dual head with interest and especially whether I can fix the 32-bit install at that time.  If so then it will potentially mean I can try both and see if I notice the difference.

I have a feeling XYZZ is right; there's nothing realy to hold you back from 64 bit anymore, so I suppose the only reason the 32-bit is listed as the "recommended" in brackets is because it fits the greatest amount of legacy hardware, making it the "one size fits all" variant....

---

### Post by xyzzyman on 2012-04-30
64bit was decided to be the default for 12.04, but I must have missed when they changed it back to 32bit. I understand (l/x)buntu being 32bit, but ubuntu 12.04 really is meant for newer hardware that'll probably have over 1GB RAM anyways so not sure why they stayed behind. Time flies when you realize how long ago that 64bit XP came out and there was so many issues.

---

### Post by MainframeGuy on 2012-04-30
> **xyzzyman said:**
> ...Time flies when you realize how long ago that 64bit XP came out and there was so many issues.

Time flies even more when I think it feels like yesterday I was overhauling code to enable 32 bit support, never mind 64!  Time was when anything over 64k (yes, that is KILOBYTES) was a rather exotic region of memory to address.... 

But back to the subject I think they should make it the default for Quantal since Unity-3D probably demands such hardware anyway, I know with Natty one of the first things I did was turn down the eye candy.

Have to say so far I am enjoying my 64 bit experience, despite the loss of my 32bit install partition in the migration (damn, I hope I can get that back as dual boot to capture a few things and make the compairson)...

There are maybe a dozen or so crashes a day, but they are not critical ones, they are more program exceptions and seem to be getting mopped up fast by development.

That dual head bug was a major one from my point of view though, and I am surprised it got through to be honest, even more surprised by exactly HOW it could break the system

---

### Post by sambledsoe on 2012-10-07
Mainframe--
I'm facing a similar decision as your 28 April post-- any updates, in retrospect, about the 64-bit transition?
--sam (ex- mainframer, long time ago)

---

### Post by MainframeGuy on 2012-10-07
this thread post came as a slight blast form the past - I made that 64 bit install and have not looked back since.  No hardware, driver, or software issues.  Have not had recourse to look back to my old installation - just continues on with the 64 bit.  Possibly ought to add that I am not a leading edge user of kit or software, no gaming here, strictly within the open source community....

I have my suspicions and feel completely unaware I have gained anything, and suspect the software I use, the way I use it, and what I expect of it, ALL means I could quite possibly be satisfied with 16 or 24 bits, equally well as 64 or 32, so the question becomes a little academic!

On the other hand no problems - would encourage others to follow my lead I think, after all - nothing much to lose, can always go back if you hit something.

---

