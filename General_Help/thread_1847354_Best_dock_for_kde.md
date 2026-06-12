---
title: "Best dock for kde"
date: 2011-09-20
forum: General Help
---

### Post by N00b-un-2 on 2011-09-20
I've been a gnome Ubuntu user since 7.10 and I was perfectly happy with it for several years.  And then with the upcoming release of 11.10 officially retiring gnome2 replacing it with gnome shell and unity (both of which I absolutely hate) I finally jumped ship to KDE.  That being said I have always set my desktop up like OSX (global menu bar on top and dock at the bottom).  Both Unity and Gnome Shell have removed the ability to customize the way I want to so it was simply time to move on.

I feel like I never gave KDE a fair shake since its disastrous initial release but I'm quite pleased to find that it's improved greatly since then back in the 8.04 days.  My biggest issue now is what dock will work best with KDE?

I've tried Cairo-dock but it is slow and buggy and like virtually every other dock, uses GTK+.
I've tried Docky which works well, but like Cairo which also uses GTK+ and tends to disregard my icon theme, favoring the default gnome icons which are hideous.  
I thought about installing Avant Window Navigator (my dock of choice on Gnome for the past several years) but when I went to 'sudo apt-get install avant-window-navigator' I saw that it basically has to install the whole gnome desktop as a dependency.  No thank you...
I tried Fancy Tasks but the program is broken (despite being available in the repos...) and crashes plasma every time I try to use it.
I'm currently using the Daisy Plasmoid which looks nice and is completely native to KDE, but it is not very configurable and is notably missing the intellihide feature and despite having a configuration option to support drag and drop launchers, it does not work as advertised.  In essence, it behaves like a simplified version of the OSX dock.
Are there any dock programs that are native to KDE the rival Docky or AWN in terms of functionality?

---

### Post by raja.genupula on 2011-09-20
Hey i hope you like them

[http://www.internetling.com/2008/03/24/linux-docks-5-mac-os-x-docks-for-ubuntu-and-other-linux-distros/](http://www.internetling.com/2008/03/24/linux-docks-5-mac-os-x-docks-for-ubuntu-and-other-linux-distros/)

---

### Post by N00b-un-2 on 2011-09-22
Thanks for the input, but I've come across that page already.  Ksmoothdock and Kiba dock are both LOOOOONG since defunct.  Cairo dock is glitchy at best with KDE and doesn't play nice with the KDE icons (prefers gnome icons since it --is-- a gtk app).  Engage dock is completely incompatible with KDE.  Sim Dock is terrible, but sticks around because it's the only one that truly doesn't require compositing.  In fact, composite effects tend to make sim dock glitchy.  And to reiterate, Avant Window Navigator relies on far too much of the Gnome desktop which I'm trying to get away from entirely.

In the end, the only dock specifically for KDE that actually works is Daisy Plasmoid but it's functionality lags far behind all other docks; no autohide, no drag and drop, no configurable effects, etc.

Avant is by far my favorite dock but it's a GTK app and I don't want any of those on my system.  Docky works the best (least worst?) out of all the docks I've tried on KDE so until Daisy improves, I'll be sticking with it.

---

### Post by Frogs Hair on 2011-09-22
This is the only dock for KDE that I found that you haven't written about .[http://kooldock.sourceforge.net/](http://kooldock.sourceforge.net/)

---

### Post by N00b-un-2 on 2011-09-24
eh.... I just got over it.  Installed AWN.  Then subsequently had to uninstall gnome (and Unity, thank you for that Canonical :@ ) Works great now though.  Having to install gconf-editor so that I could disable gnome and then uninstall it was fun...

---

### Post by sumski on 2011-09-24
Have you tried fancy tasks?

---

### Post by N00b-un-2 on 2011-09-24
fancy task seg faults on me.  I've installed it using apt and I've built from source with the same result

---

### Post by N00b-un-2 on 2011-11-13
Update!  Using IconTasks with a non expanded panel at the bottom.  Not quite as configurable as the Gnome docks are, but it is a effective KDE specific solution.  It would be nice it the maintainer would add multiple modes like 3d background.  The plasmoid works either standalone or as an applet within the panel.  I built a deb from source to make installation simple for others.  Took me days to figure out all the dependencies.

[http://kde-look.org/content/show.php/Icon+Tasks+deb+build?content=146787&PHPSESSID=71aec6bda4c578ca73c836d93021cd95](http://kde-look.org/content/show.php/Icon+Tasks+deb+build?content=146787&PHPSESSID=71aec6bda4c578ca73c836d93021cd95)

---

### Post by N00b-un-2 on 2011-11-13
Update!  Using IconTasks with a non expanded panel at the bottom.  Not quite as configurable as the Gnome docks are, but it is a effective KDE specific solution.  It would be nice it the maintainer would add multiple modes like 3d background.  The plasmoid works either standalone or as an applet within the panel.  I built a deb from source to make installation simple for others.  Took me days to figure out all the dependencies.

[http://kde-look.org/content/show.php/Icon+Tasks+deb+build?content=146787&PHPSESSID=71aec6bda4c578ca73c836d93021cd95]("http://kde-look.org/content/show.php/Icon+Tasks+deb+build?content=146787&PHPSESSID=71aec6bda4c578ca73c836d93021cd95")

---

### Post by UnsolvedCypher on 2011-11-13
Perhaps you want to try XFCE as a desktop environment? It is very similar to GNOME 2.X . Also, you can still use Gnome 2 even though it's "retired".

---

### Post by N00b-un-2 on 2011-12-05
using xubuntu 11.10 now.  KDE was fun to play with, and looks really good but I wasn't diggin' how much RAM it used up.  It got to the point where my system would be eating as much as 700+ MB of RAM just doing simple tasks.  Doing resource intensive stuff like transcoding video files was causing system lock ups.
XFCE likes to sit right around 125MB of RAM though.  Much faster on my less than impressive hardware.

---

### Post by LewisTM on 2011-12-05
If you're using Xubuntu now then you might want to give Cairo-Dock a second run. You're in GTK world now :)

I found CD to be more responsive under Xfce than under GNOME for some reason. The OpenGL mode can also be turned off for even faster performance with only a little less eye candy.

---

### Post by linuxrev on 2011-12-06
> **Frogs Hair said:**
> This is the only dock for KDE that I found that you haven't written about .[http://kooldock.sourceforge.net/](http://kooldock.sourceforge.net/)

I have used Kooldock some years ago, on an openSUSE system, quite liked it, but as far as I know it is no longer maintained.

---

### Post by Frogs Hair on 2011-12-06
> **linuxrev said:**
> I have used Kooldock some years ago, on an openSUSE system, quite liked it, but as far as I know it is no longer maintained.

You are correct , the packages are dated 2007 .

---

### Post by bluexrider on 2011-12-06
I just discovered adeskbar and it seems extremely light

---

### Post by ernestj on 2011-12-06
I currently use Xubuntu 11.10, I installed AWN and love it. My computer is still very fast, but is GNOME slowing it down? Should have I used another doc? Can I remove some of the GNOME fat?

Thanks,
Ernie

---

### Post by N00b-un-2 on 2011-12-08
I love AWN.  It and Docky are tied for my favorite Linux dock, but Docky tends to edge out AWN because A) I don't use GNOME anymore and don't like the fact that AWN installs GNOME as a dependency and B) Because Docky is lighter than AWN albeit somewhat less configurable.  Docky has a nice non-composite fallback mode.

As for kooldock and ksmoothdock, neither are maintained any longer and both are for KDE 3.5.  the Trinity Project does provide an up to date version of KDE 3.5 for those who refuse to adopt KDE4 but I would never use it since apps are developed for KDE3.5 anymore.

---

### Post by mc-rpg on 2012-12-13
The way I see it, the best case for Windows 7 is the recent wave of Linux desktop environments. It has been absolutely disastrous and have completely shattered the usual DE constituencies. For some reason, all this guys sat around a table and decided that what Linux DE needed was *less* flexibility, are you kidding me? Mark pretty said that this lack of flexibility on Unity was a feature, not a bug. If this is what I wanted I would've just bought a Mac years ago since it's been a long time FLOSS stopped being an ideological battle for me.

There's still hope though (or I like to believe there is). Cinnamon looks very promising, and gnome shell can grow on you, although it needs way more *configurability* something that doesn't seem to be very high on gnome-dev's priorities.

---

### Post by oldos2er on 2012-12-13
Old thread closed.

---

