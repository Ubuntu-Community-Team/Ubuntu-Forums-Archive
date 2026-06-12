---
title: "FireFox - Can't type in Address Bar or Search Box"
date: 2009-11-08
forum: General Help
---

### Post by distortedecho on 2009-11-08
Hi there..

Have this odd issue every now and then where I can't type in the above mentioned boxes. Instead, as soon as I stop typing (for a split second) the text highlights, so I end up over typing it with the next word or letter I'm typing?

Happened in 9.4 also.

Anybody know of this issue, what causes it etc??

---

### Post by SPr on 2009-11-08
Could it be a problem with the keyboard? Replace it and see if it happens again.

Woops. If it only happens in FF then it's not a kb problem.

---

### Post by nexoncore on 2009-11-08
I had the same problem in 9.04, its not device related. I wish I could give a less destructive alternative, but I had to resort to a fresh installation again, but never suffered it since.

I guess a possible stab at the fix, would be to uninstall firefox through Ubuntu Software Centre, restart, then reinstall.

---

### Post by distortedecho on 2009-11-08
Apparently this has been reported as a bug?? How can I check the progress?

---

### Post by aylamarguerida on 2009-12-10
I am having this same issue.  Has anybody figured anything out yet?

---

### Post by raktarok on 2009-12-10
Try starting firefox in safemode. (firefox -safe-mode) 

If the problem still persists, delete the folder .mozilla in your home directory(or you could just delete your profile folder inside it..) and start over again. Make sure that you backup your bookmarks and other firefox settings first!

---

### Post by distortedecho on 2009-12-11
I've found that, when it happens, typing 4 'w's' for a URL, allows you to type a complete URL. It's only the first 2 characters, it seems. So something you type rapidly, such as "www" is quick enough to break the... glitch or whatever it is. 3x w's gets you 2. So type 4 and you get your 3.

It's a work around until they find out what FF is doing.

---

### Post by joes7 on 2009-12-11
re install firefox, or move to another browser.

---

### Post by yipperzz on 2010-04-26
has anyone figured this out?  i thought it was my computer this whole time but i guess others have had this issue too.  i found that if i minimize the browser and restore it again, it seems to work again.  seems pretty random though.

---

### Post by johnisenglish on 2010-05-26
I've had this problem on 9.10 on multiple machines (a Lenovo T61 laptop and an old Asus motherboard desktop). It's really quite frustrating. I'm not sure if the issue is happening on my machine that's running 10.04, but I'll keep an eye on it.

Has anyone found a solution for the issue?

---

### Post by cptncatholic on 2010-06-18
I've been having this problem for the past several days. Running Unbuntu Studio 10.04 on a Lenovo Ideapad Y510. If I close firefox and restart, it fixes it for a while. But I do online Electronic Medical Records and when that happens in the middle of a note, it's very frustrating. Will try some of the suggestions here and see if it clears up.

---

### Post by cptncatholic on 2010-06-21
The problem hasn't gone away. But I've noticed that for me it starts after using the TAB key to move the cursor from one entry field to the next while I'm filling out forms. so when it starts to happen, I left-click on another field, and then left-click the field I need and I can fill it out as normal. This only happens in Firefox, I haven't noticed it happening in any other program.

---

### Post by william12 on 2010-07-05
Thank you for the hint.

I have exactly the same problem, it I tab it then starts over-typing unless you type fast.

Click into another box and then back into the box you want and it works a treat

Firefox 3.6.6
Ubuntu 10.04

---

### Post by Achillobator on 2010-07-05
I'm not sure how much progress has been made toward fixing this problem, but I do know that it also occurs if you allow your screensaver (or blank screen, whatever you have it set to) to start while Firefox is the active window. At least in this case, simply minimizing Firefox or switching to another active window, then maximizing/switching back, will set the fields back to their normal behavior for the time being. Not a permanent fix, but it also works.

---

### Post by jward3010 on 2010-07-29
Happening here on 10.04 and Firefox 3.6.8.

I've noticed something - this only happens when I do an F6 to get to the address bar. On a new tab where the cursor is placed in the address bar everything is fine, on a page where I click into the address bar it's ok, only when I do an f6. Bizzare.

---

### Post by simosx on 2010-07-29
Try to look for bug reports at
[https://bugs.launchpad.net/ubuntu/+source/firefox](https://bugs.launchpad.net/ubuntu/+source/firefox)

I already found one, 
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/598043](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/598043)

which links up to the Mozilla Bugzilla at
[https://bugzilla.mozilla.org/show_bug.cgi?id=521826](https://bugzilla.mozilla.org/show_bug.cgi?id=521826)

So, register to bugzilla.mozilla.org and add yourselves to the CC: list.

---

### Post by zeus77 on 2010-07-29
To expand a little on simosx's response --

**Other threads discussing this issue:**
[INDENT][http://ubuntuforums.org/showthread.php?t=1152059](http://ubuntuforums.org/showthread.php?t=1152059)
[http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)
[http://ubuntuforums.org/showthread.php?t=1308509](http://ubuntuforums.org/showthread.php?t=1308509)
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

### Post by sagar.kerhalkar on 2010-10-10
> **distortedecho said:**
> Hi there..

Have this odd issue every now and then where I can't type in the above mentioned boxes. Instead, as soon as I stop typing (for a split second) the text highlights, so I end up over typing it with the next word or letter I'm typing?

Happened in 9.4 also.

Anybody know of this issue, what causes it etc??
It is in network computer

---

### Post by Jeff9964 on 2011-11-03
I had this problem, but I went in "Tools" and selected "Add-ons" and disabled "Ask Tool bar".  This did it for me. I can't guarantee this is anyone else problem.  But maybe this will guide you in the right direction.

---

