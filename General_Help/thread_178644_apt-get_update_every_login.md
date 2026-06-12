---
title: "apt-get update every login?"
date: 2006-05-18
forum: General Help
---

### Post by NiTsi on 2006-05-18
I have breezy 5.10.it seems that even though i do "sudo apt-get update" the next time i login it is not kept in memory and when i do it again it begins almost from the start as if it doesn't remember it. Not from the start but I think in particular that it re-updates the repositories from security and maybe from grarchive.
  Does anybody know why this happens?
  I also think that i have noticed it in two different pc's.
  While in my old pc which is with 5.04 hoary it hasn never  happened ](*,)

---

### Post by infoburner on 2006-05-18
apt-get update updates your local package database, so every time you run it it should retreive all the package lists.

i think you might be trying to do apt-get upgrade, which upgrades your packages to the latest versions

---

### Post by sciyoshi on 2006-05-18
When you do apt-get update, it still has to check all the repositories to see if there's been changes. If nothing's changed, it shouldn't take too long though...

Samuel

---

### Post by NiTsi on 2006-05-19
the point is that it takes the same time every time it updates... and it's not little... shouldn't it take secs if you do it every day? it takes me every day about 15-20 min to update the reps with a 56kbps modem....

---

