---
title: "thumbs.db"
date: 2009-06-25
forum: General Help
---

### Post by mcgodx on 2009-06-25
Hey all,

I have a hard drive that was once on a Windows machine, and it now will remain on a Ubuntu machine.  Since it was on a Windows computer, there are "thumbs.db" files pretty much everywhere and it is pretty obnoxious.  Anyone know how to delete all the files of a certain name on a drive at one time?

Thanks

Mylan

---

### Post by mcgodx on 2009-06-25
Guess I should have waited a little while.

```
find /directory/ -type f -name "Thumbs.db" -delete
```

Good stuff.

---

