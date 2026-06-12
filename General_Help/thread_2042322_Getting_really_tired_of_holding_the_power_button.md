---
title: "Getting really tired of holding the power button"
date: 2012-08-14
forum: General Help
---

### Post by fixles on 2012-08-14
Hi,

I have 2 desktops and a laptop. A couple of weeks ago I decided to move from windows 7 to ubuntu 12.04 64Bit.

I've used linux for years so am familiar with the basics and aside from a few hiccups havent had any real problems except systems freezes on all 3 machines where I have no option but to hold the power button down and restart.

If some free software goes haywire fair enough but this just reminds me of Windows 98.

Is this common with ubuntu? If so rock solid windows 7 here I come. If not how can I find out what maybe causing the crashes?

I havent added any new hardware to any of the machines since ubuntu was installed and havent installed any software not available through the standard repositories. I was running Gnome Classic and now Gnome 3 and have had the freeze problem with both. There doesn't appear to be a pattern to when it freezes or which application I'm using. The hardware on all 3 is completely different but the software I've installed is pretty much identical, which makes me think its either Ubuntu itself or something I've installed running in the background.

Thanks.

Thanks.

---

### Post by FatFrog on 2012-08-14
I have no problems like you are seeing. Do these machines have anything in common between all of them (Manufacturer, GPU, CPU, etc...)?
If so, It could be hardware/driver related.

Have you seen anything in logs regarding this?

Also, are you able to switch between TTYs when this happens (CTRL+ALT+F1 etc..)? If so, you can just shutdown from there...

---

### Post by BBQdave on 2012-08-14
> **fixles said:**
> If not how can I find out what maybe causing the crashes?

I am curious if you used the same media for all installs? My first thought with info provided, is faulty install.

If you are able to obtain a new Ubuntu Live CD, test your machines in the live CD environment. If all runs well, then most likely it was a bad install.

Too, are your machines all 32-bit, 64-bit? Definitely smoother performance if you match install version to hardware version.

---

### Post by fixles on 2012-08-14
> **FatFrog said:**
> I have no problems like you are seeing. Do these machines have anything in common between all of them (Manufacturer, GPU, CPU, etc...)?
If so, It could be hardware/driver related.

Have you seen anything in logs regarding this?

Also, are you able to switch between TTYs when this happens (CTRL+ALT+F1 etc..)? If so, you can just shutdown from there...

The hardware is total different. One dual core amd one six core amd one Intel quad core, all have different gpu motherboards even keyboard screen and mouse is different. 

I checked syslog but it didnt show anything just the usual DHCP stuff etc.

Switching TTY is something I havent tried. I'll give that a try and see if I can get htop running. Thanks.

---

### Post by fixles on 2012-08-14
> **BBQdave said:**
> I am curious if you used the same media for all installs? My first thought with info provided, is faulty install.

If you are able to obtain a new Ubuntu Live CD, test your machines in the live CD environment. If all runs well, then most likely it was a bad install.

Too, are your machines all 32-bit, 64-bit? Definitely smoother performance if you match install version to hardware version.

I did use the same iso I downloaded for all installs. Would checking the md5 of the iso confirm this? All 64Bit running on 64Bit cpus.

---

### Post by dodo3773 on 2012-08-14
Do you get the same problem if you are running a non-compositing wm?

---

### Post by fixles on 2012-08-14
> **dodo3773 said:**
> Do you get the same problem if you are running a non-compositing wm?

As in gnome classic no effects that doesnt use compiz? I did run that for a while and I cant remember. Is it possible to run gnome 3 non-compositing?

---

### Post by dodo3773 on 2012-08-14
> **fixles said:**
> As in gnome classic no effects that doesnt use compiz? I did run that for a while and I cant remember. Is it possible to run gnome 3 non-compositing?

I don't think it is. Mutter only does compositing as far as I know. I mean like openbox, fluxbox, etc..etc...

---

### Post by fixles on 2012-08-14
> **dodo3773 said:**
> I don't think it is. Mutter only does compositing as far as I know. I mean like openbox, fluxbox, etc..etc...

I have looked at some of the other wm's like xfce but they they all looked pretty bad so I stuck with gnome.

---

### Post by dodo3773 on 2012-08-14
> **fixles said:**
> I have looked at some of the other wm's like xfce but they they all looked pretty bad so I stuck with gnome.

The window manager for xfce is a compositing one too. I did not mean completely switch. What I was trying to say is test one to see if that is related to your issue in some way. Eliminate the window manager as a possible source of your problem.

---

### Post by fixles on 2012-08-14
> **dodo3773 said:**
> The window manager for xfce is a compositing one too. I did not mean completely switch. What I was trying to say is test one to see if that is related to your issue in some way. Eliminate the window manager as a possible source of your problem.

It could be anything the ubuntu os and installed software is pretty similar.

Isnt there some log or a crash dump or some application I can run to trace the cause of these crashes?

---

### Post by dodo3773 on 2012-08-14
> **fixles said:**
> ..installed software is pretty similar.


No it's not. That seems like kind of a ridiculous thing to say actually. To answer your question though: Most log files are usually in somewhere like /var/log/. You can also type dmesg in a terminal and that will give you some information as well.

---

### Post by hakermania on 2012-08-14
I just want to clarify to the ones that are really having problems with Ubuntu, that there are situations (like mine) that not even the slightest (aside from software bugs, of course) problem exists with Ubuntu.

Just to let you know that the world who is using Ubuntu does it, because, apparently, they don't have major problems with it and they find it better than their previous systems!

---

### Post by fixles on 2012-08-14
> **hakermania said:**
> I just want to clarify to the ones that are really having problems with Ubuntu, that there are situations (like mine) that not even the slightest (aside from software bugs, of course) problem exists with Ubuntu.

Just to let you know that the world who is using Ubuntu does it, because, apparently, they don't have major problems with it and they find it better than their previous systems!

I could probably have gone back to windows 7 but I love gnome 3 too much.

Your signature about firefox is that the same for Chromium?

---

### Post by J V on 2012-08-14
I came here to ask about this problem. It started a few weeks ago for me and has recently become rediculous. (xubuntu, 64bit) The system crashes so utterly there are no logs and reisub doesn't even get a response.

---

### Post by Jay MC on 2012-08-14
I've used Ubuntu on three different laptops and have never had problems with freezing (apart from individual apps freezing, very occasionally, but then I can kill and continue).

"havent installed any software not available through the standard repositories"

Have you installed much stuff?  Anything that's common to all devices?  Does it freeze when you're doing anything in particular, or just randomly?

Also, I see you've been using Gnome - is it worth trying Unity?  I'm not trying to pimp it if you don't like it :) but it would be interesting to see if the problem goes away.  At least you'd then know it was a problem with the choice of desktop(s).

Basically, if you're in the mood to persevere, I would try changing any variables to see what does or doesn't cause the problem (like an exclusion diet for your computers).

On the other hand, I do think Windows 7 is a fine OS, and it might not be worth the bother if you've tried Ubuntu on three different PCs and are getting frustrated.  I don't know if I'd still be using Ubuntu if I'd had to troubleshoot it much!

---

### Post by nomorn on 2012-08-15
In my opinion, using video card's propietary driver can definately lead to a linux hard freeze/crash problem.
I have been using ubuntu for 4 years. Until recently, I have not a single hard freeze/lock up problem. I read through lots of posts, updated bios, tweaked every settings trying to find a fix and my hard freeze problem seems to be completely gone for a month now.
I believe my freeze problem is related to the nvidia's powermizer feature, surprisingly, turning off nvidia's powermizer not only fix my linux freeze problem, it also fix a hard freeze problem in one of the windows games on my windows machine. It's ok for a windows os to hard freeze tho. :D

---

### Post by fixles on 2012-08-17
I read that fedora doesn't include chromium in its main repositories because its so unstable so I switched to firefox to see if that solved the problem. Then I tried to watch a youtube video in firefox. Oh the latest flash-plugin crashes on ubuntu.

That was the Final straw I installed Fedora yesterday and have not had a single problem. All the machines suspend and shutdown properly and have hibernation which none of the ubuntu installs had and most importantly I haven't had a single system freeze.

Its also worth noting the software in the ubuntu forums is also very out of date compared to fedora. Gimp v2.6 and Eclipse IDE v3.7 in Ubuntu version 2.8 and 4.2 respectively in Fedora.

After 3 weeks of hassle with Ubuntu I've come to the conclusion that if you like Windows 98 use ubuntu if you like Windows 7 use Fedora.

So long Ubuntu and thanks for all the fish.

---

