---
title: "can't type in firefox address bar in karmic"
date: 2010-02-27
forum: General Help
---

### Post by v1nsai on 2010-02-27
I've been having a weird problem with firefox.  When trying to type in the address bar (or search bar) the browser highlights everything I've typed after 2 or 3 letters, so the next letter replaces all the text.  It does that only while the mouse is in the window, if I move the mouse outside of the window, the firefox window loses focus so I can't type in it, but clicking back causes it to highlight my text again.  If I actually click outside the window, then click on it again, this fixes the problem. 

I've had this problem with every version since hardy and I kind of wrote it off as a hardware quirk, but when my new laptop started doing it too, I decided to try to figure it out.

Anyone seen this or have any idea what it could be?

---

### Post by Vaphell on 2010-02-27
crazy ideas:
- you accidentally tap your overly sensitive touchpad when typing (been there, done that - very annoying)
- focus follows mouse enabled in System->Prefs->Windows
- your external mouse clicks itself

---

### Post by lovinglinux on 2010-02-27
> **v1nsai said:**
> Anyone seen this or have any idea what it could be?

Yes, I have seen this a couple of times.

[http://ubuntuforums.org/showthread.php?p=8866677#post8866677](http://ubuntuforums.org/showthread.php?p=8866677#post8866677)
[http://ubuntuforums.org/showthread.php?t=1339466](http://ubuntuforums.org/showthread.php?t=1339466)
[http://ubuntuforums.org/showthread.php?t=1417212](http://ubuntuforums.org/showthread.php?t=1417212)
[http://ubuntuforums.org/showthread.php?t=1319054](http://ubuntuforums.org/showthread.php?t=1319054)

---

### Post by zeus77 on 2010-07-29
**Yet more threads discussing this issue:**
[INDENT][http://ubuntuforums.org/showthread.php?t=1152059](http://ubuntuforums.org/showthread.php?t=1152059)
[http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)
[http://ubuntuforums.org/showthread.php?t=1308509](http://ubuntuforums.org/showthread.php?t=1308509)
[http://ubuntuforums.org/showthread.php?t=1374165](http://ubuntuforums.org/showthread.php?t=1374165)
[http://ubuntuforums.org/showthread.php?t=1489786](http://ubuntuforums.org/showthread.php?t=1489786)
[/INDENT]


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

May this bug be fixed one day...
zeus77

---

