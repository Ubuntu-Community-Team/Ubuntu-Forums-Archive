---
title: "Desktop search with Tracker/Beagle/Whatever"
date: 2010-09-07
forum: General Help
---

### Post by isecore on 2010-09-07
What happened to meta-searching your files? I remember back in the days of Edgy that Beagle was the shiznit and then it fell out of favor and Tracker came instead. This spring when I upgraded from Karmic to Lucid it was deemed that Tracker was an obsolete package.

I tried installing it manually and it works like before - which is, it doesn't work much at all. Sometimes it functions, but on the whole it's quite unreliable. Which I suppose was a contributing factor as to why it isn't included in default installs these days.

So what are we supposed to use instead when trying to locate files? Sure, I can go into a shell and do a "locate [filename]" but it's kind of crude and sometimes I don't always remember the proper filenames.

Just wondering.

---

### Post by coolaj86 on 2010-09-30
bump

---

### Post by statmonkey on 2010-10-06
I have been looking into both of them.  From what I understand Beagle is considered unstable and Tracker is pretty much doa.  I don't have confirmation on the Tracker from anyone official but that is what I have read on several sites.  I am using beagle in Lucid and can understand why people get nervy about it since it requires an adjustment to fstab.  That said I have found it to work pretty well and did not have much luck with Tracker.

---

### Post by isecore on 2010-10-06
Thanks for your input. I've come basically to the same conclusion, that Tracker is dead or dying, and that Beagle is generally regarded as a bit too unstable for everyday use. I'll go without either of them until a replacement (hopefully) pops up some day.

Until then, the locate command is my friend!

> **statmonkey said:**
> I have been looking into both of them.  From what I understand Beagle is considered unstable and Tracker is pretty much doa.  I don't have confirmation on the Tracker from anyone official but that is what I have read on several sites.  I am using beagle in Lucid and can understand why people get nervy about it since it requires an adjustment to fstab.  That said I have found it to work pretty well and did not have much luck with Tracker.

---

### Post by statmonkey on 2010-10-06
I need to correct something I said.  The old way of installing beagle (I have used it since edgy) was to edit fstab.  After I wrote that it occurred to me my memory was ... lacking? or something.  Anyway it is a as simple as sudo apt-get install beagle.  Opening search, setting preferences and then clicking Service Options and starting the service.  I think I was a bit hard on it.  I actually like it for the most part and while I still use locate, whereis, etc. Beagle does record your locate results, etc. It really is a no hassle install and I doubt you would break anything.  That said your mileage may vary.

From the Beagle home page:

Beagle is no longer in active development. It is getting some occasional maintenance done by Novell. 

Further, I keep hearing about something called Recoil as a search tool but I have never run across it in the wild.  Best of luck and happy searching.

---

