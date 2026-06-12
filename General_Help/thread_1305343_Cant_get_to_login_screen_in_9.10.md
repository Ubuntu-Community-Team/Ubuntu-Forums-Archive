---
title: "Cant get to login screen in 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Kaneda187 on 2009-10-29
I just(and I mean just) install 9.10 and im very mad!! I cant login.
this system boots up all the way to just befor the login screen and then all i can see is that brown screen with nothing on it and it plays that drum sound to signel login.
I dunno what to do now! go back to 9.04?
I think this is ridiculous I mean if i hadnt kept my windows partition i wouldnt be able to get any help now with out installing a working version of ubuntu or booting into a live disk.
I'm shocked and saddened by this experience that i had been looking forward to.
this isnt the way a new ubuntu release should be!

Help guys please!!

---

### Post by Kaneda187 on 2009-10-29
bump

---

### Post by euphemus on 2009-10-30
Yeah - know how you feel - same thing here.
You can expect more of the same though: I've been at this since GG...
Gutless Gnat (Gutsy Gibbon)...
Headless Heffer (Hardy Herron)...
Increpid Ichidna (Intrepid Ibex)...
Jaundiced Jackass (Jaunty Jackelope)...
and now Katatonic Kakapo!

Every time you upgrade from one relese to the next expect to spend many weeks and months searching for answers and fixing problems.

Don't ever sound ungrateful - these Linux types get very touchy about their beloved operating system - its going to save the world from the corporate monster (microsoft) - well not at this rate - they'll have to make it a little less frustrating.

I don't care anymore - I am going to get back into my HDD, clear out the files, remove the 30 Meg Xp and Ubuntu, reformat all 1 Gig and install only XP on it. I've had enough.

Its like owning a car: I can drive very well and I like driving too; but when I get a new car I don't expect to have to lift the hood every couple of miles to replace the radiator hoses, or tighten the steering control arm, or replace the brakes. I'm not a F.....g mechanic!

Good luck! Hope you find your answer!

---

### Post by Kaneda187 on 2009-10-30
haha! thanks for the reply!
Im thinking of doing the same as im sick of this too I've had enough!
You should give windows 7 a go Im using it now and I upgraded from xp and i cant fault it yet it plays .avi files without having to install any codecs it burnt the ubuntu .iso without installing any other software. 
It starts up and shuts down quick gotta say im very impressed its like an upgrade of xp with a few extra bells and whistles.
most importantly though it worked after i installed it i could boot up go online and check my mail not like this 9.10 sick joke install it then boot up and start asking why isnt it working the last one worked fine so this one should be an improvement right?....nah WRONG its a joke!

---

### Post by P4man on 2009-10-30
are you using dual monitor by any chance?

---

### Post by Kaneda187 on 2009-10-30
nope no dual monitors.
my guess would be something to do with the fglxr drivers, since anytime i have a problem it seem to related or be rooted to the ati card I have.
its a mobility radeon X1400
I want to fix this and I want to use ubuntu as my primary OS but with things like this happening every few months its kinda hard to trust it and take the leap of not dual booting with windows or an back up OS

---

### Post by P4man on 2009-10-30
If you manually installed binary ATI drivers for that card, then an upgrade will break it. Although I thought the X1400 was no longer supported and you are limited to using the opensource ati driver. Did you try forcing fglrx ?

---

### Post by Monotoko on 2009-10-30
Did you do an upgrade or a frash install from 9.04?

---

### Post by Kaneda187 on 2009-10-30
I did a clean install and im not sure what you mean by forcing fglxr..?
I tried uninstalling fglxr drivers and setting xorg to default settings but that didnt change anything im just guessing now maybe it has nothing to do with the ati drivers and its a different problem entirely.
I was wondering if ther is a way to set it to auto login through the recovery mode shell?
because it loads up everything and i here the login screen drum i just cant type in my login because i cant see it but if i get it to login automatically then it should skip the login screen and go straight to the desktop and then i can fix it later.
this is just an idea now.

---

### Post by P4man on 2009-10-30
> **Kaneda187 said:**
> I did a clean install and im not sure what you mean by forcing fglxr..?
I tried uninstalling fglxr drivers and setting xorg to default settings but that didnt change anything im just guessing now maybe it has nothing to do with the ati drivers and its a different problem entirely.
I was wondering if ther is a way to set it to auto login through the recovery mode shell?
because it loads up everything and i here the login screen drum i just cant type in my login because i cant see it but if i get it to login automatically then it should skip the login screen and go straight to the desktop and then i can fix it later.
this is just an idea now.

The gdm login screen would use the same settings as your gnome sessions, so auto login wont work. If you dont believe me, test it, just hit enter a few seconds after hearing the jingle (that selects the user) then type your password and hit enter again. Should log you in, but I doubt you'll see anything.

Im guessing its a problem with your videocard driver and/or monitor. Something like an invalid resolution, Perhaps you can try this shiny example of linux userfriendlyness:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Kaneda187 on 2009-11-01
Well I got this joke or a release to boot up after reinstalling and then setting it to auto login so im guessing it has something to do with the login screen and my graphics card not playing nice.
speaking of my graphics card its useless. ther is no support at all my desktop resolution looks like a PC from 1995 its horrible!
oh well thanks for the help im off to start a new thread about my silly graphics card....yay:(

---

