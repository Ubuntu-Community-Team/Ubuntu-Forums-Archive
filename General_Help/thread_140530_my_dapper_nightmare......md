---
title: "my dapper nightmare....."
date: 2006-03-06
forum: General Help
---

### Post by easyease on 2006-03-06
hi everyone. just thought id warn you to be very careful if you are thinking its time to upgrade to dapper. i had that thought last night and set about changing my repository list and upgrading.
 i really regret it now as something screwed up along the way and my eyes were bleary and attention span low. its took me all day today to find my hd and do a nice clean install of breezy again.
 I have been using ubuntu since the hoary release and i think i must have been feeling a little cocky that i could handle being in the dapper league.
 honestly dont upgrade yet unless you are happy to take a gamble, and if you do make sure you are wide awake and have a notepad handy.
 guess ill just have to try and be patient for the finished product. funny thing is i still love ubuntu more than scabby old windows.

---

### Post by Lord Illidan on 2006-03-06
What screwed up exactly? I think you should have downloaded a Dapper CD and dual booted with it. I am using Dapper fulltime at home now. No significant issues other than the Shift + Backspace issue with XGL but fixed that too.
I just downloaded a flight 4 cd.

---

### Post by easyease on 2006-03-06
not sure what went wrong but i think it could have been because i didnt remove automatix before i started, or it could have been a repository problem. yep im thinking a nice clean dapper install from disc is gonna be my method of choice in the near future. think im not going to bother using automatix this time round in breezy. it made me a bit nervous when it changed my sources list.

---

### Post by easyease on 2006-03-06
i followed this link by the way. i should have noticed the "us" repositories. lol. i guess the only thing i should be doing on my pc at 2am is looking at pr0n, not trying to be big and clever. :-D

[http://www.ubuntuforums.org/showthread.php?t=139633&highlight=dapper+upgrade](http://www.ubuntuforums.org/showthread.php?t=139633&highlight=dapper+upgrade)

---

### Post by evilgold on 2006-03-06
[QUOTE=Lord Illidan]What screwed up exactly? I think you should have downloaded a Dapper CD and dual booted with it. I am using Dapper fulltime at home now. No significant issues other than the Shift + Backspace issue with XGL but fixed that too.
I just downloaded a flight 4 cd.[/QUOTE]

How did you fix the Shift + Backspace issue, I had to disable xgl on my girlfrinds box because of it.

And to the thread starter:  I had problems upgrading myself, but the probelm wasnt dapper, it was the upgrade. I tried to do a dist-upgrade (change repos and use apt-get) i learned that hardway that this is not a good idea, for one it prompted me so many times it took literally days to finish (between work and sleep) and when it did complete the nearly 3,000 packages, I had many problems, mostly with gnome. 

However i then reinstalled from A flight 4 CD, and all was well again, and has been since.

---

### Post by easyease on 2006-03-06
yeah my problem occured in the upgrade to, mate. not sure what went wrong but it quit upgrading without finishing then i "lost" my hard drive in the process. now im tempted to download the disc and see what happens.

---

### Post by Lord Illidan on 2006-03-06
[quote=evilgold]How did you fix the Shift + Backspace issue, I had to disable xgl on my girlfrinds box because of it.

And to the thread starter:  I had problems upgrading myself, but the probelm wasnt dapper, it was the upgrade. I tried to do a dist-upgrade (change repos and use apt-get) i learned that hardway that this is not a good idea, for one it prompted me so many times it took literally days to finish (between work and sleep) and when it did complete the nearly 3,000 packages, I had many problems, mostly with gnome. 

However i then reinstalled from A flight 4 CD, and all was well again, and has been since.[/quote] 
Did you follow poofyhairguy's guide?
If so, then edit the file in /usr/bin/thefuture with ```
sudo vi /usr/bin/thefuture
``` and bring it like this:

```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.uk

``` NOTE : Replace the last part of xmodmap with your keyboard's country code. If you live in the us for example, make it xmodmap.us

If you want to know the different xmodmap styles, then enter ```
/usr/share/xmodmap/xmodmap
``` and press TAB. It should give you a list.

---

### Post by flyingbrass on 2006-03-06
I also dist-upgraded to Dapper last night.  There were dependency problems with some xfce4 packages.  apt-get -f install got things moving again.  Then I continued the dist-upgrade.

First impression: It's considerably faster - much better than Breezy.

Crossover stopped working (a reinstall might do the trick).  I can't get Bestcrypt to compile.  The fglrx driver is a step backward.  TV out is in black and white, too big for the screen, off-center, and both fglrx-control and aticonfig have so far been useless for adjusting it.  3d works.  This is with a Radeon 9600.

My Windows partitions weren't automatically shown on the desktop as they were in Breezy.  I changed a setting in gconf (show external drives, I think).  Now they appear, but aren't named identical to their mount points.  Strange.

Speaking of gconf-editor, it is no longer in the applications -> system tools menu.

I don't like the new logout menu, which appears to have been designed to appeal to children.

Being in an experimental mood, I installed KDE.  I'm not a huge fan of KDE anyway, but yuck.  With default settings it looked amateurish compared to Knoppix.

I am impressed with the speed improvement because it was the most frustrating aspect of Breezy.  I'll do a clean install when Dapper is final.

---

### Post by luopio on 2006-03-10
flyingbrass: still black and white with the tv-out? I'm having the same problem and it's pissing me off. TV-Out used to work and otherwise Dapper is so sweet...

---

### Post by powder on 2006-03-10
Isn't it a bad idea to do a dist-upgrade with backports installed?

---

### Post by lakelovers on 2006-03-10
When is Dapper scheduled for final release? I'm temped to dowload the CD, now. And  does anybody know whether Dapper makes print sharing any easter than on Breezy? I'm having a nightmare tying to get print sharing setup on Breezy.

---

### Post by hw-tph on 2006-03-10
Dapper is the *unstable* release. Do you want an *unstable* desktop? No? Then don't use it. It is very simple.

You can dual boot the stable and unstable distributions and contribute to the testing of Dapper if you want to, but posts like "Dapper is bleh" doesn't help much. It is doing great considering what it is.

lakelovers - how much do you know about printers and Linux? The [Gentoo printing guide](http://www.gentoo.org/doc/en/printing-howto.xml) is targeted at Gentoo users but very helpful for anyone using Linux.


Håkan

---

