---
title: "Playing Real Media Files"
date: 2006-03-06
forum: General Help
---

### Post by mosestruong on 2006-03-06
I was trying to play a RealPlayer file from the ABC website, [http://www.abc.net.au/ra/tokpisin/ram_files/wantok.ram](http://www.abc.net.au/ra/tokpisin/ram_files/wantok.ram)
but after clicking on it, mplayer plugin starts, but stops immediately after getting the play list and attempting to play.

I looked at the ram file, and it has the following line:
pnm://media.abc.net.au/ra/png/wantok.rm

When I put this in firefox, it launched Totem, but Totem complained that there's
No URI handler implemented for "pnm://media.abc.net.au/ra/png/wantok.rm"

Just wondering if there's anyone who could help me play this? Thanks.

moses

---

### Post by WackToMack on 2006-03-06
Realplayer has a version for Linux.  I have it installed on my machine, but I'm not sure where I got it from... lol.  Do a little Googling and you'll probably find it.  Good luck! :D

EDIT:  I got Realplayer from using Automatix.

---

### Post by ajgreeny on 2006-03-06
Realplayer 10 is in multiverse repositories so you can use synaptic and search for it direct.  Make sure you also have the w32 codecs installed for it to work.

---

### Post by mosestruong on 2006-03-07
Which repository are you using? I could only see real player 8 from my repository...

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

---

### Post by ajgreeny on 2006-03-07
I think it is in this repository.  Give it a try and see.
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

---

