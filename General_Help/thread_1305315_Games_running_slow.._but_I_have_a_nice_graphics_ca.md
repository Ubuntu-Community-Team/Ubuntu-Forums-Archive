---
title: "Games running slow.. but I have a nice graphics card?"
date: 2009-10-29
forum: General Help
---

### Post by Mekkakat on 2009-10-29
Hi guys. I'm new to the forums, and equally new to Linux, and I'm confused..

I've searched the web to fix every problem I've had so far, such as the sound not working, the ethernet not working, etc.. But I'm finally stump stumped. 

I'm running 4gb RAM, a powerful quad core processor, and an Nvidia 8800gt oc, but for some reason NOTHING will run without lag. I KNOW it can be done, but it just won't work for me.

I've tried turning Compiz off with metacity --replace, but that had no effect.

I've used the hardware manager thing, and it says I have the "recomended" drivers or whatever. 

I used that glx | ... something or other command and had nothing that *seemingly* seemed wrong (nothing said "no" or "error")

I used whatever command made that 3d gear thing come up and it told me I had like.. 85,000+ FPS.


so... Any clue at all guys? I'm using WINE, and the only games I've tried are Left 4 Dead and Guild Wars (which has low req anyhow..) and both lag a LOT. Like.. a lot a lot. Unplayable. That's absurd seeing as I could run Crysis at near max (only one slider wasn't maxed) without a single hiccup.. 

Any help is greatly appreciated guys, and thanks in advance.

---

### Post by Xero Xenith on 2009-10-29
Please go to System, Administration, NVIDIA X Server Settings, and tell us what it says for "Operating System" and "NVIDIA Driver Version". Which Ubuntu release you're running would also help :)

(If you're willing to jump in and potentially break things, [there's a PPA I use]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") for the latest (beta) drivers, which seem to run magnificently.)


EDIT: some more info that would be useful:
[list=1][*]Which WINE version are you running? Go to Applications -> Wine -> Configure Wine -> About.
[*]Did you run Crysis on Windows or WINE?[/list]

---

### Post by Mekkakat on 2009-10-29
Nvidia X driver version: 180.44

I'm running whatever the newest Ubuntu is (9. something or other I think?)

Wine version: 1.0.1

I ran Crysis on Windows Vista. 

I'm really looking for a fix guys or else it's back to 7 for me :/

I really wanted my desktop to be my main gaming machine (which it was.. ) and I figured Ubuntu would cut a lot of the resource usage down for an even faster, cleaner operation..

---

### Post by Mekkakat on 2009-10-30
Anyone at all :/ ?

---

### Post by Xero Xenith on 2009-10-31
If you want your desktop to be your main gaming machine, go with Windows 7 all the way. I'm afraid Ubuntu is nowhere close to that for gaming. There are two main issues with Windows gaming on Ubuntu - one, the drivers are usually not as good, though as I said, the latest NVIDIA 190 drivers seem to be an improvement.

But second and most importantly, the implementation of the Windows API supplied by WINE is very incomplete, and is still full of glitches and bugs. It's improving at a fast rate - [here's the changelog for just the two weeks before October 23]("http://www.winehq.org/announce/1.1.32") - but it won't be complete for quite a while yet.

Ubuntu is not for PC gamers, and I'm very sorry on behalf of anyone who misled you. I've found it to be a free, secure, hugely customisable and easy OS, which is why I use it; but gaming isn't its strong point.

(Do you still want help with your problem?)

---

### Post by Mekkakat on 2009-10-31
Well I suppose that would have to settle it then.. It's just odd.. I've seen videos and know a guy I go to college with that have games like Fallout 3 and Left 4 Dead running at max speed, super high FPS using Ubuntu/Wine. 

Well.. thanks anyhow, I doubt I'll be using Linux anymore.

---

### Post by Xero Xenith on 2009-10-31
It is possible; some games do work very well, and it's possible for the ones that do to run at higher FPS than Windows. But from my experience, doing so requires quite some setup following guides from AppDB, or alternatively, a third party program that does it for you, such as Crossover Games; however the well-supported ones usually cost money.

It might be worth checking out the AppDB entry for anything you want to run. ([Here's one from Left 4 Dead, reporting how to get a reasonable, but not great, framerate.]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592&iTestingId=44029"))

But standing by what I said before - for gaming, Windows 7 beats everything.

---

