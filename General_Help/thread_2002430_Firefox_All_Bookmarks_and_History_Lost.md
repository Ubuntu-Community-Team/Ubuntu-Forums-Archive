---
title: "Firefox All Bookmarks and History Lost"
date: 2012-06-12
forum: General Help
---

### Post by bleakgh on 2012-06-12
I lost all my history, bookmarks, and cookies on Firefox, with my OS being Ubuntu 12.04. I can't save new bookmarks, and my history isn't being created by visiting sites. I can't even alt+left or click a left arrow to go back a page (I have to crtl+click the link instead). Additionally, my passwords were still saved, but it keeps the same passwords, even when I try to change the saved password to something different (and correct). Even when I click "stay logged into this site" it doesn't keep me logged in when I restart the browser, so cookies aren't being saved anyway.

---

### Post by cycling-rod on 2012-07-04
I'm using Ubuntu 12.04, Firefox 13.0.1. Have you opened Firefox, then clicked on Edit > Preferences > Privacy and made sure History, Firefox will: Remember history, is enabled, and so on?

---

### Post by msammels on 2012-07-04
Also, the "remember me" feature doesn't seem to work in Chrome either, I have no idea. It's quite possibly a cookies issue, so you might want to check that as well, in addition to what cycling-rod has said.

---

### Post by efflandt on 2012-07-04
Did you happen to mess around with things using sudo or as root?

Check ownership and permissions of ~/.mozilla

```
ls -dl ~/.mozilla
ls -l ~/.mozilla
```

Those directories should be owned by you and your group with drwx------ permission.

---

### Post by tomfoolery92 on 2012-07-09
This just happened to me, I live in South africa and the power has cut out a few times today. Finally I can turn on my pc and lo and behold 2 years of well archived bookmarks are gone. If anyone could help me i would be super grateful

---

### Post by firekage on 2012-07-09
It's not the best solution but you can instal xmarks for firefox. It will save all your bookmarks on a xmarks server and you will have access for your ALL bookmarks on different machines when you install xmarks them, log in into it and synchronize it. I use it on Windows and Linux machines.

Just for a future, to know ;)

---

### Post by sgage on 2012-07-09
Firefox keeps bookmarks and history in places.sqlite. This file sometimes becomes corrupted.

You can try looking in ~/.mozilla/firefox/(your profile) and deleting places.*  Firefox will recreate the places files from backups that it keeps. You will, however, lose your history and favicons.

---

### Post by jlittle on 2012-07-09
> **sgage said:**
> Firefox keeps bookmarks and history in places.sqlite. This file sometimes becomes corrupted.

You can try looking in ~/.mozilla/firefox/(your profile) and deleting places.*  Firefox will recreate the places files from backups that it keeps. You will, however, lose your history and favicons.

I would first just just rename/move the file first rather than delete in case the problem is elsewhere, like a permission problem...

mv  ~/.mozilla/firefox/(your_profile)/places.sqlite ~/.mozilla/firefox/(your_profile)/places.sqlite.bak

If it does fix the problem at least you could restore it and look for trouble elsewhere.

Also, a tip: this is where backup comes into to play. If you regularly backup your profile (like daily) you could have just restored the ~/.mozilla/firefox/(your_profile) from that day prior to the problem and not lose all your stuff.

-- 

Jonathan

---

### Post by sgage on 2012-07-09
> **jlittle said:**
> I would first just just rename/move the file first rather than delete in case the problem is elsewhere, like a permission problem...

mv  ~/.mozilla/firefox/(your_profile)/places.sqlite ~/.mozilla/firefox/(your_profile)/places.sqlite.bak

If it does fix the problem at least you could restore it and look for trouble elsewhere.

Also, a tip: this is where backup comes into to play. If you regularly backup your profile (like daily) you could have just restored the ~/.mozilla/firefox/(your_profile) from that day prior to the problem and not lose all your stuff.

-- 

Jonathan

Well, the symptoms sounded like a classic corrupt places.sqlite to me, but point taken. Though he would have gotten his bookmarks back, if not his history.

I back up my whole home directory every few days, but I do back up places.sqlite more frequently. Though it hasn't gone bad on me in quite a while.

---

