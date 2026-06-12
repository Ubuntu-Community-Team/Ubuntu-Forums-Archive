---
title: "Are Source Code PPAs Really Needed?"
date: 2012-08-31
forum: General Help
---

### Post by Ubun2to on 2012-08-31
I stumbled into some errors with some of the PPAs I have added (most notably Chrome, which I replaced with Chromium). I have been going into all of my computers, giving each PPA a name that I can actually identify it, and realized I have tons of source code PPAs.
I am not a developer by any means (although I think it would be nice to be able to create apps, I prefer fixing computers and their OSs as opposed to compiling them).
So, do I really need these source code PPAs? I really would like to clean up the list of PPAs if possible-running apt-get update can take up to 5 minutes if my connection is bad, which is also a drain on my productivity.

---

### Post by SlugSlug on 2012-08-31
no - you can remove them and greatly speed up apt-get update :)

---

### Post by 2F4U on 2012-08-31
You would need the source ppa if you want to look into the source or if you intend to compile the package, for example, with different compile flags.

---

### Post by Ubun2to on 2012-08-31
Thanks! I removed the source code PPAs, and now it does it in less than a minute (compared with about 3 minutes before).

---

