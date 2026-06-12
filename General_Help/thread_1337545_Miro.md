---
title: "Miro"
date: 2009-11-25
forum: General Help
---

### Post by RedSingularity on 2009-11-25
I am trying to install miro but am running into a few problems that i have never seen.

When i go to the package manager and click to install miro i get this message.

miro:
 Depends: libxine1 but it is not going to be installed
 Depends: libxine1-plugins but it is not going to be installed
 Recommends: libxine1-ffmpeg but it is not going to be installed

I thought the dependencies would be installed for me (thats the whole point of apt-get)

Any ideas on what to do?

---

### Post by e-Gee on 2009-11-25
You installed new libxine1-ffmpeg probably with some app from unstable ppa and if you want to install Miro you will have to remove that package and probably few more apps which use  libxine1-ffmpeg

---

