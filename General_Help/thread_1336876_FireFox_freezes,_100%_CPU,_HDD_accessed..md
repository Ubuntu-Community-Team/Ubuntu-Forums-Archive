---
title: "FireFox freezes, 100% CPU, HDD accessed."
date: 2009-11-24
forum: General Help
---

### Post by hellmet on 2009-11-24
Another FF freezing issue, but on a 64 bit Ubuntu install. 
Using Firefox 3.5.5, completely updated Ubuntu system, Core2Duo 2.26 Ghz processor and 2GB Ram. No swap.
Firefox Addons:
Tiny Menu
Tabs open relative
Hide Caption
Fox Tab
FireFTP
Bookmarks Menu
Adblock Plus
FullScreen Status Bar

This is the issue: Firefox freezes randomly, but each time, it freezes thrice. Yes, three times each time. With a gap of a second or two. During the freeze Firefox uses up 100% of the CPU. At the end of each freeze-release, CPU drops down and the HDD is accessed for a second. There is HDD activity.

This has been going on since some time. It doesn't happen frequently, is random, and is not reproducible. Flash or no Flash, it makes no difference. Simple html web-pages have frozen FF. I could try disabling all Addons, but I have too many and this issue might or might not crop up. 

What I want to find out is where to look (log files) for errors or debugging messages. Where are such messages for FireFox stored? Anyone else facing a similar problem? 
Right now, I'm running FireFox from a terminal. Let me see if I can catch something.

Appreciate your time.

---

### Post by freddybob on 2009-11-26
Does increasing the *browser.sessionstore.interval* value in *about:config* make any difference?

[https://bugzilla.mozilla.org/show_bug.cgi?id=490122#c6](https://bugzilla.mozilla.org/show_bug.cgi?id=490122#c6)

---

### Post by hellmet on 2009-11-26
I'm trying that now. This looks like a very notorious bug.
**UPDATE**: Nah.. Firefox froze just now. Nothing different.

---

### Post by freddybob on 2009-11-29
Here's another idea.  Does turning off the "Block reported attack sites" and "Block reported web forgeries" options help?

[http://ubuntuforums.org/showpost.php?p=7666155&postcount=8](http://ubuntuforums.org/showpost.php?p=7666155&postcount=8)

---

### Post by hellmet on 2009-12-03
Nope. That didn't help either. But, thanks for trying to help. :)

---

### Post by abdusamed on 2010-12-28
fireofx latest also killing here... 100cpu on pages with no flash/html5 content...just 30 or 40 tabs of 4gig ram!

---

