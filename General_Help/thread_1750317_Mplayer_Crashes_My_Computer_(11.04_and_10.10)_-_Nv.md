---
title: "Mplayer Crashes My Computer (11.04 and 10.10) - Nvidia"
date: 2011-05-05
forum: General Help
---

### Post by curioususer on 2011-05-05
Reliably - both in 10.10, and after upgrading to 11.04, I get the following behavior:

After using mplayer (never right after a reboot), one of the following happens:
A. Mplayer get's invaded by random pixels (on transition to full screen), which after closing proceed to take over my screen.  Its like the ice cream sprinkles on poptart cat have launched an invasion and are winning.
B. Mplayer immediately freezes on the transition to full screen, locking up my computer to the point I have to restart.  I am unable to ctrl+alt+f1 into a terminal.

I have an nvidia card (XFX nVidia GeForce Express Video Card), and am using nvidia-current (driver version 270).

Note, I am running XFCE, but have seen this issue in Gnome 2 and in LXDE.  (I am staying away from unity and Gnome 3).

What could be causing this issue?

---

### Post by curioususer on 2011-05-07
Update: It seems 11.04 + Nividia = Sad Face.  I'm gonna look into alternative drivers, X options, Mint, and as a last resort, putting Windows on my box.

So far I've been pretty impressed with the level of responsiveness on this board.

---

### Post by curioususer on 2011-05-09
This seems to explain a lot ([slashdot]("http://news.slashdot.org/comments.pl?sid=2138848&cid=36074740")):
> [COLOR=#000000][FONT=Times New Roman][FONT=Arial]Yes, I am so mad at myself for upgrading to this latest release. Suddenly, wireless stopped working, and the new UI is horrific, and even after wasting hours of my time fixing all of this, there are these video artifacts that come and go, and the whole system just seems less stable than before. I suppose in a few months it'll be fine again, but this is getting old.[/FONT][/FONT][/COLOR]

It seems turning off opengl "flipping" has stopped (so far, fingers crossed) the crashing, but artifacts inevitably show up after a while.  Is this linux or just ubuntu?  In either case, its a crappy user experience.

---

