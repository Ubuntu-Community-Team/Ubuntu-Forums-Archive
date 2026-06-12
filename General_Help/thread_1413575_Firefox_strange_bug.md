---
title: "Firefox strange bug"
date: 2010-02-22
forum: General Help
---

### Post by Nonno Bassotto on 2010-02-22
My Firefox magic bar behaves in a very strange way. I cannot find any reference on this bug on the web.

When I leave Firefox open for a while without using it, it becomes unusable. Whenever I enter anything in the magic bar (that is the URL bar) it becomes selected after less than a second. That is, say I want to go to [www.google.it](www.google.it). I start writing "w" and it becomes selected. When I press the second "w" this just replaces the first and becomes selected. Then I only have the third "w", then only ".", only "g" and so on. If I click with the mouse after each stroke to unselect, then I can write (not very comfortable though).

Moreover when this happens, the autosuggest for visited sites and bookmarks is not working.

If I close Firefox and open it again, it works as usual. So, while not being critical, this bug is quite annoying. Any ideas where to look?

I should mention that this bug has been present thoughout the various Firefox updates, since when I was using Firefox 3 in Ubuntu 9.04.

---

### Post by ajgreeny on 2010-02-22
Type in and have a look in ```
about:config
``` if you can do so in your addressbar (urlbar) and filter **urlbar** in the top box.  I can not see anything that would point to what is happening on your machine, but it's worth a look.

---

### Post by katie-xx on 2010-02-22
I may be barking up the wrong tree here but do you have a lot of rss feeds enabled?

---

### Post by lovinglinux on 2010-02-22
[http://ubuntuforums.org/showthread.php?t=1034340](http://ubuntuforums.org/showthread.php?t=1034340)
[http://ubuntuforums.org/showthread.php?t=1319054](http://ubuntuforums.org/showthread.php?t=1319054)
[http://ubuntuforums.org/showthread.php?t=1339466](http://ubuntuforums.org/showthread.php?t=1339466)

Just to let you know that I have found those threads with Google, using the search string [firefox address bar type site:ubuntuforums.org](http://www.google.com/search?q=firefox+address+bar+type+site%3Aubuntuforums.org).

---

### Post by Nonno Bassotto on 2010-02-22
> **katie-xx said:**
> I may be barking up the wrong tree here but do you have a lot of rss feeds enabled?

Only 7, I don't think they count as "a lot"

---

### Post by Nonno Bassotto on 2010-02-22
> **lovinglinux said:**
> [http://ubuntuforums.org/showthread.php?t=1034340](http://ubuntuforums.org/showthread.php?t=1034340)
[http://ubuntuforums.org/showthread.php?t=1319054](http://ubuntuforums.org/showthread.php?t=1319054)
[http://ubuntuforums.org/showthread.php?t=1339466](http://ubuntuforums.org/showthread.php?t=1339466)

Just to let you know that I have found those threads with Google, using the search string [firefox address bar type site:ubuntuforums.org](http://www.google.com/search?q=firefox+address+bar+type+site%3Aubuntuforums.org).

Thank you, I tried other string and didn't find anything relevant (btw the first link you post is not relevant). Sadly no solution is found in these threads

---

### Post by lovinglinux on 2010-02-23
> **Nonno Bassotto said:**
> Thank you, I tried other string and didn't find anything relevant (btw the first link you post is not relevant). Sadly no solution is found in these threads

I'm not sure, but think I saw a solution somewhere else. I just don't remember what it is and where it is. I will keep looking and let you know if I find it.

---

### Post by zeus77 on 2010-07-29
To expand a little on lovinglinux's list --

**Yet more threads discussing this issue:**
[INDENT][http://ubuntuforums.org/showthread.php?t=1152059](http://ubuntuforums.org/showthread.php?t=1152059)
[http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)
[http://ubuntuforums.org/showthread.php?t=1308509](http://ubuntuforums.org/showthread.php?t=1308509)
[http://ubuntuforums.org/showthread.php?t=1374165](http://ubuntuforums.org/showthread.php?t=1374165)
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

