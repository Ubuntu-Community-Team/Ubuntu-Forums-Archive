---
title: "can't find drivers for the ATI radeon x1200?"
date: 2010-10-13
forum: General Help
---

### Post by princeofnam on 2010-10-13
my laptop currently is : [http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html](http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html)

Unfortunately I'm having trouble finding proper driver support for the ATI radeon x1200 as described by another poster:

--
You should still be able to get full 3D support for your hardware by downloading & installing the drivers manually.

This is where it gets complicated, unfortunately. 

ATI dropped support for some "older" 3D devices some time back (actually not all that old in many cases - it made a lot of ATI card owners very upset). So I'm not sure which drivers you'd need to download & install to get your 3D hardware working.

The Radeon x1200 device in your notebook is, confusingly, not the same as a desktop Radeon x1200 card. Which is kind of nuts.

I don't own any ATI products any longer, so this is really outside my experience. I hope someone who does know can help.
--

has anyone had better luck?

---

### Post by coldraven on 2010-10-13
No, give up now!
I don't think there is any way because the ATI drivers for your chip don't work at all on the latest versions of Xorg.
However they will work if you run 8.04.
Using the open source (ubuntu) drivers the 3D performance did get better, testing with Extreme Tux Racer running 9.10 it was 4fps!!!
But with 10.04 I get 14fps, yey! This is fast enough for 3D graphics like Google earth or Sketchup
Mine is a Compaq 6715b, ATI X1250.

---

### Post by princeofnam on 2010-10-13
wow. perhaps this is a clue to return to windows

---

### Post by coldraven on 2010-10-13
Maybe you should read this:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by princeofnam on 2010-10-13
i have nothing against ubuntu. i still run it on my main desktop and laptop. i'll just have to revert to windows most likely for this laptop on account of ubuntu being unable to take full advantage of its graphics card

---

### Post by Mark Phelps on 2010-10-13
Just for your information ... MS Windows does NOT have a current driver for your card ... either.  

If you run Win7, you have to install the AMD/ATI Vista drivers in compatibility mode because there is no Win7 driver for it.

However, you will get the usual MS Windows stuff like "Aero" with the Vista drivers.

---

### Post by coldraven on 2010-10-14
Like I said before, just install Ubuntu 8.04.
It will run the latest (The last one they built for your chip) ATI proprietary driver at it's full capacity.
OK, it's a two year old OS but I'll bet that in a year or so you will be replacing your laptop anyway.
How old is XP now?

I don't know for sure but other distros that do not use the latest Xorg would work fine as well, Debian maybe.
On the ATI site under "Legacy" it tells you what Xorg version is supported. AFAIR it's version 7something.

I too was disappointed when I bought this laptop and found out that ATI were not helping the Linux community very well with support for my X1250 chipset. However I don't play games and as I've said the 3D rendering is fast enough for 3D design software.
Also my laptop was cheap as it was a "downgrade" from Vista Business to XPpro. It's certainly powerful having 2GHz dual core and 4GB ram. I'm just about to scrub the hard drive and install 10.10 64bit. I really have started to detest the Mega corps like Apple and MS. I will never buy any device that is locked in to their mad plans for world domination! :P

---

### Post by Pithikos on 2010-10-14
Had same issues many times before when I was an ATI user. Just keep in mind next time to buy Nvidia 8)

If you think of keeping your driver you can just downgrade your Ubuntu version. Even if you think of switching to Windows it's not for sure that it's gonna work any better. Maybe would work if you installed XP or some older version of it. But in the big run the best solution is to get a new Nvidia card. You can get one really cheap and it still will work perfectly on Linux just like it did in Windows. I talk from experience.

edit: didn't notice it was a laptop. so not sure if u can replace the video card

---

### Post by PoopLoops on 2010-10-16
I'm in the same boat ever since my main rig died and I have to use my backup laptop. I can't run simple games like Minecraft. I'm stuck with flash games that run slooooow.

Next system will definitely have an Nvidia card. Until ATI gives better support on Linux, I have no real choice. Linux is just easier to use for me because it has less overhead and I can set it up the way I want.

But yeah, the main message here is, as coldraven put it, "No, give up now!" I've been at this for two weeks now and I have not been able to find any solution.

---

