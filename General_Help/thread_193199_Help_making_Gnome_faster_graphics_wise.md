---
title: "Help making Gnome faster graphics wise"
date: 2006-06-09
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-09
hey all, hardware accelleration seems to be working but the gnome desktop system seems to be kinda slow graphically. like when I open say places from the top menu and I click system, the icons take a quarter second to load, and I know my system is not slow like that, windows had no such problems, games run just fine graphics wise, is there anything I can possibly do to fix this?

---

### Post by taurus on 2006-06-09
What is the spec of your machine especially how much RAM do you have and what is your swap size?

---

### Post by Patrick-Ruff on 2006-06-09
1.6ghz Pentium M 2.0MB L2 Cache
512MB DDR2 PC3200 RAM
ATI Mobility Radeon X300 64MB (Dedicated) PCI Express
swap file is around 1.3GB I think.

---

### Post by Patrick-Ruff on 2006-06-10
*bump* its been 6 hours now, any suggestions at all?

---

### Post by digs on 2006-06-10
gnome is known to be slower in display draws opposite kde/win/osx. you can try the proprietary ati/nvidia drivers if you already haven't done so. and there are also some xorg options in xorg.conf to possibly speed things up, say..         Option "AGPMode" "8" <-- whatever is your AGP speed
Option "AGPFastWrite" "true"
Option      "EnablePageFlip"    "true"

---

### Post by Particle on 2006-06-10
It won't get faster.  The same thing has always happened to me with any Gnome desktop through the years.  It's also annoying how some times the menus aren't long enough and you have to scroll them...it's random.

It doesn't get better with a faster system like this one:
AMD Athlon64 3000+ (2.6GHz)
1536MB PC3200 DDR
Hitachi DeskStar 120GB

Same thing.  It isn't extremely annoying to most people I think.  Good luck finding a solution.

---

### Post by Patrick-Ruff on 2006-06-10
hmm interesting, yeah I don't have such issues with KDE however, also I'm not on a AGP card, this laptop is smokin' for being a year old, its running on a PCI-E card. perhaps ATI is the issue? or this may be just gnome, if its gnome I would hope it could possibly be tweaked, I mean, Gnome is a fairly flexable desktop system so... yeah, if anyone has any idea please feel free to post

250 posts :D yay!

---

### Post by Patrick-Ruff on 2006-06-10
I'm trying those suggestions anyways, I'm already using the proprietary driver, games work basically at a desirable speed :). now its just about speeding up the desktop system.

add:digs, your suggestion was well intended, but it did not work. I think I might just switch to Kubuntu, any thoughts? is Kubuntu basically the same as Ubuntu?

---

### Post by BarfBag on 2006-06-10
[QUOTE=Patrick-Ruff]I think I might just switch to Kubuntu, any thoughts? is Kubuntu basically the same as Ubuntu?[/QUOTE]

I tried Kubuntu 6.06 and didn't like it.  Ubuntu feels more complete.  Everyone has a preference, though.  :)

Since you already have an Ubuntu system installed, why not just install the KDE desktop via apt-get?  I haven't tried this in Dapper yet, but I assume it still works.  Just fire up a terminal window, and type:

> sudo apt-get install kde-desktop

---

### Post by Patrick-Ruff on 2006-06-10
tried already, didn't really like it, Kubuntu is like more built for KDE, all the KDE apps and all that, everything is basically installed for Kubuntu, rather then running KDE on a Ubuntu desktop which is built for Gnome, and gnome is slow so... yeah... dispite gnomes DRASTIC improovements from breezy, does anyone know if they'res a human theme for KDE?

---

