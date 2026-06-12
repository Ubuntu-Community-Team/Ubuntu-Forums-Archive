---
title: "Sluggish Performance last couple of days"
date: 2010-04-22
forum: General Help
---

### Post by Zelandeth on 2010-04-22
Only seems to have been happening since the last set of updates were installed.

Generally the system seems to be running fine, applications loading quickly enough and such.  However, every now and then, the system just seems to be slowing to a crawl.

Couple of times today, Opera ended up greying out when I'd done nothing more complex than clicking on a thread on a discussion board.

One test I just decided to try was running a slideshow through Mirage - and it's taking a good three to four seconds to load each image - and most of this is just nonsense I've saved over the years, so we're talking small files here <500K for the most part, not 10Mp RAW format photographs!

During that loading period, usage of one of my CPU cores is shooting up to 100%.

Having just had a harddrive fail by slowly grinding to a halt (thank goodness for Ubuntu actually talking to the SMART system...until they disabled it anyway) and giving me a heads up as to what what was going on there - I'm a bit nervous that this might be a similar issue - even though running the self test utility on the drive has given a clean result.

Just seems odd that this has started suddenly...Not sure if an update was responsible, but I've not installed anything else recently...so it's the first thing I look at suspiciously!  Just feels that there's a really basic bottleneck somewhere...but I've not a clue where to start looking.

Any ideas?

Ubuntu 9.10 64-bit.  AMD Athlon XP2 5000+, 4Gb RAM, Nvidia GeForce FX8500GT graphics card, Samsung HD103SI 1Tb harddrive.

Cheers.

---

### Post by tgalati4 on 2010-04-22
In a terminal:

sudo apt-get install htop

htop

Take note of the processes that are eating up your CPU cycles.

---

### Post by -humanaut- on 2010-04-22
There's been an Xorg memory leak in recent Xorg updates im not sure if it effected Karmic or not but It persistently use more and more memory the longer ubuntu runs

---

### Post by jaco223 on 2010-04-22
+1. You can keep an eye on htop. I know also there is a memory leak with 
the most recent updates for Xorg, which can eat up your RAM over time.
This is according to yesterday's stories at Slashdot.


[http://it.slashdot.org/comments.pl?sid=10/04/21/2021247](http://it.slashdot.org/comments.pl?sid=10/04/21/2021247)

[http://www.phoronix.com/scan.php?page=news_item&px=ODE3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODE3MA)

Maybe some of that info could be helpful.

Jaco

P.S. Sorry I thought you were using Lucid.

---

### Post by Zelandeth on 2010-04-23
Been keeping an eye on Htop for anything looking suspiciously like a culpret - however the CPU usage always seems to be allocated to the program in question - and today doesn't actually seem to be pegging itself at 100% like it was before - however opening images/documents when browsing and such still seems to be painfully slow.

It doesn't seem to be a cumulative problem such as a memory leak.  Memory usage is remaining stable at around the 550-600mb mark throughout the day.

Opera for example just greyed out there for a good 30 seconds when I hit submit = IOwait shot up to 100% in the taskbar CPU meter, but usage never even twitched in Htop...Have to admit that there seem to be a number of processes in there I don't recognise - but I'm guessing that's largely because I've recently switched over to 9.10, and there are inevitably things in there different to 8.04 which I'd been using since its release until the start of the month.

It almost feels like every now and then, applications are just being made to sit in a queue before being allowed access to the CPU if that makes any sense...once they get there however, they then run fine.

---

### Post by Zelandeth on 2010-07-13
Just to close this one off - I never did get to the bottom of the cause.

It seemed however that this was caused by data corruption on the harddrive - performance as indicated above continued to degrade further, until eventually the system would fall over altogether.  It then forced a disk check at startup.  This found errors, corrected them which sorted things out.  ...For a week or so until the cycle repeated.

One of a number of problems I had with 9.10, which was a short-lived version on my machine.  This problem hasn't resurfaced since I've upgraded to 10.04.

---

