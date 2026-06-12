---
title: "cant sae files in Firefox"
date: 2010-01-13
forum: General Help
---

### Post by confused_user on 2010-01-13
Hi, I have Ubuntu 9.10 dual booting with Windows7.

My ext3 /home is mounted as F: in windows.

I share a firefox profile between them so that when i am in Windows my firefox uses the same profile as it does when in Ubuntu.

It all worked great until recently.  I am unable to save files by right clicking and save as.  In the config i am unable to set a directory to save to.  It neer asks me where to save to.  Just nothing happens.

Can anyone help?

some off my book marks are all messed up as well, my rss feeds have the same post on some random website every time i log on and i have to manually refresh to get the correct feeds back.  I am unable to delete the random bookmark.

---

### Post by confused_user on 2010-01-15
I fixed this by deleting downloads.sqlite from ~./mozilla/firefox/profilename

restarted and now works

---

