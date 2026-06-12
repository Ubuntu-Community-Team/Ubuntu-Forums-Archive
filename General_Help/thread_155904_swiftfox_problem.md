---
title: "swiftfox problem"
date: 2006-04-05
forum: General Help
---

### Post by moon_dog on 2006-04-05
all of a sudden everytime i log in to my yahoo mail the browser just shutsdown.   i don't understand what's going on.  i've tried un installing and re installing swiftfox but it still happens.  only on yahoo though.

---

### Post by moon_dog on 2006-04-06
swift fox also randomly shuts down every now and then.

---

### Post by Thorin on 2006-04-06
Same thing happens here, only on different sites. My guess would be that it has something to do with the way it handles whatever is happening on that site. But it's a small price for the speed methinks.

---

### Post by moon_dog on 2006-04-06
yeah but it didn't do that before.  and it's not even a swiftfox problem cuz i un installed it and it does the same thing with just normal firefox.  i've also tried un installing are re installing firefox, but the problem keeps on occuring :(

---

### Post by Stirling on 2006-04-06
Are you able to reproduce the crashes with a new profile?  Also, are you using the new yahoo mail or the old style?  If you know of any other sites that regularly crash the browser with a clean profile I would like to know which ones.  I seem to remember a bug posting about a crash using the new yahoo mail in Firefox.  I will try to track it down.

---

### Post by Stirling on 2006-04-06
Yes I think I might have found the bug report.

[https://bugzilla.mozilla.org/show_bug.cgi?id=322683](https://bugzilla.mozilla.org/show_bug.cgi?id=322683)

Are you using version 1.5.0.1?  If this is the right bug then it is already fixed for version 1.5.0.2.  If you are using Swiftfox download the 1.8.0 branch build.  That build is pretty much a final build of 1.5.0.2, it just hasn't "officially" been released yet by Mozilla.  If that doesn't fix the problem let me know so I can keep digging.

---

### Post by moon_dog on 2006-04-06
i'm using version 1.5.0.1.  i did a complete un-install (synaptic and apt-get remove, just doing one of them wasn't enough) and re-install.  swiftfox doesn't shutdown anymore in yahoo mail.  i'm not sure which one is the new or old mail.  i use this site : mail.yahoo.com.

actually it wasn't even swiftfox, it was really firefox cuz it kept doing it even when i removed swiftfox.  seems to be doing all right now.  will download 1.5.0.2 asap, thanks for the heads up

---

