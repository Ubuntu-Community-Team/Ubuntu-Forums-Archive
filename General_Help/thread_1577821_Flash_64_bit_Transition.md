---
title: "Flash 64 bit Transition"
date: 2010-09-19
forum: General Help
---

### Post by lakerssuperman on 2010-09-19
As Adobe has finally put out a new Flash 64bit beta, I figured I would try it.  Following the instructions over at OMGUbuntu I installed it from this ppa:

sudo add-apt-repository ppa:sevenmachines/flash

It works well and no major issues to report as yet.  However, it seems as though this plugin doesn't save video clips to the /tmp directory.  Does anyone know where it does save them?

---

### Post by Vaphell on 2010-09-19
wow, what you say is true
flash seems to put stuff to ~/.mozilla/firefox/<profile>/Cache

---

### Post by mc4man on 2010-09-19
> flash seems to put stuff to ~/.mozilla/firefox/<profile>/Cache 
Which also means, at least as seen here, that the files are never deleted.
If so, then at some point you're going to want to clean out the cache which depending on usage may get quite large.

(Also don't think there can be any complaints (or thread closures based on legalities ) about copying (moving) these videos considering how they are just left there on your pc.

---

### Post by lakerssuperman on 2010-09-19
Wow, yes, I didn't even think about the legalities.  But at least they are put somewhere as I like having this functionality without having to install plugins to extract the video.  Perhaps this is only a temporary measure for the beta and they will change the location by final release.

---

### Post by lakerssuperman on 2010-09-19
It seems as though each browser uses their own individual cache file for saving videos.  I just looked in the chromium cache and videos played through Chromium save to this location.  However, I don't see where Chrome itself saves too at the moment.chrome/

---

### Post by lakerssuperman on 2010-09-19
FYI, Chrome stores it's content in ~/.cache/google-chrome/Cache

---

