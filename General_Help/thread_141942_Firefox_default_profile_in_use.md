---
title: "Firefox default profile in use"
date: 2006-03-09
forum: General Help
---

### Post by groundpounder on 2006-03-09
My friends 1 yr old hit the reset button on her computer, and now firefox won't start with the default profile, even after a proper shutdown/restart.  I'm assuming there's a firefox process running somewhere, but how do I find & kill it?

---

### Post by aysiu on 2006-03-09
Go to Applications > Accessories > Terminal and type ```
killall firefox
```

---

### Post by groundpounder on 2006-03-09
duh... I should have known that.  Thanks!

---

### Post by aysiu on 2006-03-09
Did it work?

---

### Post by RikoW on 2006-03-10
since you wrote, there was a reset of the computer already, there shouldn't be any firefox process around anymore.

However, what is probably still there is the lock file for the profile. That you can remove my hand. After doing that, firefox should start with the default profile again.

```
> cd
> cd .mozilla/firefox/
> ls
jjtvpk4v.default/  pluginreg.dat  profiles.ini
> cd jjtvpk4v.default/
> ls
bookmarkbackups/  compatibility.ini  extensions.ini   lock@          xpti.dat
bookmarks.bak     compreg.dat        extensions.rdf   mimeTypes.rdf  XUL.mfasl
bookmarks.html    cookies.txt        formhistory.dat  prefs.js*
Cache/            downloads.rdf      history.dat      search.rdf
cert8.db          extensions/        key3.db          secmod.db
chrome/           extensions.cache   localstore.rdf   signons.txt

```

the first ls shows you the profile directories. go to the default one. the second ls shows you, there is a lock file left (hopefully)

```
> rm lock
```

and you should be all set!

Good luck,

               Riko

---

