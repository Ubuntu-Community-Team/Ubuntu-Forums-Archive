---
title: "Do Old ATI cards work in 9.10?"
date: 2009-11-18
forum: General Help
---

### Post by McTricks on 2009-11-18
I remember when 9.04 was released it didn't support the old ATI catalyst drivers, and ATI doesn't support the old cards in the new drivers. But will my card work in 9.10 now? I've got an ATI xPress 1150 Integrated card.

---

### Post by Giblet5 on 2009-11-18
It supports the older M4 mobile chip. No 3D acceleration of course, but it works without doing anything.

Burn a CD. Boot from it.

"To find if a release will work, try it."
-Napoleon Bonaparte's IT guy

---

### Post by realzippy on 2009-11-18
To use catalyst driver you have to go back to 8.10.
But,the free radeon works pretty well..

---

### Post by zeusz4u on 2009-11-20
@realzippy

It works preatty well, except 3D acceleration :-( I've tried to install these daily builds on it:[URL="https://bugs.launchpad.net/%7Exorg-edgers/+archive/ppa"]
https://bugs.launchpad.net/~xorg-edgers/+archive/ppa[/URL] , but I even got fewer FPS in 3D apps (eg. Celestia, GoogleEarth), in fact they don't seem to work as good as they should, you can't use such programs with these drivers... The screen flickers, menus disappear etc. I have a Dell Inspiron 1501 Laptop with video card ATI Radeon Xpress 1150.

I was a happy Ubuntu user until ATI changed their mind and decided to release no more drivers for Xpress series. That was a bad move. Even before, my video card didn't work 100% perfect, still had some issues while compiz was active, and suspend didn't work as well, but at least I was able to use 3D programs.

If someone comes up with a solution please let us know. I won't even install Karmic until some accceptable drivers will be released. In fact this problem made me to use Windows 7, which works OK, at least it has drivers, better than Ubuntu without drivers.

I found some posts about releasing XPress cards specifications to the public, so that developers could make linux drivers more effective, but it doesn't seem to be in progress the development of these drivers. I hope it will be solved in the near future. I just don't have $800-$1000 to buy a new laptop every 2 years.

---

### Post by realzippy on 2009-11-20
So,why not installing 8.10 LTS?
You could use the catalyst driver there.Full 3D.Much better than 9.04...

---

### Post by 3rdalbum on 2009-11-20
> **realzippy said:**
> So,why not installing 8.10 LTS?

That would be a good idea, if 8.10 LTS existed.

8.10 is End Of Life in six months.

My father's Xpress 200 works with Compiz (he's never complained about things not working, so I assume the support is good) on 9.04. If you have a PCI-E or AGP slot you could get a later card (Powercolor makes RadeonHD 4000-series ATI cards in AGP).

Maybe the obvious option is: Download 9.10 and try out the live CD. If Compiz and glxgears work at reasonable speed, then you have 3D and you can install 9.10.

---

### Post by realzippy on 2009-11-20
6 month of 3D.And then there is a new LTS....

---

### Post by zeusz4u on 2009-11-20
You can downgarde Xserver, and install in this way older Catalyst releases which no longer support the current X release, but it's a lot of work and manual editing of cfg-s, lock the packages so thay not update etc. and it's risky, you may end up with no X at all. It's not for beginners, and also not a long-term solution. That's why I didn't even try it.


I don't have problems with compiz on my laptop, but 3D applications don't run properly... few FPS even in Celestia/GoggleEarth, but films and videos play well, 3D desktop is working smoothly, I've even tried the cube desktop. The only problem is in 3D Fullscreen applications such as games, or other 3D programs. I couldn't get them work :-(. I think it's better to wait, and HOPE that developers release some new better drivers. It's quite weird that Canonical doesn't invest in such driver development. Mark Sh. is the main sponsor of KDE 4 (as I know), and he has the money to and the ability to negociate with ATI (I really think and believe that he is a smart guy).

---

