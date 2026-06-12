---
title: "Help please, ubuntu11.04 dead in water!"
date: 2011-09-28
forum: General Help
---

### Post by mrjoeyman on 2011-09-28
I installed virtualbox 4.0 with the ubuntu software manager on my Toshiba Satellite laptop (in ubunto 11.04) system but never used it at all, as I figured I would wait until I got a disk for the os I wanted to run a few days later. In the meantime all was fine. Today I installed Gnome3 from information at ubuntu geek website. All went fine for this. When I restarted after install I get this now:

* Starting cups printing spooler/server           (ok)
[COLOR="Red"]*[/COLOR]No suitable module for running Kernel found (fail)
*Starting virtualbox kernel modules   (ok)
*Starting bluetooth                   (ok)
[COLOR="Orange"]*[/COLOR]PulseAudio configured for per-user sessions (ok)
saned disabled; edit /etc/default/saned
* enabling additional executable binary formats binFmt-support (ok)
*checking battery state..........
starting chron (ok)
stopping chron (ok)

As I said I never did squat with virtualbox. At this point I can't do anything. I don't know how to get to the recovery mode, (I tried the escape key, F1,  and the left shift key during early boot) and I have to do a cntrl-alt-o or a reisub, or a cntrl/alt/delete to restart. I looked up lots of things here and on google, but I seem to be the only case I can find that has the computer hang up and stop booting. I have put soooo much time into this I sure hope someone can help me get back into my OS again. Thank you.

---

### Post by mrjoeyman on 2011-09-29
Ok well after 24 hours and nearly 70 viewers I assume this problem can't easily be addressed. This thread can be removed or locked I guess, as I have now wiped and reinstalled. Thanks.

---

### Post by seawolf167 on 2011-09-30
The Gnome 3 install is[was] probably the culprit. Sorry to hear about the reinstall - in the future, may sure you have backups! I highly recommend [Clonezilla]("http://www.clonezilla.org")

Here is the [Gnome3 page]("https://launchpad.net/%7Egnome3-team/+archive/gnome3"), note the part that says:
*"This package contains packages from GNOME3 and their dependencies so  they can be used in Ubuntu 11.04 (Natty).  This PPA is EXPERIMENTAL and  MAY BREAK YOUR SYSTEM.  There is no downgrade process."*

---

### Post by mrjoeyman on 2011-10-08
I am now marking this thread solved. I turns out that the problem was not installing Gnome 3 after all but a script that I used to try to fix my touchpad on my laptop. Sometimes it takes a while to find these problems but I wanted anyone reading this to know the solution. Here is the link to the solution.

[http://ubuntuforums.org/showthread.php?t=1855664](http://ubuntuforums.org/showthread.php?t=1855664)

---

