---
title: "Firefox has lost my bookmarks"
date: 2011-12-04
forum: General Help
---

### Post by carranty on 2011-12-04
BACKGROUND

I recently (recklessly and naively) tried my hand at overclocking, however I screwed things up and ended up having to reset my CMOS by taking out the small circular battery on my motherboard.  Upon booting, the Ubuntu splash screen said something along the lines of an error in the filesystem, unable to mount.  I restarted, booted into recovery mode and it seems to have fixed itself - I can now boot normally and all is fine....

PROBLEM

....well almost.  Firefox no longer contains any of my bookmarks.  Neither does it have any of my browser history, though weirdly it does have all my stored passwords.  Any ideas how I can get my bookmarks back?

---

### Post by bluexrider on 2011-12-04
Check your 

USER/.mozilla/firefox/dxb24med.default (something like that xxxxxx.default)

you should find a bookmarkbackups file.

Restore from there

---

### Post by carranty on 2011-12-04
```
carranty@carranty-desktop ~ $ ls .mozilla/firefox/
Crash Reports  l4f2cmvq.default  profiles.ini
carranty@carranty-desktop ~ $ ls .mozilla/firefox/l4f2cmvq.default/
addons.sqlite           extensions.ini             pluginreg.dat
blocklist.xml           extensions.rdf             prefs.js
bookmarkbackups         extensions.sqlite          search.json
bookmarks.html          extensions.sqlite-journal  search.sqlite
Cache                   formhistory.sqlite         secmod.db
cert8.db                icons                      sessionstore-1.js
cert_override.txt       key3.db                    sessionstore.bak
chrome                  localstore.rdf             sessionstore.js
chromeappsstore.sqlite  lock                       signons.sqlite
compatibility.ini       mimeTypes.rdf              startupCache
compreg.dat             minidumps                  stylish.sqlite
content-prefs.sqlite    OfflineCache               urlclassifier3.sqlite
cookies.sqlite          permissions.sqlite         urlclassifierkey3.txt
cookies.sqlite-shm      places.sqlite              weave
cookies.sqlite-wal      places.sqlite.corrupt      webappsstore.sqlite
downloads.sqlite        places.sqlite-shm          xpti.dat
extensions              places.sqlite-wal          XUL.mfasl
carranty@carranty-desktop ~ $ ls .mozilla/firefox/l4f2cmvq.default/bookmarkbackups/
bookmarks-2006-01-01.json
carranty@carranty-desktop ~ $ ls -l .mozilla/firefox/l4f2cmvq.default/bookmarkbackups/bookmarks-2006-01-01.json 
-rw------- 1 carranty carranty 5360 2006-01-01 00:13 .mozilla/firefox/l4f2cmvq.default/bookmarkbackups/bookmarks-2006-01-01.json

```

As far as I can tell, the only backup file is very old, I've restored from it but haven't recovered any of my bookmarks.

Its not a big deal, I can remember any important sites, I'm more curious than anything as to why it would delete my bookmarks/history but not my stored passwords.....

---

### Post by bluexrider on 2011-12-04
I cannot answer the question as to WHY! Beginning with removing the CMOS battery.

---

### Post by carranty on 2011-12-04
OK, well my next question then is how to restore my bookmarks from a backup of my home folder.  I make a backup every month.  If i copy the xxxxx.default folder from my backed up home folder, into my current one, will that restore them?

---

### Post by bluexrider on 2011-12-04
that should be easy. just copy the .mozilla folder to your home directory replacing everything.

---

### Post by carranty on 2011-12-04
Thanks, that sorted it.

---

