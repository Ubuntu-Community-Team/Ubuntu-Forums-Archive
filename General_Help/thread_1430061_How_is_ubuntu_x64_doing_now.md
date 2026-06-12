---
title: "How is ubuntu x64 doing now?"
date: 2010-03-14
forum: General Help
---

### Post by ndefontenay on 2010-03-14
Hello,

in order to take advantage of my dual core proc and 4GB ram, I have to install the x64 version.

The last time I did that, I had no flash support, I had to use a bunch of wrappers, and all in all, the whole experience was rather painful.

Is everything running smoothly now? is it possible to install 32bit version of applications not providing a 64bit version? (I'm thinking of skype for instance)

I would like some feedback on current issues with x64.

thanks

Nico

---

### Post by BrockStrongo on 2010-03-14
I've been running 64 bit since october. Most things are smoothed out now. Flash 64 is available in beta from adobe. The only bug I have encountered is non-responsive youtube/flash buttons. The workaround is to right click outside of the area you want to use. while holding right click, left click outside of the dialog box that popped up, while still holding right click , click on the button you want to use. It is actually a lot less tedious than it sounds. 
As for 32 bit compatibility there are a bunch of 32 bit libraries that can be downloaded to run pretty much what ever you need. Cant think of the names off hand though.
All in all the 64bit karmic is a big improvement over jaunty and keeps getting better
oh, I think skype now offers 64

---

### Post by ndefontenay on 2010-03-14
Thanks a lot for the feedback. 

I'm currently running Lucid alpha 3. I will definitely get the 64bit to take advantage of my resources.
edit: Just checked, there's indeed a 64bit version of skype.

Nico

---

### Post by dcstar on 2010-03-14
> **ndefontenay said:**
> Thanks a lot for the feedback. 

**I'm currently running Lucid alpha 3**. I will definitely get the 64bit to take advantage of my resources.


Then be aware that there is **no support** in the released software forums until the official release date. 10.04 is purely for testing purposes at the moment and all issues are restricted to the appropriate development forum.

---

### Post by ndefontenay on 2010-03-15
Totally aware of that. I am testing and debugging.

As for the x64, I won't use it until it's released.

---

### Post by DeMus on 2010-03-15
> **BrockStrongo said:**
> 
All in all the 64bit karmic is a big improvement over jaunty and keeps getting better


I disagree with you here. I run Jaunty 64-bits for almost a year and everything runs smooth, no problems here. In November of last year I tried Karmic but after a few minutes I knew I had to go back to Jaunty: things just didn't run on Karmic.
Jaunty is stable, is fast, and I sure hope the new one is based on Jaunty and not on Karmic.

---

### Post by _khAttAm_ on 2010-03-15
> **DeMus said:**
> I disagree with you here. I run Jaunty 64-bits for almost a year and everything runs smooth, no problems here. In November of last year I tried Karmic but after a few minutes I knew I had to go back to Jaunty: things just didn't run on Karmic.
Jaunty is stable, is fast, and I sure hope the new one is based on Jaunty and not on Karmic.

I think the same too. Karmic was the one with most problems for me (I have extensively used Ubuntu from Hardy and up).
The 64-bit flash plugin can be installed from Adobe site and it used to run well for me most of the times. When the controls didn't, holding down the Shift keys did it for me.
But due to the problems with some USB drives (in few Motherboards I guess), I am currently using 32 bit version of Ubuntu (Lucid Aplha). I read that the problem is with the 64-bit Kernel itself, so I haven't tried other distros (I was thinking of moving to Fedora).
The 32-bit version saves me from installing the ia32libs and other libraries required to run 32-bit applications, if I have to.
I am now planning to go with x64 version of Lucid when the final release is out to see if it has gotten any better.
About the 32-bit only programs, if you have the debs, you can install with dpkg -i --force-architecture package.deb. Also get "getlibs" application to resolve the library issues that may arise.

---

### Post by thecliff on 2010-03-15
I've been using Karma 64 bit for about 5 months with no issues whatsoever (once I configured everything specifically for 64 bit).  Flash works w/ no issues after I installed the correct version.

---

### Post by dcstar on 2010-03-15
> **DeMus said:**
> I disagree with you here. I run Jaunty 64-bits for almost a year and everything runs smooth, no problems here. In November of last year I tried Karmic but after a few minutes I knew I had to go back to Jaunty: things just didn't run on Karmic.
Jaunty is stable, is fast, and I sure hope the new one is based on Jaunty and not on Karmic.

I have been testing 10.04 for the last week or so, not 100% impressed as there are (as yet) no ATI propriety video drivers and there are still heaps of broken things and annoying changes (like the window control icons now on the LHS as default). My VMware Server 1.0.10 also is not yet compatible with the 2.3.62 kernel.

You also still lose a lot of the functionality that you currently have in 9.04.

I will be retaining 9.04 until 10.04 "settles" around June and then I will check it is usable....... it does boot up and shut down very quickly through......

---

### Post by 3rdalbum on 2010-04-23
> **dcstar said:**
> I have been testing 10.04 for the last week or so, not 100% impressed as there are (as yet) no ATI propriety video drivers

Look again, they're definitely there. ATI even provides pre-release versions of its drivers to Ubuntu to make sure that there's proprietary support well before Ubuntu's release date.

> and there are still heaps of broken things

With about a week to go until release, there certainly shouldn't be **anything** broken. You need to report any breakage **straight away** so it can be fixed for release or in Post-Release-Updates. Especially if it's a critical problem. Note also that this is not an appropriate place for submitting bug reports - you should use the "apport-bug" command or the Launchpad website.

Ideally, more people would actually test the betas - there were two betas this time in the hope that people would jump onboard and test early on. One of the big problems with Ubuntu 9.10 is that not enough people did the testing, and some showstopper bugs weren't picked up before release because they didn't appear for the people who tested!

---

