---
title: "Firefox quick search bug"
date: 2010-05-17
forum: General Help
---

### Post by FrankBro on 2010-05-17
I have this weird bug since I installed 10.04 on my desktop computer with firefox. Every time I start typing in the quick search bar in the top right corner, instead of giving me suggestions, it selects what I've written. Like if I start typing "ubuntu ", normally a suggestion drop-box box appear with different subjects that are the most searched. But instead it seems to just do a "select all" (sort of like in a ctrl + a way) of what is written, making the quick search bar completely useless.

Anyone else have this weird bug ?

---

### Post by FrankBro on 2010-05-17
shameless self bump.

---

### Post by FrankBro on 2010-05-18
another weird bug, whatever icon them I apply to the system, it stays the same. =/

---

### Post by Dacke on 2010-05-18
I have a very similar (or the same) bug in Firefox.

Firefox works normally most of the time. When the bug kicks in, "**Select All**" is applied a few times every second. Both the address bar and search field stop working properly. This happens a few times a day for me.

(I also think that text boxes and text fields inside web pages stop working too. I'll have to check next time it occurs.)

**Restarting Firefox** does restore functionality, until the problem occurs again.

The problem started with the upgrade to **Ubuntu 10.04** and/or **Firefox 3.6**.

**My currently active add-ons are:**
Firebug 1.5.4
Grab and Drag 2.7.6
Greasemonkey 0.8.20100408.6 (with one script written by myself. It never touches the address bar)
NoScript 1.9.9.77
Svensk ordlista 1.41 (Swedish spell-check dictionary)
Ubuntu Firefox Modifications 0.9rc2

---

### Post by FrankBro on 2010-05-18
good to know I'm not the only one. I have no add-on except for adblock plus.

---

### Post by FrankBro on 2010-05-18
shameless self bump.

---

### Post by FrankBro on 2010-05-20
shameless self bump

---

### Post by greylion on 2010-05-30
Same problem here.
Recently installed 10.04 64-bit (fresh, not updated from an older installation).
I have set my start and home page to a blank page (about:blank)
This problem comes and goes, haven't found any pattern in it, except maybe that it goes away when you've typed enough (15-20 chars or thereabout), or if you switch back and forth between some other tabs a few times.
Anyway, Ctrl+z un-deletes what you've just typed, that way you can get a bit further every time..

This is currently, without comparison, my #1/TOP annoyance with firefox, and indirectly, Ubuntu (I've never had this problem in Debian).

Version info:
Firefox 3.6.3
Adblock Plus 1.2
Hide Bookmarksbar 1.5.2
NoScript 1.9.9.81
Ubuntu Firefox Modifications 0.9rc2

It took a few searches to even find this thread - maybe others with the same problem can't find it, because they don't know what to search for?

I've just now unchecked "Search for text when I start typing" and "Check my spelling as I type" in Preferences - Advanced - General. I'll report back later whether that makes the problem go away.

Edit: It didn't go away.
I also noticed that if I open two new tabs and close the last opened (as in Ctrl+t twice, then Ctrl+w), then the problem isn't there. Weird.

---

### Post by sites on 2010-05-30
This problem began for me in Karmic and continues until this day.  I've found that if I click around on Firefox a few times the problem stops, but it always comes back.  One of my friends had a problem with Firefox not printing pages from his banking site properly.  Installing Opera was the only workaround.  I just might switch browsers.  I hope Opera has comparable keyboard shortcuts and plugins.

Edit: Frances Ford Crappola!  Opera uses qt.  I'm not willing to sail the Seas of Dependencies in a stupid bloat.  Opera will now be referred to as Oprah.

---

### Post by lovinglinux on 2010-05-30
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jy3 on 2010-06-02
Not a fix, but a work around that seems to be working for me: right click the quick search and uncheck 'show suggestions'.

-Jim

---

### Post by greylion on 2010-06-02
Yesterday, I had the same problem for a short while in the Location bar..

Went away by itself, once I got a minimal URL written and pressed Enter.

---

### Post by Dacke on 2010-06-03
> **jy3 said:**
> Not a fix, but a work around that seems to be working for me: right click the quick search and uncheck 'show suggestions'.

-Jim

I think this is on the right track.

The suggestion function for the address field stops working at times. The problem started at the same time as the problem of this thread started.

---

### Post by sites on 2010-06-04
I also noticed the same problem with the URL bar not showing suggestions from previous entries.  I remember a similar issue a while back where the drop down menus (location, search, and app menus) were dropping behind the browser.  I noticed it with my bookmarks menu because the menu was so long it showed up below the bottom border of the browser window.  Firefox is really killing my buzz these days.  I don't want to install Lucid for other people with Firefox flaking out so much.

---

### Post by sites on 2010-06-05
I think this is another Flash related problem.  After browsing the forums for a few hours with no issues at all i went to find a clip on youtube.  Right after i played the clip the quick search problem reared it's ugly head.

Man... i really hate Adobe right now.

---

### Post by menkhaf on 2010-06-15
I can confirm this bug. I've seen it since Karmic as well, but usually blocks almost everything (Adblock Plus and NoScript with custom ABE rules) and if flash really is behind this bug as sites is getting at, that'd explain why I haven't seen it too often.

> **jy3 said:**
> Not a fix, but a work around that seems to be working for me: right click the quick search and uncheck 'show suggestions'.

-Jim
Confirmed.

> **greylion said:**
> I also noticed that if I open two new tabs and close the last opened (as in Ctrl+t twice, then Ctrl+w), then the problem isn't there. Weird.
Confirmed.

---

### Post by grj23 on 2010-06-16
There's a bug report of this issue:
[bug 583122]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/583122")

---

### Post by lovinglinux on 2010-06-28
Try this:

Go to Firefox menu "Edit >> Preferences >> Advanced >>  General" and disable the option "Search for text when I start typing".  See if that helps.

---

### Post by Dacke on 2010-08-15
> **menkhaf said:**
> 
Confirmed.

Un-confirmed.
The "*Ctrl+t twice, then Ctrl+w*"-trick only works some times. Just like with the "*click all over the place*"-trick, it only works occasionally.

---

### Post by menkhaf on 2010-08-15
> **Dacke said:**
> Un-confirmed.
The "*Ctrl+t twice, then Ctrl+w*"-trick only works some times. Just like with the "*click all over the place*"-trick, it only works occasionally.

Hmm -- I haven't actually used the combination for a while, so I believe you.
Instead I use ALT+TAB twice. Seems like it works every time.

Have a look at [https://bugs.launchpad.net/firefox/+bug/438868](https://bugs.launchpad.net/firefox/+bug/438868) for more details.

---

