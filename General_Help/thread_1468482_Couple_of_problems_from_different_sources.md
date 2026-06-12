---
title: "Couple of problems from different sources"
date: 2010-05-01
forum: General Help
---

### Post by rbaleksandar on 2010-05-01
Hi, guys.

  Hopefully the thread is on the right place in this forum...So...This morning I installed (a clean installation) the new Ubuntu 10.04 LTS. There are problems but as the hours fly I'm able to find solutions for most of them. I'm still not able to explain to myself and/or fix a couple of things:

1) The clock deamon (by default placed on the right side of the upper panel):
- It constantly crashes (I get a "reload/don't reload"-prompt).
- Weather forecast (the one that goes with the time/date-daemon) disappeares too often. Even after the n-th crash of the clock and the n-th reloading from my side, the weather doesn't appear at all. I have a good connection at the moment so it's not that the forecast can't be loaded from the internet.
  I ran a live session just to check out if it's the installation or the programm itself. Well, same things happened so I guess it's buggy after all.

2) Mail/Chat notifier (don't know how it's called; the icon is a letter and by default it's placed next to the clock daemon on the upper panel) crashes too often.

3) Sound daemon crashe too often (sound regulation with the scroll-button on the fron of my laptop works without a problem though so it's not a big deal).

4) I have Qt since 2-3 previous versions of Ubuntu. Nothing like this has ever happened. Qt Creator takes lots of time (more than 5-6 minutes) to "warm up" and show up on the screen. The process **qtcreator.bin** takes almost all the current CPU-power even when idle. I read on the internet (including a bugreport on Launchpad describing the exact same problem but form last year) and seems that this problem should have been fixed by now (that is - lastest version of Qt Creator). But it's not.


Any suggestions are more than welcome. :KS

---

### Post by dino99 on 2010-05-01
you are right, still some issues around  :(

on my end when things goes wrong, usually i remove/purge the package then reinstall it. But some packages are usefull to clean the room, like :

gconf-cleaner: use it without moderation

bleachbit: powerfull so use with care each setting

there are some commands that help too:

sudo dpkg --configure -a
sudo dpkg-reconfigure package-name

---

### Post by rbaleksandar on 2010-05-01
Thanks for the advice. That's what I do usually too. But than if it's a bug and not just some kind of corrupted installation or so, even reinstalling won't fix it. :)

---

