---
title: "Upgrades"
date: 2004-10-24
forum: General Help
---

### Post by elwis on 2004-10-24
Oki, how often do you run the scary "dist-upgrade" command?

I must ask, I've never done it yet... don't know if I dare, might break something (like a leg perhaps, when dancing around my computer while it does it's magic...)

---

### Post by ubuntu-geek on 2004-10-24
[QUOTE=elwis]Oki, how often do you run the scary "dist-upgrade" command?

I must ask, I've never done it yet... don't know if I dare, might break something (like a leg perhaps, when dancing around my computer while it does it's magic...)[/QUOTE]
 You really only need to run the dist-upgrade when a new version of ubuntu is released or if you are upgrading from a RC version of ubuntu. To get the normal updates:

apt-get update
apt-get upgrade

Will do the trick :)

---

### Post by elwis on 2004-10-24
aha, see what one can learn about handling a debian-based distro :)

so, i'll try it, and trust that if I don't dance, it won't break anything.. ;)

---

### Post by jdong on 2004-10-24
Huh? I dist-upgrade with almost every upgrade. It seems that in some cases, especially if a package changes name (like Firefox & Firebird, or some cups libs), dist-upgrade will catch it, but ordinary upgrade will claim your system's already up-to-date.


Dist-upgrade has never done anything "scary". The packages it wants to remove are usually superseded by something it wants to install.

---

### Post by adbak on 2004-10-24
dist-upgrade is nothing scary.  I did it after Ubuntu was officially released and I did it just today and noticed there were more things that needed to be upgraded.  So I would recommend once a week.  It's nothing scary.

---

### Post by rolf on 2004-10-25
I never, ever, ever upgrade anything unless there is a compelling reason.  And of course, compelling is in the eye of the beholder.

---

### Post by FLeiXiuS on 2004-10-25
I'm one who loves to stay upgraded, regardless of the release.  I would always configure it to my needs.  Plus upgrades = something to do :-)

---

### Post by normnmiles on 2004-10-25
I am a recovering upgrade junky.  I use to upgrade everything and didn't feel right unless I had the latest version of everything.  My previous distro of choice also promoted (required) regular updates.  But Ubuntu has freed me from that cycle.  Now I benefit from relatively up-to-date system that is super stable with the option of updating twice a year.

---

### Post by calvinpriest on 2004-10-25
The upside of regular upgrades between releases:
Security  fixes
Patches

Downside:
Something somewhere may break
Sometimes need to reboot

While running Debian Unstable, I avoided upgrades more and more (maybe ran them once a month just before I switched to Ubuntu).  I found that enough bugs were introduced with upgrades that it just wasn't worth the hassle of troubleshooting to fix them all the time.  At first it was fun, then it just got old.  Usually the bugs were things I could easily fix or workaround, but my wife uses my computer, and I didn't want her to have to deal with weird shit happening from time to time.

But that was Debian Unstable.  I have high hopes (and a good amount of faith) that the pros of frequently updating Ubuntu will outweigh the cons.   We shall see...

Calvin

---

### Post by jdong on 2004-10-25
[QUOTE=calvinpriest]The upside of regular upgrades between releases:
Security  fixes
Patches

Downside:
Something somewhere may break
Sometimes need to reboot

While running Debian Unstable, I avoided upgrades more and more (maybe ran them once a month just before I switched to Ubuntu).  I found that enough bugs were introduced with upgrades that it just wasn't worth the hassle of troubleshooting to fix them all the time.  At first it was fun, then it just got old.  Usually the bugs were things I could easily fix or workaround, but my wife uses my computer, and I didn't want her to have to deal with weird shit happening from time to time.

But that was Debian Unstable.  I have high hopes (and a good amount of faith) that the pros of frequently updating Ubuntu will outweigh the cons.   We shall see...

Calvin[/QUOTE]
From what I've seen, Warty upgrades (for the past few days that I've used it) are only security fixes, like Debian stable type updates. It's gonna be a new release bringing in a major upgade, in which apt will seriously be your best friend.

From my experience with bring Woody to SID/experimental, APT is godly at doing huge upgrades, and I've had more pleasant woody-to-sid upgrades than FC1->FC2 upgrades...

---

