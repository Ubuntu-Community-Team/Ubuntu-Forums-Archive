---
title: "Firefox crashes after update"
date: 2010-07-04
forum: General Help
---

### Post by dnr1128 on 2010-07-04
Tonight I updated my system with the latest updates, and now firefox keeps crashing.  The screen will darken and after about 30 seconds a windows will pop up saying firefox isn't responding.  

Any ideas?  I'm running Lucid

---

### Post by flanagan on 2010-07-05
My experience with Firefox under Lucid is similar, and it seems to be theme-related. In the Lucid (10.04) release, they seem to have mucked with the themes rather badly so that the ONLY stable theme that works with Firefox is Ambiance (see System --> Preferences --> Appearance).

As distasteful as Ambiance is, at least it is stable. All other themes cause (for me) Firefox to crash under almost any site that contains Flash, and under any use of the Google Search box. When Firefox crashes (for me) it take the whole X system with it and throws me out to the login page.

---

### Post by m_gustafsson on 2010-07-05
I had similar problems and moved my .mozilla/firefox folder...
```
$ mv .mozilla/firefox .mozilla/firefox_old
```
Killed all Firefox processes and restarted the browser.
Not the best of solutions, but a workaround that worked for me at least.

---

### Post by Slug71 on 2010-07-05
Yep and its damn annoying. I find it happens most when using sites that require Flash. Anyone know if a bug has been filed?

---

### Post by lovinglinux on 2010-07-05
> **m_gustafsson said:**
> I had similar problems and moved my .mozilla/firefox folder...
```
$ mv .mozilla/firefox .mozilla/firefox_old
```
Killed all Firefox processes and restarted the browser.
Not the best of solutions, but a workaround that worked for me at least.

When you provide such solution, please inform the user that all his FF settings, passwords, extensions, bookmarks, cookies and so on will be reset, since a new profile will be created.

I prefer to recommend trying to find the culprit before resetting profiles.

See these:

[http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)
[http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by lovinglinux on 2010-07-05
> **dnr1128 said:**
> Tonight I updated my system with the latest updates, and now firefox keeps crashing.  The screen will darken and after about 30 seconds a windows will pop up saying firefox isn't responding.  

Any ideas?  I'm running Lucid

Some users having problems with the latest updates were able to solve the problem by deleting the file secmod.db from their FF profiles.

---

### Post by flanagan on 2010-07-05
> **Slug71 said:**
> Yep and its damn annoying. I find it happens most when using sites that require Flash. Anyone know if a bug has been filed?
There seems to have been several bugs filed, but the major one dealing with Xorg crashing appears to be [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772")

From the reading of that thread it is very difficult to determine whether it it supposed to be fixed in the latest updates or not.

---

### Post by Slug71 on 2010-07-05
> **flanagan said:**
> There seems to have been several bugs filed, but the major one dealing with Xorg crashing appears to be [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772")

From the reading of that thread it is very difficult to determine whether it it supposed to be fixed in the latest updates or not.

Yeh it seems like that was supposed to fix it.

---

