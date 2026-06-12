---
title: "Desktop effects problem - probably stupidly simple but i'm stumped"
date: 2009-09-16
forum: General Help
---

### Post by user256 on 2009-09-16
I hate posting for help here, because it's usually been answered but this has been an ongoing problem for a while now, and occasional check backs reveal nothing new. 

user256@01:/$ compiz --replace
Checking for Xgl: not present.
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/kwin

I tried a Checker found here [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   KDE4
 Graphics chip:         ATI Technologies Inc RV730XT [Radeon HD 4670]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

I've learned a lot about ubuntu in the last few years but this one has me stumped. Is there a support issue with my graphics card, compiz used to work under ubuntu 8.04. I use the proprietary drivers now, although the issue existed under the open source ones too!

Am i missing something obvious?

Sorry in advance!

---

### Post by ajgreeny on 2009-09-16
It is so long since I used kde or kubuntu that I'm not certain about this, but I thought kde4 had its own desktop effects, rather than using compiz.

My apologies if I have this completely wrong.

---

### Post by user256 on 2009-09-17
well kwin seems to have some basic effects - but almost none worked with the open source drivers, no window effects no cube, pretty much nothing. and with proprietary drivers installed it says:

Compositing is not supported on your system. Required x extensions (xcomposite and xdamage) are not available.

-------------ok scratch that took me two seconds to spot the deliberate mistake but it's still not a bed of roses. 

I enabled composite in my /etc/x11/xorg.conf and now seem to have basic desktop effects. That said my splash screen flickers like an old tv, and my desktop can take upto a minute to render, even more irritating, every time i try to change anything, yeah anything! my windows start disappearing one by one, reappear and then disapear one by one all over again, this seems to go on endlessly, or when it does stop i'm left staring at the default wallpaper and nothing else. i have no control over it and have to log in via a shell to shutdown and try again.

any ideas?

---

### Post by user256 on 2009-09-18
Ok just thought i'd advise and close this thread. i finally grew a pair, got the drivers from ati and now have all sorts of shiny desktop bling with pretty much no problems. x rerenders everytime i add orr remove an effect but as thats pretty fast it's no issue. Found these instructions

# sh ./ati-driver-installer-9-9-x86.x86_64.run --listpkg
# sh ./ati-driver-installer-9-9-x86.x86_64.run --buildpkg Ubuntu/9.04
# sudo dpkg -i *.deb
# sudo /usr/bin/aticonfig --initial
# sudo reboot
:popcorn:

---

