---
title: "xubuntu scrambled screen after compositing turned on"
date: 2010-04-28
forum: General Help
---

### Post by sfarthing on 2010-04-28
I turned on screen compositing in xubuntu 9.1 and that scrambled the screen and now I can't read the screen. How do I undo that change? If I alt-ctr-F2 that goes to the command line. Then restartx goes back to the scrambled screen.  

Why does xubuntu recovery mode not offer any option to redo the video. 

Sorry, I assumed Xubuntu would ask for a confirmation like 'click yes if you can still see the screen' before allowing a change that can toast the system.

Please help.

Also I tried:

metacity --replace returns Window manager error: Unable to open X display

xfwm4 --replace returns (xfwm4:1458): Gtk-WARNING **: cannot open display

---

### Post by sfarthing on 2010-04-29
FIXMBR solves the problem.  Thanks to everyone for illustrating the effectiveness (or lack thereof) of community support.  Just one more reason linux has a sub 1% user base.  Xubuntu is readily rendered unusable with one click to the video settings and nobody here or on launchpad has a fix.  So my solution is to boot a Windows setup disc into the Recovery Console and run FIXMBR which instantly fixes every possible linux problem by converting my dual boot laptop to a Windows-only laptop.  Smooth sailing for me.  

As for the 10,000 users online on the forum when I posted initially, you have provided proof positive that when linux breaks, it is toast with no clear way to fix it.

And what about that Xubuntu wiki.  What a joke as far as user documentation.  For those who still strive for a reliable linux platform, once you get one running, encase it in lucite so you can look at it forever and write about it with the other 10,000 OS voyeurs here.  Because if you do not encase it in lucite, it could fall prey to the errant mouse click, the joke of a wiki, the wreck of the launchpad and become toast in a split second.

Also, please put a warning up that anyone interested in expanding the linux user base is not welcome here.  But it is a great club for the few with lots of time to fiddle and little common sense to fix obvious problems in your quirky OS.

---

