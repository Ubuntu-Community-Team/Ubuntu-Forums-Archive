---
title: "ATI is quite ridiculous... or sleeping..."
date: 2006-03-18
forum: General Help
---

### Post by guy2006 on 2006-03-18
ok I MUST admit: Ive learned more in the past 2 weeks about Linux than I would have imagined Id pick up during the course of a whole year otherwise. But... its for all the wrong reasons IMO

I am the proud (cringes) owner of an "ATI" 9600 series card and I've realized after 2 weeks time that Linux simply "isnt there yet" or perhaps ATI isnt (shrug)

Things which impress me about Linux:

- duh, open source (wayyyy cool)
- "package" system of delivery of software
- so many flavors (aka: distros)
- community seems to be extremely helpful and there really is this sense that
many are learning and growing together which is great
- great security
- options of different graphical environments (Gnome, KDE, etc)
- options like Kanotix for the person who wants max "plug & play" if you will and maybe Gentoo for someone who likes command line environments , compliling own kernels, etc etc
- seems so much "zippier" than Windows XP ever has for some reason

Things which dont impress me about Linux:

- ATI drivers
- ATI drivers
- typing sudo -s all the time
- did I mention ATI yet?

I am a person who is caught in the middle at this time between deciding to go back to Windows XP because hey it gets the job done -or- making the permanant switch over to Linux which IMO is absolutely the future and the way to go. The main obstacle is ATI. Ive now spent almost 2 full weeks going over every single guide to properly install ATI drivers. Ive done so on a dozen different distro's , 32 bit, 64 bit you name it, in the end it doesnt really matter I guess it seems Linux is Linux. Im currently using Ubuntu 6.04 Dapper

system consists of

Gigabyte K8NS Mobo (Nforce3-250)
AMD Athlon 64 2.8 gHz
ATI Radeon 9600 series
1GB decently good RAM
bunch of other crap that means nothing to system performance

Im the kind who wants to do the whole eat their cake too thing - Im an avid fan of gaming and my goal after reading the following article 

[http://wiki.winehq.org/BenchMark-0.9.5](http://wiki.winehq.org/BenchMark-0.9.5)

was to get framerates equal to or greater than Windows XP. Ive gone from popping in the Live-CD after the first time linux wouldnt load into a graphical interface to now being able to edit my xorg.conf file, load "vesa" driver and get into "startx" graphical gui if I need to, running apt-get's etc etc. HEY I know it aint much lol, but I still think there is some good in all these issues and they really do teach you indirectly alot about how some basic stuff works

I have gotten America's Army to run very well , somewhere around 85 fps which seems to be some built in cap from the game, anyway thats a native Linux build. Ive run tests like Futuremarks 2001SE on Windows XP and Linux Wine/Cedega/CVS/Winex/XWine/whatevertheydecidetocallitnextweek and on a test in Windows which I get 220 fps I get like 22 fps in Wine :(

One thing in all my screwing around with all this Ive learned is if you remove "fglrx" from xorg.conf via a package manager like Synaptic, etc everything seems to always goto hell even though you know you just installed the freaking ATI driver from their actual site flawlessly and that aticonfig utility seems to work.

Ive had alot of:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect

and Ive had my fair share of:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Pro

other than glxgears actually working, Ive found no REAL ATI driver which even works 1/2 *** yet for Linux or any "method" which really has all the answers. Its all a mish-mash of alot of misinformation, people's opinions but no cold hard facts that yes you can run ATI on Linux as good as Windows XP if you just do A,B and C. 

This is a call to ATI to release some real freaking drivers or at least provide detailed and exact instructions to people how they should go about getting Windows XP performance out of Linux and Wine. I know I seem to be asking for too much but after 2 weeks of Linux I am so utterly impressed with it overall that I hope I never go back to WinBlows XP but this ATI issue is quite unnerving and after reading forum after forum post after post, it looks like this has been the issue for tons of people for a long time :/

---

### Post by Caseyjp on 2006-04-11
Don't feel bad.  My main machine 'lost' its ATI card after the first couple of driver updates.  Its now a happy camper living with Nvidia and drivers that actually work.

---

