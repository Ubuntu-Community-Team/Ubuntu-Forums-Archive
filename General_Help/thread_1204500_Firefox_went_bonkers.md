---
title: "Firefox went bonkers"
date: 2009-07-04
forum: General Help
---

### Post by triangleSLO on 2009-07-04
I dont have "Go back one page" and "Go forward one page" buttons anymore. I also lost all my bookmarks. I reinstalled Firefox but it didnt help.

---

### Post by merlinus on 2009-07-04
You might look in the hidden .mozilla/firefox directory in case for some bizarre reason another profile got created.

---

### Post by triangleSLO on 2009-07-04
I am in the hidden mozilla directory but i dont know what exactly am i looking for :/

---

### Post by merlinus on 2009-07-04
Go to the firefox directory.  Your old bookmarks.html file may still be there.  Also, look in xxxxx.default for other stuff.  That is your profile, and there may be more than one.

xxxxx are numbers and letters.

---

### Post by triangleSLO on 2009-07-04
This is my xxxx.default file
> blocklist.xml
bookmarkbackups
bookmarks.html
Cache
cert8.db
cert_override.txt
chrome
compatibility.ini
compreg.dat
content-prefs.sqlite
cookies.sqlite
downloads.sqlite
EA41F07F1510CEB7620095959142E396B90353E7712C9AFBAD2DA0EFE11E3834_ff_lppri.lps
ea41f07f1510ceb7620095959142e396b90353e7712c9afbad2da0efe11e3834_ff.otp
EA41F07F1510CEB7620095959142E396B90353E7712C9AFBAD2DA0EFE11E3834_ICONS3.LPS
ea41f07f1510ceb7620095959142e396b90353e7712c9afbad2da0efe11e3834_lp.act.lps
ea41f07f1510ceb7620095959142e396b90353e7712c9afbad2da0efe11e3834_lps.act.xml
extensions
extensions.cache
extensions.ini
extensions.rdf
formhistory.sqlite
key3.db
localstore.rdf
lock
mimeTypes.rdf
OfflineCache
permissions.sqlite
places.sqlite
places.sqlite-journal
pluginreg.dat
prefs.js
search.sqlite
secmod.db
signons3.txt
urlclassifier3.sqlite
urlclassifierkey3.txt
user.js
xmarks-baseline-5211b6a398feb53d.json
xmarks.log
XPC.mfasl
xpti.dat
XUL.mfasl

---

### Post by lovinglinux on 2009-07-04
Backup your profile first, then delete the file *places.sqlite*. This should fix your problem.

This and other common Firefox issues and solutions are described in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), along with tips to avoid them.

---

### Post by triangleSLO on 2009-07-04
Thanks problem solved :KS

---

### Post by lovinglinux on 2009-07-04
> **triangleSLO said:**
> Thanks problem solved :KS

You are welcome. Spread the word about it.

---

### Post by triangleSLO on 2009-07-04
> **lovinglinux said:**
> You are welcome. Spread the word about it.

I just bookmarked your Firefox thread very useful stuff

---

