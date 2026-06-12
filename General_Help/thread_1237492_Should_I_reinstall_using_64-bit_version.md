---
title: "Should I reinstall using 64-bit version?"
date: 2009-08-11
forum: General Help
---

### Post by rslee on 2009-08-11
Hi,

I just installed the 32-bit version of Ubuntu on a Core 2 Duo machine without realizing that I could have installed the 64-bit version.  Should I reinstall using the latter, or does it not matter that much?  Everything seems to be running fine.

Thanks

---

### Post by Bucky Ball on 2009-08-11
Go for the 64bit. It will make better use of your hardware and more besides.

Get to it! :)

---

### Post by furuno on 2009-08-11
Well it actually depends on how much amount of RAM that you have now (or you will add to later shortly) if you have lesser than 4 GB than it should be OK with 32-bit. If you have 4 GB or more, you have to install 64-bit OS to make use of all of your RAM.

32-bit OS are limited to address up to 4 GB of RAM, usually less than that due to many circumstances. So, actually, if you have 3 GB or more, then you should use 64-bit instead.

---

### Post by billdotson on 2009-08-11
I keep seeing posts from 2007 on here where people are complaining about basic java, firefox, flash, sound, and video not working correctly on 64 bit Ubuntu. Have all of these issues been adequately fixed since then? I have a PC running Vista 64 bit and the only issue I have had is ogg codecs not wanting to work through windows media player. In other words, firefox, thunderbird, quicken 2007, open office, avidemux, gimp, inkscape, adobe reader, and virtual box seem to be working fine. Blender (32 and 64 bit versions) seem to lock up when I try to do a video render (normal render works fine). Could be a driver issue (even though there aren't any newer drivers my the 9300GS I have), Vista, or and/or Vista hogging so many resources.

I have ubuntu desktop and regular 64 bit downloading now, I am not wasting my time am I?

---

### Post by ukblacknight on 2009-08-11
I've been running 64bit Ubuntu for several months now, I've never had a problem!  It's always worked the same as my 32bit installs, except I noticed that my 64bit install was more responsive.

I'd say go for it.  You'll find that pretty much any application has a 64bit build as well.  I've had 64bit Vista, and running Windows 7 64 and I'd say that there are *far* more 64bit apps out there for linux.

My advice would be to go 64 :)

Note: I'm even using 64bit Adobe Flash, runs fine.

---

### Post by SlugSlug on 2009-08-11
no problems with ubuntu 64 here either...

---

### Post by XCan on 2009-08-11
> **billdotson said:**
> I keep seeing posts from 2007 on here where people are complaining about basic java, firefox, flash, sound, and video not working correctly on 64 bit Ubuntu. Have all of these issues been adequately fixed since then? I have a PC running Vista 64 bit and the only issue I have had is ogg codecs not wanting to work through windows media player. In other words, firefox, thunderbird, quicken 2007, open office, avidemux, gimp, inkscape, adobe reader, and virtual box seem to be working fine. Blender (32 and 64 bit versions) seem to lock up when I try to do a video render (normal render works fine). Could be a driver issue (even though there aren't any newer drivers my the 9300GS I have), Vista, or and/or Vista hogging so many resources.

I have ubuntu desktop and regular 64 bit downloading now, I am not wasting my time am I?

I've been running 64 bit for almost two years now and can safely say that all the apps (besides quicken which I've never run) you mentioned have worked flawlessly on all my machines.

---

### Post by rslee on 2009-08-11
Thanks everyone, I did install the 64-bit version and all is well.  What an awesome OS.

---

### Post by Bucky Ball on 2009-08-12
> **billdotson said:**
> I keep seeing posts from 2007 on here where people are complaining about basic java, firefox, flash, sound, and video not working correctly on 64 bit Ubuntu. Have all of these issues been adequately fixed since then? I have a PC running Vista 64 bit and the only issue I have had is ogg codecs not wanting to work through windows media player. In other words, firefox, thunderbird, quicken 2007, open office, avidemux, gimp, inkscape, adobe reader, and virtual box seem to be working fine. Blender (32 and 64 bit versions) seem to lock up when I try to do a video render (normal render works fine). Could be a driver issue (even though there aren't any newer drivers my the 9300GS I have), Vista, or and/or Vista hogging so many resources.

I have ubuntu desktop and regular 64 bit downloading now, I am not wasting my time am I?

Two years is a long time in technology my friend. If you have a problem now it will be because you have done something wrong. Just make sure you add these:

ubuntu-restricted-extras

(find it in Synaptics).

Add Medibuntu repository to your sources list for codecs etc and that should just about do you. My laptop has been running for over a year with all of the things you mention working fine (Skype with vid if you like ...).

ps: you will have no problem loading ogg files in just about any player in Ubuntu. :)

---

### Post by Bucky Ball on 2009-08-12
> **rslee said:**
> Thanks everyone, I did install the 64-bit version and all is well.  What an awesome OS.

Great news! Enjoy and welcome ... :)

ps: Go to System->Administration->Synaptic Package Manager and do a search for:

ubuntu-restricted-extras

Install it for Java and other third-party codec things (unless you are going totally Open-Source that is). It might pay you to do a search for something like:

"jaunty post install"

... as there are a few things you will find handy and some pretty essential. You can go trial and error and learn to fix and tweak as a problem arises which is good for learning anyhow, or you can get it out of the way all at once at the beginning with a how-to. Beautiful thing is you can take your pick. :)

---

