---
title: "How can i run 2 instances of firefox..."
date: 2009-10-28
forum: General Help
---

### Post by emigrant on 2009-10-28
hi,
how can i run two instances of firefox simultaniously?,
one with tor running and the other without tor running.
i could have achieved this by using two browsers, but obviously chromium won't remember sessions. and each time i restart the browser id have to re open all the tabs id been browsing.

sugeestions and helps are welcome.

thank you very much.

---

### Post by Anonymousable on 2009-10-28
Using the Profile Manager, you can make multiple profiles which can run seperately, and simultaneously. However, the profile management seems to have stopped working.

I'm not sure if anyone else had that problem.

---

### Post by barthel on 2009-10-28
You might be able to do this with separate profiles (using the -P option for firefox).

Another option might be to use a firefox variant like iceweasel for tor.

---

### Post by lovinglinux on 2009-10-28
Open Firefox Profile Manager and create a new profile:

```
firefox -P -no-remote
```

Then start the new profile from the Profile Manager or run this:

```
firefox -no-remote -P "nameoftheprofile"
```

---

### Post by emigrant on 2009-10-29
thank you very much,
this works...
> **lovinglinux said:**
> Open Firefox Profile Manager and create a new profile:

```
firefox -P -no-remote
```

Then start the new profile from the Profile Manager or run this:

```
firefox -no-remote -P "nameoftheprofile"
```

---

### Post by BramWillemsen on 2009-10-29
Sry wrong post...

---

