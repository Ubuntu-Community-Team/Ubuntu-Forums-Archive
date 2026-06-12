---
title: "Firefox Text Problem - better example"
date: 2009-10-05
forum: General Help
---

### Post by Nyken on 2009-10-05
Hello,

I'm using Firefox Shiretoko, which works great. However, a couple of websites like Walmart's mp3 site won't allow me access with it. Problem is, after I installed simdock, which I ended up hating (and have since uninstalled) the Firefox that came with Ubuntu a text problem effecting webpages, the status bar at the bottom and every pulldown menu from File to Help, that I can't figure out who to fix. It looks like this, for example:

                                Bookmark                    this                             page
                                Subscribe                     to                     this                    page

But each word is spaced way too far apart, about 10 places. (This forum editor won't keep the spaces between the words that way I want to show you.)

Again, it doesn't effect Shiretoko. It does effect Firefox on each account on my computer. I don't know what's corrupted and needs replacing. Anyone have this before and fixed it? :confused:

---

### Post by lovinglinux on 2009-10-05
> **Nyken said:**
> Hello,

I'm using Firefox Shiretoko, which works great. However, a couple of websites like Walmart's mp3 site won't allow me access with it. Problem is, after I installed simdock, which I ended up hating (and have since uninstalled) the Firefox that came with Ubuntu a text problem effecting webpages, the status bar at the bottom and every pulldown menu from File to Help, that I can't figure out who to fix. It looks like this, for example:

                                Bookmark                    this                             page
                                Subscribe                     to                     this                    page

But each word is spaced way too far apart, about 10 places. (This forum editor won't keep the spaces between the words that way I want to show you.)

Again, it doesn't effect Shiretoko. It does effect Firefox on each account on my computer. I don't know what's corrupted and needs replacing. Anyone have this before and fixed it? :confused:

Make a backup of your profile and then delete it. This should fix the problem. Firefox 3.0 profiles are stored at ~/.mozilla/firefox. This won't affect Shiretoko profiles, which are stored at ~/.mozilla/firefox-3.5.

Or you could simply create a new profile to test, before deleting stuff. Run the command below to access the profile manager.


```
firefox -P
```

---

### Post by Nyken on 2009-10-06
Thank you for replying - and I LOVE your Cylon Tux, BTW! Completely awesome!

Thanks for the advice, found it wasn't a Firefox issue, but an issue that effected Firefox, if that makes any sense. The package Pango-graphite and it's dbg counterpart, which I needed to download to run SimDock was the culprit. Removing it cleaned up Firefox. 

This package doesn't effect Shiretoko, at least if Shiretoko were installed after Pango, but will earlier version of Firefox, and I've been able to recreate this problem to prove it. Researching over at the fine folks @ launchpad.net showed me the way.

---

### Post by lovinglinux on 2009-10-06
> **Nyken said:**
> Thank you for replying - and I LOVE your Cylon Tux, BTW! Completely awesome!

Thanks. It was [kindly made](http://ubuntuforums.org/showthread.php?t=1106602) by [alex.rayu](http://ubuntuforums.org/member.php?u=443223).

> **Nyken said:**
> Thanks for the advice, found it wasn't a Firefox issue, but an issue that effected Firefox, if that makes any sense. The package Pango-graphite and it's dbg counterpart, which I needed to download to run SimDock was the culprit. Removing it cleaned up Firefox. 

This package doesn't effect Shiretoko, at least if Shiretoko were installed after Pango, but will earlier version of Firefox, and I've been able to recreate this problem to prove it. Researching over at the fine folks @ launchpad.net showed me the way.

Good to know.

---

