---
title: "accidental dependency hell"
date: 2006-03-16
forum: General Help
---

### Post by cerebrix on 2006-03-16
well, decided to give linux a go again.  so far things went pretty well but somehow i seem to have created dependency hell for myself and i flat have no idea how to resolve it.  my nix knowledge is pretty low still.

anyway got kbuntu installed no problem, ran automatiks (although it seems to have created the problems possibly), got the latest nvidia drivers installed, got the composite running stable and everything was running great or so i thought until i tried to compile something.  

i got to the point where i wanted to do a little desktop customization so i ran over to kde-look.org and found a theme i wanted to install.  so i decided to start with the qtcurve style.  [http://www.kde-look.org/content/show.php?content=5065]("http://www.kde-look.org/content/show.php?content=5065")

well i downloaded it, decompressed it, and then when i try to sudo ./configure i get the following error.
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


any help you guys could give me would be great, in playing around with this i think both my paths and my repositories are hosed somehow.

thanks,

- me

---

### Post by Jucato on 2006-03-16
make sure that you have the "build-essentials" package (and its dependencies) installed. It's needed to compile from source code:

---

### Post by cerebrix on 2006-03-16
according to adept, it is installed =/


build-essential

status: installed Action: keep
Section: devel    Installed Size: 48K
Maintainer: Scott James Remnant
Candidate Version: 11.1
Installed Version: 11.1

---

### Post by cerebrix on 2006-03-16
apt-get update also outputs like nothing is wrong

[http://pastebin.com/606420](http://pastebin.com/606420)

---

### Post by cerebrix on 2006-03-16
the mighty l3m got me all setup in irc and installed =D

just had a few things i needed to install.  someone give that man an extra drink this st. patricks day =D

---

### Post by bender unit on 2006-03-26
You don't by chance remember what you had to install, do you? Because I'm stuck with the same stupid message that says it can't find the X includes. But I can't figure out which file it is actually missing, so I have no idea what packages might be missing. 
I already have all of the usual suspects like build-essential and I already have successfully compiled at least one app that uses X (was something for GNOME). Why do I keep getting that error message?

---

### Post by cerebrix on 2006-03-26
sadly i dont man..  and have since moved on and been running dapper.

hopefully someone here can chime in, it was like 3 or 4 things and it was like 5:30 am when i was helped so i couldnt even begin to tell you what was done.

id HIGHLY reccomend hitting the irc server, someone in there should totally be able to help you out.

---

### Post by jrib on 2006-03-26
install the xlibs-dev xlibs-static-dev x-window-system-dev packages

---

### Post by lupine_nickt on 2006-03-26
You'd need to install libx11-dev at a minimum. That sticks a fair number of packages in, and *might* solve the problem - or at least, get you a bit further along the dependencies route :) 

xF,

...Nick

---

### Post by bender unit on 2006-03-26
x11libs-dev did the trick, now I have more problems with finding the right Qt and KDE stuff to install. I think I got libx11-dev installed before - what the hell is the difference between these two? Just from the name I'd think it's (almost) the same package!

---

### Post by lupine_nickt on 2006-03-26
xlibs-dev is a transitional package - it depends on libx11-dev, among others.

KDE & Qt dev libraries to install:- kde-devel & kde-devel-extras

Sometimes, I'm tempted to just install *-dev , but then I remember I've only got a little hard drive... ;)

xF,

...Nick

---

### Post by bender unit on 2006-03-26
[QUOTE=lupine_nickt]xlibs-dev is a transitional package - it depends on libx11-dev, among others.

KDE & Qt dev libraries to install:- kde-devel & kde-devel-extras

Sometimes, I'm tempted to just install *-dev , but then I remember I've only got a little hard drive... ;)

xF,

...Nick[/QUOTE]
Well, me too (or at least I don't want to litter it with a bunch of dev packages I never use). When I saw what kde-devel and kde-devel-extras wanted to install, that was too much for me. That's not only libraries, but a whole bunch of tools, too. 
I just wanted the stuff that I need to compile QtCurve! Well, I installed kdelibs4-dev (why is that 4? It's still KDE 3.4!) and I could finally compile it. Well that's done now. Anyways, why is QtCurve not in the repositories?

---

