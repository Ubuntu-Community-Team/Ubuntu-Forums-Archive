---
title: "Got into a bit of a mess with Firefox"
date: 2010-11-22
forum: General Help
---

### Post by thered on 2010-11-22
A month or so ago I installed the beta version of FF4 - it was too buggy and gave me problems so I uninstalled and went back to FF3.x.x -or so I thought. For some reasons it set the PPA for daily updates and I ended up with Namoroka updating nearly every day, at present version 3.6.13pre.

I disabled the repositories and have been using it but I have noticed at times it 'freezes' i.e. high CPU use and also when typing into a textbox, like this the text is slow to appear.

I want to go back to my original FF3.x.x version that came with 10.10.

Can anyone point me to a tutorial or take time out to reply here with a procedure to do this?

Cheers R.

Edit: I have checked with nautilus and I seem to have various firefox folders all over the place - and a bunch more mozilla folders :o:

---

### Post by WorMzy on 2010-11-22
Go into software sources (System -> Administration -> Software Sources) and disable the Firefox PPA.

Then open a terminal and run
```
sudo apt-get update
sudo apt-get purge firefox
sudo apt-get install firefox=3.6.12+build1+nobinonly-0ubuntu0.10.10.1
```

---

### Post by thered on 2010-11-22
Excellent WorMzy! \\:D/

I'm back to FF 3.6.12 - Kept my profile too.

Hopefully this will resolve my problems

Thanks.

---

### Post by Frogs Hair on 2010-11-22
Administration > Synaptic Package Manager , search for Firefox when you find 3.6.13 right click and mark for complete removal and select apply. After removal if all software sources for the PPA , you should be able to install Firefox from the software center or terminal. Note: you must remove Namoroka first or you will get a message stating the newest version is installed.

---

