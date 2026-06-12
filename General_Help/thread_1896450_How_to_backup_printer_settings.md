---
title: "How to backup printer settings?"
date: 2011-12-17
forum: General Help
---

### Post by CactusSam on 2011-12-17
Hey all, I've been experimenting with Ubuntu for a few months now, and have to say, if it weren't for Netflix and a few utilities that I need for school, my dual boot machine would be a sole Ubuntu OS machine.  But alas, it just can't happen... yet.

So my question, after some tweaking I'm noticing a bit of system instability and I'm planning on just doing a clean new install of Ubuntu.  The only things that I can't live without are my Banshee database, which I believe I can just make a copy of the banshee.db file (right?) and move it back once my re-install happens, and more importantly, my printer.

The short reason as to WHY I want to backup my printer settings is because it took me FOREVER to get the damn thing installed, and I REALLY don't want to go through the hassle of setting that up again.  Like, literally took me around 10-15 hours of time, and I just can't go through that again.

The reason I'm not just doing a total system backup, is well, because I'm worried that some of the things that I've screwed up will just carry over with the backup and continue happening.

The primary instability that I've noticed is the system locking up when I "wake it up" after it's been in sleep mode (or whatever it's called when the screen goes dark) every once in a while.  At this point, the only thing I've been able to do is a hard reboot of my system, and I hate doing that if I don't ABSOLUTELY have to.  This is an inconvenience, but more importantly, I need to be able to continue proving that Linux > Mac to my gf, lol.

I've been able to copy my CUPS folder to an external HD, what else might I need to do to restore all the information for my printer later on?

---

### Post by jerrrys on 2011-12-18
look in:  /etc/cups/printers.conf

thats the only one I know of

---

