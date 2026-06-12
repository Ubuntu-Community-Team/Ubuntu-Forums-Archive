---
title: "Ubuntu Randomly Freezes"
date: 2009-10-04
forum: General Help
---

### Post by mechgt on 2009-10-04
I've got 2 Ubuntu (Jaunty) machines at my hosue, and 1 of them will randomly freeze (the other runs awesome).  This has been occurring for a couple years now over several releases (Feisty or Gutsy maybe.)  This box typically acts as a file server (running mdadm software Raid5 with 4 SATA drives), but I'll ssh in to do various things as well.  When it crashes, it completely stops responding to keyboard or mouse input (including caps lock on/off), and will not respond to pings or other network requests (ssh for example.)  It's totally locked, and my only recourse is to hold the power button and turn it off, and then back on.

It seems to crash most often when I'm 'doing something' on it (as opposed to in the middle of the night when nothing's happening) specifically if I'm moving large files, or if I'm actually sitting in front of it (using Firefox, nautilus, or really anything.)  If I've got something to get done on it, then it can crash several times an hour, or only once/week; and a few times we've even gone 2 or 3 weeks with no crash.  If I VNC remote desktop in I have better luck than physically sitting in front of it.  Luckily I very rarely sit in front of it.  This is an older HP NetServer.

How on earth do I troubleshoot and/or fix this?

---

### Post by stinger30au on 2009-10-05
this has happened to me

shut down pc and remove power to it

clean all fans in pc

remove cpu heatsink & remove heat sink compount & apply new compund

do not go stupid with the heatsink compound, tooo much is worse then none at all

check the hdd's for defects with dos boot cd

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

see you you go

---

### Post by mechgt on 2009-10-12
So I went out and bought some thermal compound and remounted each of the two processors following the directions on the arcticsilver.com website (including going through a few thermal cycles over several days.)  My CPU doesn't have temp sensors to monitor temperature, or I'd post what I was seeing there.

So far the results are inconclusive... It took me many tries (over several days) to get it all booted up and my mdadm raid drives back sync'd and online.  It would boot indicating some raid problem, so I'd have to re-build the array and it'd take forever and a day to sync.  Well somewhere in there (I'd let this run overnight) it'd freeze again, so I'd have to start over.  This went on for a few days (week maybe?) and now that I've finally gotten it back up, it's been running fine; although I haven't put too much load on it.

Is there any way (log files, diagnostic commands/messages) that might be able to help me pinpoint why this thing is giving me so much trouble?

---

