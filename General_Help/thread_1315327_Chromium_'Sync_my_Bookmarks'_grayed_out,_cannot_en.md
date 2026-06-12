---
title: "Chromium 'Sync my Bookmarks' grayed out, cannot enable bookmark sync"
date: 2009-11-05
forum: General Help
---

### Post by martini1179 on 2009-11-05
I've just upgraded to the spanking new Chromium 4.0.236.0 and for the first time, felt like trying out the in-browser bookmark sync. But I can't get it to work; instead 'Sync my Bookmarks' is grayed out, even when I use a flag. 

The flags I've used are:

chromium-browser --enable-sync --enable-plugins %U 

and 

chromium-browser --enable-plugins %U --enable-sync

Any help is appreciated. I'm sorry, but I've Googled this and checked the forums and I couldn't find a satisfactory answer.

---

### Post by damijit on 2009-11-13
The grayed-out "Sync my bookmarks" menu item only appeared a week or two ago. I suspect it just hasn't been fully implemented on linux yet.

---

### Post by martini1179 on 2009-11-13
Yeah I just noticed that the newest Chromium version, 4.0.247.0, if memory serves, has working bookmark sync.

---

### Post by Donhcd on 2009-11-14
How did you get 4.0.247.0? I just updated and got  4.0.245.1. And Sync Bookmarks is still grayed out even with --enable-sync :'(

---

### Post by martini1179 on 2009-11-15
> **Donhcd said:**
> How did you get 4.0.247.0? I just updated and got  4.0.245.1. And Sync Bookmarks is still grayed out even with --enable-sync :'(

I was referring to Chromium, whereas I believe you were referring to Chrome. 

Chromium is the open-source project on which Chrome is based. It's more of an alpha release whereas Chrome is more of a beta, so it has a higher version number, and advanced features are typically tested in Chromium first before being included in Chrome. The latest version of Chromium, 4.0.248.0, has bookmark sync capability. Chrome should also have it within a week or so.

If you want to try out Chromium (and bookmark sync), install the following PPA:

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

