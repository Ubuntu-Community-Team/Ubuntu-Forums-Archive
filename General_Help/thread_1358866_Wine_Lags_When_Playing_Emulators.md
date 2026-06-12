---
title: "Wine Lags When Playing Emulators"
date: 2009-12-18
forum: General Help
---

### Post by joelandsonja on 2009-12-18
I have been having this problem since I switched over to Ubuntu, and only now decided to do something about it. 

The problem is that every time I want to play a game on one of my emulators through wine (Neo Geo, Nintendo 64, Nintendo, etc) the games lag terribly. What generally happens is that the sound and video appear to be skipping endlessly, and it seems that it is never able to catch up to the normal rate. I've tried changing the frameskip and sound settings, but I can't seem to find a solution that works. 

I should also mention that I have tried to use the Linux emulators, but unfortunately they all suck ... so I'm reduced to working with wine. 

It is also frustrating to see that many of the games I used to play on the windows emulators don't work in Ubuntu. This is almost enough to make me switch back to Windows, but I would rather get the problem fixed so I don't have to do that. 

Any suggestions would be helpful!

---

### Post by orlox on 2009-12-18
I've never had problems with the linux emulators, but as far as trying to see what can be done with wine, you can start by mentioning what ubuntu and wine versions you're using.

---

### Post by orlox on 2009-12-18
Also, the name of the emulators you're getting issues with would be usefull.

---

### Post by joelandsonja on 2009-12-19
I'm running Ubuntu 9.10

Attempting to get the following Emulators to work:

- Project 64
- Snes9x
- Jnes
- Gens
- NeorageX

Has anyone had this lagging experience when playing these emulators?

Could this be a result of an incompatible video card? I have an older version of an Nvidia card not originally supported by Linux, but thankfully Ubuntu developers created the drivers for the card so I'm not sure if they missed something or not. (I think the card I have is an Nvidia 9600 or 9400 with 512mb)

I'm also a newbie when it comes to Ubuntu, so just a heads up to keep the questions simple for my sake.

---

### Post by orlox on 2009-12-19
First, snes9x is available in ubuntu (look for it as snes9express). I remember using it a while ago and it worked fine (also, zsnes does the job, but I don't like it very much).

You still didn't provide your wine version. Did you installed it using the synaptic package manager? You should be able to chek the version by looking for the package "wine" in synaptic, and looking under the "installed version" column.

Did you try gfceu as a nes emulator? It's very simple and straightforward to use.

---

### Post by joes7 on 2009-12-19
Update Wine and Ubuntu.

---

### Post by joelandsonja on 2009-12-19
I am using Wine Version 1.0.1 

I have tried GFCE Ultra, but it doesn't want to work for me for some reason.

Not only that, but Linux doesn't have emulators for Sega Genesis and other systems I need to have. 

I would rather try to address the lagging issue I seem to be having rather than find Linux emulators.

I certainly appreciate the help!

---

### Post by orlox on 2009-12-19
1.0.1 is a very old version. You should install the latest version.

You should follow [this]("http://www.winehq.org/download/deb") instructions to use the official wine repository and have always the most recent version.

If you have doubts on that, just ask. Also, you check previous test from other users on several apps at [http://appdb.winehq.org/](http://appdb.winehq.org/) (keep in mind though, that some apps haven't been tested with recent versions of wine...)

---

### Post by orlox on 2009-12-19
Also, gens has a linux version (just because you can't find something on synaptic doesn't mean it's unexistant). You can get the installer [here]("http://sourceforge.net/projects/gens/files/Gens%20for%20Linux/Gens%202.15.5/gens_2.15.5_i386.deb/download")

---

### Post by joelandsonja on 2009-12-20
Hmm ... you have been most helpful sir! 

I will reinstall wine, and give the other emulators a try.

---

