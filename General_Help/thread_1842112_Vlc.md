---
title: "Vlc"
date: 2011-09-10
forum: General Help
---

### Post by bananagins on 2011-09-10
hi. i'm running 10.10 maverick and i'm trying to install the latest version of vlc. should i go with this guide:
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

or 

this ppa:
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

or
another ppa?

can someone give me like pros and cons of each option? much appreciated. thanks.

EDIT: i also used fakeoutdoorsman's guide to install ffmpeg and andrew.46's guide to install mplayer if that's relevant.

---

### Post by rolandrock on 2011-09-10
Assuming both methods retrieve the same daily build:

PPA method allows you to install without having to compile manually and will provide automatic updates.

The Ubuntu guide is a more sophisticated approach that compiles manually from source code.  This means you can modify the code and test your changes.  It also gives you control over what modules are installed and what capabilities the resulting vlc will have.  If you want updates, you will have to manage them manually.

Summary:

If you just want the latest features, use PPA.  If you are a developer who likes to play with source code or you have very specific requirements, use manual compile method.

I may be corrected by a cleverer person but that is how I understand it.

Hope that helps.

---

### Post by mc4man on 2011-09-10
The videolan ppa has been having major issues getting successful packages built for several months.
So if you add it to your 10.10 install you may either install a non-working vlc or one that's a bit dated
(doesn't hurt to try - if it doesn't work out remove the ppa and packages

Building your own should work out fine - Andrew's guide is probably based on natty but there's no reason you  can't basically use it for 10.10
You may need to make some adjustments to the build deps, nothing that can't be worked out and fixed... *if some 10.10 lib's are outdated that can be worked out also

---

### Post by bananagins on 2011-09-10
hey thanks for the reply. but what i was looking for were pros and cons specifically about each approach, not generalizations about compiling from source and installing from PPA. in other words, people who have used either the ppa i listed or another one, and any opinions they may have concerning their specific version. or people who have used the guide and can tell me specifically about that install.

i'm a little wary of ppas as i heard they can trash other packages you may hve installed and i don't want to mess up my ffmpeg and mplayer install that took me a while to get right. (thanks to fakeoutdoorsman and andrew.46 for their excellent guides)

but thanks for taking the time to reply.

---

### Post by mc4man on 2011-09-10
There no generalization about the ppa - it can't build packages very reliably atm (or for some time now
Currently I have a videolan master ppa build installed on 11.10 - was asked to test some things, it works fine. (build of aug. 27

Otherwise building one's own version is generally better, though with vlc-1.2+ there is always a chance of some minor breakage,though many times not noticeable

As far as any other ppa offering a vlc-1.2+ - haven't tried any but would certainly be wary of any ppa that replaces your shared ffmpeg libs

---

### Post by bananagins on 2011-09-10
> **mc4man said:**
> There no generalization about the ppa - it can't build packages very reliably atm (or for some time now
Currently I have a videolan master ppa build installed on 11.10 - was asked to test some things, it works fine. (build of aug. 27

Otherwise building one's own version is generally better, though with vlc-1.2+ there is always a chance of some minor breakage,though many times not noticeable

As far as any other ppa offering a vlc-1.2+ - haven't tried any but would certainly be wary of any ppa that replaces your shared ffmpeg libs

mc4man: my apologies. my reply was directed at rolandrock. you happened to reply while i was writing my reply! :p

... but thanks for the info about the videolan ppa. i will give andrew.46's guide a go. i was leaning towards it anyway seeing as his mplayer guide worked very well.

---

### Post by mc4man on 2011-09-10
> **bananagins said:**
> mc4man: my apologies. my reply was directed at rolandrock. you happened to reply while i was writing my reply! :p

... but thanks for the info about the videolan ppa. i will give andrew.46's guide a go. i was leaning towards it anyway seeing as his mplayer guide worked very well.
I was thinking that but not sure - the guide should be good - if any problems post here or there & they should be easily resolved

As far as the videolan ppa - I'd rate it 100% trustworthy, it's just that the packaging, (not the builds), are quite a pita atm with 1.2+ sources

---

