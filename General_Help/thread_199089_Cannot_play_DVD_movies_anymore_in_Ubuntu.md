---
title: "Cannot play DVD movies anymore in Ubuntu"
date: 2006-06-18
forum: General Help
---

### Post by joe343 on 2006-06-18
Hi,

Since last update, I unable to play my dvd movies.  I always get "movie cannot be read" error (in totem or mplayer).  Before last update, everything was fine. 

Any help appreciated !

---

### Post by deadgobby on 2006-06-18
When I up graded from breezy to dapper. I lost all my codecs and had to reload them all. Perhaps you may have to do the same. If you run Automatix should fix it back right up.
Gobby

---

### Post by Lunar_Lamp on 2006-06-18
Do you know what got updated?

Have you tried reinstalling the dvdcss codecs?

---

### Post by joe343 on 2006-06-18
Hi, I've tried reinstalling the codecs with Automatix... didn't work.  I also tried reinstalling the codecs manually with synaptic (libdvdcss2, libdvdnav4, libdvdplay0, libdvdread4) and it didn't work either. 

The update was pretty big. There was 62 updates (kernel, gnome, etc...)

I tried playing my movies with Totem and MPlayer.

No files even show up when I browse the dvds in nautilus (I don't see the .vob)...  but everything is ok with data dvds.

Thanks for your help

---

### Post by alphaomega on 2006-06-18
I am having trouble with the various players either crashing, not showing the DVD menu, bad and flaky picture, etc.  I've tried mplayer, totem and ogle and they are all acting badly. I am running a P4 with a Intel Integrated graphics card. I know I have all the proper codecs. I am going to reinstall them and see if there is a change for the better.

---

### Post by joe343 on 2006-06-18
Are you guys still able to play dvds ?  What can I try ?

---

### Post by syxbit on 2006-06-18
i had the same problem
know how i fixed it?
installed kaffeine by typing the following in the terminal
sudo aptitude install kaffeine
i know it's KDE (means it won't look like the rest of the OS), but it works.
that's all i can say, i'm not impressed with Dapper's multemedia offerings.
rythmnbox sucks (i use "listen") and totem/mplayer sucks too

---

### Post by joe343 on 2006-06-18
Solved !

After removing and reinstalling all the codecs, I tried rebooting and that did the trick.  Apparently loggin out and in again wasn't enough.  I shouldn't have lost my windoze habits of REBOOTING !

Thanks for your help guys.

---

