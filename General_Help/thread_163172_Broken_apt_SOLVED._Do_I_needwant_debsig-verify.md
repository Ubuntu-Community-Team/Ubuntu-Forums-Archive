---
title: "Broken apt: SOLVED. Do I need/want debsig-verify?"
date: 2006-04-20
forum: General Help
---

### Post by casfindad on 2006-04-20
Ok, I solved (kinda) the broken apt problem described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=162711"), as well as [this one]("http://www.ubuntuforums.org/showthread.php?t=162593").

The key was googling the error message "debsig: Origin Signature check failed". I found [this advice]("http://lists.debian.org/debian-amd64/2004/07/msg00293.html"), which recommended removing the debsig-verify package. After doing so, I can install packages using apt-get and adept again.

My question now is: do I need or want debsig-verify? I tried re-installing it, and I was immediately back to getting verification errors. A search for debsig-verify in  the forums came up empty.

casfindad

---

