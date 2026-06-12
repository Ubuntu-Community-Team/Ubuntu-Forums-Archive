---
title: "Bus error in knotify and vlc"
date: 2011-11-21
forum: General Help
---

### Post by charles.figura on 2011-11-21
What do the multimedia players and knotify have in common?  Both cause bus errors on my machine as of about a week and a half ago.

Specifically, when I try to use vlc to display a movie (flv, mpg, whatever), I get a 14-second or so pause, then the console window comes back with 'bus error'.  The vlc window never opens up.

I tried reinstalling vlc, and synaptic (and apt-get) hung up at installing vlc-nox - returning a "bus error".

The dragon player has somewhat better luck - sometimes it seems to work, and sometimes it crashes as well.

When I get new mail (in kmail), knotify pops up to let me know about it - and my system is unresponsive for about the same amount of time, when a 'knotify has experienced a bus error' alert window pops up.

I did not make any changes to my machine that I'm aware of.  I've gone back and looked at the package update history on synaptic.

A friend suggested that there could be a hardware problem, so I tried swapping the harddrive from my Dell Latitude laptop into another Dell laptop - and experienced the same problem there.  It does not appear to be a hardware problem.

Does anyone have any ideas?  I suspect that if I reinstalled my system that whatever got borked would become fixed, but I don't want to go through that hassle if I don't have a clue what went south in the first place.

Thanks!

---

### Post by charles.figura on 2011-11-22
And an update - it's NOT knotify.  It's that my new mail notification included playing a wav file.

I've done testing now - wav files are the root cause of the knotify bus error.  So what I've got now:

vlc-nox (or package configuration of vlc-nox) causes a bus error.
playing wav files causes a bus error.

Strangeness!

---

