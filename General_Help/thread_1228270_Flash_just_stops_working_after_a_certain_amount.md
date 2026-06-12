---
title: "Flash just stops working after a certain amount"
date: 2009-07-31
forum: General Help
---

### Post by nbv4 on 2009-07-31
I have no idea what causes this, but sometimes, usually after firefox is open for a while, flash will just stop working. I'll go to youtube and all videos will just not be there. I'll go to Google Analytics and the little flash graphs just won't be there. Firefox never crashes and I'll see no error messages. If I close all instances of Firefox, then open Firefox again, it'll fix the problem. This is very annoying. I'm using 64bit Ubuntu 9.04 and everything else stock.

---

### Post by Kai Summers on 2009-07-31
I was also having a similar problem. Also when in Full Screen mode Flash video would become very jumpy and not watchable. Recently I upgraded to the Karmic Koala testing version of Ubuntu and have had no problems with flash at all!! Smooth video and very few errors with the distro (except Google Earth). 

**Installed Flash version:** 10.0.22.87

---

### Post by Zorael on 2009-08-01
(FWIW, this is largely a 64-bit issue, and as such more suitable for the 64-bit forums. Copying this from another post.)


That's Flash crashing.

Historically Flash has only been available as a 32-bit binary, and as it isn't open source it was up to Adobe to supply a 64-bit one.

To work around this, you either had to run a 32-bit browser (which is possible but doesn't work if you use native, 64-bit input methods, for instance), or despair. Since people didn't want to despair, a 64-bit wrapper was written to allow 32-bit plugins to run in. A dirty solution, but it mostly worked, until later Flash releases and the advent of Firefox 3 when it suddenly started becoming very, very sketchy.

There is nowadays a [64-bit Flash alpha](http://labs.adobe.com/downloads/flashplayer10.html) available for Linux (and Linux alone). Installation howto [here](http://ubuntuforums.org/showthread.php?t=1081964). Try that.

---

