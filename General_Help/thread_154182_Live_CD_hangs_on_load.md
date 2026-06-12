---
title: "Live CD hangs on load"
date: 2006-04-02
forum: General Help
---

### Post by starchildmom on 2006-04-02
I have Ubuntu with the Edubuntu desktop installed on two computers (homeschool "computer lab" and my 4yo's computer). I love it and want to try it out on my laptop.

I have downloaded and buned the Live CD twice now (in case the first was a bad download or burn). It hangs immediatly after pressing "enter" to boot. "Loading" appears on the screen, then nothing. I tried noapic nolapic (sp? I spelled it right when I tried) and vga=771. Still did not work.

I have an HP ze4900 laptop . The video is Intel 82852/82855 .

I als tried a live gnoppix cd. It also hangs at the start.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=starchildmom]I have Ubuntu with the Edubuntu desktop installed on two computers (homeschool "computer lab" and my 4yo's computer). I love it and want to try it out on my laptop.

I have downloaded and buned the Live CD twice now (in case the first was a bad download or burn). It hangs immediatly after pressing "enter" to boot. "Loading" appears on the screen, then nothing. I tried noapic nolapic (sp? I spelled it right when I tried) and vga=771. Still did not work.

I have an HP ze4900 laptop . The video is Intel 82852/82855 .

I als tried a live gnoppix cd. It also hangs at the start.[/QUOTE]
What speed did you burn it at ? Try a slow speed like 2 or 4x.

---

### Post by starchildmom on 2006-04-02
[QUOTE=MasterChief1234]What speed did you burn it at ? Try a slow speed like 2 or 4x.[/QUOTE]


I burned the first at 10 then slowed it to 8 for the second. I am downloading a fresh copy right now, just in case I got two bad downloads in a row. I will try burning it at 4 and see how that works.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=starchildmom]I burned the first at 10 then slowed it to 8 for the second. I am downloading a fresh copy right now, just in case I got two bad downloads in a row. I will try burning it at 4 and see how that works.[/QUOTE]
It might have messed it up when you changed from 10 to 8. Just use 4 and you won't have any problems :)

---

### Post by starchildmom on 2006-04-02
[QUOTE=MasterChief1234]It might have messed it up when you changed from 10 to 8. Just use 4 and you won't have any problems :)[/QUOTE]

I did not change the speed while I was burning:)   

Thanks for the help! Burning at 4x did the trick. Loaded up fine. Everything is working except for my wireless card. On my way to research the problem now.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=starchildmom]I did not change the speed while I was burning:)   

Thanks for the help! Burning at 4x did the trick. Loaded up fine. Everything is working except for my wireless card. On my way to research the problem now.[/QUOTE]
I am almost 100 % certian that your wireless card will work. All you need are the windows drivers for your card and then you just follow the wiki tutorial.

---

### Post by starchildmom on 2006-04-03
[QUOTE=MasterChief1234]I am almost 100 % certian that your wireless card will work. All you need are the windows drivers for your card and then you just follow the wiki tutorial.[/QUOTE]

Me too. I found the tutorial for my card (BCM4306). Now that the kids are in bed I am going to borrow one of their cables so I can hardwire into the network and try it out.

Thanks for your help!

---

### Post by Zyphrexi on 2006-04-04
I'm having problems here as well. I know my system is fine, since i'm running dapper right now, but i'm trying to burn a kubuntu live cd for a client, even at 4x, it hangs. This isn't the first time either, i've tried and wasted at least 10 cd's. I'm running out of cdrs...


EDIT:: (ubuntu/kubuntu breezy livecd)

---

### Post by ryanmbruce on 2006-04-04
I too am having trouble booting with any kind of live/install cd.  I tried the following cds:

Dapper Install
Breezy Install
Breezy Live
Hoary Install
Hoary Live
Gentoo Live
Knoppix Live

None of these will get past a certain point in the kernel loading process.  Usually the system hangs somewhere around when the CPU is stepping is detected, the 'hlt' procedure is tested, or the system checks if the image is initrd.  It then just stops outputting messages and will not continue.

The kernel will load just dandily if I use any version of a Slackware install cd.  I have also tried the 'failsafe' option in knoppix which turns just about everything off, but no go.

I'm on an Iwill MPX2 with only one Athlon XP 1600+.  Let me know if I've left anything out.

---

### Post by Zyphrexi on 2006-04-04
wow this seems to be a recurring problem, It'd be nice if there was a decent solution. I always wonder if it's the iso, or the burning speed, or the planets aren't aligned? :confused: ](*,)

---

### Post by ryanmbruce on 2006-04-05
While it may very well be that the planets are out of alignment, I am sure that this problem is not caused by anything to do with the burning of the cd or the corruption of the iso.  Given that the problem spans several different distributions, kernels, and cds made by a few different burners, I would be more inclined to believe that this is a hardware compatibility issue (at least in my case).

I would like to know what the difference is between all these other distributions' cds and the Slackware cd that loads a kernel image where all the others dive face first into the gravel.  Is there simply some boot option burried somewhere that makes the kernel load?  Maybe 'boot: make-everything-work'?  Or am I going to have to learn how to make my own Livecd images that are more suited for my hardware?

---

### Post by ryanmbruce on 2006-04-14
Is there no one else having this problem?  Has anyone found any bug reports for similar problems?  Can any developers offer an opinion?  Anything?



I've noticed that the few posts I have made in the forums tend to get overlooked.  Is there some trick to getting replies that I haven't been informed of?  I'm sure it helps to make reference to XGL or compiz, maybe both.  But I'd probably get even better results if I say something like "Ubuntu sucks because Windows is better."  That apparently draws the largest crowd...

---

### Post by ryanmbruce on 2006-04-20
I have filed support request #739 here:
[https://launchpad.net/distros/ubuntu/+ticket/739](https://launchpad.net/distros/ubuntu/+ticket/739)

and I filed bug #40093 here:
[https://launchpad.net/distros/ubuntu/+bug/40093/+index](https://launchpad.net/distros/ubuntu/+bug/40093/+index)

The 'nolapic' option seems to get me into the installer.  When the install menu appears select the appropriate method, hit F6, delete the 'quiet' option if it appears.  After the '--' type 'nolapic' and hit enter.

I'll update more when or if the bug is confirmed.

---

