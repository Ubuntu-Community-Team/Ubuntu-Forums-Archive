---
title: "How to change resolution frequency"
date: 2006-01-20
forum: General Help
---

### Post by Inarius03 on 2006-01-20
Currently running 1600x1200 @ 75 Hz, but I can go up to 100 Hz. Read a couple threads, but they all pointed to how to add resolution only, and not changing to a new frequency afterward.

The following is the monitor section of my xorg.conf, which looks to me like it's already got the frequencies right:
> Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Something I'm missing, or do I just need to run the xorg configure program again?

EDIT: I meant to say refresh rate... sorry

---

### Post by 23meg on 2006-01-20
Did you see [this thread]("http://www.ubuntuforums.org/showthread.php?t=83973")?

---

### Post by Inarius03 on 2006-01-20
Can't get it to work, but it's alright. Thanks anyway :P

---

