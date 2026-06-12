---
title: "Boxee, I don't want to install flash for flash sake"
date: 2010-10-03
forum: General Help
---

### Post by LowSky on 2010-10-03
I installed Boxee on my 64bit install. I had to edit the DEB so it did not install Flash, because Ubuntu still insists on installing the 32bit version which always borks Firefox.

But now I cant run synaptic without getting complaints of broken packages. I just want to blacklist boxee from from annoying the hell out of me, but keep it installed. How do I go about doing that?

---

### Post by mikewhatever on 2010-10-03
Don't know about Boxee, but Ubuntu never insists on installing any kind of Flash player by default. Is the 32bit flash, perhaps the dependency of Boxee?

---

### Post by snowpine on 2010-10-03
It sounds like you did not "edit the DEB" correctly; if you had, it would not list Flash as a dependency, and the package would not show up as "broken" in Synaptic. I would recommend contacting Boxee for assistance, as Boxee is not part of the Ubuntu repositories. :)

---

### Post by LowSky on 2010-10-03
Solved, went to software sources and disabled boxee from there

---

