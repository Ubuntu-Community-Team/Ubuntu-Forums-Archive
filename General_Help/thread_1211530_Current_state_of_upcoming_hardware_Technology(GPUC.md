---
title: "Current state of upcoming hardware Technology(GPU/CPU/RAM/HDD)+Purchasing advice"
date: 2009-07-12
forum: General Help
---

### Post by Andy06 on 2009-07-12
Going to be advising my college dorm admin about buying approx. 2 dozen notebooks.

Just thought I'd pick up some advise here on the current state of implementation of some upcoming and recent technology.[Do answer everything with Linux in mind since I'll be installing Ubuntu on all of them, apart from keeping the windows partition]

**1.Wireless cards**
What's the status with wireless cards.How are recent Broadcom and Atheros ones faring? Hearing a lot about them now being much better, but is it relatively full proof support like for Intel cards? Should I stick with Intel to be on the safe side?

**2.Wireless cards II**
Where are we with the 802.11n specification? Most OEMs are selling N cards already but I understand that these are mostly draft or pre N devices. When will N specification be finalised and when will the first "official" devices hit the notebook market. Will there be a significant lag from the desktop market?

**3.GPU**
I've used Nvidia as far back as I can remember so what are the integrated Intel chips like? GMA ones and others, also what about ATI ones. Are ATI drivers as good as the Nvidia ones for Ubuntu?
I tried a liveUSB on a notebook with Intel integrated graphics and desktop effects and streaming youtube both worked fine. In fact it was better than fine since they work out of the box. You can never get a LiveUSB to work with compiz if you have Nvidia or ATI cards (or can you?)

If I enable all fancy effects, will the Intel GPUs be able to handle it? What about DVD,HD, youtube, flash video? There will be NO gaming whatsoever on this comps so gaming is not an issue.

When the new X server upgrade caused the Intel performance regression in 9.04, how bad was it? Could you use effects/youtube? Is it likely to repeat?

**4.CPU**
Core 2 is old, Core i7 is the new desktop line right, where is the corresponding notebook line and when will it be released? I've heard about Core i5 and Core i3 and Core i9 as well, besides there is Lynnefield which will come under both the Core i5 and i7 brands. What is Lynnefield? How is it different from Nehalem. Which of these are 45nm, which is the next gen 32nm and then the 22nm they seem to talk about. How does all this tie together, can someone break it down and explain :D

It seems I have the architecture, the actual chips and the sales branding all mixed up. I'm sure lots of users would like to know.

**5.RAM**
DDR3 worth it? The people who have it on the desktop say no its not, no perceivable difference. But big difference in cost, for which you can get far more DDR2 and that physical difference IS perceivable.
Has the cost come down to DDR2 level yet? DDR3 is only compatible with Core i7 onwards right? (or is the other way round, that core i7 can only work with DDR3?) 
When will we start seeing DDR3 in notebooks? With the next gen Intel chips?

**6.HDD**
5400RPM or 7200RPM is a bigger noticeable jump in speed or 5400RPM to SSD?
I ask because I have never used 7200RPM and dunno what its like but with SSDs its like hit and miss, sometimes it will go through at jaw dropping speed, other times it will crawl. Especially write speed is very inconsistent. 

**7.USB3.0**
When will this be standardised as the notebook port by OEMs? Does it make a big difference when connecting an external HDD with USB2.0 to USB3.0 or is the hard drive itself the bottleneck?

**8.Bluray**
Does it matter, does the optical drive itself matter? I last used mine I dunno how long ago. With windows I used it often, with linux, barely if ever.

**9.Netbooks**
Finally netbooks, for the use case of needing fancy desktop effects (compiz) + smooth youtube videos but not much else in the way of graphics prowess, would you:
a) recommend Atom 
b) recommend Via
c) recommend ARM
d) recommend Nvidia Ion with Atom
e) something else or none of the above

I mean sure Ion, but how far behind are the rest? Feel free to add a chip I've missed, haven't kept up to date with netbook technology :D


Thanks a lot guys.
Can't wait for the replies, this should be a good discussion.

---

### Post by earthpigg on 2009-07-12
for most of that, i have no idea.

what i can tell you:

**_avoid ATI like the plague._** NVidia for the win.

_at least_ 90% of the people posting on these forums with display issues are using ATI cards.... and a lot of us that have been using Linux for a while simply cannot help them, since we know better and do not purchase ATI cards, thus meaning we have no idea how to get them to work with ubuntu (since we dont have them, we've never needed to learn how to make them work).

trying to use an ATI video card is a double-whammy: they dont work well, *_and_* fewer people can help you make them work since fewer linux users bother with them.


linux makes more efficient use of RAM than windows... if you install the app 'preload' on all of the laptops and have lots of fast ram, they will get *faster* over time as preload learns what apps each user uses the most and loads them into RAM ahead of time.

---

### Post by Andy06 on 2009-07-12
Thanks for that :D

Will avoid ATI.

Have preload on my system, In my experience though, its not as efficient as Windows Superfetch/prefetch. You can check yourself by comparing cold and warm start up times of Firefox for example or any heavy app like GIMP or OpenOffice Word. Also I think Windows uses its RAM better because it actually USES it as opposed to linux which keeps it empty. Although the tables will turn when you open something new and windows now has to do a swap operation.

Thanks :)

---

### Post by Gizenshya on 2009-07-12
Universities almost always have a set plan in place for upgrades.  I'm curious about the time period set at your university.

You said no gaming, ok.  What will they be used for?  Academic use only?  Leisure as well?

Personally, I see no point in adding Blu-ray to them.  A DVD/CD writer combo should be just fine.  If anything, just get it on a few of them.

Core 2 duo's will be more than sufficient.  Only gaming rigs even need that much power to be honest with you.  anything more will be a waste.

I prefer 7200 RPM drives.  I use 7200 RPM SATA II drives now and there is little room for improvement.  The SSD drives are not worth the cost IMO.

GPU... I recommend nvidia graphics.  They typically use less power, give off less heat, and are more compatible with linux distros.

---

### Post by blueridgedog on 2009-07-12
Here is a cpu link that may help:

[http://www.neowin.net/news/main/09/06/21/intel-clarifies-new-core-i3-i5-and-i7-cpu-branding](http://www.neowin.net/news/main/09/06/21/intel-clarifies-new-core-i3-i5-and-i7-cpu-branding)

It seems that anything in those lines in a laptop form factor is still vaporware.

My take:  Core 2 Duo, any wireless chipset that is compatible with Linux, DDR2 as much as you can get (unless memory is shared with the GPU, then go DDR3), Nvidia, DVD burner, USB 2.0 and the largest drive you can afford.

I love my netbook, but could not imagine it in place of my desktop or laptop when I need one of them.

---

### Post by Andy06 on 2009-07-13
> Universities almost always have a set plan in place for upgrades. I'm curious about the time period set at your university.

You said no gaming, ok. What will they be used for? Academic use only? Leisure as well?

This isn't university, its the university's dorm computers, so a little less official and smaller scale (about 25 computers). Since there is no official IT department, they replace them when all the students start complaining and passing comments about how old the admins PCs are :D

I need them to be future proof........for the next 4 years at least. That's the minimum time they will be using these. No serious gaming (just the pre installed ones if someone likes sudoku etc and maybe flash based games on the web). The limits of graphics usage will be flash, DVD and HD video and full compiz effects (coz I showed that as an integral part of Ubuntu :roll:

> Here is a cpu link that may help:

[http://www.neowin.net/news/main/09/0...7-cpu-branding](http://www.neowin.net/news/main/09/0...7-cpu-branding)

I read the link and the comments. Still confused, as are the people posting the comments it seems. Still have no idea what the Intel product line will look like in 1 year and which of those will be for laptops? Core i3 and Core i5? But all of these Core i's are just fronts or brands, the real chips are now the codenames like lynnfield and clarefield right? So which of those? Nehalem is the common future architecture of them all?

If people on neowin, ubuntuforums and linux users are having trouble grasping this, what exactly is Intel thinking? 90% of buyers then have no clue as to what they should get and when it doubt, they will stick to cheap. Which is fine I guess, since the cheapest chips are more than capabale of everything except gaming (right?).

Anyone have any advice on the rest of the sub-topics in the original post?

Thanks a lot guys

---

### Post by Andy06 on 2009-07-15
*bump*

---

### Post by t4thfavor on 2009-07-15
1. Intel WIFI, then Atheros

2. No N I hate pre-standard.

3. Intel to have less probles, Nvidia for more performance. Avoid ATI like the plague.

4. If you can go i7 do it it has 2 physical threads per core as opposed to the c2d's single thread per core.

5. I have 8GB ddr3 on a core 2 quad, and it screams. It was marginally more expensive at the time, and I think it leaves you open to *upgrade* later in your PC's life. So if 50 USD difference matters to you go DDR2.

6. No SSD they are too expensive for a fast enough one to make a difference go 7200 or even 10k SATA :)

7. Again pre standard stuff scares me.

8. I avoid Sony anything like the plague. (so no)

9. I have intel Atom (ASUS 900a) and love it. I wish was 64 bit, and had a dual core. 

Thats all!

Hope this helps you.

---

### Post by Andy06 on 2009-07-16
> 1. Intel WIFI, then Atheros

What about Broadcom? Wasn't Atheros later in the game than Broadcom who have been at it for a while trying to produce Linux drivers? I will definitely try Intel though. Most HP/DELL notebooks come with Intel anyway right?


> 2. No N I hate pre-standard.

Ya I hate speculative standards as well. When will it come to market in notebooks though, any idea?

> 3. Intel to have less probles, Nvidia for more performance. Avoid ATI like the plague.


Understood. Have always used Nvidia, never ATI, but I am curious about Intel, it saves cost big time and what will the performance be like? Since you have a Atom netbook with an Intel card, can it run full blown compiz with burn and wobble and cube effects? :D

What about streaming full screen youtube and DVD quality movies saved on local HD?

Also you said Intel for less problems, but din't 9.04 have a huge performance regression with Intel cards due to the new X?

> 
4. If you can go i7 do it it has 2 physical threads per core as opposed to the c2d's single thread per core.

Core i7 is desktop only I think, so not an option for me (as I am going to be ordering notebooks, all of them). What's the notebook next gen? Core i5? Core i3? Core i9? All names are floating around....Lynnefield? Clarefield? And when? :D

All on Nehalem? 45nm? 32nm? 22nm? 

Intel hates its users. :mrgreen:


> 5. I have 8GB ddr3 on a core 2 quad, and it screams. It was marginally more expensive at the time, and I think it leaves you open to *upgrade* later in your PC's life. So if 50 USD difference matters to you go DDR2.

Problem is people at notebook forums keep saying there is no difference, I din't feel any myself but then again DDR3 does not even promise a night and day difference, I'm not sure I am perceptive enough to feel it even if its there :).
I'll get DDR3 anyway just to be futureproof.

I checked at Kingston's site and as of now 2 GB DDR3 (USD45-50) is almost twice the price of DDR2 (USD25). 1 GB DDR3 (USD25-30) is bit  more than 1 GB DDR2(USD16), the absolute differences are small however. When will be begin to see partiy? Q1 2010?

> 6. No SSD they are too expensive for a fast enough one to make a difference go 7200 or even 10k SATA

Agreed. It *felt* as if 7200 RPM are faster than the early SSDs that I tried.

> 7. Again pre standard stuff scares me.

When will USB3.0 be standard though?

> 
9. I have intel Atom (ASUS 900a) and love it. I wish was 64 bit, and had a dual core.

Nvidia Ion uses Atom. Plus an Nvidia for GPU :D
How does the Atom and Intel fare with full blown compiz, streaming full screen youtube and DVD movies from HD though?

What about Via's claims of being better than Atom at just about everything? And ARM? Is that just for lower cost smaller tablets?

Thanks a lot

---

### Post by earthpigg on 2009-07-16
> **Andy06 said:**
> 

Understood. Have always used Nvidia, never ATI, but I am curious about Intel, it saves cost big time and what will the performance be like? Since you have a Atom netbook with an Intel card, can it run full blown compiz with burn and wobble and cube effects? :D
...
Also you said Intel for less problems, but din't 9.04 have a huge performance regression with Intel cards due to the new X?


compiz + ubuntu netbook remix + intel netbook = epic fail (at present).

take out compiz, and UNR works fine.
take out UNR, and compiz works fine.* 

more info:
[https://bugs.launchpad.net/netbook-remix/+bug/247175](https://bugs.launchpad.net/netbook-remix/+bug/247175)

my personal opinion on the matter:
[https://bugs.launchpad.net/netbook-remix/+bug/398534](https://bugs.launchpad.net/netbook-remix/+bug/398534)




*that is, compiz works fine with the *default* 'extra' settings in system -> preferences -> appearance -> visual effects. compiz in general has always been a bit buggy/awkward with certain custom setting combinations in CompizConfig Settings Manager, as we all know. :D

---

### Post by blueridgedog on 2009-07-17
> **earthpigg said:**
> 
take out compiz, and UNR works fine.
take out UNR, and compiz works fine.* 


I only use UNR on a netbook of mine and I wouldn't really want to try compiz on that system (I don't need the extra cpu/gpu cycles either dragging the battery life down).

---

### Post by egalvan on 2009-07-17
> **Andy06 said:**
> This isn't university, its the university's dorm computers, so a little less official and smaller scale (about 25 computers).
 [B] they replace them when all the students start complaining and passing comments about how old the admins PCs are :D
[/B]

If I know college students, they will ** start complaining and passing comments about how old the[COLOR="Red"] admins[/COLOR] PCs are :D** the second time they boot them :D

> 
I need them to be **future proof.**.......for the next 4 years at least. That's the minimum time they will be using these.

"Future Proof"... doesn't exist in the real world.
As long as newer software comes along that demands bigger/faster hardware, machines will become outdated.

that said, if the software does not change appreciably, then yes,
you can make hardware work for a longer period.

I'm still using P-II machines in some applications...

---

### Post by 3rdalbum on 2009-07-17
> **Andy06 said:**
> **1.Wireless cards**
What's the status with wireless cards.How are recent Broadcom and Atheros ones faring? Hearing a lot about them now being much better, but is it relatively full proof support like for Intel cards? Should I stick with Intel to be on the safe side?

Atheros seem to be on a win - very stable drivers, good range, good speed, good Linux compatibility. Forget Broadcom, I don't think many Linux users really trust their drivers.

> **3.GPU**
I've used Nvidia as far back as I can remember so what are the integrated Intel chips like? GMA ones and others, also what about ATI ones. Are ATI drivers as good as the Nvidia ones for Ubuntu?

Go Nvidia if available. They are orders of magnitude faster than Intel. Also, the GMA 500 Intel graphics chipsets are not supported on Linux yet! With Nvidia you might not get Compiz effects from a live CD, but you *do* get VDPAU video playback acceleration with Mplayer when using proprietary drivers. Which would you rather have?

> **4.CPU**
Core 2 is old, Core i7 is the new desktop line right, where is the corresponding notebook line and when will it be released? I've heard about Core i5 and Core i3 and Core i9 as well, besides there is Lynnefield which will come under both the Core i5 and i7 brands. What is Lynnefield? How is it different from Nehalem. Which of these are 45nm, which is the next gen 32nm and then the 22nm they seem to talk about. How does all this tie together, can someone break it down and explain :D

I'm not completely up with my CPUs, but Core 2 is still a good solution on notebooks, and virtually the only serious option. Core i7 is only an option for high-end desktops (yeah, I know Pioneer has released an i7 notebook but it's a monster). I haven't heard of Core i9.

> **5.RAM**
DDR3 worth it? The people who have it on the desktop say no its not, no perceivable difference. But big difference in cost, for which you can get far more DDR2 and that physical difference IS perceivable.
Has the cost come down to DDR2 level yet? DDR3 is only compatible with Core i7 onwards right? (or is the other way round, that core i7 can only work with DDR3?) 
When will we start seeing DDR3 in notebooks? With the next gen Intel chips?

Apparently there isn't quite so much a difference in cost between similarly-specced DDR2 and DDR3. Some Core 2 compatible motherboards offer dual-channel DDR3, as well as all AM3 motherboards (on the AMD side). I believe DDR3 is available in notebooks but I'd say it might be overkill there.

> **7.USB3.0**
When will this be standardised as the notebook port by OEMs? Does it make a big difference when connecting an external HDD with USB2.0 to USB3.0 or is the hard drive itself the bottleneck?

The interface is the bottleneck, not the hard drive. I don't know when USB 3 will be coming out, but I don't see the sense in delaying a purchase based on this; there's always something new coming out in IT.

> **8.Bluray**
Does it matter, does the optical drive itself matter? I last used mine I dunno how long ago. With windows I used it often, with linux, barely if ever.

Blu-ray is pretty cool to have, but when you're talking about Linux you have to be careful what movies you buy. The hackers don't have a public decryption key for the latest discs (MKBv12) so you can't play them on Linux until we get that key. If you get an Nvidia GPU you can offload much of the decoding load to the GPU using VDPAU, which is very important!

> **9.Netbooks**
Finally netbooks, for the use case of needing fancy desktop effects (compiz) + smooth youtube videos but not much else in the way of graphics prowess, would you:
a) recommend Atom 
b) recommend Via
c) recommend ARM
d) recommend Nvidia Ion with Atom
e) something else or none of the above

You don't need fancy desktop effects. You want them, but you don't need them.

It restricts you to Atom + GMA, or Ion. Obviously Ion is the better choice, but I haven't seen any Ion netbooks on sale yet.

---

### Post by 3rdalbum on 2009-07-17
> **Andy06 said:**
> 
I need them to be future proof........for the next 4 years at least.

To quote Daryl from the movie The Castle: "Tell him he's dreaming!"

You won't get 4-year futureproofing on a notebook. Even on a desktop you need to swap out components to do it; it ends off being an entirely new computer :-)

> Still have no idea what the Intel product line will look like in 1 year and which of those will be for laptops? Core i3 and Core i5? But all of these Core i's are just fronts or brands, the real chips are now the codenames like lynnfield and clarefield right? So which of those? Nehalem is the common future architecture of them all?

If people on neowin, ubuntuforums and linux users are having trouble grasping this, what exactly is Intel thinking? 90% of buyers then have no clue as to what they should get and when it doubt.

Heh, well that's the idea. Intel doesn't want people to hold out for laptops in a year's time, they want to drive sales now. If they don't get sales now, then they don't have the money to research new products, and if everyone holds out for the next big thing, then nobody would ever buy anything.

Intel doesn't need to tell ordinary tech enthusiasts the differences between future CPU lines - that's why they are given code names rather than branding. They are in heavy development and while Intel has a good idea what might be in Lynnfield and Clarefield and Sandy Bridge, anything can happen and most "features" are still on the drawing board.

---

### Post by t4thfavor on 2009-07-17
Netbook remix is not good for general use, but neither is a netbook. I run full compiz, and watch full screen youtube, but due to the lack of a dvd drive I have never tried one. 

I was giving general specs for any machine, but when looking specifically for a laptop, I look for "decent" performance, and excellent battery life.


If you can go 5400 rpm drives, ddr2, and a core 2 duo in the latest family, I think you will be much happier with the battery life. What good is a laptop if you have to have it plugged in after 20 min.


As far as Intel vs Nvidia, I get great compiz speed from my laptop gma950, not as good as my desktop 9600GT, but pretty good (and the difference is almost negligable).

I love my intel + atom, and would only change the size of the ssd in it if I had the chance.

I dunno about ARM since it will never run full Windows, it might be a good thing :) I do however like PPC which was an arm chip? Wasn't it? Probably stay away from VIA until you have used one, Does the VIA chip have Hyperthreading like my ATOM, prolly not.

---

### Post by Andy06 on 2009-07-19
Has anyone seen Ubuntu on a netbook with Intel GPU? Does it handle compiz and full screen youtube without stuttering?

I'm finding it very hard to find a friend with a netbook, everyone is interested, yet no one has one :D

---

### Post by Andy06 on 2009-07-25
Can anyone confirm the Intel compatibility with Compiz?

I tried Compiz on a friends GMA950 and it was working fine, burn effect, wobble, cube and everything.  GMA950 is old right? What's on latest netbooks? X1300?

Anyone using a netbook here with an Intel card? Need just 3 things to work with it:

1) Compiz
2) Full screen youtube/streaming
3) DVD movies played from local HDD

---

### Post by Andy06 on 2009-07-29
*bump*

---

