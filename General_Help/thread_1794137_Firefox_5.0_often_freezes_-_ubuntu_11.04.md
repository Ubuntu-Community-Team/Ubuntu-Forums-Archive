---
title: "Firefox 5.0 often freezes - ubuntu 11.04"
date: 2011-06-30
forum: General Help
---

### Post by langmarp on 2011-06-30
Hi!

Firefox 5 very often (several times every day) freezes under ubuntu 11.04
the same was happening with firefox 4
everything is uptodate

I have attached detailed info about the firefox extension in use

please, let me know if you have any idea.

thanks!

best,
peter

---

### Post by jerrrys on 2011-06-30
disable all addons (except ubuntu ff modifications) and run it for a while

---

### Post by ajgreeny on 2011-06-30
> **jerrrys said:**
> disable all addons (except ubuntu ff modifications) and run it for a while
If that seems to help, enable the add-ons one by one and see when you get the problem again.  That may give a clue to where the problem lies.

---

### Post by lovinglinux on 2011-06-30
All-in-One Sidebar, TabMixPlus are [slow performing add-ons]("https://addons.mozilla.org/en-US/firefox/performance/"), at least when considering startup. I don't have any data right now, but I think I remember FastestFox being included in that list too. Not sure tho.

Nevertheless, if I had to guess, I would say it is probably Xmarks, because it can be very slow during sync. Firefox 4 and 5 have a built in sync feature that never gave me any problems (some users had). I would backup you profile folder (~/mozilla/firefox/<profilename>/), activate Firefox Sync in the preferences and disable Xmarks for a while, at least for testing if it improves performance and if it works as you expect.

I also recommend to [optimize your databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization"). See other optimizations available there.

---

### Post by jesseconibear on 2011-06-30
i am having the same problem as you, but i am running xubuntu 11.04.

i just did a fresh install and do not have many add ons in my list.

extensions
ubuntu firefox modifications 0.9.1
global menu bar integration

plug ins
adobe reader 9.4
parole media player plug-in
shockwave flash

If it is an add-on problem the only one we have in common besides ubuntu firefox modifications 0.9.1 is that global menu bar integration.

I disabled mine, i'll get back to you on if and when it freezes again

---

### Post by lovinglinux on 2011-06-30
> **jesseconibear said:**
> i am having the same problem as you, but i am running xubuntu 11.04.

i just did a fresh install and do not have many add ons in my list.

extensions
ubuntu firefox modifications 0.9.1
global menu bar integration

plug ins
adobe reader 9.4
parole media player plug-in
shockwave flash

If it is an add-on problem the only one we have in common besides ubuntu firefox modifications 0.9.1 is that global menu bar integration.

I disabled mine, i'll get back to you on if and when it freezes again

I forgot to mention that the global menu bar integration is buggy and can cause serious problems like preventing Firefox from starting in some machines, among other problems. See [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by jesseconibear on 2011-07-01
24 hours since disabling global menu bar integration 1.0.6, and have not had firefox freeze up on me once.  i used to get 3-5 freeze ups per day.  i am glad that is solved.  now i just need someone really smart to get 3d for my radeon 9100 IGP.

my full switch to linux is going good....

---

### Post by jesseconibear on 2011-07-01
spoke to soon, just had a freeze in firefox.  this time it happened when i used my scroll wheel on my mouse...

---

### Post by lovinglinux on 2011-07-01
> **jesseconibear said:**
> spoke to soon, just had a freeze in firefox.  this time it happened when i used my scroll wheel on my mouse...

That is probably related to video card then. Check if you have the latest video driver and disable smooth scrolling in Firefox advanced preferences.

---

### Post by langmarp on 2011-07-11
FastestFox was the problem
since turning off this add-on Firefox 5 is running fine
(I have also disabled xmarks)

---

### Post by idoitprone on 2011-07-11
Seriously, learn to make do with less addons. It will make your browsing experience so much better since there is less crude running in the background.

Please read this article, this will dismystify why many firefox addon just suck at times

[http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons](http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons)

---

### Post by lovinglinux on 2011-07-11
> **idoitprone said:**
> Seriously, learn to make do with less addons. It will make your browsing experience so much better since there is less crude running in the background.

As a general rule, the more add-ons you have, more the performance will drop, specially on startup. However, there are add-ons and add-ons. You just need to be selective about which add-ons you install. I have 55 add-ons running at the moment I don't have problems with Firefox performance whatsoever. I don't even have a fast machine. My main HD is slow and my CPU is just a Core 2 Duo.

There are great add-ons that make the browsing experience a lot better. For me, the web wouldn't be the same without FF add-ons.

> **idoitprone said:**
> Please read this article, this will dismystify why many firefox addon just suck at times

[http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons](http://www.oxymoronical.com/blog/2011/06/Why-do-Firefox-updates-break-add-ons)

That article, which is very informative, dismystify why the fast release model is not bad for add-ons and why some of them break with Firefox updates, not why some add-ons have performance issues.

Performance issues are more related to what add-ons do and how they are coded. For instance, XMarks does a lot of sqlite queries to merge bookmarks and sqlite is essentially slow, specially if you don't optimize your databases very often and/or have a slow hard drive. However, Firefox Sync does the same job and uses less resources.

---

