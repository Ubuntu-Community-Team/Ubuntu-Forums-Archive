---
title: "Address bar problems with Ubuntu and Firefox, Help!!"
date: 2009-10-31
forum: General Help
---

### Post by Kangaroo_Style on 2009-10-31
This is a little hard to describe, but I will do my best to write it clearly as possible.

Often times I will stop using my computer, and I will leave my browser going (Firefox), and my computer will go into sleep mode. Then when I "wake" up my computer, and try to type into the address bar I am unable to do so, unless I alt+tab back and fourth. 

What happens is that it will constantly erase what I type in the address bar. For example if I start to type www. It will not write down the second and third w's, and will only keep the first w. Or it will revert the last letter I typed. So if I were to type "http" it will keep the "p" but erase the "htt" part. 

Anyone have any suggestions how I can fix this? It's really annoying.

---

### Post by Kangaroo_Style on 2009-11-01
Just a friendly bump

---

### Post by eoinoc333 on 2009-11-07
I have the same issue, with a similar cause.

Description: as I type in the address bar, Firefox selects all the text I have typed (one or two characters), so that when I continue to type it overwrites what was already there. So basically every character I type is overwritten because it automatically gets selected, as if I were hitting Ctrl+A after every character I typed.

Cause: Similar to as Kangaroo_Style states, it only happens when the computer has gone in to screensaver mode.

BTW, if I type at least 5 characters really quickly into the address bar, then the select-all behaviour no longer happens.

---

### Post by Kangaroo_Style on 2010-03-26
Anyone else have any suggestions? It's been 5 months now...

---

### Post by svenni on 2010-07-23
I'm having the exact same problem and I'm thinking it might have something to do with compiz. I had some problems with Open Office and compiz after wake ups earlier, even though that was a huge performance hit rather than characters being overwritten.

It just feels like something similar, although I don't really know if it is at all related to compiz. Maybe we could investigate it further and file a bug if we figure out what it might be related to.

---

### Post by zeus77 on 2010-07-29
**Other threads discussing this issue:**
[INDENT][http://ubuntuforums.org/showthread.php?t=1152059](http://ubuntuforums.org/showthread.php?t=1152059)
[http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)
[http://ubuntuforums.org/showthread.php?t=1319054](http://ubuntuforums.org/showthread.php?t=1319054)
[http://ubuntuforums.org/showthread.php?t=1339466](http://ubuntuforums.org/showthread.php?t=1339466)
[http://ubuntuforums.org/showthread.php?t=1374165](http://ubuntuforums.org/showthread.php?t=1374165)
[http://ubuntuforums.org/showthread.php?t=1413575](http://ubuntuforums.org/showthread.php?t=1413575)
[http://ubuntuforums.org/showthread.php?t=1417212](http://ubuntuforums.org/showthread.php?t=1417212)
[http://ubuntuforums.org/showthread.php?t=1489786](http://ubuntuforums.org/showthread.php?t=1489786)[/INDENT]


**Bug reports about this issue:**
[INDENT][https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/428703)
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868)
[https://bugzilla.mozilla.org/show_bug.cgi?id=507269](https://bugzilla.mozilla.org/show_bug.cgi?id=507269)[/INDENT]


**Current "best" fix:**
[INDENT]Minimize the firefox window, then restore it.  Or, press Alt-Tab twice.[/INDENT]


**How to let the developers know that you are experiencing this bug:**
[LIST=1]
[*][Create a launchpad account]("https://login.launchpad.net/+new_account") if you don't have one already.
[*]Click [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/428703/+affectsmetoo") and [here]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/438868/+affectsmetoo") to indicate that these bugs affect you, too (only if they truly do, of course!).
[/LIST]


May this bug be fixed one day soon...
zeus77

---

### Post by svenni on 2010-07-29
Thanks for the info! I had no idea this issue was so common.

---

