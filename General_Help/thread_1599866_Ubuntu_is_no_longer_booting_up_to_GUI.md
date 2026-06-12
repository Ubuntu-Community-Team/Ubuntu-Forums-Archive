---
title: "Ubuntu is no longer booting up to GUI"
date: 2010-10-18
forum: General Help
---

### Post by godfromdfo on 2010-10-18
Hey guys, did some updates on the buntu-box but everytime I start it it now goes to some CMD-like screen that lets you go through F1-FX and comes up with diffrent tty thingies, before the update it used to go into the proper GUI, I have 10.10 installed, I think I updated my GPU driver and looked on here for some hints on what to do, I have tried:

cd /etc/x11
^
Above command did not work for some reason, think it couldn#t find it?

Sudo service gdm start
^
Said above process is already started or something

Please Hawlp teh mes? :D

---

### Post by VMC on 2010-10-18
From the command prompt, type 'startx' and see if that gets you to the Desktop.

Alternatively you could try 'Alt+F7' and see if that gets to Desktop.

---

### Post by godfromdfo on 2010-10-18
> **VMC said:**
> From the command prompt, type 'startx' and see if that gets you to the Desktop.

Alternatively you could try 'Alt+F7' and see if that gets to Desktop.

startx doesnt bring up the gui it just shows a block of text and ALT & F7 brings up another tty thing or asks for username or w/e it is..

:(

---

### Post by Refalm on 2010-10-18
What videocard do you have?

---

### Post by godfromdfo on 2010-10-18
think it's something like 4760 or something like that, eith way, it worked fully fine before I updated to some strange driver which had some numbers before it 0_o

---

### Post by barnestech on 2010-10-22
A recent group of updates did the same to me.
I did get to a GUI after an extended delay.
The offending package was GDM.
The offending version was "2.30.2.is.2.30.0-0ubuntu4" from the lucid-updates repo.
If this version is installed in this machine (and so far only this one-I am running several with lucid) It delays the boot process for over a minute and shows a CLI login before the GUI starts.

I forced the version down to the earlier version.

Synaptic>Package>force version>lock version

It worked for me on this machine in this case.

---

